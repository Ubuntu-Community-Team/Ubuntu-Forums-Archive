---
title: "convert flv to mp3"
date: 2009-09-10
forum: Multimedia Software
---

### Post by yaron86 on 2009-09-10
i wrote in terminal:
youtube-dl URL
and it download to my home folder a file named "xi1BMP66gGo.flv" and i am tying to convert it to MP3 format but i get some error

when i', writing 
[php]ffmpeg -i xi1BMP66gGo.flv mysong.mp3[/php]it said:
[php]yach@yach-laptop:~$ ffmpeg -i xi1BMP66gGo.flv mysong.mp3
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'xi1BMP66gGo.flv':
  Duration: 00:04:11.11, start: 0.000000, bitrate: 124 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 60 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
Output #0, mp3, to 'mysong.mp3':
    Stream #0.0: Audio: 0x0000, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
yach@yach-laptop:~$ 
[/php]how can i get it fixed?

---

### Post by andrew.46 on 2009-09-10
Hi yaron,

> **yaron86 said:**
> how can i get it fixed?

If you have a quick read of the FakeOutdoorsman's guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

you should be successfully converting your file pretty quickly :).

Andrew

---

### Post by yaron86 on 2009-09-10
ok i saw the guide, i did those command on terminal:
sudo apt-get install ffmpeg libavcodec-unstripped-52
sudo apt-get install ffmpeg ubuntu-restricted-extras
and then i typed:
ffmpeg -i xi1BMP66gGo.flv -acodec libmp3lame -ab 128k rename.mp3
and it worked, i have now the song, thank you. but i have some questions now
what are those parameters? :
-i, -acodec, -ab?

and is there a way to just download the mp3 from youtube without the movieclip and then convert it to mp3?

---

### Post by andrew.46 on 2009-09-10
Hi yaron,

> **yaron86 said:**
> 
what are those parameters? :
-i, -acodec, -ab?

[LIST=1]
[*]-i This marks the input file
[*]-acodec This designates the audio codec. You could also use '-acodec copy' in this case and omit the -ab setting...
[*]-ab This sets the audio bitrate
[/LIST]

> and is there a way to just download the mp3 from youtube without the movieclip and then convert it to mp3?

Not that I am aware of although I am sure there will be somebody who has found a way :).

Andrew

---

