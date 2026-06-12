---
title: "Trying to compile a newer version of sooperlooper"
date: 2010-01-09
forum: Multimedia Software
---

### Post by s0l1dsnak3123 on 2010-01-09
Hi guys :D

I'm trying to compile and checkinstall a new version of sooperlooper (the one in the repos is extremely old), however i get this dependancy error (and older version of sooperlooper is currently installed, so i shouldn't get any dependancy errors).

```
snak3@Panther:~/Downloads/sooperlooper-1.6.14$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
OPT_CXXFLAGS is set based on -D_REENTRANT -Os -fomit-frame-pointer -mmmx -msse -mfpmath=sse -pipe -Wall -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE
checking for ranlib... ranlib
checking for --with-macosx-sdk... 
checking for --with-macosx-version-min... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... no
checking for LOSC... configure: error: Package requirements (liblo >= 0.10) were not met:

No package 'liblo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LOSC_CFLAGS
and LOSC_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

snak3@Panther:~/Downloads/sooperlooper-1.6.14$ 
```

Also, it says "checking for JACK... no" when I do have jack installed. I know I have to specify the path, but I'm not sure how. ./configure --help shows:

```

snak3@Panther:~/Downloads/sooperlooper-1.6.14$ ./configure --help
`configure' configures this package to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
			  [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
			  [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --datarootdir=DIR      read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR          read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR          info documentation [DATAROOTDIR/info]
  --localedir=DIR        locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR           man documentation [DATAROOTDIR/man]
  --docdir=DIR           documentation root [DATAROOTDIR/doc/PACKAGE]
  --htmldir=DIR          html documentation [DOCDIR]
  --dvidir=DIR           dvi documentation [DOCDIR]
  --pdfdir=DIR           pdf documentation [DOCDIR]
  --psdir=DIR            ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

System types:
  --build=BUILD     configure for building on BUILD [guessed]
  --host=HOST       cross-compile to build programs to run on HOST [BUILD]
  --target=TARGET   configure for building compilers for TARGET [HOST]

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --disable-optimize       avoid optimizations to allow for gdb debugging.
  --enable-debug    not optimized and includes debug symbols

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-macosx-sdk=PATH  use an OS X SDK at PATH
  --with-macosx-version-min=VER   build binaries which require at least this OS X version
  --with-wxconfig-path=PATH    full path to wx-config to use

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++/Objective C preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CXX         C++ compiler command
  CXXFLAGS    C++ compiler flags
  CPP         C preprocessor
  PKG_CONFIG  path to pkg-config utility
  JACK_CFLAGS C compiler flags for JACK, overriding pkg-config
  JACK_LIBS   linker flags for JACK, overriding pkg-config
  LOSC_CFLAGS C compiler flags for LOSC, overriding pkg-config
  LOSC_LIBS   linker flags for LOSC, overriding pkg-config
  SIGCPP_CFLAGS
              C compiler flags for SIGCPP, overriding pkg-config
  SIGCPP_LIBS linker flags for SIGCPP, overriding pkg-config
  XML_CFLAGS  C compiler flags for XML, overriding pkg-config
  XML_LIBS    linker flags for XML, overriding pkg-config
  SNDFILE_CFLAGS
              C compiler flags for SNDFILE, overriding pkg-config
  SNDFILE_LIBS
              linker flags for SNDFILE, overriding pkg-config
  SAMPLERATE_CFLAGS
              C compiler flags for SAMPLERATE, overriding pkg-config
  SAMPLERATE_LIBS
              linker flags for SAMPLERATE, overriding pkg-config
  RUBBERBAND_CFLAGS
              C compiler flags for RUBBERBAND, overriding pkg-config
  RUBBERBAND_LIBS
              linker flags for RUBBERBAND, overriding pkg-config
  FFTW_CFLAGS C compiler flags for FFTW, overriding pkg-config
  FFTW_LIBS   linker flags for FFTW, overriding pkg-config
  CXXCPP      C++ preprocessor

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

snak3@Panther:~/Downloads/sooperlooper-1.6.14$ 

```

Any help would be much appreciated.

John :)

---

### Post by andrew.46 on 2010-01-10
Hi s0l1dsnak3123,

I suspect the problem is that Ubuntu splits up source packages and you are missing the so-called -dev packages. An easy way to get these packages is to run:

```
sudo apt-get build-dep sooperlooper
```

and this will pull in the required libraries, or more exactly the libraries used by the Ubuntu developers to build their own package of sooperlooper. For this version to succeed under Karmic looks like you also need:

```

sudo apt-get install libfftw3-3 librubberband-dev librubberband2 libvamp-sdk1 \
rubberband-vamp libvamp-hostsdk2 vamp-plugin-sdk libfftw3-dev libwxgtk2.8-dev
```

This enabled compilation but I confess I am unsure if this is a full compilation or more libraries are required. Should get you started though?

Andrew

---

### Post by s0l1dsnak3123 on 2010-01-10
Thanks alot, I have it working now :)

---

### Post by andrew.46 on 2010-01-10
Hi s0l1dsnak3123,

> **s0l1dsnak3123 said:**
> Thanks alot, I have it working now :)

Great news, I was not entirely sure if the extra libraries I described were enough to fully build the program :).

Andrew

---

