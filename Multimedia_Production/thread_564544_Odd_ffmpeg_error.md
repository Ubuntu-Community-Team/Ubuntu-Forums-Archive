---
title: "Odd ffmpeg error"
date: 2007-10-01
forum: Multimedia Production
---

### Post by anton_pm on 2007-10-01
Hi Guys,

I'm getting the following error when encoding using ffmpeg:

root@anton-main:/usr/local/src/ffmpeg# ffmpeg -i /media/80_ATA/Arrested\ Development/arrested.development.301.hdtv-lol.\[VTV\].avi -y -vcodec libx264 -acodec libfaac -title test -mbd rd -flags dct8x8+skiprd -level 41 -b 1500 -bf 3 -ac 2 -ab 128 -threads 1 /home/anton/
FFmpeg version SVN-r10629, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-pthreads --enable-gpl --enable-libx264 --enable-libfaac
  libavutil version: 49.5.0
  libavcodec version: 51.44.0
  libavformat version: 51.14.0
  built on Oct  1 2007 14:07:57, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from '/media/80_ATA/Arrested Development/arrested.development.301.hdtv-lol.[VTV].avi':
  Duration: 00:21:15.6, start: 0.000000, bitrate: 1147 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
ffmpeg: unrecognized option '-flags'


Not too sure what that unrecognized flag is all about.

I compiled with:

./configure --enable-pthreads --enable-gpl --enable-libx264 --enable-libfaac

---

### Post by anton_pm on 2007-10-01
Think i've been a bit of a mug and put a typo in, should be -flags2 not -flags.

---

