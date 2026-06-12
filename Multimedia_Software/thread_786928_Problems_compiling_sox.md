---
title: "Problems compiling sox"
date: 2008-05-08
forum: Multimedia Software
---

### Post by SteelDragon on 2008-05-08
Hello all.

I have followed [this guide]("http://ubuntuforums.org/showthread.php?t=17272") (post 6) to compile sox with mp3 encoding support successfully before, but this time, it won't work. When I try to build the deb with dpkg-buildpackage, it exits with a bunch of undefined reference errors, all related to vorbis.c.

I recently (i.e. yesterday) clean installed gutsy on this machine, and have installed vorbis-tools, libvorbis* and libogg*, but the problem sticks around.

Anybody have any ideas or answers?

Thanks

SteelDragon

dpkg-buildpackage output:
```

dpkg-buildpackage: source package is sox
dpkg-buildpackage: source version is 13.0.0-1build1
dpkg-buildpackage: source changed by Steve Kowalik <stevenk@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 13.0.0-1build1
 debian/rules clean
/usr/share/cdbs/1/rules/buildcore.mk:68: parsing sox-13.0.0.tar.gz ...
test -x debian/rules
test "`id -u`" = 0
rm -rf build-tree
rm debian/stamp-sox-13.0.0.tar.gz
rm debian/stamp-patch-* 2>/dev/null
make: [cleanbuilddir] Error 1 (ignored)
for i in ./build-tree/sox-13.0.0/config.guess ./build-tree/sox-13.0.0/config.sub  ; do \
		if test -e $i.cdbs-orig ; then \
			mv $i.cdbs-orig $i ; \
		fi ; \
	done
dh_clean 
/usr/bin/make -C build-tree/sox-13.0.0 -k distclean
make: *** build-tree/sox-13.0.0: No such file or directory.  Stop.
make: [makefile-clean] Error 2 (ignored)
rm -f debian/stamp-makefile-build
rm -f debian/stamp-autotools-files
 debian/rules build
/usr/share/cdbs/1/rules/buildcore.mk:68: parsing sox-13.0.0.tar.gz ...
test -x debian/rules
mkdir -p "build-tree/sox-13.0.0"
tar -C build-tree  -xzf sox-13.0.0.tar.gz
touch debian/stamp-sox-13.0.0.tar.gz
if test -e /usr/share/misc/config.guess ; then \
		for i in sox-13.0.0/config.guess ; do \
			cp --remove-destination /usr/share/misc/config.guess \
			build-tree/$i ; \
		done ; \
	fi
if test -e /usr/share/misc/config.sub ; then \
		for i in sox-13.0.0/config.sub ; do \
			cp --remove-destination /usr/share/misc/config.sub \
			build-tree/$i ; \
		done ; \
	fi
touch debian/stamp-autotools-files
chmod a+x /usr/local/src/sox-13.0.0/build-tree/sox-13.0.0/configure
cd build-tree/sox-13.0.0 && CC="cc" CXX="g++" CFLAGS="-g -Wall -O2" CXXFLAGS="-g -Wall -O2" CPPFLAGS="" LDFLAGS="" CFLAGS="-fPIC -D_REENTRANT" LDFLAGS="-Wl,-z,defs" /usr/local/src/sox-13.0.0/build-tree/sox-13.0.0/configure --build=i486-linux-gnu --prefix=/usr --includedir="\${prefix}/include" --mandir="\${prefix}/share/man" --infodir="\${prefix}/share/info" --sysconfdir=/etc --localstatedir=/var --libexecdir="\${prefix}/lib/sox" --disable-maintainer-mode --disable-dependency-tracking --srcdir=.   
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... cc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of cc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i486-pc-linux-gnu
checking host system type... i486-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by cc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... cc -E
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
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
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
checking command to parse /usr/bin/nm -B output from cc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if cc supports -fno-rtti -fno-exceptions... no
checking for cc option to produce PIC... -fPIC
checking if cc PIC flag -fPIC works... yes
checking if cc static flag -static works... yes
checking if cc supports -c -o file.o... yes
checking whether the cc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if we want a debug build... no
checking whether byte ordering is bigendian... no
checking for inline... inline
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for getopt_long... yes
configure: checking if math library is required during link...
checking for pow... no
checking for pow in -lm... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for _LARGEFILE_SOURCE value needed for large files... no
checking for fseeko... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for snd_pcm_open in -lasound... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking sun/audioio.h usability... no
checking sun/audioio.h presence... no
checking for sun/audioio.h... no
checking gsm/gsm.h usability... yes
checking gsm/gsm.h presence... yes
checking for gsm/gsm.h... yes
checking for gsm_create in -lgsm... yes
checking for SNDFILE... yes
checking sndfile.h usability... yes
checking sndfile.h presence... yes
checking for sndfile.h... yes
checking for sf_open... yes
checking for sf_open_virtual... yes
checking vorbis/codec.h usability... yes
checking vorbis/codec.h presence... yes
checking for vorbis/codec.h... yes
checking for ogg_packet_clear in -logg... yes
checking for ov_clear in -lvorbisfile... yes
checking for vorbis_encode_init_vbr in -lvorbisenc... yes
checking FLAC/file_encoder.h usability... no
checking FLAC/file_encoder.h presence... no
checking for FLAC/file_encoder.h... no
checking mad.h usability... yes
checking mad.h presence... yes
checking for mad.h... yes
checking for mad_stream_buffer in -lmad... yes
checking lame/lame.h usability... yes
checking lame/lame.h presence... yes
checking for lame/lame.h... yes
checking for lame_init in -lmp3lame... yes
checking for SAMPLERATE... yes
checking samplerate.h usability... yes
checking samplerate.h presence... yes
checking for samplerate.h... yes
checking for src_new... yes
checking for stdint types... stdint.h (shortcircuit)
make use of stdint.h in src/ststdint.h (assuming C99 compatible system)
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/libgsm/Makefile
config.status: creating src/libst-config
config.status: creating src/stconfig.h
config.status: executing depfiles commands
config.status: executing src/ststdint.h commands
config.status: creating src/ststdint.h : _SOX_SRC_STSTDINT_H

ALSA driver....................... yes
OSS driver........................ yes
SUN audio driver.................. no
libgsm............................ external
libsndfile formats................ yes
Ogg Vorbis format................. yes
FLAC format....................... no
MAD MP3 reader.................... yes
LAME MP3 writer................... yes
Secret Rabbit Code resampling..... yes

Configure finished.  Do 'make && make install' to compile and install SoX.

/usr/bin/make -C build-tree/sox-13.0.0 
make[1]: Entering directory `/usr/local/src/sox-13.0.0/build-tree/sox-13.0.0'
Making all in src
make[2]: Entering directory `/usr/local/src/sox-13.0.0/build-tree/sox-13.0.0/src'
cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sox.c
sox.c: In function ‘usage’:
sox.c:1731: warning: string length ‘2397’ is greater than the length ‘509’ ISO C89 compilers are required to support
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o 8svx.lo 8svx.c
mkdir .libs
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c 8svx.c  -fPIC -DPIC -o .libs/8svx.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c 8svx.c -o 8svx.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o adpcm.lo adpcm.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c adpcm.c  -fPIC -DPIC -o .libs/adpcm.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c adpcm.c -o adpcm.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o adpcms.lo adpcms.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c adpcms.c  -fPIC -DPIC -o .libs/adpcms.o
adpcms.c:22:1: warning: "range_limit" redefined
In file included from adpcms.c:20:
st_i.h:50:1: warning: this is the location of the previous definition
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c adpcms.c -o adpcms.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o aiff.lo aiff.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c aiff.c  -fPIC -DPIC -o .libs/aiff.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c aiff.c -o aiff.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o au.lo au.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c au.c  -fPIC -DPIC -o .libs/au.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c au.c -o au.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o auto.lo auto.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c auto.c  -fPIC -DPIC -o .libs/auto.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c auto.c -o auto.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o avr.lo avr.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c avr.c  -fPIC -DPIC -o .libs/avr.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c avr.c -o avr.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o cdr.lo cdr.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c cdr.c  -fPIC -DPIC -o .libs/cdr.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c cdr.c -o cdr.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o cvsd.lo cvsd.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c cvsd.c  -fPIC -DPIC -o .libs/cvsd.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c cvsd.c -o cvsd.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o dat.lo dat.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c dat.c  -fPIC -DPIC -o .libs/dat.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c dat.c -o dat.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o flac.lo flac.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c flac.c  -fPIC -DPIC -o .libs/flac.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c flac.c -o flac.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o g711.lo g711.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g711.c  -fPIC -DPIC -o .libs/g711.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g711.c -o g711.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o g721.lo g721.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g721.c  -fPIC -DPIC -o .libs/g721.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g721.c -o g721.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o g723_24.lo g723_24.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g723_24.c  -fPIC -DPIC -o .libs/g723_24.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g723_24.c -o g723_24.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o g723_40.lo g723_40.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g723_40.c  -fPIC -DPIC -o .libs/g723_40.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g723_40.c -o g723_40.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o g72x.lo g72x.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g72x.c  -fPIC -DPIC -o .libs/g72x.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c g72x.c -o g72x.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o gsm.lo gsm.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c gsm.c  -fPIC -DPIC -o .libs/gsm.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c gsm.c -o gsm.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o hcom.lo hcom.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c hcom.c  -fPIC -DPIC -o .libs/hcom.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c hcom.c -o hcom.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o ima_rw.lo ima_rw.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c ima_rw.c  -fPIC -DPIC -o .libs/ima_rw.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c ima_rw.c -o ima_rw.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o maud.lo maud.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c maud.c  -fPIC -DPIC -o .libs/maud.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c maud.c -o maud.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o mp3.lo mp3.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c mp3.c  -fPIC -DPIC -o .libs/mp3.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c mp3.c -o mp3.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o nulfile.lo nulfile.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c nulfile.c  -fPIC -DPIC -o .libs/nulfile.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c nulfile.c -o nulfile.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o prc.lo prc.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c prc.c  -fPIC -DPIC -o .libs/prc.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c prc.c -o prc.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o raw.lo raw.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c raw.c  -fPIC -DPIC -o .libs/raw.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c raw.c -o raw.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o sf.lo sf.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sf.c  -fPIC -DPIC -o .libs/sf.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sf.c -o sf.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o skelform.lo skelform.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c skelform.c  -fPIC -DPIC -o .libs/skelform.o
skelform.c: In function 'read':
skelform.c:89: warning: unused variable 'sk'
skelform.c: At top level:
skelform.c:121: warning: unused parameter 'ft'
skelform.c: In function 'startwrite':
skelform.c:128: warning: unused variable 'sk'
skelform.c: In function 'write':
skelform.c:164: warning: unused variable 'sk'
skelform.c: At top level:
skelform.c:189: warning: unused parameter 'ft'
skelform.c:197: warning: unused parameter 'ft'
skelform.c:197: warning: unused parameter 'offset'
skelform.c:224: warning: no previous prototype for 'st_skel_format_fn'
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c skelform.c -o skelform.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o smp.lo smp.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c smp.c  -fPIC -DPIC -o .libs/smp.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c smp.c -o smp.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o sndfile.lo sndfile.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sndfile.c  -fPIC -DPIC -o .libs/sndfile.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sndfile.c -o sndfile.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o sndrtool.lo sndrtool.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sndrtool.c  -fPIC -DPIC -o .libs/sndrtool.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sndrtool.c -o sndrtool.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o sphere.lo sphere.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sphere.c  -fPIC -DPIC -o .libs/sphere.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sphere.c -o sphere.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o tx16w.lo tx16w.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c tx16w.c  -fPIC -DPIC -o .libs/tx16w.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c tx16w.c -o tx16w.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o voc.lo voc.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c voc.c  -fPIC -DPIC -o .libs/voc.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c voc.c -o voc.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o vorbis.lo vorbis.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vorbis.c  -fPIC -DPIC -o .libs/vorbis.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vorbis.c -o vorbis.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o vox.lo vox.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vox.c  -fPIC -DPIC -o .libs/vox.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vox.c -o vox.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o wav.lo wav.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c wav.c  -fPIC -DPIC -o .libs/wav.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c wav.c -o wav.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o wve.lo wve.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c wve.c  -fPIC -DPIC -o .libs/wve.o
wve.c: In function 'st_wvestopwrite':
wve.c:171: warning: control reaches end of non-void function
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c wve.c -o wve.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o xa.lo xa.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c xa.c  -fPIC -DPIC -o .libs/xa.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c xa.c -o xa.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o biquad.lo biquad.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c biquad.c  -fPIC -DPIC -o .libs/biquad.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c biquad.c -o biquad.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o biquads.lo biquads.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c biquads.c  -fPIC -DPIC -o .libs/biquads.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c biquads.c -o biquads.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o chorus.lo chorus.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c chorus.c  -fPIC -DPIC -o .libs/chorus.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c chorus.c -o chorus.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o compand.lo compand.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c compand.c  -fPIC -DPIC -o .libs/compand.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c compand.c -o compand.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o dcshift.lo dcshift.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c dcshift.c  -fPIC -DPIC -o .libs/dcshift.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c dcshift.c -o dcshift.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o dither.lo dither.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c dither.c  -fPIC -DPIC -o .libs/dither.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c dither.c -o dither.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o earwax.lo earwax.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c earwax.c  -fPIC -DPIC -o .libs/earwax.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c earwax.c -o earwax.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o echo.lo echo.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c echo.c  -fPIC -DPIC -o .libs/echo.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c echo.c -o echo.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o echos.lo echos.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c echos.c  -fPIC -DPIC -o .libs/echos.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c echos.c -o echos.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o fade.lo fade.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c fade.c  -fPIC -DPIC -o .libs/fade.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c fade.c -o fade.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o FFT.lo FFT.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c FFT.c  -fPIC -DPIC -o .libs/FFT.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c FFT.c -o FFT.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o filter.lo filter.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c filter.c  -fPIC -DPIC -o .libs/filter.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c filter.c -o filter.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o flanger.lo flanger.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c flanger.c  -fPIC -DPIC -o .libs/flanger.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c flanger.c -o flanger.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o mcompand.lo mcompand.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c mcompand.c  -fPIC -DPIC -o .libs/mcompand.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c mcompand.c -o mcompand.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o mixer.lo mixer.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c mixer.c  -fPIC -DPIC -o .libs/mixer.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c mixer.c -o mixer.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o noiseprof.lo noiseprof.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c noiseprof.c  -fPIC -DPIC -o .libs/noiseprof.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c noiseprof.c -o noiseprof.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o noisered.lo noisered.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c noisered.c  -fPIC -DPIC -o .libs/noisered.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c noisered.c -o noisered.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o pad.lo pad.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c pad.c  -fPIC -DPIC -o .libs/pad.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c pad.c -o pad.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o pan.lo pan.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c pan.c  -fPIC -DPIC -o .libs/pan.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c pan.c -o pan.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o phaser.lo phaser.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c phaser.c  -fPIC -DPIC -o .libs/phaser.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c phaser.c -o phaser.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o pitch.lo pitch.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c pitch.c  -fPIC -DPIC -o .libs/pitch.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c pitch.c -o pitch.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o polyphas.lo polyphas.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c polyphas.c  -fPIC -DPIC -o .libs/polyphas.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c polyphas.c -o polyphas.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o rabbit.lo rabbit.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c rabbit.c  -fPIC -DPIC -o .libs/rabbit.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c rabbit.c -o rabbit.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o rate.lo rate.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c rate.c  -fPIC -DPIC -o .libs/rate.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c rate.c -o rate.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o repeat.lo repeat.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c repeat.c  -fPIC -DPIC -o .libs/repeat.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c repeat.c -o repeat.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o resample.lo resample.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c resample.c  -fPIC -DPIC -o .libs/resample.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c resample.c -o resample.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o reverb.lo reverb.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c reverb.c  -fPIC -DPIC -o .libs/reverb.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c reverb.c -o reverb.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o reverse.lo reverse.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c reverse.c  -fPIC -DPIC -o .libs/reverse.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c reverse.c -o reverse.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o silence.lo silence.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c silence.c  -fPIC -DPIC -o .libs/silence.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c silence.c -o silence.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o skeleff.lo skeleff.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c skeleff.c  -fPIC -DPIC -o .libs/skeleff.o
skeleff.c: In function 'getopts':
skeleff.c:39: warning: unused variable 'skeleff'
skeleff.c: At top level:
skeleff.c:37: warning: unused parameter 'argv'
skeleff.c: In function 'flow':
skeleff.c:70: warning: unused variable 'skeleff'
skeleff.c: At top level:
skeleff.c:100: warning: unused parameter 'effp'
skeleff.c:100: warning: unused parameter 'obuf'
skeleff.c:113: warning: unused parameter 'effp'
skeleff.c:122: warning: unused parameter 'effp'
skeleff.c:151: warning: no previous prototype for 'st_skel_effect_fn'
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c skeleff.c -o skeleff.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o speed.lo speed.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c speed.c  -fPIC -DPIC -o .libs/speed.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c speed.c -o speed.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o stat.lo stat.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c stat.c  -fPIC -DPIC -o .libs/stat.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c stat.c -o stat.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o stretch.lo stretch.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c stretch.c  -fPIC -DPIC -o .libs/stretch.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c stretch.c -o stretch.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o swap.lo swap.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c swap.c  -fPIC -DPIC -o .libs/swap.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c swap.c -o swap.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o synth.lo synth.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c synth.c  -fPIC -DPIC -o .libs/synth.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c synth.c -o synth.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o tremolo.lo tremolo.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c tremolo.c  -fPIC -DPIC -o .libs/tremolo.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c tremolo.c -o tremolo.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o trim.lo trim.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c trim.c  -fPIC -DPIC -o .libs/trim.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c trim.c -o trim.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o vibro.lo vibro.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vibro.c  -fPIC -DPIC -o .libs/vibro.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vibro.c -o vibro.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o vol.lo vol.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vol.c  -fPIC -DPIC -o .libs/vol.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c vol.c -o vol.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o alsa.lo alsa.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c alsa.c  -fPIC -DPIC -o .libs/alsa.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c alsa.c -o alsa.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o oss.lo oss.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c oss.c  -fPIC -DPIC -o .libs/oss.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c oss.c -o oss.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o sunaudio.lo sunaudio.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sunaudio.c  -fPIC -DPIC -o .libs/sunaudio.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c sunaudio.c -o sunaudio.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o handlers.lo handlers.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c handlers.c  -fPIC -DPIC -o .libs/handlers.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c handlers.c -o handlers.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o misc.lo misc.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c misc.c  -fPIC -DPIC -o .libs/misc.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c misc.c -o misc.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o stio.lo stio.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c stio.c  -fPIC -DPIC -o .libs/stio.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c stio.c -o stio.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o util.lo util.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c util.c  -fPIC -DPIC -o .libs/util.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c util.c -o util.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o xmalloc.lo xmalloc.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c xmalloc.c  -fPIC -DPIC -o .libs/xmalloc.o
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c xmalloc.c -o xmalloc.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o getopt.lo getopt.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c getopt.c  -fPIC -DPIC -o .libs/getopt.o
getopt.c:2: warning: ISO C forbids an empty source file
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c getopt.c -o getopt.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=compile cc -DHAVE_CONFIG_H -I. -I. -I.     -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c -o getopt1.lo getopt1.c
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c getopt1.c  -fPIC -DPIC -o .libs/getopt1.o
getopt1.c:2: warning: ISO C forbids an empty source file
 cc -DHAVE_CONFIG_H -I. -I. -I. -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -c getopt1.c -o getopt1.o >/dev/null 2>&1
/bin/bash ../libtool  --tag=CC --mode=link cc  -fPIC -D_REENTRANT -Wall -W -Wmissing-prototypes -Wstrict-prototypes -pedantic -lsndfile   -lsamplerate   -Wl,-z,defs -o libst.la -rpath /usr/lib  8svx.lo adpcm.lo adpcms.lo aiff.lo au.lo auto.lo avr.lo cdr.lo cvsd.lo dat.lo flac.lo g711.lo g721.lo g723_24.lo g723_40.lo g72x.lo gsm.lo hcom.lo ima_rw.lo maud.lo mp3.lo nulfile.lo prc.lo raw.lo sf.lo skelform.lo smp.lo sndfile.lo sndrtool.lo sphere.lo tx16w.lo voc.lo vorbis.lo vox.lo wav.lo wve.lo xa.lo biquad.lo biquads.lo chorus.lo compand.lo dcshift.lo dither.lo earwax.lo echo.lo echos.lo fade.lo FFT.lo filter.lo flanger.lo mcompand.lo mixer.lo noiseprof.lo noisered.lo pad.lo pan.lo phaser.lo pitch.lo polyphas.lo rabbit.lo rate.lo repeat.lo resample.lo reverb.lo reverse.lo silence.lo skeleff.lo speed.lo stat.lo stretch.lo swap.lo synth.lo tremolo.lo trim.lo vibro.lo vol.lo alsa.lo oss.lo sunaudio.lo handlers.lo misc.lo stio.lo util.lo xmalloc.lo getopt.lo getopt1.lo  -lmp3lame -lmad -lvorbisenc -lvorbisfile -logg -lasound -lm  -lgsm
cc -shared  .libs/8svx.o .libs/adpcm.o .libs/adpcms.o .libs/aiff.o .libs/au.o .libs/auto.o .libs/avr.o .libs/cdr.o .libs/cvsd.o .libs/dat.o .libs/flac.o .libs/g711.o .libs/g721.o .libs/g723_24.o .libs/g723_40.o .libs/g72x.o .libs/gsm.o .libs/hcom.o .libs/ima_rw.o .libs/maud.o .libs/mp3.o .libs/nulfile.o .libs/prc.o .libs/raw.o .libs/sf.o .libs/skelform.o .libs/smp.o .libs/sndfile.o .libs/sndrtool.o .libs/sphere.o .libs/tx16w.o .libs/voc.o .libs/vorbis.o .libs/vox.o .libs/wav.o .libs/wve.o .libs/xa.o .libs/biquad.o .libs/biquads.o .libs/chorus.o .libs/compand.o .libs/dcshift.o .libs/dither.o .libs/earwax.o .libs/echo.o .libs/echos.o .libs/fade.o .libs/FFT.o .libs/filter.o .libs/flanger.o .libs/mcompand.o .libs/mixer.o .libs/noiseprof.o .libs/noisered.o .libs/pad.o .libs/pan.o .libs/phaser.o .libs/pitch.o .libs/polyphas.o .libs/rabbit.o .libs/rate.o .libs/repeat.o .libs/resample.o .libs/reverb.o .libs/reverse.o .libs/silence.o .libs/skeleff.o .libs/speed.o .libs/stat.o .libs/stretch.o .libs/swap.o .libs/synth.o .libs/tremolo.o .libs/trim.o .libs/vibro.o .libs/vol.o .libs/alsa.o .libs/oss.o .libs/sunaudio.o .libs/handlers.o .libs/misc.o .libs/stio.o .libs/util.o .libs/xmalloc.o .libs/getopt.o .libs/getopt1.o  /usr/lib/libsndfile.so -L/usr/lib /usr/lib/libsamplerate.so /usr/lib/libmp3lame.so /usr/lib/libmad.so /usr/lib/libvorbisenc.so /usr/lib/libvorbisfile.so /usr/lib/libogg.so /usr/lib/libasound.so -lm -lgsm  -Wl,-z -Wl,defs -Wl,-soname -Wl,libst.so.0 -o .libs/libst.so.0.0.0
.libs/vorbis.o: In function `write_vorbis_header':
vorbis.c:(.text+0x7f3): undefined reference to `vorbis_analysis_headerout'
.libs/vorbis.o: In function `st_vorbisstartwrite':
vorbis.c:(.text+0x91f): undefined reference to `vorbis_info_init'
vorbis.c:(.text+0xa1b): undefined reference to `vorbis_analysis_init'
vorbis.c:(.text+0xa38): undefined reference to `vorbis_block_init'
.libs/vorbis.o: In function `st_vorbiswrite':
vorbis.c:(.text+0xaeb): undefined reference to `vorbis_analysis_buffer'
vorbis.c:(.text+0xb74): undefined reference to `vorbis_analysis_wrote'
vorbis.c:(.text+0xb96): undefined reference to `vorbis_analysis'
vorbis.c:(.text+0xba6): undefined reference to `vorbis_bitrate_addblock'
vorbis.c:(.text+0xc4b): undefined reference to `vorbis_bitrate_flushpacket'
vorbis.c:(.text+0xc70): undefined reference to `vorbis_analysis_blockout'
.libs/vorbis.o: In function `st_vorbisstopwrite':
vorbis.c:(.text+0xce4): undefined reference to `vorbis_block_clear'
vorbis.c:(.text+0xcf4): undefined reference to `vorbis_dsp_clear'
vorbis.c:(.text+0xd04): undefined reference to `vorbis_info_clear'
collect2: ld returned 1 exit status
make[2]: *** [libst.la] Error 1
make[2]: Leaving directory `/usr/local/src/sox-13.0.0/build-tree/sox-13.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/sox-13.0.0/build-tree/sox-13.0.0'
make: *** [debian/stamp-makefile-build] Error 2

```

---

### Post by mc4man on 2008-05-08
> Anybody have any ideas or answers? not sure but compiled fine on gutsy (13.0.0) and hardy (14.0.0)
Why don't you start over, make a dir. in home called sox, cd to it and apt-get the source. Don't use sudo, just apt-get source sox. Then just browse to the rules file in debian and delete --disable-lame (leave --disable-shared, ie. don't use #). The readme implies this for this version, (not so in hardy). Then use dpkg-buildpackage -rfakeroot -b and see.
You do have fakeroot installed ?
If it builds you could try again with the --disable-shared removed, I'll try it now and see if it matters

Edit : removing --disable-shared will cause build to fail in 13.0.0, that probably was your only issue, though life is easier if you don't use sudo when apt-getting sources

---

### Post by SteelDragon on 2008-05-08
That did it. Thanks a lot. :)

> **mc4man said:**
> though life is easier if you don't use sudo when apt-getting sources

How do you mean?

---

### Post by mc4man on 2008-05-08
If you sudo apt-get then you don't have permission to edit files (like rules) or delete the source dir.'s when your done building your package(s). You should notice that nothing in your build dir. is locked, the same for your new deb(s). (when just using apt-get)

---

