---
title: "No sound when playing .wmv"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by krusk on 2007-05-06
Hi 

I have a 64-bit feisty ubuntu system. I have installed codecs and videoplayers with automatix, so i think I have most of the codecs available installed. Im not certain about that, because i cant seem to find w32codecs in any repositories (is that because of my 64-bit system?).

Anyway, my problem is that i cant sound on certain .wmv files. There is no problem with avi, mp3 so on, only with some wmvs. I get video, but no sound. Its the same problem with every player; vlc, mplayer, xine and totem.

Here's my mplayer command line output, when trying to run one of these files:

```
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Dual Core AMD Opteron(tm) Processor 165    (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 07_0427_Joe_DrMatt_HU_Holecards.wmv.
ASF file format detected.
VIDEO:  [WMV3]  800x608  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0xf04c30]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Forced audio codec: mad
Requested audio codec family [wma9spdmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wma9spdshow] (afm=dshow) not available.
Enable it at compilation.
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 800 x 608 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 800x608 => 800x608 Planar YV12  [zoom]
SwScaler: using unscaled yuv420p -> rgb32 special converter
V:   7.1  32/ 32 11% 10%  0.0% 0 0 
Exiting... (Quit)

```

Any ideas for a quick fix? Thanks

---

### Post by mhenry35 on 2007-06-19
I have the same problem - But in my case, the file played before I upgraded from Feisty to Ubuntu Studio.

I double click the file - It does a missing codec search - it finds gstream (which is already installed) so I tried installing it again, but no luck.

---

