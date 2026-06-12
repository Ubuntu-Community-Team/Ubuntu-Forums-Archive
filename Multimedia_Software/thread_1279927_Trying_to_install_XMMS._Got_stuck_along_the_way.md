---
title: "Trying to install XMMS. Got stuck along the way"
date: 2009-10-01
forum: Multimedia Software
---

### Post by IAmNoodle on 2009-10-01
Hi

I'm part-way through following instructions on how to install XMMS via the terminal, and I've hit a problem. I still don't know a thing about how to use Linux or the terminal, so my apologies if I'm missing the obvious.

So far, I'm at ```
./configure --prefix=/usr
``` on step 3 of the guide [http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html) and the terminal has spat out the folowing:

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking whether assembler supports --noexecstack option...     .section    .note.GNU-stack,"",@progbits
yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

What should I do now?

---

### Post by lloyd_b on 2009-10-01
```
sudo apt-get install libglib1.2-dev libgtk1.2-dev
```You're missing the glib1.2 libraries/development files.  You'll also need the gtk1.2 libraries and dev files, so I've included that package as well.

Don't be surprised if it fails again, with another missing dependency - this is pretty common when building from source.

Note: If you're just trying to get something with the look/feel of XMMS, try Audacious (it's in the repositories, so no compiling required).

Lloyd B.

---

### Post by Yellow Pasque on 2009-10-01
You seem to have skipped step 1 :P

---

### Post by IAmNoodle on 2009-10-16
Ok, I've come back to this. I downloaded what lloyd gave, and got as far as I have done before, but

```
# ./configure --prefix=/usr
```
give me this:
> configure: error: invalid variable name: ~prefix


Once again, can anyone help me with what I need to do?

---

### Post by IAmNoodle on 2009-10-16
Anyone able to help? even if it's just someone telling me what prefix should be

---

### Post by IAmNoodle on 2009-10-21
Last bump before I give this one up

---

### Post by blazk on 2009-10-27
Hi,
./configure --prefix=/usr  should definitely work, the error looks strange...

Anyway, you can invoke ./configure without any options, so the default prefix will be used (/usr/local). Setting it to /usr is probably not good idea - it will pollute Ubuntu system directories.

---

### Post by AutoStatic on 2009-10-27
Or you could try this PPA: [https://launchpad.net/~punischdude/+archive/ppa](https://launchpad.net/~punischdude/+archive/ppa)

---

### Post by Uncle Spellbinder on 2009-10-27
Or, XMMS2 is in the Karmic repos.

---

### Post by IAmNoodle on 2009-10-27
Hi guys. Thanks for the replies. I've found a great alternative that isn't in the ubuntu repositories, and I'm now using Songbird.

---

### Post by blazk on 2009-10-27
> **AutoStatic said:**
> Or you could try this PPA: [https://launchpad.net/~punischdude/+archive/ppa](https://launchpad.net/~punischdude/+archive/ppa)

I dind't try it, but I'd expect problem installing it in Karmic - xmms depends on glib1 and gtk1 libraries which are no longer in repositories. They can be compiled from source:

build-essential and xorg-dev packages must be installed first
```
sudo apt-get install build-essential xorg-dev
```


Installing glib1:
```
wget http://ftp.gnome.org/Public/gnome/sources/glib/1.2/glib-1.2.10.tar.gz
tar zxvf glib-1.2.10.tar.gz
cd glib-1.2.10
./configure
make
sudo make install
sudo ldconfig
```

NOTE: you will get an error while compiling glib1; edit gstrfuncs.c file and change lines containing
```
        g_warning (G_GNUC_PRETTY_FUNCTION
```
to
```
        g_warning ("%s%s", G_GNUC_PRETTY_FUNCTION,
```
(there are 4 such lines) and re-run make

Next, install gtk1:
```
cd ../
wget http://ftp.gnome.org/Public/gnome/sources/gtk+/1.2/gtk+-1.2.10.tar.gz
tar zxvf gtk+-1.2.10.tar.gz
cd gtk+-1.2.10
./configure
make
sudo make install
sudo ldconfig
```

and finally xmms:
```
cd ../
wget http://www.xmms.org/files/1.2.x/xmms-1.2.11.tar.bz2
tar jxvf xmms-1.2.11.tar.bz2
cd xmms-1.2.11
./configure
make
sudo make install
```


good luck!

---

### Post by IAmNoodle on 2009-10-27
I think I'm going to set this thread as solved. It hasn't been in a way, since I'm using something different now, but I appreciate your time and suggestions. Hopefully it'll help someone else wanting to give it a go

---

