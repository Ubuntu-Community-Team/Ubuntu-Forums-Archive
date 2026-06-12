---
title: "WinFF issue"
date: 2010-01-30
forum: Multimedia Software
---

### Post by antiphoton on 2010-01-30
When converting any video file into any other format besides DVD format WinFF gives me back this error:

> FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[matroska @ 0x9b6c700]Unknown entry 0x80

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 59.94 (60000/1001)
Input #0, matroska, from '/home/matt/Videos/Inglorious.Basterds[2009]DVDRip.x264-Ch4cal/Inglorious.Basterds[2009]DVDRip.x264-Ch4cal.mkv':
  Duration: 02:32:59.52, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 720x356, PAR 186:157 DAR 33480:13973, 59.94 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16
    Stream #0.2(eng): Audio: aac, 48000 Hz, stereo, s16
    Stream #0.3(spa): Audio: aac, 48000 Hz, stereo, s16
    Stream #0.4(fra): Audio: aac, 48000 Hz, stereo, s16
    Stream #0.5(eng): Subtitle: dvdsub
    Stream #0.6(spa): Subtitle: dvdsub
    Stream #0.7(fra): Subtitle: dvdsub
    Stream #0.8(spa): Subtitle: dvdsub
    Stream #0.9(fra): Subtitle: dvdsub
Unknown encoder 'libfaac'
Press Enter to Continue


Any assistance as to how to fix this is greatly appreciated.

---

### Post by e-Gee on 2010-01-30
Add Medibuntu repozitory and go to synaptic and on medibuntu multiverse and install libavcodec-exstra-52 , libavdevice-exstra-52 , libavformat-exstra-52 and libavutil-exstra-52

---

### Post by SuperSonic4 on 2010-01-30
Alternatively change your audio encoder to something else. I believe ac3 might work

---

### Post by antiphoton on 2010-01-30
> **SuperSonic4 said:**
> Alternatively change your audio encoder to something else. I believe ac3 might work

How do I do this? I already did what the guy above you said to do and that didn't work.

---

