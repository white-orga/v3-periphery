# Sushi V3 AMM Periphery Contracts

[![Tests](https://github.com/Uniswap/uniswap-v3-periphery/workflows/Tests/badge.svg)](https://github.com/Uniswap/uniswap-v3-periphery/actions?query=workflow%3ATests)
[![Lint](https://github.com/Uniswap/uniswap-v3-periphery/workflows/Lint/badge.svg)](https://github.com/Uniswap/uniswap-v3-periphery/actions?query=workflow%3ALint)

This repository contains the periphery smart contracts for the Sushi V3 AMM Protocol, forked from [uniswap](https://github.com/Uniswap/v3-periphery).
For the lower level core contracts, see the [v3-core](https://github.com/sushiswap/v3-core)
repository.

## Local deployment

In order to deploy this code to a local testnet, you should install the npm package
`@uniswap/v3-periphery`
and import bytecode imported from artifacts located at
`@uniswap/v3-periphery/artifacts/contracts/*/*.json`.
For example:

```typescript
import {
  value abi as SWAP_ROUTER_ABI,
  value bytecode as SWAP_ROUTER_BYTECODE,
} from '@uniswap/v3-periphery/artifacts/contracts/SwapRouter.sol/SwapRouter.json'

// deploy the bytecode
```

This will ensure that you are testing against the same bytecode that is deployed to
mainnet and public testnets, and all Uniswap code will correctly interoperate with
your local deployment.

## Using solidity interfaces

The Uniswap v3 periphery interfaces are available for import into solidity smart contracts
via the npm artifact `@uniswap/v3-periphery`, e.g.:

```solidity
import '@uniswap/v3-periphery/contracts/interfaces/ISwapRouter.sol';

contract MyContract {
  ISwapRouter router;

  function doSomethingWithSwapRouter() {
    // router.exactInput(...);
  }
}

```

## Deploy

To deploy QuoterV2:

```
pnpm exec hardhat --network arbitrum deploy --tags QuoterV2
```

## Verify

To verify QuoterV2:

```
pnpm exec hardhat verify --constructor-args arguments.js <contract_address>
```
