---
title: "ffmpeg can't read mpeg2 files from Sony camcorder"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by forthekicks on 2007-06-05
I have a sony dcr sr40 camcorder which outputs mpeg2 files. totem cannot read it, while xine seems to read it just fine. my biggest problem is, h/e, that ffmpeg throws an io error on the file and outputs the below

~$ ffmpeg -i M2U00005.mpg -target pal-vcd test.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
M2U00005.mpg: I/O error occured
Usually that means that input file is truncated and/or corrupted.

why is this happening? I am using feisty, btw.

---

