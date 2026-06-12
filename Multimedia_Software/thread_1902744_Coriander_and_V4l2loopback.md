---
title: "Coriander and V4l2loopback"
date: 2011-12-31
forum: Multimedia Software
---

### Post by Core2idiot on 2011-12-31
I have been trying to get my Firewire iSight to work with linux and I found that Coriander will see the camera.  But I need it outputted over Video4Linux2 in order to use it, Right?  I looked high and low and I found a lot of information regarding V4l and vloopback, and after a while I found V4l2loopback ([https://github.com/umlaeute/v4l2loopback](https://github.com/umlaeute/v4l2loopback)) I installed that and now I have a device in Skype, Gtalk, among others called dummy video device,  how ever it just gives me a black screen, even when I tell coriander to output over V4l. I know that the camera works as I can see the video in coriander but when I tell coriander to output over V4l I get no error except when I run in terminal, then I have
"ioctl (VIDIOCGCAP): Invalid argument
ioctl VIDIOCGPICT: Invalid argument
ioctl VIDIOCSPICT: Invalid argument
ioctl VIDIOCGWIN: Invalid argument
ioctl VIDIOCSWIN: Invalid argument"
If anyone has any way of helping me get my iSight going please tell me.

On a side note the microphone showed up for a while but now it does not, what gives?

My Machine is running 11.10, Linux 3.0.0, x64

Thanks a ton

---

