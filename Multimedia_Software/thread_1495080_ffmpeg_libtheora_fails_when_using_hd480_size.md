---
title: "ffmpeg libtheora fails when using hd480 size"
date: 2010-05-27
forum: Multimedia Software
---

### Post by Cyan_Fire on 2010-05-27
I'm trying to transcode a video I took with a digital camera to an ogv, but get an error from ffmpeg when I try to downsize it from 720p to 480p. I'm using Ubuntu 10.04.

```
ffmpeg -i bridal_shower.mov -acodec libvorbis -vcodec libtheora -b 2048k -t 30 bridal-2048.ogv
```
Works fine, but

```
david@fueron:~/Videos$ ffmpeg -i bridal_shower.mov -acodec libvorbis -vcodec libtheora -b 2048k -s hd480 -t 30 bridal-2048.ogv
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
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'bridal_shower.mov':
  Duration: 00:08:00.11, start: 0.000000, bitrate: 7140 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 30 tbr, 30.03 tbn, 30 tbc
    Stream #0.1(eng): Audio: pcm_mulaw, 16000 Hz, mono, s16, 128 kb/s
File 'bridal-2048.ogv' already exists. Overwrite ? [y/N] y
Output #0, ogg, to 'bridal-2048.ogv':
    Stream #0.0(eng): Video: libtheora, yuv420p, 852x480 [PAR 1:1 DAR 71:40], q=2-31, 2048 kb/s, 90k tbn, 30 tbc
    Stream #0.1(eng): Audio: vorbis, 16000 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libtheora @ 0x2341af0]theora_encode_init failed
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

The only difference between the two is the -s hd480 parameter. Any ideas? Has anyone run into this?

---

