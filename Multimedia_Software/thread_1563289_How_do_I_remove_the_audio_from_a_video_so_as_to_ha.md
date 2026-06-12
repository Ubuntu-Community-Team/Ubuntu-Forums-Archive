---
title: "How do I remove the audio from a video so as to have silent video"
date: 2010-08-28
forum: Multimedia Software
---

### Post by MechaMechanism on 2010-08-28
I would like to know how to remove the audio from a video, without touching or changing the video in anyway, so I can have a silent video.  Like old time silent movies.

I tried Cinelerra and it allows for audio removal but it transcodes the video unfortunately.  I tried Avidemux and could not see any option to remove the audio while leaving the video untouched.  Then I tried ffmpeg and it does not work because it transcodes the video.
```
$ ffmpeg -i 1.MOV -an 2.mov
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 60.00 (60/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '1.MOV':
  Duration: 00:01:24.30, start: 0.000000, bitrate: 11426 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 640x480, 30 tbr, 30 tbn, 60 tbc
    Stream #0.1(eng): Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
Output #0, mov, to '2.mov':
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480, q=2-31, 200 kb/s, 90k tbn, 30 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame= 2529 fps=163 q=31.0 Lsize=    6557kB time=84.30 bitrate= 637.2kbits/s    
video:6536kB audio:0kB global headers:0kB muxing overhead 0.325759%
```

---

### Post by mc4man on 2010-08-28
ffmpeg -i 1.MOV -vcodec copy -an 2.mov

---

### Post by MechaMechanism on 2010-08-29
> **mc4man said:**
> ffmpeg -i 1.MOV -vcodec copy -an 2.mov
Thank you very much, that worked great.

---

