# Cardano NFT

A project to mint "true" NFT in Cardano. For "true" NFT, it means there is only ONE token under a unique policy-ID. 

Broadly speaking, if you want to create NFTs in Cardano, the first thing you need to do would be to generate a unique policy-ID, then with this policy-ID you can mint the NFT. In this sense, policy-ID is quite similar to contract address in EVM-based blockchains. The major difference is in Cardano you can generate this unique policy-ID completely off-chain because Cardano supports native assets. 

For now, this question is how we can make sure there is only ONE token allowed under a policy-ID? We can define a timestamp after which all minting action will be disallowed. In theory, you can always just mint one token, then "wait" until it gets past that timestamp. For other, they can always look up your policy-ID to see if there is such timestamp being defined. But that would be too much a hassle to do that. There must be a better way to do that.

It can be achieved by using plutus script to mint true NFT. The idea is to put something unique as the input and wrap it up as singleton. How do we do that? With UTXOs model, that is very easy. Since by default every UTXO is unique, we can simply use one of our UTXOs (it doesn't matter which one) to make sure we have that uniqueness. In that way, even with the same asset name, we can guarantee that the output will be unique.
