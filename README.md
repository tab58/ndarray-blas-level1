# ndarray-blas-level1

[![Build Status](https://travis-ci.org/scijs/ndarray-blas-level1.svg?branch=master)](https://travis-ci.org/scijs/ndarray-blas-level1) [![npm version](https://badge.fury.io/js/ndarray-blas-level1.svg)](http://badge.fury.io/js/ndarray-blas-level1)  [![Dependency Status](https://david-dm.org/scijs/ndarray-blas-level1.svg)](https://david-dm.org/scijs/ndarray-blas-level1)

[BLAS Level 1 operations](http://www.netlib.org/blas/) for [ndarrays](https://github.com/scijs/ndarray)

*A quick note on why this exists*: The goal is not to reinvent the wheel. There are lots of implementations of BLAS out there. Even for JS. There's a [nodejs wrapper for LAPACK](https://www.npmjs.com/package/lapack). Depending on what you need, maybe you should use that. The goal of this is to bring standardized BLAS operations to [ndarrays](https://github.com/scijs/ndarray) so that algorithms can be made as future-resistant as possible by writing them in terms of standardized, easily-translatable operations.

## Usage

This library implements the basic vector operations of the Level 1 Basic Linear Algebra Subprograms (BLAS). Many of these functions are also implemented in [ndarray-ops](https://github.com/scijs/ndarray-ops)—which also has functions that are not included in BLAS. So the right answer is probably some blend of the two. This library exists mainly to frame things in a relatively standard, coherent framework.

*NB: This library performs no checks to ensure you're only passing one-dimensional vectors. It simply iterates across the first dimension of the array, so if you pass it higher-dimensional arrays, don't expect a meaningful result.*

| Function | Operation | Description |
| -------- | --------- | ----------- |
| `swap(x,y)` | <img alt="x &bsol;leftrightarrow y" valign="middle" src="images/x-leftrightarrow-y-9aed41cf97.png" width="57" height="16.5"> | Swap the elements of x and y |
| `scal(alpha,x)` | <img alt="x &bsol;leftarrow &bsol;alpha x" valign="middle" src="images/x-leftarrow-alpha-x-daa7a2db38.png" width="71" height="13"> | Multiple vector x by scalar alpha |
| `copy(x,y)` | <img alt="y &bsol;leftarrow x" valign="middle" src="images/y-leftarrow-x-dc4dfb7fd0.png" width="57" height="16.5"> | Copy x into y |
| `axpy(alpha, x, y)` | <img alt="y &bsol;leftarrow &bsol;alpha x &plus; y" valign="middle" src="images/y-leftarrow-alpha-x-y-812ce8de82.png" width="105" height="19.5"> | Multiple x by alpha and add it to y |
| `cpsc(alpha, x, y)` | <img alt="y &bsol;leftarrow &bsol;alpha x" valign="middle" src="images/y-leftarrow-alpha-x-bc5d06c8ea.png" width="70" height="16.5"> | Multiply x by alpha and assign it to y |
| `dot(x,y)` | <img alt="dot &bsol;leftarrow x&Hat;T y" valign="middle" src="images/dot-leftarrow-xt-y-25cde5531d.png" width="97" height="25"> | Calculate the inner product of x and y. |
| `nrm2(x)` | <img alt="nrm2 &bsol;leftarrow &vert;&vert;x&vert;&vert;&lowbar;2" valign="middle" src="images/nrm2-leftarrow-x_2-75057a8787.png" width="126.5" height="24">| Calculate the 2-norm of x |
| `asum(x)` | <img alt="asum &bsol;leftarrow &vert;&vert;x&vert;&vert;&lowbar;1" valign="middle" src="images/asum-leftarrow-x_1-ae4c1bf200.png" width="126.5" height="24"> | Calculate the 1-norm of x |
| `iamax(x)` |  <img alt="&bsol;underset&lcub;i&rcub; &lcub;&bsol;mathrm&lcub;argmax&rcub;&rcub; &vert;x&lowbar;i&vert;" valign="middle" src="images/underseti-mathrmargmax-x_i-2aaceffdc3.png" width="98" height="37.5"> | the argmax of x |

## Example

Usage should be pretty straightforward. There aren't really any options or variations.

```javascript
var blas1 = require('ndarray-blas-level1');

var x = ndarray([1,2,3]);
var y = ndarray([3,4,5]);

blas1.axpy( 2, x, y );
```





## Credits
(c) 2015 Ricky Reusser. MIT License