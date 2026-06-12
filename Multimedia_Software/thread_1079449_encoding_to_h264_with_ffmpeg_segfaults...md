---
title: "encoding to h264 with ffmpeg segfaults.."
date: 2009-02-24
forum: Multimedia Software
---

### Post by cowmix on 2009-02-24
I'm running 8.10 x86.. Avidemux works fine (for what that is worth)...

The source is a DV AVI..

cowmix@maupin:~/vidz$ ffmpeg -y -i VID.avi -pass 1 -deinterlace -vcodec libx264 -b 1.5Mb -g 18 -bf 3 -b_strategy 1 -trellis 2 -subcmp 2 -cmp 2 -coder 1 -flags +loop -qmax 51 -acodec libfaac -ab 128k ./output.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
Input #0, avi, from 'VID.avi':
  Duration: 00:09:16.1, start: 0.000000, bitrate: 30453 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480 [PAR 0:1 DAR 0:1], 29.97 tb(r)
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, mp4, to './output.mp4':
    Stream #0.0: Video: libx264, yuv420p, 720x480 [PAR 0:1 DAR 0:1], q=2-51, pass 1, 1500 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x7f2b209cca00]using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64
Press [q] to stop encoding
Segmentation fault

---

### Post by cowmix on 2009-02-24
Installing the new version 'solved' this issue:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

> **cowmix said:**
> I'm running 8.10 x86.. Avidemux works fine (for what that is worth)...

The source is a DV AVI..

cowmix@maupin:~/vidz$ ffmpeg -y -i VID.avi -pass 1 -deinterlace -vcodec libx264 -b 1.5Mb -g 18 -bf 3 -b_strategy 1 -trellis 2 -subcmp 2 -cmp 2 -coder 1 -flags +loop -qmax 51 -acodec libfaac -ab 128k ./output.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
Input #0, avi, from 'VID.avi':
  Duration: 00:09:16.1, start: 0.000000, bitrate: 30453 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480 [PAR 0:1 DAR 0:1], 29.97 tb(r)
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, mp4, to './output.mp4':
    Stream #0.0: Video: libx264, yuv420p, 720x480 [PAR 0:1 DAR 0:1], q=2-51, pass 1, 1500 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libfaac, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x7f2b209cca00]using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64
Press [q] to stop encoding
Segmentation fault

---

