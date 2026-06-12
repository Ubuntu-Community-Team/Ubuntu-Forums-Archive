---
title: "dv grab"
date: 2009-04-09
forum: Multimedia Software
---

### Post by Komir on 2009-04-09
I try do compile dvgrab without libdv, and I have some error? Can anybody help me with that problem?
```

komir@komir:~/Desktop/dvgrab-3.3$ ./configure without-package libdv
configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for without-package-gcc... no
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
checking for library containing strerror... none required
checking for without-package-g++... no
checking for without-package-c++... no
checking for without-package-gpp... no
checking for without-package-aCC... no
checking for without-package-CC... no
checking for without-package-cxx... no
checking for without-package-cc++... no
checking for without-package-cl.exe... no
checking for without-package-FCC... no
checking for without-package-KCC... no
checking for without-package-RCC... no
checking for without-package-xlC_r... no
checking for without-package-xlC... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for without-package-gcc... gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for without-package-pkg-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBRAW1394... yes
checking for LIBAVC1394... yes
checking for LIBIEC61883... yes
checking for pthread_create in -lpthread... yes
checking for LIBDV... no
libdv not installed; I make better dv2 AVI files with libdv 0.103 or newer.
checking for LIBQUICKTIME... no
checking quicktime/quicktime.h usability... no
checking quicktime/quicktime.h presence... no
checking for quicktime/quicktime.h... no
configure: WARNING: No package 'libquicktime' found
configure: WARNING: libquicktime missing; install libquicktime or quicktime4linux to support Quicktime files.
checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no
configure: WARNING: jpeglib headers missing; install jpeglib to save to JPEG files.
checking for jpeg_CreateCompress in -ljpeg... no
configure: WARNING: jpeglib missing; install jpeglib to save to JPEG files.
checking linux/videodev2.h usability... yes
checking linux/videodev2.h presence... yes
checking for linux/videodev2.h... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking return type of signal handlers... void
checking for mktime... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
komir@komir:~/Desktop/dvgrab-3.3$ sudo make
[sudo] password for komir:
make  all-am
make[1]: Entering directory `/home/komir/Desktop/dvgrab-3.3'
source='avi.cc
 
' object='avi.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ./depcomp \
    g++ -DHAVE_CONFIG_H -I.    -D_REENTRANT -D_FILE_OFFSET_BITS=64  -c -o avi.o avi.cc
./depcomp: line 571: exec: g++: not found
make[1]: *** [avi.o] Error 127
make[1]: Leaving directory `/home/komir/Desktop/dvgrab-3.3'
make: *** [all] Error 2
komir@komir:~/Desktop/dvgrab-3.3$ 
```

---

### Post by gandaran on 2009-04-09
looks as if you don't have the necessary compiling tools installed, install build-essential.
you can install the older version of dvgrab in synaptic or do you need the new version?

---

### Post by Komir on 2009-04-09
Thx,:lolflag: work

---

