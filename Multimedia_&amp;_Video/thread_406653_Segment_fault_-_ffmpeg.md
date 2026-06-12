---
title: "Segment fault - ffmpeg"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by musse1 on 2007-04-11
This is what I get when I try to encode videos to .flv files with ffmpeg. Some files work, some don't. Any ideas why I get segment fault?


root@server:/home/server# ffmpeg -i /var/www/www/stream/final/video/Fight.wmv -s
 320x240 -ar 44100 /var/www/www/stream/final/video/movie.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --ena
ble-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp
3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Apr 11 2007 11:43:44, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-
13ubuntu5)

Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from '/var/www/www/stream/final/video/Fight.wmv':
  Duration: 00:00:45.1, start: 2.000000, bitrate: 1345 kb/s
  Stream #0.0: Video: msmpeg4v2, yuv420p, 320x240, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 64 kb/s
Output #0, flv, to '/var/www/www/stream/final/video/movie.flv':
  Stream #0.0: Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault
root@server:/home/server#

---

### Post by musse1 on 2007-04-11
Help please.

---

### Post by musse1 on 2007-04-16
No one?

---

### Post by musse1 on 2007-04-17
Help!

---

### Post by madd02 on 2007-04-18
Hello musse1,
i have hit the same problem. Were you able to get your install of ffmpeg to work?

---

### Post by robertmf on 2007-10-09
[COLOR="DarkRed"]Same segmentation fault using Feisty ffmpeg.  Shiat.  mencoder is broken ... tovid switched from mpeg2enc to ffmpeg so now I have nada to encode an .AVI to .mpg
[/COLOR]

---

