---
title: "MPlayer error &quot;Frame Skip 8&quot;"
date: 2009-02-11
forum: Multimedia Software
---

### Post by redjedi on 2009-02-11
Hi guys

This is my first post as I've always been able to solve my Ubuntu issues from previous threads, but this one has got me stumped.

I've got a group of .avi videos which when I play with MPlayer I get an error box appear which just says 

"ERROR! Frame skip 8".

I am able to click OK and the video carries on but will regularly pop up during playback. It usually re-appears when there is a scene/camera change.

I can play other .avi (and all other movie types) without any issues, it's just this one group (Lost season 1 - I'm a little behind :P )

These files play fine in VLC or TOTEM, but I don't like using them as I get "flickering" lines when there is any fast movement, I think this is an ATI driver issue, even though I have the latest driver installed, but I managed to find settings in MPlayer which allows good playback (with Compiz turned off).

I've opened MPlayer with the Terminal and get this

> MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option msglevel: Unknown suboption 5
Warning unknown option msglevel at line 6
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[GUI] Adding video filter: pp

Playing /home/luke/Desktop/Lost - s01e11 - All the Best Cowboys Have Daddy Issues.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
Forced NON-INTERLEAVED AVI file format.
VIDEO:  [XVID]  608x336  12bpp  23.976 fps  1038.6 kbps (126.8 kbyte/s)
Clip info:
 Software: VirtualDub
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [pp]
Opening video filter: [scale]
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
[PP] Using external postprocessing filter, max q = 6.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 608 x 336 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.81:1 - prescaling to correct movie aspect.
[swscaler @ 0x89662f0]SwScaler: using unscaled yuv420p -> rgb32 special converter
VO: [gl] 608x336 => 608x336 BGRA 
[mpeg4 @ 0x896b2d0]frame skip 8t:  0.000   1/  1 ??% ??% ??,?% 0 1              
[mpeg4 @ 0x896b2d0]frame skip 8t:  0.007   6/  6 ??% ??% ??,?% 5 0              
A:   4.3 V:   4.2 A-V:  0.077 ct:  0.004 102/102 26% 42%  3.0% 33 0             
  =====  PAUSE  =====


I'm afraid this doesn't mean anything to me, as I'm very new to Linux.

I'm using the GL driver for playback, but I've tried the others without any luck (I've also tried a few different audio outputs with no change)·

This is really annoying as it took me weeks to get video playback working without any flickering (finally got it with a fresh install, this week, and took things one step at a time), then this.

It is only this one group of files at the moment, so not the end of the world , but it does bug me.

Your help would be much appreciated.

Thank you

Red

p.s. If you need any other read-outs from Terminal, you will need to talk me through it, as I don't know how to do much in it yet.

---

### Post by lazyfirecloud on 2009-04-10
It's probably not very useful information but I get the same problem when watching Bleach except it only happens once at the beginning. I couldn't never really get other players to work properly =(

---

### Post by andrew.46 on 2009-04-10
Hi,

There are few things to try. The first would be to upgrade your copy o MPlayer to a more recent svn version, there are detailed guides for this available on these forums. If the problem persists [the MPlayer FAQs]("http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ") gives a few strategies under 'General Questions' that might well be worth trying.

Andrew

---

### Post by alcCapone on 2009-05-17
Got the same problem with gmplayer.

---

### Post by shusai on 2009-06-15
I also had this error but adding "-really-quiet" solved it.

The entry in System->Preferences->Main Menu->Sound & Video->MPlayer Movie Player now is:
```
gmplayer -really-quiet %F
```

---

### Post by yang_hui1986527 on 2009-12-29
Got the same problem

---

