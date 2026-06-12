---
title: "Strange lsusb output. Any ideas?"
date: 2008-10-28
forum: Multimedia Software
---

### Post by cellulararrest on 2008-10-28
Ok so I've been trying to get my webcam to work properly for awhile now. I've read almost every thread there is on the subject.

Here is how I got to where I am:
- Plugged webcam in.
- Read Ubuntu Wiki page on webcam's which advised EasyCam2
- I installed EasyCam2 and proceeded to let it install my webcam.
- Camera now is recognized and works fine in Cheese Webcam Booth however it won't work properly in any other programs (Skype, Camorama)

In trying to diagnose this I ran lsusb and here is what it outputted for my webcam:

> **"te SC-120/ICGear TravelCam/Easy Snap Snake Eye WebCam"**

I'm thinking this is the problem as all my other devices output with a prefix like:

> **"Bus 001 Device 004: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth"**

However I am now stumped and don't know how I can go about having it recognized properly.

Anyone have any ideas?

**EDIT:**

Just for some more info, the output of v4l-info is: 

> [B]### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "CIF Single Chip     "
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 352
	maxheight               : 288
	minwidth                : 48
	minheight               : 32

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "pac207"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0
[/B]

Added Screenshot to show how the webcam performs in Skype and How it works in Cheese.

---

