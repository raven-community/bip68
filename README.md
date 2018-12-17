# bip68

A [BIP68](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki) relative lock-time encoding library.


## Example
``` javascript
let bip68 = require('bip68')

bip68.encode({ seconds: 2048 })
// => 0x00400004

bip68.encode({ seconds: 102 })
// => TypeError: Expected Number seconds as a multiple of 512 (as per the BIP)

bip68.encode({ blocks: 54 })
// => 0x00000036

bip68.encode({ blocks: 200 })
// => 0x000000c8

bip68.decode(0x03ffffff)
// => { seconds: 33553920 }

bip68.decode(0x0100fffe) // safely ignores extension bits
// => { blocks: 65534 }

bip68.decode(0xffffffff) // final sequence
// => {}
```


## LICENSE [ISC](LICENSE)
