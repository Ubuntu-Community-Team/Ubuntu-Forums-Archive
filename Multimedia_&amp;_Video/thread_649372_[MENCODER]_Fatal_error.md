---
title: "[MENCODER] Fatal error"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by sabb on 2007-12-24
Hi !
sorry, i searched a lot but i didn't find:

i used to convert my avi files on windows with this mencoder script :

> mencoder one.avi -o converted.avi -oac copy -ovc x264 -x264encopts pass=1:subq=5:frameref=6:me=3:bitrate=250:4x4mv:8x8dct:psnr:bframes=16:b_pyramid:qcomp=0.8:keyint=500:weight_b:scenecut=0:b_bias=25 

And i would to do the same on Ubuntu (feisty) but, after a lot of installation (mencoder ... codecs ... mplayer ... vlc etc ...) i can't resolve this problem:
> FATAL: Cannot initialize video driver.

There is the complete report:
> 
mencoder [I-A]_Seto_no_Hanayome_-_07_[49A40594].avi -o [I-A]_Seto_no_Hanayome_-_07_[49A40594].avi.light -oac copy -ovc x264 -x264encopts pass=1:subq=5:frameref=6:me=3:bitrate=250:4x4mv:8x8dct:psnr:bframes=16:b_pyramid:qcomp=0.8:keyint=500:weight_b:scenecut=0:b_bias=25 
MEncoder 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU          220  @ 1.20GHz (Family: 6, Model: 22, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option x264encopts: Bad argument me=3
Option x264encopts: Unknown suboption 4x4mv
success: format: 0  data: 0x0 - 0xc0a2800
AVI file format detected.
VIDEO:  [XVID]  704x396  24bpp  23.976 fps  985.6 kbps (120.3 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:704x396  fps:23.98  ftime:=0.0417
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
audiocodec: framecopy (format=55 chans=2 rate=48000 bits=0 B/s=16227 sample-0)
VDec: vo config request - 704 x 396 (preferred colorspace: Planar YV12)
VDec: using Planar I420 as output csp (no 1)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
FATAL: Cannot initialize video driver.

Exiting...


THX and merry chrismas !
Sabb

---

### Post by sabb on 2007-12-25
up x) :guitar:

---

### Post by sabb on 2007-12-26
up plz :D :popcorn:

---

### Post by cor2y on 2007-12-26
i think this has more to do with your encoding argument than anything else.
Not too familiar with x264 encoding in linux but mencoder has no idea what the arguments are.
```

Option x264encopts: Bad argument me=3
Option x264encopts: Unknown suboption 4x4mv
```And also if i remember correctly the early versions x264 had a scaling limit meaning videos have to be resized to a specific scale before encoding can occur, don't ask me what it is because i forget :) don't quote me on it but i believe its a multiple of 4 or 8.
You might have to custom compile mplayer/mencoder ffmpeg and x264 from svn and see if you can encode then but i think its your x264 encoding arguments.
See the mencoder manual page on x264 to get an idea of what arguments to use for a proper encode.

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html)

---

### Post by sabb on 2007-12-26
thx very much !
I'll read this doc and see what to do.

have a good day ;)
Sabb

---

