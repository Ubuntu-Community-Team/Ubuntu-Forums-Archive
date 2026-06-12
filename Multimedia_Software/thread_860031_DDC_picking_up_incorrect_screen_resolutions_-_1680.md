---
title: "DDC picking up incorrect screen resolutions - 1680x1050@60 not in list :("
date: 2008-07-15
forum: Multimedia Software
---

### Post by Illarane on 2008-07-15
Hiya,

I've got an Asus mini-desktop with an SiS651 graphics chipset.  I'm having a real pig of a time trying to get it to output at 1680x1050, as DDC is overriding the configuration I'm putting in xorg.conf.

The screen is a Dell 2007WFPb which supports up to 1680x1050@60 via DVI, but I get edidfail (EDID fail indeed. :() when I run ddcprobe manually.  Xorg is (I guess) probing the device, getting a fail and loading the default set of screen resolutions.

Since there is a DVI output, I'd assume it actually supports decent resolutions, but this may not be the case.  I've attached my xorg.conf and Xorg.0.log files for reference.  If anyone can help me get 1680x1050 on this feeble excuse a graphics chipset, I'd be very grateful. :)

The Xorg.0.log file is gzipped as Ubuntu obviously don't believe in verbose logging (c.f: upload limits). ;)

Regards,

Ben.

---

### Post by xc3RnbFO8P on 2008-07-15
did you try Screen and Graphics.
atl+f2
> gksudo displayconfig-gtk
try geniric 1680x1050

---

### Post by Illarane on 2008-07-15
Ok, if I select the right monitor in that screen and hit test I get an XServer instance pop up, but it looks like it's the same resolution I'm currently using - i.e: 1280x768 - instead of 1680x1050. :/  If I pick the generic one, I get 1680x1050 virtual inside 1280x768. :/

Where does that programme save its settings?  /etc/X11/xorg.conf?  If so, it didn't. :/  Also, if I hit OK in there and restart, the settings don't take effect.

**Edit:** *Actually, tell a lie, it does display correctly when I hit test.  It just doesn't keep the settings when I hit OK. :/*

---

### Post by Illarane on 2008-07-16
Anyone got any ideas why that config programme doesn't actually apply the settings when I hit OK? :)

---

### Post by Illarane on 2008-07-22
Boing?

---

### Post by karrank% on 2008-07-22
does the command gksudo nvidia-settings apply here? it worked for me when I couldn't save the twinview settings...

---

### Post by Illarane on 2008-07-23
No, it's an SIS card rather than an nVIDIA one. :(  I'm reinstalling the box now anyway, as my Windows one has gone boom and I'm taking the opportunity to swap them so that Ubuntu's installed on the decent machine. :)

---

