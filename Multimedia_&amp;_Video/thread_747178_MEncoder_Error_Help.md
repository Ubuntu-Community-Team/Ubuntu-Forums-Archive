---
title: "MEncoder Error Help"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by Literati on 2008-04-06
Hi all,

I looked up how to use MEncoder, and I THOUGHT I did it right, but I suppose not.
From start to finish, this is what my terinal looks like:

root@Matt:/home/matt# mencoder /home/matt/Videos/Cloverfield.DVDRip.XviD-DiAMOND/dmd-cloverfield.avi -o Cloverfield.avi -oac copy -ovc x264 vcodec=mpeg4
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 5)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x2bc0e000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  974.3 kbps (118.9 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:624x352  fps:23.98  ftime:=0.0417
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
audiocodec: framecopy (format=55 chans=2 rate=48000 bits=0 B/s=21112 sample-0)
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar I420 as output csp (no 1)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities MMX MMXEXT SSE SSE2 
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: vprp aspect is 16384:9242.
Writing header...
ODML: vprp aspect is 16384:9242.
File not found: 'vcodec=mpeg4'35fps Trem:   0min 460mb  A-V:0.022 [591:168]
Failed to open vcodec=mpeg4.
Cannot open file/device.

Exiting...

Do I not have the codec installed? Because I could've sworn that I did.

---

### Post by Literati on 2008-04-06
Bump

---

