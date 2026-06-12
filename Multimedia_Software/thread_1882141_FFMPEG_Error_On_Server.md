---
title: "FFMPEG Error On Server"
date: 2011-11-16
forum: Multimedia Software
---

### Post by darksniper404 on 2011-11-16
I'm using Debian but I thought you guys might be able to help me. I'm trying to get a PHP script to work with FFMPEG but I'm getting this error in the output.


FFmpeg version SVN-r0.5.5-4:0.5.5-1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.5-1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov  5 2011 14:36:22, gcc: 4.4.5
downloaded_videos/1321489278995.mp4: Unknown format

I just installed FFMPEG and PHP5-FFMPEG with apt-get. Thanks if anyone can help.

---

### Post by dniMretsaM on 2011-11-16
It doesn't look like you have MP4 compatibility enabled. See [this]("http://ubuntuforums.org/showthread.php?t=1117283") guide.

EDIT: You're on Debian, so you'll have to find equivalent packages or compile.

---

### Post by FakeOutdoorsman on 2011-11-19
You should remove a layer of complexity by probing the file with FFmpeg directly:
```
ffmpeg -i downloaded_videos/1321489278995.mp4
```
If FFmpeg still says "unknown format" then you know it is an issue with FFmpeg or your input file and not a result of PHP or php5-ffmpeg.

---

