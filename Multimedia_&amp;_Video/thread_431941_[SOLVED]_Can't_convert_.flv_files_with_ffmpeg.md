---
title: "[SOLVED] Can't convert .flv files with ffmpeg"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by Megaqwerty on 2007-05-03
I used to be able to convert flv files to avi, wmv, etc. with ffmpeg, but recently it has been giving me errors.

```

$ ffmpeg -i /tmp/FlashxdaJkS.flv -ab 56 -ar 22050 -b 500 -s 800x600 /tmp/FlashxdaJkS.avi >data.txt
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
...
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7f9b2d0]Unsupported video codec (4)
[flv @ 0xb7fb22d0]Unsupported video codec (4)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from '/tmp/FlashxdaJkS.flv':
  Duration: 00:09:58.5, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, stereo
  Stream #0.1: Video: 0x0004, 15.00 fps(r)
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, avi, to '/tmp/FlashxdaJkS.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 800x600, q=2-31, 500 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, stereo, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec (id=0) for input stream #0.1

```

Does anyone know why this is happening/how to fix it?

-Megaqwerty

---

### Post by Megaqwerty on 2007-05-08
*bump*

---

### Post by headchange on 2007-07-24
yeah i dont know im gettin the same error :/

---

### Post by Megaqwerty on 2007-08-10
I have solved the problem by building ffmpeg from SVN source. It works flawlessly now.

-Megaqwerty

---

### Post by deepesh on 2007-12-01
Thanks. It solved the same problem for me too.
Deepesh

---

