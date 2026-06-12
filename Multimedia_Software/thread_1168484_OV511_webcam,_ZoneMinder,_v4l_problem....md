---
title: "OV511 webcam, ZoneMinder, v4l problem..."
date: 2009-05-24
forum: Multimedia Software
---

### Post by krazyman on 2009-05-24
Hi All,

I've been trying to get ZoneMinder to work on my Ubuntu Intrepid server (almost vanilla, and bang up-to-date). I've got the prog installed fine, the web console comes up fine etc.

My problem is with the webcam I'm using. It's a Creative CT6840 (Creative Labs WebCam 3), which uses an OV511 bridge and OV7610 sensor, according to the messages in dmesg. Now the camera itself works fine with xawtv, unless I try to capture images or video, then it gives me messages like 

```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-11-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
libv4l2: error getting capabilities: Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=48;width=64;format=7): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=48;width=64;format=5): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=48;width=64;format=4): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=48;width=64;format=13): Invalid argument
```

If I do xawtv -hwscan, I get

```
libv4l2: error getting capabilities: Invalid argument
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l
    name : OV511 USB Camera
    flags:  capture 
```

which indicates that v4l2 can't quite interface with the cam correctly even with the v4l1-compat module loaded.

Now all the reading I've done so far indicates that this camera is operating with the v4l1-compat kernel module, since old-skool v4l was removed after some kernel version like 2.6.18-something.

I've tried the ov51x-jpeg module from rastageeks, which lets me capture in xawtv, but the picture is all green with the occasional flicker of the right picture!

I'm trying to get capture working in xawtv first, because the zoneminder documentation says not to even bother trying to fix zoneminder if you can't capture with xawtv (zoneminder sends the picture through a capture layer before it sends it to the screen. ie - if the capture bit aint working, your monitoring no worky either).

So, I have three options:

1. Try to run an older kernel with v4l support (don't really want to go down that route as I'd like to keep the server present and correct as per ubuntu official updates etc)

2. Try to find another driver module that works with my cam (think I've exhausted the possibilities already)

3. Go out and buy a new webcam/capture card GGGRRRRRRRR!!!!!!!!!!

Anyone got any good suggestions????

TIA,

Andy

---

### Post by fabertawe on 2009-07-14
I have a similar camera... 
model: Creative Labs WebCam 3
Sensor is an OV7620
ID 05a9:a511 OmniVision Technologies, Inc. OV511+ WebCam

It's quite a few years old but always worked perfectly with Ubuntu (since 2006, when I came to Linux). Presently the only app it works in is aMSN and that is with regular green flashing artifacts in the picture. GYachE, for example, has the same artifacts but the colours are screwed anyway. The cam is not faulty as it works perfectly under Windows apps. In Skype it's recognised as /dev/video0 but there is no picture whatsoever.

I've also tried the ov51x-jpeg module but same as you there, green pic with two matching ghost images along the top.

Not much use to you I'm afraid but at least it revives this thread and more light may be shed by someone else.

---

