---
title: "converting flv to mpg using ffmpeg ... troubles"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by cvmostert on 2006-10-16
Hi there, I do not know what i did wrong, but something is not as it was.

I could convert .flv files with ffmpeg to .mpg files.. 

Then I installed the latest ffmpeg and that must have been the mistake... 

i could not see ffmpeg.. or the link was wrong... bottom line... didnt work.

THEN I uninstalled ffmpeg and installed the ffmpeg from the repositories...

now i can use ffmpeg... but it does not want to convert flv to mpg... this is the output i get:

>   ffmpeg -i n70assembly.flv -ab 56 -ar 22050 -b 500  -s 320x240 testn70.mpg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Oct  4 2006 10:57:36, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 14.92 (194/13)
Input #0, flv, from 'n70assembly.flv':
  Duration: 00:07:31.6, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, mono
  Stream #0.1: Video: flv, yuv420p, 320x240, 1000.00 fps
Output #0, mpeg, to 'testn70.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, 15.00 fps, q=2-31, 500 kb/s
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mpeg1video @ 0x8336c48]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


IF anyone has had and solved the problem.. please help.. 

Ideas will be welcome too..

ps. or is it actually true that mpeg does not support 15fps?

---

### Post by hulet on 2006-10-16
> **cvmostert said:**
> Hi there, I do not know what i did wrong, but something is not as it was.

I could convert .flv files with ffmpeg to .mpg files.. 

Then I installed the latest ffmpeg and that must have been the mistake... 

i could not see ffmpeg.. or the link was wrong... bottom line... didnt work.

THEN I uninstalled ffmpeg and installed the ffmpeg from the repositories...

now i can use ffmpeg... but it does not want to convert flv to mpg... this is the output i get:



IF anyone has had and solved the problem.. please help.. 

Ideas will be welcome too..

ps. or is it actually true that mpeg does not support 15fps?

Can you try the mpeg4 codec? -just add the "-vcodec mpeg4" without the quotes to your command above.

---

