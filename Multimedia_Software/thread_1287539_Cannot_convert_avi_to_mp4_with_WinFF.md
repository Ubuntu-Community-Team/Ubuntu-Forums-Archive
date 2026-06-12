---
title: "Cannot convert avi to mp4 with WinFF"
date: 2009-10-10
forum: Multimedia Software
---

### Post by themusicalduck on 2009-10-10
Every time I try to encode an avi file as an mp4 using WinFF, a terminal window pops up with this output and error:

```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/media/Stuff/Videos/Anime/Spirited Away/Spirited Away.avi':
  Duration: 02:04:36.47, start: 0.000000, bitrate: 785 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 512x272 [PAR 1:1 DAR 32:17], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
Unknown encoder 'libx264'
Press Enter to Continue

```

I've tried to install any packages in synaptic that look related to x264 or h264, but it hasn't helped.

I'm getting similar errors while trying other formats, but this is what I need to work firstly.

---

### Post by paul.gevers on 2009-10-11
> **themusicalduck said:**
> I've tried to install any packages in synaptic that look related to x264 or h264, but it hasn't helped.


Install libavcodec-unstripped-52.

---

