---
title: "Ipod video convert"
date: 2008-05-24
forum: Multimedia Software
---

### Post by iceotope on 2008-05-24
Hi

I want to convert an avi (Video codec: XVID MPEG-4 and Audio codec: AC-3) to MPEG4 for my ipod, but it fails.

What is wrong? What codec do i need and where do I get it?

 ffmpeg -i test.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec mp3 -ar 44100 -ab 192 -s 320x240 -aspect 4:3 test.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, avi, from 'test.avi':
  Duration: 00:41:46.5, start: 0.000000, bitrate: 2334 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 960x528, 25.00 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, stereo, 384 kb/s
File 'test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'test.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=3-5, 0 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

---

### Post by FakeOutdoorsman on 2008-05-25
ffmpeg from the Ubuntu repo hasn't been compiled with mp3 support, so you should use the the [Medibuntu]("http://www.medibuntu.org/") repository which has ffmpeg compiled with restricted formats.  Also see: [iPod Video Encoding]("https://wiki.ubuntu.com/iPodVideoEncoding") on Ubuntu Wiki.

---

