---
title: "i810 driver brightness/contrast bug"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by eldy on 2006-09-13
I have a laptop with an Intel 855GM video chipset. It exhibits the bug reported here: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-i810/+bug/32963](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-i810/+bug/32963)

In that thread there is a post by FrogPR at 2006-08-09 11:28:47. I tried following the solution there by downloading [http://xorg.freedesktop.org/releases/individual/driver/xf86-video-i810-1.6.5.tar.bz2](http://xorg.freedesktop.org/releases/individual/driver/xf86-video-i810-1.6.5.tar.bz2) referenced in the post.

After I unzip and tar the file, however, I do not know what to do next. "./configure" gives an error about dependencies: 
rewt@donovan:~/Desktop/i810$ ls
xf86-video-i810-1.6.5  xf86-video-i810-1.6.5.tar
rewt@donovan:~/Desktop/i810$ cd xf86-video-i810-1.6.5/
rewt@donovan:~/Desktop/i810/xf86-video-i810-1.6.5$ ls
aclocal.m4    config.h.in  configure.ac  libtool      man          src
ChangeLog     config.log   COPYING       ltmain.sh    missing
compile       config.sub   depcomp       Makefile.am  README
config.guess  configure    install-sh    Makefile.in  README.sgml
rewt@donovan:~/Desktop/i810/xf86-video-i810-1.6.5$ clear

rewt@donovan:~/Desktop/i810/xf86-video-i810-1.6.5$ ls
aclocal.m4    config.h.in  configure.ac  libtool      man          src
ChangeLog     config.log   COPYING       ltmain.sh    missing
compile       config.sub   depcomp       Makefile.am  README
config.guess  configure    install-sh    Makefile.in  README.sgml
rewt@donovan:~/Desktop/i810/xf86-video-i810-1.6.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if XINERAMA is defined... no
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XF86DRI is defined... no
checking if DPMSExtension is defined... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server xproto xvmc fontsproto ) were not met:

No package 'xorg-server' found
No package 'xvmc' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I tried to install the "xorg-server", "xvmc" and "fontsproto" packages using apt-get with the required repositories enabled but they cannot be found/depend on other packages not available.

I've run out of avenues to explore... How do I upgrade or downgrade the version of the i810 driver that I am using so that it does not have the brightness/contrast bug when playing movies?

Thanks!

---

### Post by mcbane on 2006-11-27
A hint when trying to compile from source: if a package already exists in the repositories, check its dependencies on packages.ubuntu.com (look under "source package"). Installing them should enable you to compile the newer version.

So here's the link.

[http://packages.ubuntu.com/edgy/source/xserver-xorg-video-i810](http://packages.ubuntu.com/edgy/source/xserver-xorg-video-i810)

Now install all the packages that it lists as dependencies, and then run

```
./configure
make
sudo make install
```

BTW, changing the i810 version didn't work, either upgrading or downgrading. My main reason for staying with Windows. :( 

Anyways, trying it didn't break anything, either, so it's worth trying. Let me know if you have better luck.

---

