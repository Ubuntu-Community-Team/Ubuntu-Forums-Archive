---
title: "ffmpeh error"
date: 2008-11-25
forum: Multimedia Software
---

### Post by lsutiger on 2008-11-25
I recently did a few changes in audio/video setup because the mplayer plugin did not work in Firefox. Now I can not convert flv vids. Here is the error I am getting:
```
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```
The code I am using is a simple ffmpeg -i <inputfile> <outputfile>.
Here is the rest of the output:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'freestyle.flv':
  Duration: 00:03:38.4, start: 0.000000, bitrate: 64 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 15.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Output #0, mpeg, to 'freestyle.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg1video @ 0xb7e459a8]MPEG1/2 does not support 15/1 fps

```

What should I do?

---

### Post by FakeOutdoorsman on 2008-11-26
Looks like MPEG-1 doesn't support 15 frames per second, so you can try to force a frame rate, although I don't know how it will affect your video.
```
ffmpeg -i input.flv -r ntsc output.mpg
```
Another option is to try something else, such as mpeg4, which may support 15 fps.

---

### Post by lsutiger on 2008-11-26
Thanx!! It worked!
I will read the man page and figure out what frame rate works best.

---

