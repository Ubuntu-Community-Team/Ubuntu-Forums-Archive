---
title: "Cinepaint install on Ubuntu 13.04"
date: 2013-06-19
forum: Multimedia Software
---

### Post by Derelinquat fenestras on 2013-06-19
Hello all,

I've been using Ubuntu since 2007 and have been using Gimp all of that time, but I'm interested in the Deep Painting capabilities of Cinepaint.

I'm trying to Install it on an Ubuntu 13.04 system.  I've downloaded a .tgz of version 1.0 from Softpedia.net.

I do not have a great deal of experience building applications from these files... (as most of the programs that I have used are available as .deb packages, but I was unable to find a deb package for Cinepaint)

So, I cd to the directory to which it was extracted and ran:

./configure
Output below:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
configure: error: cannot run /bin/bash ./config.sub

```
wasn't sure what the error in the last line was for, so I went ahead and ran (perhaps erroniously)

make install

Output below:

```
Making install in libhalf
make[1]: Entering directory `/home/jacob/cinepaint/libhalf'
g++ -DHAVE_CONFIG_H -I. -I../lib -I../config    -g -O2 -MT eLut.o -MD -MP -MF .deps/eLut.Tpo -c -o eLut.o eLut.cpp
mv -f .deps/eLut.Tpo .deps/eLut.Po
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2   -o eLut eLut.o  
libtool: link: g++ -g -O2 -o eLut eLut.o 
./eLut > eLut.h
g++ -DHAVE_CONFIG_H -I. -I../lib -I../config    -g -O2 -MT toFloat.o -MD -MP -MF .deps/toFloat.Tpo -c -o toFloat.o toFloat.cpp
mv -f .deps/toFloat.Tpo .deps/toFloat.Po
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2   -o toFloat toFloat.o  
libtool: link: g++ -g -O2 -o toFloat toFloat.o 
./toFloat > toFloat.h
make  install-am
make[2]: Entering directory `/home/jacob/cinepaint/libhalf'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../lib -I../config    -g -O2 -MT half.lo -MD -MP -MF .deps/half.Tpo -c -o half.lo half.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../lib -I../config -g -O2 -MT half.lo -MD -MP -MF .deps/half.Tpo -c half.cpp  -fPIC -DPIC -o .libs/half.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../lib -I../config -g -O2 -MT half.lo -MD -MP -MF .deps/half.Tpo -c half.cpp -o half.o >/dev/null 2>&1
mv -f .deps/half.Tpo .deps/half.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../lib -I../config    -g -O2 -MT cinepaint_half.lo -MD -MP -MF .deps/cinepaint_half.Tpo -c -o cinepaint_half.lo cinepaint_half.cpp
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../lib -I../config -g -O2 -MT cinepaint_half.lo -MD -MP -MF .deps/cinepaint_half.Tpo -c cinepaint_half.cpp  -fPIC -DPIC -o .libs/cinepaint_half.o
libtool: compile:  g++ -DHAVE_CONFIG_H -I. -I../lib -I../config -g -O2 -MT cinepaint_half.lo -MD -MP -MF .deps/cinepaint_half.Tpo -c cinepaint_half.cpp -o cinepaint_half.o >/dev/null 2>&1
mv -f .deps/cinepaint_half.Tpo .deps/cinepaint_half.Plo
/bin/bash ../libtool --tag=CXX   --mode=link g++  -g -O2 -version-info 0:25:0  -o libcinepaintHalf.la -rpath /usr/local/lib half.lo cinepaint_half.lo  
libtool: link: g++  -fPIC -DPIC -shared -nostdlib /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crti.o /usr/lib/gcc/i686-linux-gnu/4.6.1/crtbeginS.o  .libs/half.o .libs/cinepaint_half.o   -L/usr/lib/gcc/i686-linux-gnu/4.6.1 -L/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu -L/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../../lib -L/lib/i386-linux-gnu -L/lib/../lib -L/usr/lib/i386-linux-gnu -L/usr/lib/../lib -L/usr/lib/gcc/i686-linux-gnu/4.6.1/../../.. -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i686-linux-gnu/4.6.1/crtendS.o /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crtn.o  -O2   -Wl,-soname -Wl,libcinepaintHalf.so.0 -o .libs/libcinepaintHalf.so.0.0.25
g++: error: /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crti.o: No such file or directory
g++: error: /usr/lib/gcc/i686-linux-gnu/4.6.1/crtbeginS.o: No such file or directory
g++: error: /usr/lib/gcc/i686-linux-gnu/4.6.1/crtendS.o: No such file or directory
g++: error: /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/crtn.o: No such file or directory
make[2]: *** [libcinepaintHalf.la] Error 1
make[2]: Leaving directory `/home/jacob/cinepaint/libhalf'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/jacob/cinepaint/libhalf'
make: *** [install-recursive] Error 1

```


So unfortunately, I'm kind of flying blind here...

Not sure how to proceed... If anyone has any suggestions or can set me on the correct path, I would be very appreciative.

---

