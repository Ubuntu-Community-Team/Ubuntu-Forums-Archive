---
title: "Green webcam video on HP dv4-1530"
date: 2009-11-12
forum: Multimedia Software
---

### Post by gpaciga on 2009-11-12
I'm having a problem with my webcam video being very green.

I'm using Karmic Koala (64bit) on an HP dv4-1530. This is a built in webcam. I'm not sure of the hardware but the lsusb shows "Bus 002 Device 002: ID 174f:1107 Syntek" (and there are no USB devices connected).

When I first installed ubuntu the camera worked, but after about a week it turned green. This is true in kopete, skype, and gstreamer. Maybe some package that was upgraded along the way broke it? It camera is not detected at all in cheese (and I don't care so much about using cheese anyway).

There have been lots of threads about green video issues and none of their solutions have worked.

[This bug report]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/345080?comments=all") has a solution for this problem on Macbooks. I'm using libv4l-0 version 0.6.0-1, which is more recent than the version they claimed fixed the bug. I thought maybe the problem was that the plugin gstreamer was using was v4l2 but v4l gives an error: "Could not get/set settings from/on resource."

I've tried a few variations on the video input in gstreamer-properties but they have not worked. The popular one seems to be "v4l2src device="/dev/video0" ! videoscale" to no effect. Others involved things like xvideosink and ffmpeg but I forget the exact strings.

I wanted to try the trick with forcing a palette in ov511 described in [this thread]("http://ubuntuforums.org/showthread.php?t=126696") but my system doesn't have such a thing and I'm not sure what module I could try it with instead:

```
$ modprobe -l | grep ov
kernel/drivers/media/video/ov7670.ko
kernel/drivers/media/video/ov772x.ko
kernel/drivers/media/video/ovcamchip/ovcamchip.ko
kernel/drivers/media/video/gspca/gspca_ov519.ko
kernel/drivers/media/video/gspca/gspca_ov534.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-nova-t-usb2.ko
kernel/ubuntu/lenovo-sl-laptop/lenovo-sl-laptop.ko
```

Some threads talk about green video but have slightly different problems, e.g. green in skype *only* whereas mine seems to be green in everything I try.

Any help with more things to try or more information I can provide (and how to get that information) would be appreciated.

---

### Post by Mikeoak on 2009-11-16
I might have stumbled upon a solution.  I was using my Logitech 9000 with some success under Ubuntu 9.10 and Skype  (2.1.0.47), but when I tried the webcam with Kopete I got severe color distortion.  I tried adjusting the color under preferences, but with little success.  Then when I tried the webcam under Skype, the bad settings got carried over, also cheese gave me an ugly pic and colors.

I then shut all video down and brought up a console and typed in **sudo cheese** .  Cheese came back up with normal colors and so did Skype.  I am not going to use Kopete anymore.

My system: Gateway Quad CPU, 64, Ram 3

---

### Post by gpaciga on 2009-11-16
Doesn't sound like my problem. Using video through a sudo command has no effect. Still all green.

By the way, rebooting also doesn't help.

---

