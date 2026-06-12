---
title: "Having some trouble converting videos -&gt; XVid with FFMPEG"
date: 2009-10-02
forum: Multimedia Software
---

### Post by rob86 on 2009-10-02
I'm trying to convert videos with ffmpeg, and it works, but if I try to use a non default codec libxvid it won't work and immediately fails. Any idea why? Am I typing something wrong?

Here's what happens:
```

ffmpeg -i ~/Desktop/save-video.flv -vcodec libxvid out.avi 
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

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from '/home/rob/Desktop/save-video.flv':
  Duration: 00:03:39.05, start: 0.000000, bitrate: 799 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 743 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 56 kb/s
File 'out.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'out.avi':
    Stream #0.0: Video: libxvid, yuv420p, 320x240, q=2-31, 200 kb/s, 90k tbn, 29.92 tbc
    Stream #0.1: Audio: mp2, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[libxvid @ 0x8c5d770]Invalid pixel aspect ratio 0/1
Video encoding failed

```

By the way, I wouldn't mind using DivX but I didn't see any codec to do it?

---

### Post by andrew.46 on 2009-10-02
Hi rob,

> **rob86 said:**
> By the way, I wouldn't mind using DivX but I didn't see any codec to do it?

Can't help with the 'invalid pixel ratio' error but encoding to DivX is an easier question. Simply use:

```
-vcodec mpeg4 -vtag xvid
```

Andrew

---

### Post by rob86 on 2009-10-02
So are XVid and DivX both mpeg4? I'm kind of confused about that, I read it on a website that to encode in Xvid or DivX you use mpeg4 like you said and change the tag to xvid or divx. I thought there was something special about DivX and XVid? No?

---

### Post by andrew.46 on 2009-10-03
Hi rob,

> **rob86 said:**
> So are XVid and DivX both mpeg4?

They are both implementations of the same standard. Have a look at the few lines here:

[http://ffmpeg.org/faq.html#SEC23](http://ffmpeg.org/faq.html#SEC23)

Andrew

---

