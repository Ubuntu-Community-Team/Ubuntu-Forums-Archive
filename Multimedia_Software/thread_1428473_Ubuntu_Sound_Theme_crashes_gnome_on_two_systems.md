---
title: "Ubuntu Sound Theme crashes gnome on two systems"
date: 2010-03-12
forum: Multimedia Software
---

### Post by wonk-o-matic on 2010-03-12
Using Karmic.

I can, on rare occasions, login to my gnome desktop with the sound theme enabled, but it usually crashes back to gdm while I'm still looking at the ubuntu logo.  It does a resolution change, and I thought that might be my problem.  

Then, my son noticed that, on those rare occasions we get into the desktop,the gnome-session crashes whenever a system sound plays.  

I disabled the Ubuntu sound theme in failsafe mode, then could login to the normal gnome session.  

This isn't the only machine that does this, and the other has the same model of motherboard, the ASRock 4CoreDual-VSTA.  

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci shows:
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

Any ideas?

---

### Post by Yellow Pasque on 2010-03-12
Play around with /usr/bin/canberra-gtk-play if you're good with command line. You could also try installing the libcanberra-pulse package.

---

