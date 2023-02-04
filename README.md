# Checkpoint indexer - adapted for briq contract

## Getting started

This is part of project [sybil-shield](https://github.com/carbonable-labs/sybil-shield) serve as indexer to index events from [briq contract](https://starkscan.co/contract/0x01435498bf393da86b4733b9264a86b58a42b31f8d8b8ba309593e5c17847672)


**Requirements**

- Node.js (>= 16.x.x)
- Docker with `docker-compose`
- Yarn

> You can also use npm, just make sure to replace the subsequent 'yarn' commands with their npm equivalent.

After cloning this project, run the following command to install dependencies:

```bash
yarn # or 'npm install'
```

Next, you'll need a MySQL server running and a connection string available as environment variable `DATABASE_URL`.
You can use `docker-compose` to set up default MySQL server in container:

```bash
docker-compose up -d
```

> For local development, you can create a .env file from the .env.example file and the application will read the values on startup.

Next, start up the server:

```bash
yarn dev # for local development or else `yarn start` for production build.
```

This will expose a GraphQL API endpoint locally at http://localhost:3000. You can easily interact with this endpoint using the graphiql interface by visiting http://localhost:3000 in your browser.

To fetch a list of Transfer's try the following query:

```graphql

# Welcome to Checkpoint. Try running the below example query from
# your defined entity.    
query {
    transfers (
      first: 1000
      # skip: 1000
      orderBy: created_at_block
      orderDirection: asc
    )  {
        id
        from
        to
        token_id
        tx_hash
        created_at
        created_at_block
      
    }
}
```

To learn more about the different ways you can query the GraphQL API, visit the Checkpoint documentation [here](https://docs.checkpoint.fyi/core-concepts/entity-schema).

## License

MIT
