# PoolTogether Generic Minimal Proxy Factory

[![Coverage Status](https://coveralls.io/repos/github/pooltogether/pooltogether-proxy-factory/badge.svg?branch=master)](https://coveralls.io/github/pooltogether/pooltogether-proxy-factory?branch=master)

[![CircleCI](https://circleci.com/gh/pooltogether/pooltogether-proxy-factory.svg?style=svg)](https://circleci.com/gh/pooltogether/pooltogether-proxy-factory)

PoolTogether uses the [EIP-1167](https://eips.ethereum.org/EIPS/eip-1167) Minimal Proxy Factory throughout its contracts.
This repo provides this contract pattern as an [npm package](https://www.npmjs.com/package/@pooltogether/pooltogether-proxy-factory) for use in other repo's deployment scripts.

# Usage
Add package to repo using:
`yarn add @pooltogether/pooltogether-proxy-factory`

Using hardhat and ethers.js, add the GenericProxyFactory singleton for the network of choice under the `namedAccounts` in your `hardhat.config.js`.

Deploy a new Proxy Contract: 
```javascript
    let { genericProxyFactoryAddress } = await getNamedAccounts()
    genericProxyFactoryContract = await ethers.getContractAt("GenericProxyFactory", genericProxyFactoryAddress)

    // deploy using create
    const implementationAddress = "<address>"
    const dataToCallOnNewProxy = "0x"

    const newProxyContractResult = await genericProxyFactory.create(implementationAddress, dataToCallOnNewProxy)

```

# Installation
Install the repo and dependencies by running:
`yarn`

## Deployment
These contracts can be deployed to a network by running:
`yarn deploy <networkName>`

# Testing
Run the unit tests locally with:
`yarn test`

## Coverage
Generate the test coverage report with:
`yarn coverage`