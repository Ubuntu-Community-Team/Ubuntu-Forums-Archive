---
title: "ffmpeg no worky"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by rickycodie on 2007-06-18
this is the output of what happens when i try to convert a .flv to mpeg 

ricky@ricky-laptop:~$ ffmpeg -i firefly2.flv -ab 64 -ar 44100 -b 500 -s 160x128 firefly2.mpeg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 12.00 (12/1)
Input #0, flv, from 'firefly2.flv':
  Duration: 00:42:44.4, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, mono
  Stream #0.1: Video: flv, yuv420p, 540x294, 12.00 fps(r)
File 'firefly2.mpeg' already exists. Overwrite ? [y/N] y
Output #0, mpeg, to 'firefly2.mpeg':
  Stream #0.0: Video: mpeg1video, yuv420p, 160x128, q=2-31, 500 kb/s, 12.00 fps(c)
  Stream #0.1: Audio: mp2, 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mpeg1video @ 0xb7e08508]MPEG1/2 does not support 12/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

 i set the programs to the defaults and still it won't work.  any ideas?

---

### Post by david_2001 on 2007-06-18
Try forcing the framerate to 24 or 25 fps, e.g.:
```
ffmpeg -i firefly2.flv -ab 64 -ar 44100 **-r 24** -b 500 -s 160x128 firefly2.mpeg
```

---

### Post by rickycodie on 2007-06-18
it worked yay!!!

---

