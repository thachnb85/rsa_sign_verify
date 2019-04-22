## Overview
How to sign and verify message using SHA256/RSA

## Dummy data
echo -n "abc" > data.txt

## RSA keys
```
openssl genrsa -out private.pem 2048
openssl rsa -in private.pem -pubout >  public.pem
```

```
cat private.pem
```

```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEA1SU2jzpFxPleVwlMMjz73LMQAzVcJ1l82Jm8/meif4Jhi8Sa
oNPGofzZJE4WOBFf9vTEZERyVuL3/TezABUlMqYqP3djPj27FJWjrc28CbOLQkVh
HeM2EEwJjeZEk2qsUCnDGUze5lpqUPvZKY1URrbv8qTJsBGNC5DFyNIXyiz2o/xK
OgA2kJApwA97h0R5SfvxgpXEkJ5c6kIkCnqm4ec0xdc9aPVxirNquHonCtqEzQP6
FJlvQg87Z5H/BDATcjuBSEs1DqGjZ3tpKm4Exih6OWmeQFUqF3/7zMWCxoG8WZmR
uYtVujB85jclX5550A94qHhczxw4f2aCl3gimQIDAQABAoH/QptecWPEacmDsa82
IHzuOAm890O1iJZubUGdzeKU5UPZN9Q4fgmwCO767F16lArZ8lKLDMpW8M/8ryS4
y03QUgObMDoeyVSBIe2hOK8SE/YHjq4fqzdVrcIVOkK7K1YqguKKFV3wSgv3LVeG
hXWk4HRKh4j3fg3+BZ84L4l35bWUwkjwbUO44H+ywKEVHnMWbBwHIyh6JHmFZ1Zc
OxxBh0QwdF74gP6EnrDprsPgR2JRqesxFrXCGewBhsKaotwvTsl6P0w1HC3ks9FB
fob1QLzvka4HRZsOcQr71eQGsNS1dNRSCdv7WQBhF1tAs7r6fWuIL9eh4VGA7s4m
7BBBAoGBAP/7OespVSZyIUZvp7C1374mJznRnaQ8LN2z2fCpKljKKEQxPAul4OXG
6s0DD3oKqbujt/8y7otyryy4T7IegmnbWDcX+ZCbOShXXf+YjkQ/4mymtkYhtTQV
YRyDfRsPI4O9G2u1U5dVw0HU6AmLePw9tYGC6e/2ABFDy8Fo5fefAoGBANUpMCMw
BC+qhqW1weufsN7AABOzkvXEmPkzqPTDAfJy39ffnQiP/hNmUILppbAPW6w1Vgrb
lPrQZh1AAeIHZKKm+mB6o2MlXt6kPYvFxLRtpXL9h9US/ukOmk+s4nKn01exK6mj
pHqHrhrFWs7XZoNERrIBKJqJRIZt0OIN4ZrHAoGBAL3MuBAucG12OEfyqAK1h/WE
cpdDXkCVQasNHK59r+Fv21VcsCnuz4dv608hUstptppjdR0q1Ybd/RcKfkUSrB3z
PkBzbV8USNgpl4/ZvLrMJ4XqQsJTYfkBVSUANbXnjqyyfe9p3lYaiBF63KWfHZDh
7H/f4rdCzp/+hcidj83/AoGBALHvnupQo73yeFGNxuHcvPVEiwvnI+8afKPRluEy
g8aSU/7NADXslSg2iVCun4u3VkwLfda0c8lm+0bBbpDyoPQRtQGifg8+W9I4gdPS
dCA1Qx4ZOzEHmViMww1tgN467/XMxGjoXF2YMyLPybzOHBnJfcYLp4xQt64Lr4l0
EvZzAoGASzkBmq1d9O5t/0GUHlQFHN4vafqrPEGC5kCBpyczSYoZ65zswGYHNV0S
gYPiTWGnN+6HUPQQ14jOZ7eLpAHlbgzcelZOuCgBfzcmQ2TjG1aGWCuuOuZXNTEW
V2g2rWuHeGvGnwg7KJTYCaYvIUlpbpNFF3K5NOrjWietvUH4UuY=
-----END RSA PRIVATE KEY-----
```

### Open SSL

Generate signature:
```
openssl dgst -sha256 -sign private.pem -out sign_using_openssl data.txt
hexdump signature


0000000 7c e7 8f 44 2a 6e 8d 73 95 68 f1 d5 ed a7 f0 bc
0000010 c6 4a 64 2d 3d 02 b8 c9 04 b7 1b be c7 c0 60 e2
0000020 34 b5 ce ba a5 2e 70 21 4f eb 0e 53 27 7a ba 6b
0000030 0d b8 65 2b 2b 29 4f ad 5d 92 f1 b2 33 1d 94 8f
0000040 cd e9 2f 6e 34 49 13 52 b4 ed 0a 93 2c 5f a0 7a
0000050 78 71 e2 b7 e5 ae 7a 25 dd 20 97 e7 46 85 28 c6
0000060 a6 f4 75 23 66 53 f0 96 b1 55 0f 9b e6 6c 97 52
0000070 47 1d 64 96 68 47 48 aa c4 eb da 1a a3 bb 4b 43
0000080 93 c8 ab 13 00 9b 6c d8 30 ec 09 dd 06 29 ba 71
0000090 c5 ab d5 7c fe d4 bc ed eb 5f 39 b8 2d 45 5d 08
00000a0 c7 d5 33 5b 25 9f a2 c4 39 da 3b 9e 39 ce 9e a7
00000b0 b4 c3 40 a0 6f 71 ba 2c 25 79 a6 cf 93 56 8c ff
00000c0 72 f4 c0 cc 5c 4f f9 7a e6 0e 3c 64 77 a6 72 f8
00000d0 80 b2 bf 62 b2 66 3f 71 89 f5 8b e1 91 32 97 eb
00000e0 60 b2 31 c2 2a d4 35 8d 18 1c 1b c1 42 5f 07 ea
00000f0 a4 bb d9 5c 18 5b 79 ed 6d 55 f4 64 34 7c 07 87
```
Verify signature:
```
openssl dgst -sha256 -verify public.pem -signature sign_using_openssl data.txt
Verified OK
```

### Python using M2Crypto
```
import M2Crypto
import hashlib
rsa = M2Crypto.RSA.load_key("private.pem")
digest = hashlib.new('sha256', 'abc').digest()
open("sig_python_using_m2crypto", "w").write(rsa.sign(digest, "sha256"))
```

```
openssl dgst -sha256 -verify public.pem -signature sig_python_using_m2crypto data.txt
Verified OK
```
### Dart
```
import 'package:encrypt/encrypt.dart';
import 'package:crypto/crypto.dart' as crypto;
import 'package:pointycastle/asymmetric/api.dart';
import 'package:pointycastle/api.dart';

String msg = "abc";
List<int> messageBytes = utf8.encode(msg);

final parser = RSAKeyParser();
final RSAPrivateKey rsaPrivateKey = parser.parse(RSA PRIVATE KEY STRING);

// For Signing
var privParams = new PrivateKeyParameter<RSAPrivateKey>(rsaPrivateKey);
var signer = new Signer("SHA-256/RSA");
signer.init(true, privParams);
Signature sig = signer.generateSignature(messageBytes);

// For Signature verification
var publicExponent = BigInt.parse("65537");
final RSAPublicKey rsaPublicKey = new RSAPublicKey(rsaPrivateKey.modulus, publicExponent);
var pubParams = new PublicKeyParameter<RSAPublicKey>(rsaPublicKey);
var verifier = new Signer("SHA-256/RSA");
verifier.init(false, pubParams);

if (verifier.verifySignature(messageBytes, sig) == false){
  print("Signature verification failed.");
}
```
