---
title: "usb webcam deviceid to /dev/videoX mapping"
date: 2013-07-17
forum: Multimedia Software
---

### Post by kgokare on 2013-07-17
Hi folks,

I have a setup with several webcams attached to the computer and I run a small diagnostic program which will run on 1 webcam at a time. Now I want to show a list of webcams with device/mfctr names and VID/PID. When the user selects, the appropriate /dev/video device is opened and diagnostics is run. 

Is there any way to map these two ? don't want to use udev rules or any other type of hard coding.
 Also webcam models vary randomly and some of them may not even support uvc.

Just need to find out the mapping part.

Any pointers is appreciated.

---

