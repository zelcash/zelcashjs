# zelcashjs
Dead simple and easy to use JavaScript based Zelcash library. Inspired by [pybitcointools](https://github.com/vbuterin/pybitcointools)

# Getting started (Dev)
```bash
git clone https://github.com/TheTrunk/zelcashjs.git
cd zelcashjs
yarn install
yarn build

# Dev flow
flow status
yarn build
yarn test
```

# Example usage
```javascript
var zelcash = require('zelcashjs')

var priv = zelcashjs.address.mkPrivKey('chris p. bacon, defender of the guardians')
// 2c3a48576fe6e8a466e78cd2957c9dc62128135540bbea0685d7c4a23ea35a6c

var privWIF = zelcashjs.address.privKeyToWIF(priv)
// 5J9mKPd531Tk4A73kKp4iowoi6EvhEp8QSMAVzrZhuzZkdpYbK8

var pubKey = zelcashjs.address.privKeyToPubKey(priv)
// 048a789e0910b6aa314f63d2cc666bd44fa4b71d7397cb5466902dc594c1a0a0d2e4d234528ff87b83f971ab2b12cd2939ff33c7846716827a5b0e8233049d8aad

var zAddr = zelcashjs.address.pubKeyToAddr(pubKey)
// t1aYp69J595Rhaof2AEFuEvJjLWVboddB2x

// To create and sign a raw transaction. This section is no longer valid for v4 transaction. Please use https://github.com/zelcash/bitgo-utxo-library for transaction construction
var txobj = zelcashjs.transaction.createRawTx([{txid: '196173ec34d22a52cc689a21d01dd33b633671cbe1141e7e66240c7f3b4ccf7b', vout: 0}], [{address: 't1aYp69J595Rhaof2AEFuEvJjLWVboddB2x', satoshis: 100000}])
// zelcashjs.transaction.serializeTx(txobj)
// 01000000017bcf4c3b7f0c24667e1e14e1cb7136633bd31dd0219a68cc522ad234ec7361190000000000ffffffff01a0860100000000003f76a914da46f44467949ac9321b16402c32bbeede5e3e5f88ac205230ff2fd4a08b46c9708138ba45d4ed480aed088402d81dce274ecf01000000030b2b02b400000000

var tx0 = zelcashjs.transaction.signTx(txobj, 0, '2c3a48576fe6e8a466e78cd2957c9dc62128135540bbea0685d7c4a23ea35a6c')
// zelcashjs.transaction.serializeTx(tx0)
// 01000000017bcf4c3b7f0c24667e1e14e1cb7136633bd31dd0219a68cc522ad234ec736119000000008b483045022100b69baff0eb5570fd8ddda7b180463035d47eb3b1c07a808a68085fd58e9e22b102202eb3983a2137af4f8c3967b3c6c16c024ad952a712ab92b8911a8797f1864d3d0141048a789e0910b6aa314f63d2cc666bd44fa4b71d7397cb5466902dc594c1a0a0d2e4d234528ff87b83f971ab2b12cd2939ff33c7846716827a5b0e8233049d8aadffffffff01a0860100000000003f76a914da46f44467949ac9321b16402c32bbeede5e3e5f88ac205230ff2fd4a08b46c9708138ba45d4ed480aed088402d81dce274ecf01000000030b2b02b400000000

// You can now do zelcash-cli sendrawtransaction `SERIALIZED_TRANSACTION`
```
