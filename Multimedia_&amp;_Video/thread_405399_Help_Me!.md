---
title: "Help Me!"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by north zulch computer geek on 2007-04-09
im trying to install cinelerra.

it tells me that i need gcc3.x

i already entered ./configure, it worked just fine

i tried to do a "make" and got this:

christopher@G4-test-drive:~/programs/gcc-4.1.2$ make
make[1]: Entering directory `/home/christopher/programs/gcc-4.1.2'
make[2]: Entering directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/zlib'
true "AR_FLAGS=rc" "CC_FOR_BUILD=gcc" "CFLAGS=-g -O2 " "CXXFLAGS=-g -O2" "CFLAGS_FOR_BUILD=-g -O2 " "CFLAGS_FOR_TARGET=-O2 -g -O2  " "INSTALL=/usr/bin/install -c" "INSTALL_DATA=/usr/bin/install -c -m 644" "INSTALL_PROGRAM=/usr/bin/install -c" "INSTALL_SCRIPT=/usr/bin/install -c" "LDFLAGS=" "LIBCFLAGS=-g -O2 " "LIBCFLAGS_FOR_TARGET=-O2 -g -O2  " "MAKE=make" "MAKEINFO=/home/christopher/programs/gcc-4.1.2/missing makeinfo --split-size=5000000 --split-size=5000000 " "PICFLAG=" "PICFLAG_FOR_TARGET=" "SHELL=/bin/sh" "EXPECT=expect" "RUNTEST=runtest" "RUNTESTFLAGS=" "exec_prefix=/usr/local" "infodir=/usr/local/info" "libdir=/usr/local/lib" "prefix=/usr/local" "tooldir=/usr/local/powerpc-unknown-linux-gnu" "AR=ar" "AS=as" "CC=gcc" "CXX=c++" "LD=ld" "LIBCFLAGS=-g -O2 " "NM=nm" "PICFLAG=" "RANLIB=ranlib" "DESTDIR=" DO=all multi-do # make
make[2]: Leaving directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/zlib'
make[2]: Entering directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/libiberty'
make[3]: Entering directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/libiberty/testsuite'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/libiberty/testsuite'
make[2]: Leaving directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/libiberty'
make[2]: Entering directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/fastjar'
make "AR_FLAGS=rc" "CC_FOR_BUILD=gcc" "CFLAGS=-g -O2 " "CXXFLAGS=-g -O2" "CFLAGS_FOR_BUILD=-g -O2 " "CFLAGS_FOR_TARGET=-O2 -g -O2  " "INSTALL=/usr/bin/install -c" "INSTALL_DATA=/usr/bin/install -c -m 644" "INSTALL_PROGRAM=/usr/bin/install -c" "INSTALL_SCRIPT=/usr/bin/install -c" "JC1FLAGS=" "LDFLAGS=" "LIBCFLAGS=-g -O2 " "LIBCFLAGS_FOR_TARGET=-O2 -g -O2  " "MAKE=make" "MAKEINFO=/home/christopher/programs/gcc-4.1.2/missing makeinfo --split-size=5000000 --split-size=5000000 " "PICFLAG=" "PICFLAG_FOR_TARGET=" "SHELL=/bin/sh" "exec_prefix=/usr/local" "infodir=/usr/local/info" "libdir=/usr/local/lib" "prefix=/usr/local" "AR=ar" "AS=as" "CC=gcc" "CXX=c++" "LD=ld" "LIBCFLAGS=-g -O2 " "NM=nm" "PICFLAG=" "RANLIB=ranlib" "DESTDIR=" all-am
make[3]: Entering directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/fastjar'
restore=: && backupdir=".am$$" && \
        rm -rf $backupdir && mkdir $backupdir && \
        for f in fastjar.info fastjar.info-[0-9] fastjar.info-[0-9][0-9] fastjar.i[0-9] fastjar.i[0-9][0-9]; do \
          if test -f $f; then mv $f $backupdir; restore=mv; else :; fi; \
        done; \
        if /home/christopher/programs/gcc-4.1.2/missing makeinfo --split-size=5000000 --split-size=5000000  -I ../.././fastjar/../gcc/doc/include  -I ../.././fastjar \
         -o fastjar.info `test -f 'fastjar.texi' || echo '../.././fastjar/'`fastjar.texi; \
        then \
          rc=0; \
        else \
          rc=$?; \
          $restore $backupdir/* `echo "./fastjar.info" | sed 's|[^/]*$||'`; \
        fi; \
        rm -rf $backupdir; exit $rc
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `**Texinfo**' package or
         the `**GNU make**' package.  Grab either from any GNU archive site.
make[3]: *** [fastjar.info] Error 1
make[3]: Leaving directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/fastjar'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/christopher/programs/gcc-4.1.2/host-powerpc-unknown-linux-gnu/fastjar'
make[1]: *** [all-fastjar] Error 2
make[1]: Leaving directory `/home/christopher/programs/gcc-4.1.2'
make: *** [all] Error 2
christopher@G4-test-drive:~/programs/gcc-4.1.2$

i installed GNU make and texinfo, and got this same message!

i have basic experience with ubuntu.

what do i do?     :(

---

