---
title: "quicktime 7.1 codec"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by smith19 on 2007-08-05
I try to see a quicktime movie on Totem Movie Player and it's ask me codec to download. since i don't have internet on feisty i can't download it. where i find the codec or player to download with other pc.                                                             


                                           sorry i am fresh on linux

---

### Post by smith19 on 2007-08-05
anyboady please!

---

### Post by davem2312 on 2007-08-05
for totem, you need to install the ffmpeg plugins  try this.


sudo apt-get install gstreamer0.10-ffmpeg

---

### Post by smith19 on 2007-08-08
hey i don't have Internet Connection on UBUNTU. please help me ,i am stacked.

---

### Post by endre on 2007-08-08
You can download the packages you need directly from the internet using your browser, then move them to your Ubuntu system by the way of a USB stick or something, and then install them from the local files. Just be sure to get all the dependencies you need!

Check here for details on the package: [http://packages.ubuntu.com/edgy/libs/gstreamer0.10-ffmpeg](http://packages.ubuntu.com/edgy/libs/gstreamer0.10-ffmpeg)

I would recommend however to get internet access on your Ubuntu system as well. You are almost completely dependent on having internet access to do any kind of updates, modifications, tweaks etc. Remember that access to open software through the internet is at the core of what Ubuntu and other linux systems do, and without access to the resources on synaptic, you are cut off from a very important part of the whole Ubuntu experience.

---

### Post by smith19 on 2007-08-09
ok i downloaded "http://packages.ubuntu.com/edgy/libs...mer0.10-ffmpeg" and i read INSTALL file after that i stack on step 2  here is what i did .

root@ubuntu:~/Desktop/gst-ffmpeg-0.10.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
configure: configuring gst-ffmpeg for release
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking to see if compiler understands -Wall... yes
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GST... configure: error: no gstreamer-0.10 >= 0.10.0 (GStreamer) found
**root@ubuntu:~/Desktop/gst-ffmpeg-0.10.1$ make**
make: *** No targets specified and no makefile found.  Stop.

guys is there anything i missed? Thanks endre and anybody reading these. please help me out.

---

### Post by apetresc on 2007-08-09
Yup, you're missing the gstreamer library. Simply do
```
sudo apt-get install libgstreamer0.10-0 libgstreamer0.10-dev
```
Then run the configure script again. There shouldn't be any errors this time.

---

### Post by smith19 on 2007-08-10
i download gstreamer0.10 and when i compile it list a lots of thing finally it's says

" checking for XML... configure: error: Need libxml2 for glib2 builds -- you should be able to do without it -- this needs fixing"

---

### Post by apetresc on 2007-08-10
> **smith19 said:**
> i download gstreamer0.10 and when i compile it list a lots of thing finally it's says

" checking for XML... configure: error: Need libxml2 for glib2 builds -- you should be able to do without it -- this needs fixing"

Okay, then now do ```
sudo apt-get install libxml2 libxml2-dev
```
Noticing a pattern? :)

---

### Post by smith19 on 2007-08-10
libxml2 is installed in Synaptic Packager Manager and it's the result is same.

---

### Post by apetresc on 2007-08-10
> **smith19 said:**
> libxml2 is installed in Synaptic Packager Manager and it's the result is same.

But is libxml2-dev also installed? These two packages are quite different.

---

### Post by Skrypt on 2007-08-10
also make sure you have the build-essential

```

sudo apt-get build-essential

```

Really a pain without internet.

---

### Post by smith19 on 2007-08-14
Hello, finally gstreamer0.10-ffmpeg compiled and installed successfully  but still Totem won't play H264,MPEG4,MOV. any idea please.

---

