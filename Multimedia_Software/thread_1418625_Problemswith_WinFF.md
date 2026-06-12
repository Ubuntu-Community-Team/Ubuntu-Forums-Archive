---
title: "Problemswith WinFF"
date: 2010-02-28
forum: Multimedia Software
---

### Post by rva1945 on 2010-02-28
I installed it, along with the suggested package. Then I run it and tried to convert a MP4 to MP3, the Terminal pops up with this (even after installing the libmp3lame package):

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 1 codec frame rate differs from container frame rate: 60.00 (60/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/media/Disco local/Documents and Settings/All Users/Documentos/Mi música/Riff/riff - ruedas de metal.mp4':
  Duration: 00:05:59.16, start: 0.000000, bitrate: 436 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 30 tbr, 30 tbn, 60 tbc
Unknown encoder 'libmp3lame'
Press Enter to Continue

---

### Post by byStanderone on 2010-02-28
...what i see in the repo are, libmp3lame0 and libmp3lame-dev, are you referring to this two packages when you said libmp3lame?

---

### Post by FakeOutdoorsman on 2010-03-01
This is a common question:
[why winff will not work to convert avi to mpg4](http://ubuntuforums.org/showthread.php?p=8559062)
[9.10 WINFF help](http://ubuntuforums.org/showthread.php?p=8645077)
[Unknown encoder 'libmp3lame'](http://ubuntuforums.org/showthread.php?t=1385688)
[winff problem](http://ubuntuforums.org/showthread.php?p=7987975)

With an easy fix:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

