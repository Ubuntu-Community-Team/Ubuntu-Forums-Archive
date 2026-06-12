---
title: "mencoder avi to mp4 hang"
date: 2009-07-26
forum: Multimedia Software
---

### Post by HarmonicaGoldfish on 2009-07-26
Hi - I'm trying to convert an avi file to mp4 using this command


```
mencoder original.avi -o new.mp4 -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg
```

It seemed to start out ok but I've been waiting over 10 minutes now at this point. Here is what has happend to now

```

tracy@tracy-laptop:~$ mencoder VID00006.AVI -o myhouse1.mp4 -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg

MEncoder 2:1.0~rc2-0ubuntu19 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _MPEG_. See -of help.
success: format: 0  data: 0x0 - 0xdd7a424
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x480  24bpp  30.000 fps  3685.8 kbps (449.9 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x480  fps:30.00  ftime:=0.0333
PACKET SIZE: 2048 bytes, deltascr: 245760
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
audiocodec: framecopy (format=2 chans=1 rate=44100 bits=4 B/s=22179 sample-1)
Limiting audio preload to 0.4s.
Increasing audio density to 4.
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
videocodec: libavcodec (640x480 fourcc=3167706d [mpg1])
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
```

any ideas? should I just wait or is something stalled here?

---

### Post by HarmonicaGoldfish on 2009-07-26
killed it. was apparently doing nothing, though using 66% of processor. 
am trying winff instead. seems to be doing something at least.

---

