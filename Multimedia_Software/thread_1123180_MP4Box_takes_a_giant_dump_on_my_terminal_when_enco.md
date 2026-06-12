---
title: "MP4Box takes a giant dump on my terminal when encoding Stargate Atlantis"
date: 2009-04-11
forum: Multimedia Software
---

### Post by u-slayer on 2009-04-11
So I wrote a script that automatically converts dvd iso files into mkv files. It works great. I ripped a whole bunch of different movies and Stargate SG1 season 1,2 and 7 without too many problems.

Now when I try to rip Stargate Atlantis, every single title on every single disc is failing when I try to use my mp4box command and I don't understand why. Here's my mencoder and mp4box output:

```
mencoder -quiet /media/disk/mkv/STARGATE_ATLANTIS_S1_D4.15/STARGATE_ATLANTIS_S1_D4.15.vob -vf pullup,softskip,crop=704:352:10:62,yadif,pp=ac,harddup -ofps 23.976 -passlogfile /media/disk/mkv/STARGATE_ATLANTIS_S1_D4.15/divx2pass.log -ovc x264 -x264encopts threads=auto:log=2:subq=6:8x8dct:me=umh:frameref=5:bframes=3:b_pyramid:weight_b:partitions=all:crf=18 -oac copy -of rawvideo -o /media/disk/mkv/STARGATE_ATLANTIS_S1_D4.15/STARGATE_ATLANTIS_S1_D4.15.264
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x1f315000
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [pp=ac]
Opening video filter: [yadif]
Opening video filter: [crop w=704 h=352 x=10 y=62]
Crop: 704 x 352, 10 ; 62
Opening video filter: [softskip]
Opening video filter: [pullup]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=24000 sample-1)
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0xe1f8d0]SwScaler: using unscaled yuv420p -> yuv420p special converter
x264 [info]: using SAR=8/9
x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.

Flushing video frames.

Video stream: 2369.723 kbit/s  (296215 B/s)  size: 247883980 bytes  836.837 secs  25082 frames

Audio stream:  192.000 kbit/s  (24000 B/s)  size: 20072448 bytes  836.352 secs
x264 [info]: slice I:149   Avg QP:16.67  size: 33989
x264 [info]: slice P:9116  Avg QP:19.19  size: 18067
x264 [info]: slice B:10798 Avg QP:20.85  size:  7234
x264 [info]: mb I  I16..4: 18.7% 44.8% 36.5%
x264 [info]: mb P  I16..4:  5.5% 14.1%  8.3%  P16..4: 44.4% 19.3%  4.4%  0.5%  0.3%    skip: 3.2%
x264 [info]: mb B  I16..4:  2.1%  4.6%  0.8%  B16..8: 36.0%  3.7%  5.9%  direct:21.8%  skip:25.2%
x264 [info]: 8x8 transform  intra:52.9%  inter:34.1%
x264 [info]: ref P  63.9% 17.1%  8.1%  5.9%  4.9%
x264 [info]: ref B  73.0% 16.1%  7.0%  4.0%
x264 [info]: kb/s:2369.8
Wrote 236 MiB in 735 seconds 329 KiB/s - 163 fps
```

```
MP4Box -fps 23.976 -add /media/disk/mkv/STARGATE_ATLANTIS_S1_D4.15/STARGATE_ATLANTIS_S1_D4.15.264 -tmp /media/disk/mkv/STARGATE_ATLANTIS_S1_D4.15 /media/disk/mkv/STARGATE_ATLANTIS_S1_D4.15/STARGATE_ATLANTIS_S1_D4.15.mp4
AVC-H264 import - frame size 704 x 352 at 23.976 FPS
Import results: 20063 samples - Slices: 149 I 9116 P 10798 B - 1 SEI - 139 IDR
	Stream uses B-slice references - max frame delay 2
*** buffer overflow detected ***: MP4Box terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7fcb44e022c7]
/lib/libc.so.6[0x7fcb44e00170]
MP4Box[0x408a88]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fcb44d215a6]
MP4Box[0x406949]
======= Memory map: ========
00400000-00424000 r-xp 00000000 08:01 294944                             /usr/bin/MP4Box
00624000-00628000 r--p 00024000 08:01 294944                             /usr/bin/MP4Box
00628000-00629000 rw-p 00028000 08:01 294944                             /usr/bin/MP4Box
018ab000-01c81000 rw-p 018ab000 00:00 0                                  [heap]
7fcb43e6e000-7fcb43e84000 r-xp 00000000 08:01 639894                     /lib/libgcc_s.so.1
7fcb43e84000-7fcb44084000 ---p 00016000 08:01 639894                     /lib/libgcc_s.so.1
7fcb44084000-7fcb44085000 r--p 00016000 08:01 639894                     /lib/libgcc_s.so.1
7fcb44085000-7fcb44086000 rw-p 00017000 08:01 639894                     /lib/libgcc_s.so.1
7fcb44086000-7fcb44088000 r-xp 00000000 08:01 639050                     /lib/libdl-2.9.so
7fcb44088000-7fcb44288000 ---p 00002000 08:01 639050                     /lib/libdl-2.9.so
7fcb44288000-7fcb44289000 r--p 00002000 08:01 639050                     /lib/libdl-2.9.so
7fcb44289000-7fcb4428a000 rw-p 00003000 08:01 639050                     /lib/libdl-2.9.so
7fcb4428a000-7fcb442a1000 r-xp 00000000 08:01 639097                     /lib/libpthread-2.9.so
7fcb442a1000-7fcb444a0000 ---p 00017000 08:01 639097                     /lib/libpthread-2.9.so
7fcb444a0000-7fcb444a1000 r--p 00016000 08:01 639097                     /lib/libpthread-2.9.so
7fcb444a1000-7fcb444a2000 rw-p 00017000 08:01 639097                     /lib/libpthread-2.9.so
7fcb444a2000-7fcb444a6000 rw-p 7fcb444a2000 00:00 0 
7fcb444a6000-7fcb44609000 r-xp 00000000 08:01 246508                     /usr/lib/libcrypto.so.0.9.8
7fcb44609000-7fcb44808000 ---p 00163000 08:01 246508                     /usr/lib/libcrypto.so.0.9.8
7fcb44808000-7fcb44815000 r--p 00162000 08:01 246508                     /usr/lib/libcrypto.so.0.9.8
7fcb44815000-7fcb4482b000 rw-p 0016f000 08:01 246508                     /usr/lib/libcrypto.so.0.9.8
7fcb4482b000-7fcb4482f000 rw-p 7fcb4482b000 00:00 0 
7fcb4482f000-7fcb44878000 r-xp 00000000 08:01 246618                     /usr/lib/libssl.so.0.9.8
7fcb44878000-7fcb44a78000 ---p 00049000 08:01 246618                     /usr/lib/libssl.so.0.9.8
7fcb44a78000-7fcb44a79000 r--p 00049000 08:01 246618                     /usr/lib/libssl.so.0.9.8
7fcb44a79000-7fcb44a7e000 rw-p 0004a000 08:01 246618                     /usr/lib/libssl.so.0.9.8
7fcb44a7e000-7fcb44b02000 r-xp 00000000 08:01 639055                     /lib/libm-2.9.so
7fcb44b02000-7fcb44d01000 ---p 00084000 08:01 639055                     /lib/libm-2.9.so
7fcb44d01000-7fcb44d02000 r--p 00083000 08:01 639055                     /lib/libm-2.9.so
7fcb44d02000-7fcb44d03000 rw-p 00084000 08:01 639055                     /lib/libm-2.9.so
7fcb44d03000-7fcb44e6b000 r-xp 00000000 08:01 639024                     /lib/libc-2.9.so
7fcb44e6b000-7fcb4506b000 ---p 00168000 08:01 639024                     /lib/libc-2.9.so
7fcb4506b000-7fcb4506f000 r--p 00168000 08:01 639024                     /lib/libc-2.9.so
7fcb4506f000-7fcb45070000 rw-p 0016c000 08:01 639024                     /lib/libc-2.9.so
7fcb45070000-7fcb45075000 rw-p 7fcb45070000 00:00 0 
7fcb45075000-7fcb4508c000 r-xp 00000000 08:01 249406                     /usr/lib/libz.so.1.2.3.3
7fcb4508c000-7fcb4528b000 ---p 00017000 08:01 249406                     /usr/lib/libz.so.1.2.3.3
7fcb4528b000-7fcb4528d000 rw-p 00016000 08:01 249406                     /usr/lib/libz.so.1.2.3.3
7fcb4528d000-7fcb4550b000 r-xp 00000000 08:01 303539                     /usr/lib/libgpac-0.4.4.so
7fcb4550b000-7fcb4570b000 ---p 0027e000 08:01 303539                     /usr/lib/libgpac-0.4.4.so
7fcb4570b000-7fcb4570d000 r--p 0027e000 08:01 303539                     /usr/lib/libgpac-0.4.4.so
7fcb4570d000-7fcb45715000 rw-p 00280000 08:01 303539                     /usr/lib/libgpac-0.4.4.so
7fcb45715000-7fcb45717000 rw-p 7fcb45715000 00:00 0 
7fcb45717000-7fcb45737000 r-xp 00000000 08:01 639001                     /lib/ld-2.9.so
7fcb45915000-7fcb45919000 rw-p 7fcb45915000 00:00 0 
7fcb45930000-7fcb45931000 rw-p 7fcb45930000 00:00 0 
7fcb45932000-7fcb45936000 rw-p 7fcb45932000 00:00 0 
7fcb45936000-7fcb45937000 r--p 0001f000 08:01 639001                     /lib/ld-2.9.so
7fcb45937000-7fcb45938000 rw-p 00020000 08:01 639001                     /lib/ld-2.9.so
7fff4d8fe000-7fff4d938000 rw-p 7ffffffc5000 00:00 0                      [stack]
7fff4d9ff000-7fff4da00000 r-xp 7fff4d9ff000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]


```

---

### Post by u-slayer on 2009-04-12
...

---

