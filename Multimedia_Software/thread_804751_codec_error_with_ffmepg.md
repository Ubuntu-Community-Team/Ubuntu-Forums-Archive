---
title: "codec error with ffmepg"
date: 2008-05-23
forum: Multimedia Software
---

### Post by rabid9797 on 2008-05-23
hey all, ive tried the ffmpeg forums, but they aren't as active as i would like, so i would see if anybody here can help me.

im having a(what i think must be) simple problem converting a video with ffmpeg.

here is what i am doing atm:

```

**ffmpeg -i "1. Pole to Pole.avi" -aspect 16:9 -b "6366 kb/s" -vcodec mpeg4 -ac 6 -ab "384 kb/s" poletopole.avi**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, avi, from '1. Pole to Pole.avi':
  Duration: 00:48:12.4, start: 0.000000, bitrate: 6366 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 1280x720, 25.00 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, 5:1, 384 kb/s
File 'poletopole.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'poletopole.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 1280x720, q=2-31, 6366 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 48000 Hz, 5:1, 384 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

so as you can see..i've got almost everything specified. can anybody help me in figuring out what it is that is incorrect in my parameters? thanks

---

### Post by rabid9797 on 2008-05-23
nevermind, i figured it out, i hadn't specified the audio codec for the output file.

---

