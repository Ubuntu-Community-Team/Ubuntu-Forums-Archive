---
title: "ffmpeg won't change video frame rate"
date: 2008-10-02
forum: Multimedia Software
---

### Post by nixscripter on 2008-10-02
Hello.

I'm trying to a rather odd conversion: a set of FLVs to MPEG-2 transport streams. The command I'm using is:

```
ffmpeg -i myvid.flv -s 480x360 -b 384k **-r 30** -f mpegts -
```

Most of the time it works. However, some FLVs are encoded differently than others, and I sometimes get this error:

```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-shared --prefix=/home/video/software
libavutil version: 49.3.0
libavcodec version: 51.38.0
libavformat version: 51.10.0
built on Mar 15 2008 19:17:26, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'myvid.flv':
Duration: 00:00:52.1, start: 0.000000, bitrate: 64 kb/s
Stream #0.0: Video: flv, yuv420p, 160x120, 15.00 fps(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Output #0, mpegts, to 'pipe:':
Stream #0.0: Video: mpeg2video, yuv420p, 480x360, q=2-31, 384 kb/s, **15.00 fps(c)**
Stream #0.1: Audio: mp2, 22050 Hz, mono, 64 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
[mpeg2video @ 0xb7e64188]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


```

If I remember right, the MPEG-2 standard doesn't support 15 fps. That's why I'm trying to raise it.

Why isn't the command working?

---

