# myfam
A script helping you maintaining your Tor family members' configuration.

The `MyFamily` configuration parameter in a torrc file contains a list of fingerprints with all family members. Technically one can configure on all its Tor nodes the same string, so every node contains all other nodes' fingerprints as well as its own fingerprint. According to the [manual](https://www.torproject.org/docs/tor-manual.html.en) this won’t hurt. But wouldn't it be cool to get a unique, separate string with each fingerprint of the other family members without the node's own one? This exactly is the very purpose of `myfam`!

With `myfam` you maintain one list of comma separated fingerprints and nicknames with all your nodes in it and let `myfam` generate the unique configuration string per node family member.


## Example
Content of sample.txt:
```
$ cat example/sample.txt 
01ABCDEF604669E636FFD5B503F382A4B7AD6NOT, myTorNode1
ADBCDEFA49573D52A7B6F4A35750F161AAD89NOT, myTorNode2
88CDEFAB980BF6E72092EE690E8C51C0AA4A5NOT, myTorNode3
95DEFABCF23A6C851028C1AA88AD8593F659ENOT, myTorNode4
```

Feed it into `myfam`:

```
$ ./myfam example/sample.txt 
total nicknames 4 and total fingerprint 4

myTorNode1
ADBCDEFA49573D52A7B6F4A35750F161AAD89NOT,88CDEFAB980BF6E72092EE690E8C51C0AA4A5NOT,95DEFABCF23A6C851028C1AA88AD8593F659ENOT

myTorNode2
01ABCDEF604669E636FFD5B503F382A4B7AD6NOT,88CDEFAB980BF6E72092EE690E8C51C0AA4A5NOT,95DEFABCF23A6C851028C1AA88AD8593F659ENOT

myTorNode3
01ABCDEF604669E636FFD5B503F382A4B7AD6NOT,ADBCDEFA49573D52A7B6F4A35750F161AAD89NOT,95DEFABCF23A6C851028C1AA88AD8593F659ENOT

myTorNode4
01ABCDEF604669E636FFD5B503F382A4B7AD6NOT,ADBCDEFA49573D52A7B6F4A35750F161AAD89NOT,88CDEFAB980BF6E72092EE690E8C51C0AA4A5NOT
```

## Usage
```
Usage: ./myfam FILE
```

## Getting started

  0. Download this project as .zip or by cloning it and switch to the unziped directory.
  1. Create a text file with one fingerprint-nickname-combo per line (see `example/sample.txt`)
  2. Run `./myfam <your-text-file>` to get the torrc MyFamily string

## License
This script is licensed under BSD 3-Clause license (see LICENSE.md for more information).
