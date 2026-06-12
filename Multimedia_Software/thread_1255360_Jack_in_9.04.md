---
title: "Jack in 9.04"
date: 2009-09-01
forum: Multimedia Software
---

### Post by johnnytucats on 2009-09-01
I'm trying to build Jack in Ubuntu 9.04 and I'm stuck. Using the directions from:

[http://subversion.ffado.org/wiki/JackForFfado](http://subversion.ffado.org/wiki/JackForFfado)

One thing is, I don't have a prior Jack install. Another is, when I enter the line

$ sudo ./autogen.sh

I get

libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: linking file `config/ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/ltsugar.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
./autogen.sh: 29: aclocal: not found
aclocal $ACLOCAL_FLAGS where $ACLOCAL_FLAGS= failed, exiting...

Also, I can already see that I don't understand what I'm supposed to  enter when the instructions say this:

$ ./configure --prefix=YOUR_PREFIX --with-default-tmpdir=/dev/shm

Anyone got a good guide for installing Jack, particularly on an ext3 system with a swap partition?

---

### Post by johnnytucats on 2009-09-03
By the way, this is all in order to get a Focusrite Saffire LE firewire audio device up and running.

---

