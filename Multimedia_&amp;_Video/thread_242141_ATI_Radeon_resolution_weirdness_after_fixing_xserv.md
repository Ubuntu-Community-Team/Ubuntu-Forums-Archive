---
title: "ATI Radeon: resolution weirdness after fixing xserver-xorg-core"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by bbolker on 2006-08-23
Installed Ubuntu a few days ago, everything was autodetected
fine.  Was caught by the xserver-xorg-core upgrade, but managed
to delay until the update was available.

  Installed upgrade; tried reinstalling ATI proprietary drivers
(linux-restricted-modules-2.6.15-26-386 2.6.15.11-3, 
 xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3)

  The problem now is that no resolution above 1024x768
seems to work reliably any more.   Resolutions up to 1400x1050
are listed, and the screen responds, but the video is somewhat
mangled (still recognizable, but chunks are in the wrong place).
Have tried restarting gdm, rebooting, etc..  I could try setting
the resolution and then rebooting, but I'm afraid I'll end up
with an unusable video setting.

  Any clues?

ben@bolker-lap:~$ lspci -n | grep 0300
0000:01:00.0 0300: 1002:4c66 (rev 02)
ben@bolker-lap:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

---

### Post by bbolker on 2006-08-24
hmm.  problem appears to have gone away.

 Could have been hardware, since I've got
a few-year-old, hard-used laptop that's
beginning to get flaky.

  Ben Bolker

---

### Post by cneil on 2006-08-24
No, I am having a similar problem.  I started using the driver fglrx and I stopped using ATI so that I could run compiz.  Now the highest resolution that I can get is 1024x768.  I am running a gateway 7510GX laptop with an x600 ATI card.
the output from fglrxinfo is the following
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

here's a bit of my xorg.conf file
Section "Device"
	Identifier  "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"

If anyone can help I would appreciate it greatly.  I  should be able to run at 1200x800.
Thanks!

---

