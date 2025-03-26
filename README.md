# MongoDB

We're going to get started with MongoDB today, using MongoDB Atlas. MongoDB Atlas is a cloud-based database service that makes it easy to deploy and manage MongoDB clusters.  
  
We'll start by opening up the [docs](docs.atlas.mongodb.com) and:  
  * Create an account
  * Create a cluster
  * Connect to the Cluster  
 
  
```js
const { MongoClient, ServerApiVersion } = require('mongodb');
const username = "<MYUSERNAME>";
const db_password = "<MYPASSWORD>";
const uri = `mongodb+srv://${username}:${db_password}$@cluster1.soeglnr.mongodb.net/?appName=Cluster1$`;
// Create a MongoClient with a MongoClientOptions object to set the Stable API version
const client = new MongoClient(uri, {
  serverApi: {
    version: ServerApiVersion.v1,
    strict: true,
    deprecationErrors: true,
  }
});
async function run() {
  try {
    // Connect the client to the server	(optional starting in v4.7)
    await client.connect();
    // Send a ping to confirm a successful connection
    await client.db("admin").command({ ping: 1 });
    console.log("Pinged your deployment. You successfully connected to MongoDB!");
  } finally {
    // Ensures that the client will close when you finish/error
    await client.close();
  }
}
run().catch(console.dir);
```

If all goes well, you should be able to see
```
Pinged your deployment. You successfully connected to MongoDB!
```

Make sure to install mongodb if you need to:

```
npm install mongodb
npm run app.js
```

