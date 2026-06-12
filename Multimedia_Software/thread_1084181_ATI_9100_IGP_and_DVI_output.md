---
title: "ATI 9100 IGP and DVI output"
date: 2009-03-01
forum: Multimedia Software
---

### Post by whocarez on 2009-03-01
Hi,

I have some real trouble with getting the DVI-output to work on this card. Actually it's probably just part of a integrated chipset in a cheap Asus Pundit-R computer. This is in Ubuntu Intrepid 8.10 (i386).

I am using the open source radeon-driver, and that is the one I would really like to work. Looking at /var/log/Xorg.0.log, everything seems perfect. The resolution is figured out by DDC, the list of resolutions detected seems ok. There are no errors in the log file either. All I get is "no signal" once X is fired up. Tried to follow some settings from [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), but it didn't help. Also tried to fiddle with vsync/hsync values in xorg.conf for the monitor. Tried also some options from "man radeon", but it didn't help either. Even tried disabling the S-video and VGA-0 output, and left only DVI-0 in.

If I change to the vesa-driver, then the DVI-output works, but it is slow and with lower resolution. Same goes if I change to the vga-connector. Tried this with two different LCD-monitors, and both go blank on DVI with the radeon-driver. Last chance is to try the fglrx-driver, but then of course I will not get any 3D.

Is it possible to force the card to initialize the DVI-output? If anyone got a working xorg.conf with the radeon driver for this card, I would be happy.

---

### Post by whocarez on 2009-03-03
A little bump on this one.

---

### Post by whocarez on 2009-03-03
It was dead impossible to get the DVI output to work. I tried almost every option from "man radeon" and it did not help at all. Judging from google, this problem is not uncommon with this card, although it should work in older versions of Ubuntu. At the end, I even tried to install fglrx 8.28.8, but it looks like this was not possible with the xorg version in Intrepid. 8.28.8 is the last version with support for my card. For now, I gave up and new hardware is on its way :)

---

