---
title: "Fullscreen Video Error, partial screen freeze"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by NS2-10 on 2008-03-19
Hi,

I have a weird error that I don't even know where to begin with.

***When I go to fullscreen video only the top left corner of the screen, roughly a quarter, updates while the rest freezes showing only black! ***

Also when I take screenshots only that bit ends up in the picture. Strange indeed!!!

I use compiz fusion with a number of effect and extensions. Sometimes I wonder if its wobbly windows but I don't know. I think it started when I installed Feisty and Compiz. Please help me! I hate not being able to watch fullscreen videos!!

---

### Post by xc3RnbFO8P on 2008-03-19
Try to run the video program in terminal and  post it here.

---

### Post by NS2-10 on 2008-03-22
This is what I get when I run mplayer in forced fullscreen with a random movie. I am a little suspisiouce about the screensaver thing because I have a screensaver issue as well. The problem with that is that the screensaver kicks in every 10 min regardless of the fact that I turned it off. Don't know if the two are connected though.

> 
[email]dlang@dlang-laptop:~/Movies/Into.The.Blue[/email][2005]DVDrip[ENG]-MissRipZ$ mplayer -vo xv -fs -zoom Into.The.Blue\[2005\]DVDrip\[ENG\]-MissRipZ.avi
 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Into.The.Blue[2005]DVDrip[ENG]-MissRipZ.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [XVID]  576x240  12bpp  25.000 fps  822.5 kbps (100.4 kbyte/s)
Clip info:
 Software: AVI-Mux GUI 1.17.7, Aug  8 2006  20:59:17
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 32000 Hz, 2 ch, s16le, 96.0 kbit/9.38% (ratio: 12000->128000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 576 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.40:1 - prescaling to correct movie aspect.
VO: [xv] 576x240 => 576x240 Planar YV12  [fs] [zoom]
gnome_screensaver_control()00 ct:  0.000 344/344  2%  0%  2.4% 2 0 
Exiting... (Quit)


---

