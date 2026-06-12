---
title: "Can't play FLV files with mplayer after upgrading to 7.10"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-10-19
Here's what happens when I try to play FLV files using *mplayer*:> MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.40GHz (Family: 15, Model: 3, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/pdedecker/Desktop/CCN_33_240.flv.flv.
libavformat file format detected.
VIDEO:  [VP6F]  240x192  0bpp  12.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)
What's that all about? It worked fine before I upgraded to 7.04. Is there a way to fix this?

---

### Post by stooshbunutu on 2008-03-11
use vlc player instead

---

