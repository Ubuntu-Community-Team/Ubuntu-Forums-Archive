---
title: "Cannot access /dev/video* Error initializing camera"
date: 2009-05-07
forum: Multimedia Software
---

### Post by mdmcginn on 2009-05-07
I'm unsuccessfully trying to use my Kodak EasyShare C653 camera as a webcam.

$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
I get that both before and after plugging the camera in. The Community webcam documentation at [https://help.ubuntu.com/community/Webcam#Driver%20installation](https://help.ubuntu.com/community/Webcam#Driver%20installation) implies that the command should work either way.

When I plug in the camera, I get a popup "Unable to mount Kodak Co. Digital Camera" and "Error initializing camera: -60: Could not lock the device."

Nautilus shows me the still images on the camera, even though the camera is set on video. Skype doesn't detect any video device.

$ dmesg | grep video gives no results. 
$ lsusb includes Bus 003 Device 012: ID 040a:05af Kodak Co. Digital Camera

What should I try next?

---

### Post by Zenmij on 2009-05-15
I have the same problem.

Should there be /dev/video when the cam is plugged in? I get the same report either way...

---

