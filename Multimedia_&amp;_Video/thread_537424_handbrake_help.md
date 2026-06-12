---
title: "handbrake help?"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by CoriolisSTORM on 2007-08-28
Sorry guys, did search, didn't find.  Anyway, I have followed the instructions on the Handbrake site to install handbrake.  the instructions were here:  [http://handbrake.m0k.org/trac/wiki/CompileGuide#cli](http://handbrake.m0k.org/trac/wiki/CompileGuide#cli)
So, what do I use to execute the program?  I have compiled it with jam and the build was alright I suppose.  Now what?  I cant seem to find HandBrake.app like it says. Would it be something else with Linux?  What do I use to execute the program?  the last thing set of stuff my terminal lists is thus:
>  /usr/bin/install -c -m 644 'floor1-4.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/floor1-4.png'
 /usr/bin/install -c -m 644 'hufftree.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/hufftree.png'
 /usr/bin/install -c -m 644 'hufftree-under.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/hufftree-under.png'
 /usr/bin/install -c -m 644 'residue-pack.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/residue-pack.png'
 /usr/bin/install -c -m 644 'residue2.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/residue2.png'
 /usr/bin/install -c -m 644 'white-xifish.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/white-xifish.png'
 /usr/bin/install -c -m 644 'window1.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/window1.png'
 /usr/bin/install -c -m 644 'window2.png' '/home/rob/HandBrake-source/contrib/share/doc/libvorbis-1.1.1/window2.png'
Making install in examples
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
Making install in win32
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
Making install in debian
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
Making install in vq
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Nothing to be done for `install-exec-am'.
test -z "/home/rob/HandBrake-source/contrib/share/aclocal" || mkdir -p -- "/home/rob/HandBrake-source/contrib/share/aclocal"
 /usr/bin/install -c -m 644 'vorbis.m4' '/home/rob/HandBrake-source/contrib/share/aclocal/vorbis.m4'
test -z "/home/rob/HandBrake-source/contrib/lib/pkgconfig" || mkdir -p -- "/home/rob/HandBrake-source/contrib/lib/pkgconfig"
 /usr/bin/install -c -m 644 'vorbis.pc' '/home/rob/HandBrake-source/contrib/lib/pkgconfig/vorbis.pc'
 /usr/bin/install -c -m 644 'vorbisenc.pc' '/home/rob/HandBrake-source/contrib/lib/pkgconfig/vorbisenc.pc'
 /usr/bin/install -c -m 644 'vorbisfile.pc' '/home/rob/HandBrake-source/contrib/lib/pkgconfig/vorbisfile.pc'
LibVorbisEnc ./lib/libvorbisenc.a
Wget ./x264.tar.gz
--21:05:59--  [http://download.m0k.org/handbrake/contrib/x264-r665.tar.gz](http://download.m0k.org/handbrake/contrib/x264-r665.tar.gz)
           => `./x264.tar.gz'
Resolving download.m0k.org... 88.191.201.36
Connecting to download.m0k.org|88.191.201.36|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 751,198 (734K) [application/octet-stream]

100%[=================================================================================>] 751,198       35.98K/s    ETA 00:00

21:06:18 (40.34 KB/s) - `./x264.tar.gz' saved [751198/751198]

LibX264 ./lib/libx264.a
(Stripping trailing CRs from patch.)
patching file encoder/encoder.c
Hunk #1 succeeded at 479 (offset 9 lines).
(Stripping trailing CRs from patch.)
patching file encoder/analyse.c
Hunk #1 succeeded at 31 with fuzz 1 (offset 2 lines).
Hunk #2 succeeded at 2032 (offset 5 lines).
Hunk #3 succeeded at 2110 (offset 5 lines).
(Stripping trailing CRs from patch.)
patching file x264.c
(Stripping trailing CRs from patch.)
patching file common/pixel.c
Hunk #2 succeeded at 481 (offset 2 lines).
(Stripping trailing CRs from patch.)
patching file common/pixel.h
(Stripping trailing CRs from patch.)
patching file common/common.c
Hunk #3 succeeded at 951 (offset 5 lines).
(Stripping trailing CRs from patch.)
patching file x264.h
Hunk #1 succeeded at 227 (offset 4 lines).
No suitable assembler found.  x264 will be several times slower.
Please install 'yasm' to get MMX/SSE optimized code.
svn: This client is too old to work with working copy '.'; please get a newer Subversion client
Platform:   X86
System:     LINUX
avis input: no
mp4 output: no
pthread:    yes
gtk:        no
debug:      no
gprof:      no
PIC:        no
shared:     no
visualize:  no

You can run 'make' or 'make fprofiled' now.
rm -f .depend
( echo -n "`dirname common/mc.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/mc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/predict.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/pixel.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/pixel.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/macroblock.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/frame.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/frame.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/dct.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/dct.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cpu.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/cpu.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cabac.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/common.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/common.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/mdate.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/mdate.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/csp.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/csp.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/set.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/quant.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  common/quant.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/analyse.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/analyse.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/me.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/me.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/ratecontrol.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/ratecontrol.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/set.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/macroblock.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cabac.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cavlc.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/cavlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/encoder.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/encoder.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/eval.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  encoder/eval.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname x264.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  matroska.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname muxers.c`/" && gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer  muxers.c -MM -g0 ) 1>> .depend;
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o x264.o x264.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o matroska.o matroska.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o muxers.o muxers.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/mc.o common/mc.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/predict.o common/predict.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/pixel.o common/pixel.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/macroblock.o common/macroblock.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/frame.o common/frame.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/dct.o common/dct.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/cpu.o common/cpu.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/cabac.o common/cabac.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/common.o common/common.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/mdate.o common/mdate.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/csp.o common/csp.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/set.o common/set.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o common/quant.o common/quant.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/analyse.o encoder/analyse.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/me.o encoder/me.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/ratecontrol.o encoder/ratecontrol.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/set.o encoder/set.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/macroblock.o encoder/macroblock.c
encoder/macroblock.c: In function &#8216;x264_macroblock_probe_skip&#8217;:
encoder/macroblock.c:611: warning: &#8216;mvp[0]&#8217; may be used uninitialized in this function
encoder/macroblock.c:611: warning: &#8216;mvp[1]&#8217; may be used uninitialized in this function
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/cabac.o encoder/cabac.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/cavlc.o encoder/cavlc.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/encoder.o encoder/encoder.c
gcc -O4 -ffast-math  -Wall -I. -DHAVE_MALLOC_H -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD -s -fomit-frame-pointer   -c -o encoder/eval.o encoder/eval.c
ar rc libx264.a common/mc.o common/predict.o common/pixel.o common/macroblock.o common/frame.o common/dct.o common/cpu.o common/cabac.o common/common.o common/mdate.o common/csp.o common/set.o common/quant.o encoder/analyse.o encoder/me.o encoder/ratecontrol.o encoder/set.o encoder/macroblock.o encoder/cabac.o encoder/cavlc.o encoder/encoder.o encoder/eval.o
ranlib libx264.a
gcc -o x264 x264.o matroska.o muxers.o libx264.a -lm -lpthread -s
install -d /home/rob/HandBrake-source/contrib/bin /home/rob/HandBrake-source/contrib/include
install -d /home/rob/HandBrake-source/contrib/lib /home/rob/HandBrake-source/contrib/lib/pkgconfig
install -m 644 x264.h /home/rob/HandBrake-source/contrib/include
install -m 644 libx264.a /home/rob/HandBrake-source/contrib/lib
install -m 644 x264.pc /home/rob/HandBrake-source/contrib/lib/pkgconfig
install x264 /home/rob/HandBrake-source/contrib/bin
ranlib /home/rob/HandBrake-source/contrib/lib/libx264.a
Wget ./xvidcore.tar.gz
--21:06:52--  [http://download.m0k.org/handbrake/contrib/xvidcore-1.1.2.tar.gz](http://download.m0k.org/handbrake/contrib/xvidcore-1.1.2.tar.gz)
           => `./xvidcore.tar.gz'
Resolving download.m0k.org... 88.191.201.36
Connecting to download.m0k.org|88.191.201.36|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 740,185 (723K) [application/octet-stream]

100%[=================================================================================>] 740,185       21.09K/s    ETA 00:00

21:07:24 (23.10 KB/s) - `./xvidcore.tar.gz' saved [740185/740185]

LibXvidCore ./lib/libxvidcore.a
configure: loading cache /home/rob/HandBrake-source/contrib/config.cache
checking build system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking target system type... (cached) i686-pc-linux-gnu
checking whether to use default CFLAGS... yes
checking for gcc... (cached) gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking for ranlib... (cached) ranlib
checking for whether to use assembly code... yes
checking for architecture type... ia32
checking how to run the C preprocessor... (cached) gcc -E
checking for egrep... (cached) grep -E
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for int *... yes
checking size of int *... 4
checking whether byte ordering is bigendian... (cached) no
checking for build extensions... .so .a .o
checking for platform specific LDFLAGS/CFLAGS... ok
checking for yasm... no
checking for nasm... no
configure: WARNING: no correct assembler was found - Compiling generic sources only
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
updating cache /home/rob/HandBrake-source/contrib/config.cache
configure: creating ./config.status
config.status: creating platform.inc
  D: =build
  C: ./decoder.c
  C: ./encoder.c
  C: ./xvid.c
  C: bitstream/bitstream.c
  C: bitstream/cbp.c
  C: bitstream/mbcoding.c
  C: dct/fdct.c
  C: dct/idct.c
  C: dct/simple_idct.c
  C: image/colorspace.c
  C: image/image.c
  C: image/interpolate8x8.c
  C: image/font.c
  C: image/postprocessing.c
  C: image/qpel.c
  C: image/reduced.c
  C: motion/estimation_bvop.c
  C: motion/estimation_common.c
  C: motion/estimation_gmc.c
  C: motion/estimation_pvop.c
  C: motion/estimation_rd_based.c
  C: motion/estimation_rd_based_bvop.c
  C: motion/gmc.c
  C: motion/motion_comp.c
  C: motion/vop_type_decision.c
  C: motion/sad.c
  C: prediction/mbprediction.c
  C: plugins/plugin_single.c
  C: plugins/plugin_2pass1.c
  C: plugins/plugin_2pass2.c
  C: plugins/plugin_lumimasking.c
  C: plugins/plugin_dump.c
  C: plugins/plugin_psnr.c
  C: quant/quant_h263.c
  C: quant/quant_matrix.c
  C: quant/quant_mpeg.c
  C: utils/emms.c
  C: utils/mbtransquant.c
  C: utils/mem_align.c
  C: utils/mem_transfer.c
  C: utils/timer.c
  L: libxvidcore.a
...updated 34 target(s)...
Checking dependencies...
Cc common.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc hb.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc ports.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc scan.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc work.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc decmpeg2.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc encavcodec.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc update.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc demuxmpeg.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc fifo.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc render.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc reader.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc muxcommon.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc stream.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc muxmp4.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc sync.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc decsub.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc deca52.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc decdca.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc encfaac.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc declpcm.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc encx264.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc decavcodec.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
decavcodec.c: In function &#8216;decavcodecWork&#8217;:
decavcodec.c:108: warning: &#8216;avcodec_decode_audio&#8217; is deprecated (declared at ../contrib/include/ffmpeg/avcodec.h:2552)
Cc encxvid.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc muxmkv.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc muxavi.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc enclame.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc muxogm.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc encvorbis.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc dvd.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc ipodutil.o
Cc deblock.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc deinterlace.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc denoise.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc detelecine.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Cc lang.o
echo cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION=\""0.9.0"\" -DHB_BUILD=2007082800 -DSYS_LINUX  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
cc -I../contrib/include -D__LIBHB__ -DUSE_PTHREAD -DHB_VERSION="0.9.0" -DHB_BUILD=2007082800 -DSYS_LINUX -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Library libhb.a
ar: creating libhb.a
Shared library libhb.so
Link HandBrakeCLI
(rm -rf HandBrake HandBrake*.tar.gz ; mkdir -p HandBrake/api HandBrake/doc; cp test/BUILDSHARED AUTHORS BUILD COPYING CREDITS NEWS THANKS TRANSLATIONS HandBrake/doc ;  cp -rp libhb/libhb.so HandBrake/api ; cp -rp libhb/hb.h libhb/common.h libhb/ports.h HandBrake/api ; cp -rp HandBrakeCLI HandBrake ; tar zcvf HandBrake-"0.9.0"_i386.tar.gz HandBrake ; rm -rf HandBrake )
HandBrake/
HandBrake/api/
HandBrake/api/libhb.so
HandBrake/api/hb.h
HandBrake/api/common.h
HandBrake/api/ports.h
HandBrake/doc/
HandBrake/doc/BUILDSHARED
HandBrake/doc/AUTHORS
HandBrake/doc/BUILD
HandBrake/doc/COPYING
HandBrake/doc/CREDITS
HandBrake/doc/NEWS
HandBrake/doc/THANKS
HandBrake/doc/TRANSLATIONS
HandBrake/HandBrakeCLI
rob@rob-desktop:~/HandBrake-source$


Sorry, my terminal won't show when I first started the process.  It stopped there.

---

### Post by juxtaposed on 2007-08-31
You should now have a HandBrakeCLI file. Just go to the terminal and set it to that, along with all the options you want (like input, output, formats, etc). To get a list of those, do the --help command into handbrake (/home/blah/handbrake/HandBrakeCLI --help)

You do know handbrake on linux is only command line, right? :P

---

### Post by frame45 on 2008-02-04
I have installed HankBrakeCLI and when i try to run it on a staor bought DVD (CSS'd) it doesn't work. 

I have used HandBrake on Mac OSX 10.4 It works great. First time every time. 

Also I have used it on Windows XP. you have to use DVD43 to decrypt the CSS. (then it works)

I couldn't find any DVD decrypters for Linux, so I tried to run DVD43.exe thru wine, it says something about can't find a driver. 

Does Anyone know what I can do to get HandBrake working with CSS'd DVDs??:confused:

---

### Post by maubp on 2008-02-07
Have you installed de-CSS library? (can you play DVDs on linux?)

I think its called libdvdcss2 or something, check the FAQ.

---

