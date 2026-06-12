---
title: "Win FF not converting"
date: 2009-08-17
forum: Multimedia Software
---

### Post by voteforcondit on 2009-08-17
when i try to use win ff i get this 

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (27956/583) -> 23.98 (24000/1001)
Input #0, matroska, from '/media/foster/Azureus Downloads/True Blood S01 Complete/S01E01 - Strange Love.mkv':
  Duration: 00:58:17.34, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 640x352, PAR 1:1 DAR 20:11, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: aac, 24000 Hz, stereo, s16
Unknown encoder 'libxvid'


simpatic says i have libxvid installed 
do i need to set it up diffrent?

---

### Post by Shapierian on 2009-08-17
Do you have "libavcodec-unstripped-52" installed?

---

### Post by bu3askoor on 2009-10-30
Thank you [Shapierian]("http://ubuntuforums.org/member.php?u=7962") ,

Your reply helped me.

---

### Post by kavoura on 2009-12-24
I am having the same problem, and I have libavcodec-unstripped-52 installed.

---

