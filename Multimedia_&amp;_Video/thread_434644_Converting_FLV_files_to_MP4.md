---
title: "Converting FLV files to MP4"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by Skootle on 2007-05-06
Hi there. I'm trying to convert FLV files I've downloaded from YouTube to watch them on my iPod Video. I know there are quite a few HowTo's and Tutorials on this forum, but none of them seem to work for me... :confused: 

First of all, I've tried using this command:
```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 video.mpg
```
but I get the following output (and a corrupted MPEG file):
```
fabian@fabian-desktop:~$ ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 video.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'video.flv':
  Duration: 00:03:29.0, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, mono
  Stream #0.1: Video: flv, yuv420p, 320x240, 15.00 fps(r)
Output #0, mpeg, to 'video.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, q=2-31, 500 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mpeg1video @ 0xb7e7ff08]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

I've also tried installing Vive!, but when I try to convert the file, it just closes (**Segmentation fault (core dumped)**).

I have no idea what I'm doing wrong. Any help is greatly appreciated! :) Thanks.

---

