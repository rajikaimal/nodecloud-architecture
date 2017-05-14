# nodecloud-architecture

POC for NodeCloud using different design patterns

## Install

```
$ git clone https://github.com/rajikaimal/nodecloud-architecture
$ cd nodecloud-architecture
$ yarn install
```

```js
const nodeCloud = require('nodecloud');
const config = require('./config');

// AWS
const ncAWS = nodeCloud.getProvider('aws');
const awsStorage = ncAWS({ key: config.aws.S3, service: 'S3' });

awsStorage.createStorage({ Bucket: 'MyBucket', Body: 'Hello !' })
	.then(res => {
		console.log(`All done ! ${res}`);
	})
	.catch(err => {
		console.log(`Oops something happened ${err}`);
	})

// Google cloud platform
const ncGoogle = nodeCloud.getProvider('google');
const googleStorage = ncGoogle({ key: config.google.storage, service: 'Storage' });

googleStorage.createStorage({ projectId: 'grape-spaceship-123' })
googleStorage.createStorage({ Bucket: 'MyBucket' })
	.then(res => {
		console.log(`All done ! ${res}`);
	})
	.catch(err => {
		console.log(`Oops something happened ${err}`);
	})
```
