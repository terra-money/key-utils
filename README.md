# Terra Key Utils

This library contains several utilities related to keys used by Terra official tools.

## Contents

### Keystore

Utilities for storing keys as an encrypted string (used for mnemonics).

```ts
import { encrypt, decrypt } from "@terra-money/key-utils/keystore"

const encrypted = encrypt("mnemonic", "password")
const decrypted = decrypt(encrypted, "password")

// decrypted === "mnemonic"
```

### Mnemonic

Utilities for restoring mnemonics.

```ts
import {
  validateMnemonic,
  getMnemonicKeys
} from "@terra-money/key-utils/mnemonic"

const test1 =
  "satisfy adjust timber high purchase tuition stool faith fine install that you unaware feed domain license impose boss human eager hat rent enjoy dawn"

const wrong =
  "symbol force gallery make bulk round subway violin worry mixture penalty kingdom"
// should be true
validateMnemonic(test1)
// should be false (only 12 words)
validateMnemonic(test2)

// get assets
getMnemonicKeys(test1, {
  chainID: "columbus-4",
  URL: "https://lcd.terra.dev"
}).then(keys => console.log(keys[118].assets, keys[330].assets))
```
