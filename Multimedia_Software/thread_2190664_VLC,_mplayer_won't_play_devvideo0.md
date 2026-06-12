---
title: "VLC, mplayer won't play /dev/video0"
date: 2013-11-28
forum: Multimedia Software
---

### Post by pdkok on 2013-11-28
I just found that I had a "USB Instant Video CD" of ADS Tech laying around, unopened for years, and I wanted to give it a try to digitalize old mini-DV tapes of my camcorder.

When I hook up the device to my Ubuntu 13.10 system, a new /dev/video0 device (and after unplugging and plugging it in again, /dev/video1) appears. I tried reading from this device with VLC by going to Media > Open Capture Device. I tried to open the device in modes "Video camera" and "TV - analog" (with video standards Undefined, All, PAL, PAL B/G, PAL D/K and NTSC), but no output was shown. Also, no errors were reported.

Then I tried reading from the analog-to-USB device with mplayer, with command [FONT=courier new]mplayer tv:// -tv driver=v4l2:device=/dev/video1[/FONT] (I had it replugged). This resulted in the following error message:

```
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB Camera (06e1:a190)
 Capabilities:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = spca506;
 Current input: 0
 Current format: unknown (0x35303553)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Inappropriate ioctl for device
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
==========================================================================
Cannot find codec matching selected -vo and video format 0x35303553.
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 1 frames dropped.

Exiting... (End of file)
```

Could someone help me finding the right way to read from this device?

Many thanks and kudos in advance! :D

---

### Post by mikewhatever on 2013-11-29
Such devices usually require a driver, and, obviously, none is provided for linux. Perhaps you can get it working in wine.

---

### Post by tgalati4 on 2013-11-29
Install and run *xawtv* and play around with the switches.  It will either work, work poorly, or not work at all.

---

### Post by pdkok on 2013-11-30
Thanks for the advice and help! I got read errors with xawtv, and nothing was displayed. Too bad, but I will look for something that does work (now that I found all the old mini-dv tapes, I really want them digitalized). 

Was "It will either work, work poorly, or not work at all" a remark in general, or mainly because of the old device?

---

