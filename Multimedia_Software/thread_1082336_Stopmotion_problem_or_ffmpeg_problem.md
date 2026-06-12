---
title: "Stopmotion problem or ffmpeg problem?"
date: 2009-02-27
forum: Multimedia Software
---

### Post by The_Real_Anna on 2009-02-27
I tried to export my animation to video and this is the error I got:

> FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, image2, from '/home/anna/.stopmotion/packer/test/images/%06d.jpg':
  Duration: 00:00:00.8, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj440p, 240x320 [PAR 0:1 DAR 0:1], 10.00 tb(r)
Unable to find a suitable output format for '/home/anna/Pictures/Kids/kids'

So what's going on? :mad:
I am using Ubuntu Intrepid

---

### Post by FakeOutdoorsman on 2009-02-27
You could blame both.  You need to give the exported movie an extension so FFmpeg knows what type of video you want: .mp4, .ogg, .mpg, .avi, etc.  It doesn't help that stopmotion doesn't use optimal encoding settings for exporting.  To be able to encode to mpg and mp4 you will need to install the **libavcodec-unstripped-51** package.

Nooooo!  The 1000th post.  I never knew I was a nerd until now.  Curse you, Ubuntu!  Look at what you've done to me!

---

### Post by The_Real_Anna on 2009-03-02
> **FakeOutdoorsman said:**
> You could blame both.  You need to give the exported movie an extension so FFmpeg knows what type of video you want: .mp4, .ogg, .mpg, .avi, etc.  It doesn't help that stopmotion doesn't use optimal encoding settings for exporting.  To be able to encode to mpg and mp4 you will need to install the **libavcodec-unstripped-51** package.

Nooooo!  The 1000th post.  I never knew I was a nerd until now.  Curse you, Ubuntu!  Look at what you've done to me!


I did that and still nothing. Same error:

---

### Post by katoiam on 2009-08-19
I am also having a problem with exporting video with stop motion, can any one help
thanx
I get this output now:
swScaler: Compile-time maximum width is 2048 change VOF/VOFW and recompile
Cannot get resampling context
any ideas, is it to do with the size of my pictures?

---

### Post by katoiam on 2009-08-24
any one?:confused:

---

### Post by Philabrow on 2010-09-29
I'm also having problems with ffmpeg, this is what I get

```
 p, li { white-space: pre-wrap; } FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
   configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
   libavutil     49.15. 0 / 49.15. 0
   libavcodec    52.20. 0 / 52.20. 0
   libavformat   52.31. 0 / 52.31. 0
   libavdevice   52. 1. 0 / 52. 1. 0
   libavfilter    0. 4. 0 /  0. 4. 0
   libswscale     0. 7. 1 /  0. 7. 1
   libpostproc   51. 2. 0 / 51. 2. 0
   built on Apr 23 2010 15:08:34, gcc: 4.3.3
 /home/philip/.stopmotion/packer/bollocks/images/%3d.jpg: I/O error occurred
 Usually that means that input file is truncated and/or corrupted.
 
```

---

### Post by theepdinker on 2011-01-04
Here is how I was able to get Stopmotion to work

[http://ubuntuforums.org/showthread.php?t=1659325&highlight=stopmotion](http://ubuntuforums.org/showthread.php?t=1659325&highlight=stopmotion)

---

