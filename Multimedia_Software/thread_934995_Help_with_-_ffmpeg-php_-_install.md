---
title: "Help with - ffmpeg-php - install"
date: 2008-10-01
forum: Multimedia Software
---

### Post by andyase on 2008-10-01
Hello
I have tried a few times to install ffmpeg-php onto 7.10, all goes fine until I try to "make". I get the following errors:

> /home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:41:22: error: avformat.h: No such file or directory
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c: In function 'zm_startup_ffmpeg':
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:91: warning: implicit declaration of function 'av_register_all'
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c: In function 'zm_info_ffmpeg':
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:133: error: 'LIBAVFORMAT_IDENT' undeclared (first use in this function)
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:133: error: (Each undeclared identifier is reported only once
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:133: error: for each function it appears in.)
make: *** [ffmpeg-php.lo] Error 1


Can anyone tell me why I am getting this error, and how to fix it.

I have seen this error all over the net but no fix!

Thanks Andy

---

### Post by renzokuken on 2008-10-01
firstly, apologies if i'm stating the obvious, but do you have the compile tools installed?

```
sudo apt-get install build-essential
```

---

### Post by andyase on 2008-10-01
Hi
Yes I have those installed, I am a "newbie" however so any help appreciated.

I installed 
LAME MP3 Encoder, Libogg + Libvorbis , Mencoder and also Mplayer so far when I got to ffmpeg-php thats where I got yhe errors.

Andy

---

### Post by renzokuken on 2008-10-01
ok, i just noticed its actually in the repos but under a slighty different name.

```
sudo apt-get install php5-ffmpeg
```

that should install it along with any dependencies. much easier and better than compiling from source

EDIT: ok, being an idiot now, its actually only in the Hardy (8.04) repos but not the Gutsy (7.10) repos apparently

---

### Post by renzokuken on 2008-10-01
try this instead to compile from source, run each command one at a time, waiting for the previous one to finish (version number may differ so make sure you change it to right one in the first line)

```

cd ffmpeg-php-0.5.3.1
phpize
./configure --prefix=/usr
make
make install
cd
```

---

### Post by andyase on 2008-10-01
It failed at the "make" command again!

This is the complete output:

> hhomelist@pertd:~/ffmpeg-php-0.5.1$ ./configure --prefix=/usr
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr                              /include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/inclu                              de/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20060613+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.9.11 or later if you want to regenerate                               PHP parsers.
checking for gawk... gawk
checking for ffmpeg support... yes, shared
checking for ffmpeg headers... ...found in /usr/include/ffmpeg
checking for ffmpeg libavcodec.so... ...found in /usr/lib
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
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
configure: creating ./config.status
config.status: creating config.h
config.status: config.h is unchanged
hhomelist@perilla:~/ffmpeg-php-0.5.1$ make
/bin/bash /home/hhomelist/ffmpeg-php-0.5.1/libtool --mode=compile gcc  -I. -I/ho                              me/hhomelist/ffmpeg-php-0.5.1 -DPHP_ATOM_INC -I/home/hhomelist/ffmpeg-php-0.5.1/                              include -I/home/hhomelist/ffmpeg-php-0.5.1/main -I/home/hhomelist/ffmpeg-php-0.5                              .1 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/                              include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LA                              RGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/ffmpeg  -DHAVE_CONFIG_H  -g                               -O2 -Wall -fno-strict-aliasing   -c /home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php                              .c -o ffmpeg-php.lo
mkdir .libs
 gcc -I. -I/home/hhomelist/ffmpeg-php-0.5.1 -DPHP_ATOM_INC -I/home/hhomelist/ffm                              peg-php-0.5.1/include -I/home/hhomelist/ffmpeg-php-0.5.1/main -I/home/hhomelist/                              ffmpeg-php-0.5.1 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php                              5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/                              date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/ffmpeg -DHAVE                              _CONFIG_H -g -O2 -Wall -fno-strict-aliasing -c /home/hhomelist/ffmpeg-php-0.5.1/                              ffmpeg-php.c  -fPIC -DPIC -o .libs/ffmpeg-php.o
In file included from /home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:40:
/usr/include/ffmpeg/avcodec.h:2447: warning: 'ImgReSampleContext' is deprecated
/usr/include/ffmpeg/avcodec.h:2450: warning: 'ImgReSampleContext' is deprecated
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:41:22: error: avformat.h: No such                               file or directory
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c: In function 'zm_startup_ffmpeg':
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:91: warning: implicit declaration                               of function 'av_register_all'
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c: In function 'zm_info_ffmpeg':
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:133: error: 'LIBAVFORMAT_IDENT' un                              declared (first use in this function)
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:133: error: (Each undeclared ident                              ifier is reported only once
/home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:133: error: for each function it a                              ppears in.)
make: *** [ffmpeg-php.lo] Error 1

---

### Post by renzokuken on 2008-10-01
weird, have a look at this post

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=902247](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=902247)

---

### Post by renzokuken on 2008-10-01
seem to have found a step by step installation guide for Hardy

[http://escapegoat.org/2007/11/11/installing-ffmpeg-php-on-ubuntu-7-10](http://escapegoat.org/2007/11/11/installing-ffmpeg-php-on-ubuntu-7-10)

---

### Post by andyase on 2008-10-01
Ive tried both of them examples... thanks
I'll keep looking.

---

### Post by Yellow Pasque on 2008-10-01
I believe you're missing libavcodec-dev (or a dependency). Install it through Synaptic and see if that solves it or at least allows the build process to get further.

Edit: Actually, it looks like libavformat-dev, but install both packages.

> /home/hhomelist/ffmpeg-php-0.5.1/ffmpeg-php.c:41:22: error: avformat.h: No such file or directory

---

### Post by andyase on 2008-10-01
Temüjin

Thanks for the reply.
It was libavformat-dev, installed this and was able to install ffmpeg-php without errors, thank you :popcorn:

---

