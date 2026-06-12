---
title: "trying to run shorten shn format in Lucid and having problems"
date: 2010-06-20
forum: Multimedia Software
---

### Post by shantiq on 2010-06-20
[COLOR=Blue]**ok so this is my favourite audio format (please kindly refrain from dissuading me to use it , it is not my question) and it worked fine up to karmic but i spent time today it seems ok**[B]
but then when i run [/B][/COLOR]

```
shorten -h
```or > man shorten[COLOR=Blue]**it simply is not there and neither is is picked up by soundkonverter or pacpl**[/COLOR]

[COLOR=Blue]**if you look at the code below any idea why not?**[/COLOR]



```
shantiq@shantiq-desktop:~$ cd ./shorten-3.6.1
shantiq@shantiq-desktop:~/shorten-3.6.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for main in -lm... yes
configure: checking for headers
checking for ANSI C header files... (cached) yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for inttypes.h... (cached) yes
configure: checking for win32 environment
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
configure: checking for data types
checking for unsigned long... yes
checking size of unsigned long... 4
configure: checking for library functions
checking for strerror... yes
checking for truncate... yes
configure: creating ./config.status
config.status: creating man/Makefile
config.status: creating utils/Makefile
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating Makefile
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands
configure: ready to compile.

shorten is now configured with the following options:

version:  3.6.1
install:  /usr/local/bin

Type 'make' to build shorten.  Afterwards,
type 'make check' to run some verification tests.

shantiq@shantiq-desktop:~/shorten-3.6.1$ make
Making all in man
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/man'
Making all in utils
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/utils'
Making all in src
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/src'
make  all-am
make[2]: Entering directory `/home/shantiq/shorten-3.6.1/src'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/shantiq/shorten-3.6.1/src'
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/src'
Making all in tests
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/tests'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/tests'
make[1]: Entering directory `/home/shantiq/shorten-3.6.1'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1'
shantiq@shantiq-desktop:~/shorten-3.6.1$ make check
Making check in man
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/man'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/man'
Making check in utils
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/utils'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/utils'
Making check in src
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/src'
make  check-am
make[2]: Entering directory `/home/shantiq/shorten-3.6.1/src'
make[2]: Nothing to be done for `check-am'.
make[2]: Leaving directory `/home/shantiq/shorten-3.6.1/src'
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/src'
Making check in tests
make[1]: Entering directory `/home/shantiq/shorten-3.6.1/tests'
make  check-TESTS
make[2]: Entering directory `/home/shantiq/shorten-3.6.1/tests'

=========================  shorten error tests  ==========================

+ Running error tests against mono benchmark files...

shorten: cannot use -e, -k or -i with data on standard input
shorten: for more information use: shorten -h
shorten: cannot use -e, -k or -i with data on standard input
shorten: for more information use: shorten -h
shorten: cannot use -e, -k or -i with data on standard input
shorten: for more information use: shorten -h
shorten: will not input data from a tty
shorten: for more information use: shorten -h
shorten: will not input data from a tty
shorten: for more information use: shorten -h
shorten: will not input data from a tty
shorten: for more information use: shorten -h
shorten: will not output data to a tty
shorten: for more information use: shorten -h
shorten: will not output data to a tty
shorten: for more information use: shorten -h
shorten: missing seek table filename for -S
shorten: for more information use: shorten -h
shorten: number of bytes to copy must be positive
shorten: for more information use: shorten -h
shorten: block size must be greater than zero
shorten: for more information use: shorten -h
shorten: number of channels must be greater than zero
shorten: for more information use: shorten -h
shorten: number of bytes to discard must be positive
shorten: for more information use: shorten -h
shorten: number of blocks for mean estimation must be positive
shorten: for more information use: shorten -h
shorten: Useful signal to noise ratios are positive
shorten: for more information use: shorten -h
shorten: linear prediction order must be in the range 0 ... 64
shorten: for more information use: shorten -h
shorten: linear prediction order must be in the range 0 ... 64
shorten: for more information use: shorten -h
shorten: quantisation level must be positive
shorten: for more information use: shorten -h
shorten: unknown file type: bad
shorten: for more information use: shorten -h
shorten: currently supported versions are in the range 1 ... 3
shorten: for more information use: shorten -h
shorten: currently supported versions are in the range 1 ... 3
shorten: for more information use: shorten -h
shorten: -k, -s and -S can only be used on shorten files
shorten: for more information use: shorten -h
shorten: -k, -s and -S can only be used on shorten files
shorten: for more information use: shorten -h
shorten: -k, -s and -S can only be used on shorten files
shorten: for more information use: shorten -h
shorten: cannot use -s with -S
shorten: for more information use: shorten -h
shorten: cannot use -e with -i
shorten: for more information use: shorten -h
shorten: cannot use -e with -k
shorten: for more information use: shorten -h
shorten: cannot use -i with -k
shorten: for more information use: shorten -h
shorten: cannot use -e with -x
shorten: for more information use: shorten -h
shorten: cannot use -i with -x
shorten: for more information use: shorten -h
shorten: cannot use -x with -k
shorten: for more information use: shorten -h
shorten: cannot use -x with -s
shorten: for more information use: shorten -h
shorten: cannot use -x with -S
shorten: for more information use: shorten -h
shorten: cannot use -k with -s
shorten: for more information use: shorten -h
shorten: cannot use -k with -S
shorten: for more information use: shorten -h
shorten: the predictor order must be less than the block size
shorten: for more information use: shorten -h
shorten: the -u flag is only applicable to ulaw coding
shorten: for more information use: shorten -h
shorten: too many filenames
shorten: for more information use: shorten -h
shorten: EOF on input when discarding header
shorten: for more information use: shorten -h
shorten: EOF on input when discarding header
shorten: for more information use: shorten -h
shorten: file 'seekable.shn' already contains seek information
shorten: for more information use: shorten -h
shorten: file 'test.shn' does not contain seek information
shorten: for more information use: shorten -h
shorten: could not open file 'missing.wav' for input
shorten: for more information use: shorten -h
shorten: could not open file 'missing.shn' for input
shorten: for more information use: shorten -h
shorten: input file is not a valid RIFF WAVE file
shorten: for more information use: shorten -h

+ Running error tests against stereo benchmark files...

shorten: cannot use -e, -k or -i with data on standard input
shorten: for more information use: shorten -h
shorten: cannot use -e, -k or -i with data on standard input
shorten: for more information use: shorten -h
shorten: cannot use -e, -k or -i with data on standard input
shorten: for more information use: shorten -h
shorten: will not input data from a tty
shorten: for more information use: shorten -h
shorten: will not input data from a tty
shorten: for more information use: shorten -h
shorten: will not input data from a tty
shorten: for more information use: shorten -h
shorten: will not output data to a tty
shorten: for more information use: shorten -h
shorten: will not output data to a tty
shorten: for more information use: shorten -h
shorten: missing seek table filename for -S
shorten: for more information use: shorten -h
shorten: number of bytes to copy must be positive
shorten: for more information use: shorten -h
shorten: block size must be greater than zero
shorten: for more information use: shorten -h
shorten: number of channels must be greater than zero
shorten: for more information use: shorten -h
shorten: number of bytes to discard must be positive
shorten: for more information use: shorten -h
shorten: number of blocks for mean estimation must be positive
shorten: for more information use: shorten -h
shorten: Useful signal to noise ratios are positive
shorten: for more information use: shorten -h
shorten: linear prediction order must be in the range 0 ... 64
shorten: for more information use: shorten -h
shorten: linear prediction order must be in the range 0 ... 64
shorten: for more information use: shorten -h
shorten: quantisation level must be positive
shorten: for more information use: shorten -h
shorten: unknown file type: bad
shorten: for more information use: shorten -h
shorten: currently supported versions are in the range 1 ... 3
shorten: for more information use: shorten -h
shorten: currently supported versions are in the range 1 ... 3
shorten: for more information use: shorten -h
shorten: -k, -s and -S can only be used on shorten files
shorten: for more information use: shorten -h
shorten: -k, -s and -S can only be used on shorten files
shorten: for more information use: shorten -h
shorten: -k, -s and -S can only be used on shorten files
shorten: for more information use: shorten -h
shorten: cannot use -s with -S
shorten: for more information use: shorten -h
shorten: cannot use -e with -i
shorten: for more information use: shorten -h
shorten: cannot use -e with -k
shorten: for more information use: shorten -h
shorten: cannot use -i with -k
shorten: for more information use: shorten -h
shorten: cannot use -e with -x
shorten: for more information use: shorten -h
shorten: cannot use -i with -x
shorten: for more information use: shorten -h
shorten: cannot use -x with -k
shorten: for more information use: shorten -h
shorten: cannot use -x with -s
shorten: for more information use: shorten -h
shorten: cannot use -x with -S
shorten: for more information use: shorten -h
shorten: cannot use -k with -s
shorten: for more information use: shorten -h
shorten: cannot use -k with -S
shorten: for more information use: shorten -h
shorten: the predictor order must be less than the block size
shorten: for more information use: shorten -h
shorten: the -u flag is only applicable to ulaw coding
shorten: for more information use: shorten -h
shorten: too many filenames
shorten: for more information use: shorten -h
shorten: EOF on input when discarding header
shorten: for more information use: shorten -h
shorten: EOF on input when discarding header
shorten: for more information use: shorten -h
shorten: file 'seekable.shn' already contains seek information
shorten: for more information use: shorten -h
shorten: file 'test.shn' does not contain seek information
shorten: for more information use: shorten -h
shorten: could not open file 'missing.wav' for input
shorten: for more information use: shorten -h
shorten: could not open file 'missing.shn' for input
shorten: for more information use: shorten -h
shorten: input file is not a valid RIFF WAVE file
shorten: for more information use: shorten -h

PASS: test-errors.sh

========================  General shorten tests  =========================

+ Running general shorten tests against mono benchmark files...

  + Checking wav test files...
  + Checking aiff test files...

+ Running general shorten tests against stereo benchmark files...

  + Checking wav test files...
  + Checking aiff test files...

PASS: test-general.sh

=======================  shorten seek table tests  =======================

+ Running seek table tests against mono benchmark files...

creating seek table file: 'seektest.skt'
creating seek table file: 'seektest.skt'
creating seek table file: 'nametest.ext.skt'
appending seek table to 'seektest.shn'
creating seek table file: 'stdin.skt'
creating seek table file: 'stdin.skt'
appending seek table to 'seektest.shn'
appending seek table to 'test.shn'
removing seek table from file 'seekable.shn'

+ Running seek table tests against stereo benchmark files...

creating seek table file: 'seektest.skt'
creating seek table file: 'seektest.skt'
creating seek table file: 'nametest.ext.skt'
appending seek table to 'seektest.shn'
creating seek table file: 'stdin.skt'
creating seek table file: 'stdin.skt'
appending seek table to 'seektest.shn'
appending seek table to 'test.shn'
removing seek table from file 'seekable.shn'

PASS: test-seek.sh
==================
All 3 tests passed
==================
make[2]: Leaving directory `/home/shantiq/shorten-3.6.1/tests'
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1/tests'
make[1]: Entering directory `/home/shantiq/shorten-3.6.1'
make[1]: Nothing to be done for `check-am'.
make[1]: Leaving directory `/home/shantiq/shorten-3.6.1'
shantiq@shantiq-desktop:~/shorten-3.6.1$ shorten -h
No command 'shorten' found, did you mean:
 Command 'shorter' from package 'lisaac' (universe)
shorten: command not found
shantiq@shantiq-desktop:~/shorten-3.6.1$ cd ../
shantiq@shantiq-desktop:~$ shorten -h
No command 'shorten' found, did you mean:
 Command 'shorter' from package 'lisaac' (universe)
shorten: command not found
shantiq@shantiq-desktop:~$
```

---

### Post by mc4man on 2010-06-20
Why don't you go ahead and install after your make?

Otherwise it's in the shorten-3.6.1/src directory. (-h and man only w/ install

Attached full build, install and -h log to compare if need be

---

### Post by shantiq on 2010-06-21
[B][COLOR="Blue"]thank you very much mc4man

the problem was that i read the Install document wrong

and that I missed the basic ```
sudo make install
```    DER !

i was reading instructions and forgot the basics

i ran


```
./configure
```   ```
make
```   then i finished with the ```
make check
```


and forgot stage 4   ```
sudo make install
```

and the instructions were clear

> [COLOR="Black"][SIZE="1"]The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.

     Running `configure' might take a while.  While running, it prints
     some messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.[/SIZE][/COLOR]


So a big thank you for your time  :p:p:p

a computer without shorten is just not the same for me ( i am a huge fan of its clarity )

I realize it now plays in audacious 2.3 in the Lucid repo too with the native sndfile plugin (i think)
and off course in xmms

also in gxine and totem

any other programs you might be aware of ?



[/COLOR][/B]

---

### Post by mc4man on 2010-06-21
> any other programs you might be aware of ?
If meaning playback I'd say pretty much any player except vlc

---

### Post by shantiq on 2010-06-21
**[COLOR="Blue"]shame about vlc no cuefiles and no shorten and yet such a great program:p[/COLOR]**

---

