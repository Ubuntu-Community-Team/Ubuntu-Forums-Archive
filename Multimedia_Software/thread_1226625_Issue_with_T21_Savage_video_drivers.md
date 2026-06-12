---
title: "Issue with T21 Savage video drivers"
date: 2009-07-29
forum: Multimedia Software
---

### Post by endoftime on 2009-07-29
Ok, I'm fairly new at Ubuntu, about 6 months in, and haven't had any insurmountable difficulties, until now.

I have an elderly Thinkpad T21 which runs Hardy quite nicely. I've been trying to sort out the video for a little gaming, and on asking if DRI rendering was enabled, the response was: direct rendering: No

In order to try to remedy this, I checked out xorg.conf, and found under device:

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDevice"		"true"
        EndSection

Taking this to mean that I needed to set it up for my video card, I altered the above to:

Section "Device"
        Identifier      "S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
        Driver           "savage"
        BusID            "PCI:1:0:0"
        EndSection

Having restarted, this made no apparent difference, and although I had made no alteration to "Input Device" I discovered that the thinkpad blue multi-function key no longer operated. I returned xorg.conf to how I had found it, but the button still no longer operates, and am now at something of a loss...

Jonathan.

---

### Post by igorzwx on 2009-07-29
Some bug report:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/199502](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/199502)
My thinkpad X40 has a blue "Access IBM" button above the keyboard which in previous Ubuntu releases I mapped to Lock Screen.
In hardy, the key event is not being detected by GNOME's Keyboard Shortcut preferences capplet.

---

### Post by endoftime on 2009-07-29
That's rather interesting, however the key I'm having difficulty with is the third mouse button that permits scrolling with the nipple mouse.

Cheers,
J.

---

### Post by endoftime on 2009-07-30
I've managed to fix the scrolling issue, but still at a loss with regards the video; any ideas?

---

