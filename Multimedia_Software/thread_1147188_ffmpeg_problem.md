---
title: "ffmpeg problem"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Malcy on 2009-05-03
I want to convert some video clips to mpeg2. If I use ffmpeg on the cli or winff or even try to render the file from kdenlive, ffmpeg stops with this fault:

> mb@mbpc:~$ ffmpeg -i 00003.MTS 00003.mpg
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.24. 0
  libavformat   52.31. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 2. 0
  libavfilter    0. 4. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation faultIt doesn't matter what the format of the input file is. I can output these input files to any other format with ffmpeg without a problem but every time I choose a .mpg output this occurs. It all works correctly in a windows install and a Slax Linux install. It also works correctly with the 9.04 64bit install on my laptop (same as this) so clearly it's a local issue.

I have tried uninstalling ffmpeg and reinstalling but I still get the problem. Any ideas?

---

### Post by paul.gevers on 2009-05-03
Looks like you really hit a bug. Consider reporting the bug to Launchpad. On your machine run ```
ubuntu-bug ffmpeg
``` in a console and fill in the web page after you are directed to it.

---

### Post by Malcy on 2009-05-03
Well, so close after the 9.04 install, everything is pretty fresh so I just reinstalled the OS and it now works. I'm not sure at all what caused the problem but I hope that it doesn't reappear. I will report it if it pops up again.

---

