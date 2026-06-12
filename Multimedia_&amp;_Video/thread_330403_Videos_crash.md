---
title: "Videos crash??"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by Silent Warrior on 2007-01-03
Uh, well, I can't play any video-file without having Ubuntu reboot. Doesn't seem to matter which video-player I use, they all crash. Now, I think I managed to work out which settings to use when I had 6.6, but those have been lost in time. I don't suppose anyone can tell me right off what codec/Xorg-settings I should use? (I ran Automatix 2 recently, so Win32-codecs should be up to scratch.) I have something against sending my gear into frequent crashes if I can avoid it...

OS: Ubuntu 6.10 64-bit
Vid. card: Radeon 1900XT
Driver: 8.32.5

Entries in xorg.conf:
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "FSAAEnable" "on"
	Option	    "FSAAScale" "2"
	Option	    "Capabilities" "0x00000800"
EndSection

(It seems I don't get the ATI Control to start, but I HAVE followed some step-by-step guide... Well, that's, hopefully, a matter for another day.)

Mplayer video-driver set to xv (X11/Xv) - I notice it wasn't set before. Um, I'll just try if that did the trick AFTER I post this, shall I? ;) [Nope, no change there.] Double buffering and direct rendering are both enabled. Codecs (sound + video) set to FFmpeg libavcodec.
(Audio-driver set to ALSA - I have an X-Fi, but, well... I'm using an onboard 7.1-wossname for Ubuntu. Works like a charm when I bother to connect the speakers.)

Totem... Not sure what to do with that one.

---

### Post by Silent Warrior on 2007-01-04
Um, I still need some help with this. Does this crash happen because of a maladjusted codec? Should I perhaps try an OpenGL-driver? Does the hardware look to be properly configured?

---

### Post by Algar on 2007-01-08
Hello Silent Warrior.
  Im a debian etch user, but I had the same problem with the ATI drivers > 8.28 and some new versions of Xorg.

  I fix this problem  as follows:
  1.- For totem player, you need to install the package totem-gstreamer instead of totem-xine.
  2.- run gstreamer-properties
     2.1.- Go to the video tab
     2.2.- Select _*X Window System (No Xv)*_ in the output video field.

Good Luck!

---

### Post by traeskapa on 2007-01-11
I got the exact same problem, on almost the same machine.
Algar; I tried, but no sucess :/
I still got the problem :<

---

### Post by Algar on 2007-01-12
That solution only works with totem player under gnome (maybe kde too, but no sure).
Today, ATI has released a new driver, and another testing subversion of xorg has seen the light too.

I gt try with this versions.

Cya

---

### Post by Algar on 2007-01-13
Sorry guys...
The problem remains.....

I only can use totem following those steps.

If anyone knows the solution, please tell us.

Salut!

---

