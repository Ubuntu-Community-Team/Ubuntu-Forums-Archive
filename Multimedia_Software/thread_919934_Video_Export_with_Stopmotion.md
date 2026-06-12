---
title: "Video Export with Stopmotion"
date: 2008-09-14
forum: Multimedia Software
---

### Post by xchecker on 2008-09-14
I am having trouble exporting video from Stopmotion v0.6.0-1.  I use Heron 8.04.

I have tried both mencoder and ffmpeg as the encoder, but neither works.  For example, if I choose mencoder for mpeg4 output with the default encoding command I get a 'Failed' message with this:

```
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/crichmond/.stopmotion/packer/The*
[mf] number of files: 1 (4)
VIDEO:  [IJPG]  0x0  24bpp  8.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps: 8.00  ftime:=0.1250
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================

Exiting...

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
File not found: 'Star'
Failed to open Star.
Cannot open file/device.
```

If I choose ffmpeg as the encoder, then I get an error message that the encoder is not valid.

Has anyone got this function working and could offer suggestions?  Thanks.

---

### Post by Yellow Pasque on 2008-09-14
What version of Ubuntu are you using? I hope you're using 64-bit Ubuntu since you're working with video. I've built an amd64 .deb for stopmotion 0.6.2-1. I suppose I could build an x86 version too.

---

### Post by xchecker on 2008-09-15
Yes 64-bit, Edubuntu specifically.

---

### Post by adambh on 2010-09-03
How is this "solved"? Care to share?

---

### Post by shanefiddle on 2011-06-28
Hmmm... It appears this thread died without a solution.  I am having this problem as well:  two windows appear shortly after I try to export to mpeg video, one that says Failed! and the other which contains the following:

[FONT="Arial Narrow"][SIZE="1"]FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
/home/fiddlehomusic/.stopmotion/packer/turn the page/images/%06d.jpg: I/O error occurred
Usually that means that input file is truncated and/or corrupted.[/SIZE][/FONT]

Any brave souls care to wade in with a guess?  I'm stumped.

---

### Post by magpiie on 2012-02-18
I am having the same issue. no matter what encoders I install I still cannot export the video. any help please?

---

