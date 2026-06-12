---
title: "Getting different resolutions from MU437 module using V4L2 A"
date: 2011-09-21
forum: Multimedia Software
---

### Post by srinureddy on 2011-09-21
Hello,

We are using 1.3 Mega pixel MU437ASA Camera module (VID : 10f1,  PID:1a36). As per the datasheet, the following are the resolutions supported by the device: 

1280x1024
640x480
320x240
160x120

While using the camera with linux 2.6.30 kernel, we are able to get streaming with 320x240 resolution only.

We have tried the other resolutions with VIDIOC_S_FMT ioctl, however we are getting streaming with 320x240 resolution only. We wish to get the video streaming in other resolutions (those mentioned in the datasheet) as well. How do we achieve this?


Thanks,
Srinureddy

---

