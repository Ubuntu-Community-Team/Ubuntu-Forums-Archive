---
title: "mplayer works, but no skin :-("
date: 2008-11-23
forum: Multimedia Software
---

### Post by mmcmonster on 2008-11-23
I installed mplayer in Ubuntu Intrepid.  Actually, I installed mplayer, mplayer-fonts, mplayer-skin-blue, and mplayer-skins.  mplayer works fine when I play a file by double-clicking on it in nautilus.

The problem is, once the video is running, there is no skin.  Also, right-click on a running video doesn't bring up a context menu, so I can't change the skin (or any other options).

This happens even when I delete ~/.mplayer/.

When I run mplayer from the command line, I get the following (note that I pressed a mouse button during video play, and mplayer says that the button is not bound):
```
$ mplayer 1.avi 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/karthik/.mplayer/config
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 1.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  1063.6 kbps (129.8 kbyte/s)
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
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
No bind found for key 'MOUSE_BTN2'.                         7% 0 0 
GNOME screensaver enabled.002 ct: -0.008  79/ 79  7%  0%  1.6% 0 0 

Exiting... (Quit)

```

---

### Post by mc4man on 2008-11-23
If you want a gui (skin) then you need to run gmplayer, either from the applications menu, cli (gmplayer...) or set a file association pointing to it (gmplayer

If wanting a gui you might consider using smplayer instead of the default gui (gmplayer
It's far, far superior.

[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)

You could add the appropriate repo to software sources -. third party, this will allow you to install a good, recent mplayer build and latest smplayer.

---

### Post by mmcmonster on 2008-11-23
Damn!  I used to know this.  Thanks!

---

