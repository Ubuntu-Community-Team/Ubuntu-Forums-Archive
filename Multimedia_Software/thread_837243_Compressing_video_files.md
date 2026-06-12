---
title: "Compressing video files"
date: 2008-06-22
forum: Multimedia Software
---

### Post by ianq on 2008-06-22
Folks, under Windows I frequently employ DivX Converter to compress some video files. Does anyone know of a program under Ubuntu that can do the same in the command line? Thanks a lot in advance!

---

### Post by Major_Kong on 2008-06-22
mencoder

---

### Post by ma_nkooo on 2008-06-22
Use Avidemux.

link- [http://www.avidemux.org/admWiki/index.php?title=Main_Page](http://www.avidemux.org/admWiki/index.php?title=Main_Page)

---

### Post by ianq on 2008-06-22
Avidemux looks like it utilizes a GUI. Trying mencoder now...

---

### Post by aeiah on 2008-06-22
as well as mencoder, there is ffmpeg. they're very similar. most gui applications for converting video will use either mencoder or ffmpeg under the hood. i advise using the xvid codec rather than divx. they're very similar. the best size vs quality codec around right now is x264 however, but it can get complicated

---

### Post by ianq on 2008-06-22
Well, complicated is bad seeing that I'm still trying to figure out how to compile mencoder lol

---

### Post by xc3RnbFO8P on 2008-06-22
Try:
> sudo apt-get install mencoder

---

### Post by ianq on 2008-06-22
Got it, cool. Can anybody explain why the following isn't working?

root@inetserv:/home/movies# mencoder "video.avi" -vf crop=714:548:0:14 -oac copy -ovc lavc \ -lavcopts vcodec=mpeg4:mbd=2:trell:autoaspect -o "video_small.avi"
MEncoder 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 1.70GHz (Family: 15, Model: 1, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

success: format: 0  data: 0x0 - 0x2bc52800
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  576x288  12bpp  23.976 fps  574.8 kbps (70.2 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:576x288  fps:23.98  ftime:=0.0417
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [crop w=714 h=548 x=0 y=14]
Crop: 714 x 548, 0 ; 14
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
audiocodec: framecopy (format=2000 chans=6 rate=48000 bits=0 B/s=48000 sample-1)
VDec: vo config request - 576 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.00:1 - prescaling to correct movie aspect.
[CROP] Bad position/width/height - cropped area outside of the original!
FATAL: Cannot initialize video driver.

Exiting...

~Edit~
Never mind, I got it. Didn't see the original video's size ;)

---

