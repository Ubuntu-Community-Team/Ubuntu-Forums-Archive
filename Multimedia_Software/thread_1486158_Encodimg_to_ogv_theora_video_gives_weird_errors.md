---
title: "Encodimg to ogv theora video gives weird errors"
date: 2010-05-17
forum: Multimedia Software
---

### Post by skatebiker on 2010-05-17
When I try encoding to ogv video I get the following:

```



ffmpeg -i funehood.flv  -vcodec libtheora -acodec libvorbis -b 256k -ab 64k output.ogv


FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'fumehood.flv':
  Duration: 00:01:00.93, start: 0.000000, bitrate: 445 kb/s
    Stream #0.0: Video: flv, yuv420p, 480x360, 389 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
Output #0, ogg, to 'output.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 480x360, q=2-31, 256 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: vorbis, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libtheora @ 0x9e30700]theora_encode_init failed
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

What is the problem here ?

---

