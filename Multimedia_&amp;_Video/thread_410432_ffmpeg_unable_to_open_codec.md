---
title: "ffmpeg unable to open codec"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by klugja on 2007-04-15
I have edgy ffmpeg 3.0.cvs20060823-3.1ubuntu1

How do I determine the cause of this 2 pass ffmpeg problem?  If I use only one pass, I get buffer underrun errors.  I can't get 2 pass started at all.  I have tried the default and 704x480 for NTSC DVD.  I was hoping that with 2 pass, ffmpeg would pick the bit rate.  Any suggestions?

+ ffmpeg -pass 2 -i UKC4DocumentaryTheGr.avi -passlogfile /backup/video/UKC4DocumentaryTheGr -target ntsc-dvd /backup/video/UKC4DocumentaryTheGr.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Input #0, avi, from 'UKC4DocumentaryTheGr.avi':
  Duration: 01:13:32.3, start: 0.000000, bitrate: 1053 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x360, 30.00 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, dvd, to '/backup/video/UKC4DocumentaryTheGr.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, pass 2, 6000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

