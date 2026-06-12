---
title: "Openshot"
date: 2010-02-16
forum: Multimedia Software
---

### Post by dmfagan9 on 2010-02-16
Hi all-

I have been inching closer and closer to getting openshot to work but am still a ways out I fear. I think (but i may be wrong about this) that i am having problems with the MLT import. I will post some of the outputs I have been getting and if anyone can help I'd really appreciate it. Thanks

...
dylan@dylan-laptop:~/openshot_wizard$ cd ~/mlt/demo
dylan@dylan-laptop:~/mlt/demo$ $ sudo bash mlt_watermark
bash: $: command not found
dylan@dylan-laptop:~/mlt/demo$ ffplay file:///home/dylan/Photos/2010/02/04/mvi_3459.avi 
FFplay version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2003-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
dylan@dylan-laptop:~/mlt/demo$ cd ~/mlt/demo
dylan@dylan-laptop:~/mlt/demo$ sudo bash mlt_watermark
Failed to load "clip2.dv"
Failed to load "watermark1.png"
+-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+
|1=-10| |2= -5| |3= -2| |4= -1| |5=  0| |6=  1| |7=  2| |8=  5| |9= 10|
+-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+
+---------------------------------------------------------------------+
|               H = back 1 minute,  L = forward 1 minute              |
|                 h = previous frame,  l = next frame                 |
|           g = start of clip, j = next clip, k = previous clip       |
|                0 = restart, q = quit, space = play                  |
+---------------------------------------------------------------------+
Current Position:       1000




a new window opened after this but there was no blue icon and no image

THANKS

---

