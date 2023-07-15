# Ray Dex DAO Subgraphs

Subgraph for Delegate and Token Holders on PulseChain.

### Setup

```
# Install dependencies (yarn or npm)
$ yarn or npm install

# Generate types constants
$ yarn or npm run codegen

# build subgraph
$ yarn or npm run build

# create local subgraph
$ yarn or npm run create-local

# deploy local subgraph
$ yarn or npm run deploy-local

```

### (README)

Deliver analytics & historical data for DAO holders.
The Graph exposes a GraphQL endpoint to query the events and entities within the RayDex ecosytem.

## Example

Query the top 10 token holders:

```graphql
{
	tokenHolders(first: 10) {
		id
		tokenBalance
		delegate {
			id
		}
	}
	delegates(first: 10) {
		id
		delegatedVotes
		numDelegators
	}
}
```

## Schema

```graphql
type TokenHolder @entity {
	"Address of this TokenHolder"
	id: ID!

	"Delegate entity that this TokenHolder has delegated their vote weight to"
	delegate: Delegate

	"Number of tokens this TokenHolder has"
	tokenBalance: BigDecimal!
}
```
