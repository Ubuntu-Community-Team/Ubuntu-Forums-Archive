---
title: "Apple iSight, firewire connection"
date: 2010-10-25
forum: Multimedia Software
---

### Post by fast_ian on 2010-10-25
Hi,

I searched, and it seems many have successful installations of this camera using USB and various tools.

Mine however is F/W based and while close, the little green light never comes on!....

All 10.04.

From dmesg:

[   11.038831] video1394: Installed video1394 module
[   11.060923] ieee1394: raw1394: /dev/raw1394 device initialized

"gstreamer -properties" gives the following with subtly different wording between v4l1 and v4l2, but the same:

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline3/GstV4l2Src:v4l2src1:
system error: No such file or directory]

Who or what creates "dev/video0"?

I guess I'll try another device (an old Sony DVCam) and see if that gets recognised....

Cheers,
Ian

---

