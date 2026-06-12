---
title: "video files: X11 error: BadAlloc (insufficient resources for operation)"
date: 2008-10-30
forum: Multimedia Software
---

### Post by codilx on 2008-10-30
hi there,

I can't get any video to work. totem crashes instantly when pressing play, so I tried it with mplayer, here's what I got:

root@LittleBrother:~# mplayer /media/disk/Users/iPC/Documents/Downloads/Clarkson.Thriller.DVDRip.XviD-HAGGiS/clarkson.thriller.dvdrip.xvid-haggis.avi 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/disk/Users/iPC/Documents/Downloads/Clarkson.Thriller.DVDRip.XviD-HAGGiS/clarkson.thriller.dvdrip.xvid-haggis.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  25.000 fps  1101.5 kbps (134.5 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
VO: [xv] 640x352 => 640x352 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.4% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.4% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.4% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.4% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.4% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.4% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.5% 1 0 
X11 error: BadAlloc (insufficient resources for operation)1.5% 1 0 
GNOME screensaver enabled.004 ct:  0.004  25/ 25 18%  0%  1.5% 1 0 

Exiting... (Quit)

---

### Post by codilx on 2008-10-31
anyone?

---

### Post by Embedded Linux Guy on 2008-11-02
Try 

mplayer -vo x11 filename

If you're lucky you might get fullscreen with

mplayer -vo x11 -zoom filename

---

### Post by thanhquanky on 2011-03-26
@Embedded Linux Guy: I have the same problem and your solution works! :)

---

