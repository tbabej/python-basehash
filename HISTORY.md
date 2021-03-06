3.0.2 (2015-06-28)
==================

- Modified `setup.py` to no longer read from `README.md` and `HISTORY.md` as it
  was causing errors when installing from PyPi.

3.0.1 (2015-06-19)
==================

- `pip install basehash` giving error. Corrected this in `setup.py`

3.0.0 (2015-06-19)
==================

- Massive overhaul on the primes.py methods. Each method was benchmarked to
  get the best optimization possible.

- Uses [gmpy2](https://gmpy2.readthedocs.org/) if available, otherwise use the 
  baillie_psw primality check and the next_prime methods in primes.py

- `base.hash()` no longer accepts argument `length`. One instance per hash length.

- `base.maximum()`, `base.maximum_value()`, and `base.prime()` have been
  removed. To get maximum hash value, call `base.maximum`. To get the prime used
  call `base.prime`

- `primes.miller_rabin` was removed as it was replaced by `primes.baillie_psw`
  in v1.0.2.

2.2.1 (2015-05-28)
==================

- Implemented [six](https://bitbucket.org/gutworth/six) to allow use of `xrange`
  in Python 2 and `range` in Python 3

2.2.0 (2015-05-14)
==================

- Fixed ussues with python 3.4

2.1.0 (2013-07-24)
==================

- Create custom random alphabets using `basehash.generate_alphabet(alphabet)`.

- BaseHash.base now checks `alphabet` for duplicates using `set`.

2.0.2 (2013-07-10)
==================

- base and baseN now accept a length parameter, defaulted to HASH_LENGTH so that
  baseN.hash(num, length) is set globally, not locally.

2.0.0 (2013-07-07)
==================

- Moved everything to an object. Removed baseN.py files, allows for easier
  configuration of `GENERATOR` and for extending to a custom alphabet.

1.0.7 (2013-07-06)
==================

- There was an issue with hashes sometimes being returned one to two charcters
  shorter than `length`, causing `base.base_unhash` to not function properly. To
  fix this, the hashes are right-padded with `alphabet[0]`.

- Since `0` raises an error inside `primes.invmul`, `base.base_unhash` is unable
  to unhash it. To allow the start of your number sequence to be `0` instead of
  `1`, if needed, hashing `base.base_hash(0, length=6)` will return
  `''.rjust(length, alphabet[0])`.

1.0.6 (2013-06-29)
==================

- Fixed issues with setup.py. First time using a setup.py within a package,
  first time publishing the library outside of GitHub.

1.0.5 (2013-06-28)
==================

- Added nose unittests.

1.0.4 (2013-06-28)
==================

- Added setup.py, LICENSE, HISTORY.rst, and .travis.yaml.

1.0.3 (2013-06-27)
==================

- Added a simple test for `prime < 31` to reduce calculation time.

- Fixed issue of `strong_pseudoprime(n, 3)` giving false results.

1.0.2 (2013-06-27)
==================

- Changed primality test from Miller-Rabin to Baillie-PSW. This algorithm is
  significantly faster.

- Changed determination to use `sqrt(n)` or `isqrt(n)` to an improved version of
  `isqrt(n)`.

- BaseHash is now PEP compliant.

1.0.1 (2013-06-25)
==================

- Changed primality test from Fermat to Miller-Rabin. Improved accuracy on false
  results when it comes to pseudoprimes.

1.0.0 (2013-06-24)
==================

- Released code to GitHub repository python-basehash
  https://github.com/bnlucas/python-basehash

0.0.1 (2013-06-23)
==================

- Initialization
