# Zero-Knowledge Circuit

This document offers an overview of a custom zero-knowledge circuit developed using the Circom language. Named `Multiplier2`, this circuit exemplifies the creation of logic gates and their connections to enable custom computations. This framework allows for the generation of zero-knowledge proofs for specific computations while ensuring the privacy of input values.

## Installation
To install dependencies, execute:
```
npm install
```

## Compilation
Compile the circuit using the following command:
```
npx hardhat circom
```
This action generates the **out** file containing circuit intermediaries and produces the **MultiplierVerifier.sol** contract.

## Circuit Signals
- **Input signals:**
  - `a`: Denotes the first input signal
  - `b`: Denotes the second input signal
- **Intermediate signals:**
  - `x`: Holds the result of the AND operation between `a` and `b`
  - `y`: Holds the result of the NOT operation on `b`
- **Output signal:**
  - `Q`: Represents the output signal reflecting the multiplication result of `a` and `b`

The circuit comprises the following components:
1. **AND Gate (`andG`):** Computes the logical AND of inputs `A` and `B`, storing the output in the intermediate signal `x`.
2. **NOT Gate (`notG`):** Computes the logical NOT of input `B`, storing the output in the intermediate signal `y`.
3. **OR Gate (`orG`):** Computes the logical OR of the intermediate signals `x` and `y`, resulting in the final output signal `Q`.

## Logic Gates Templates
These templates define the logic for the `AND`, `NOT`, and `OR` gates, respectively. Each gate processes input signals to produce an output signal based on the defined logic.

## Proving and Deploying
Execute the command:
```
npx hardhat run scripts/deploy.ts
```
This script performs the following tasks:
1. Sets up the `MultiplierVerifier.sol` contract.
2. Utilizes `generateProof()` to create a proof using circuit intermediaries.
3. Generates calldata using `generateCallData()`.
4. Invokes `verifyProof()` on the verifier contract using calldata.

With just two commands, you can compile a Zero-Knowledge Proof, generate a proof, deploy a verifier, and validate the proof seamlessly. 🎉

## Authors

- Satya N 

## License

This project is licensed under the MIT License - see the LICENSE.md file for details