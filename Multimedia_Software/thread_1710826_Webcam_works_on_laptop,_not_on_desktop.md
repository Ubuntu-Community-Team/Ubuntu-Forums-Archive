---
title: "Webcam works on laptop, not on desktop"
date: 2011-03-20
forum: Multimedia Software
---

### Post by mistapotta on 2011-03-20
I'm running Ubuntu 10.10 on both my laptop and desktop.  I've gotten a Gigaware Webcam with Mic (Radio Shack) 25-157 camera to work out of the box on my Del E-1505, no problems.  Even interfaces with Skype correctly.  

On my desktop, though, the camera light comes on, the camera is recognized through lsusb:
```
Bus 005 Device 003: ID 093a:2620 Pixart Imaging, Inc. 

```
and /dev/video0 exists, but I can't access it through VLC or Skype.  

Any ideas on how I can fix it?  Thanks!

---

### Post by no2498 on 2011-03-21
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin

---

### Post by mistapotta on 2011-03-27
Thanks!  That plus pre-pending 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```
to the launcher made it work fine!  I appreciate all the help!

---

