---
title: "UVC v4l2 Logitech QuickCam Orbit/Sphere AF not detected"
date: 2012-05-08
forum: Multimedia Software
---

### Post by jcllings on 2012-05-08
This is just a technical note regarding the device mentioned in the title. Some small note like this would have saved me a lot of time so I am posting this in the hopes that others will find it useful and so that I can look it up later, if I forget. 

This device *is* supported out of box on Ubuntu 12.04 and several previous versions HOWEVER, you cannot plug it into a USB hub. At least not for any of the hubs I own. Your best bet for detection is directly connecting it to your machine. This appears to be the case on both USB versions 2 and 3 nor does it seem to matter whether or not the hub has it's own power. 


user@host:~$ lsusb | grep Quick
Bus 003 Device 041: ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF
user@host:~$

---

### Post by rakaone on 2012-11-04
I am trying to tune C920 webcam for picture quality using v4l2-ctl  utility on ubuntu PC. I am unable to set exposure_auto to 'Auto' mode!  It can only be set to 'Manual Mode' or in 'Aperture Priority Mode'. Any  clues?
 
*lenovo@ubuntu:~$ v4l2-ctl -d /dev/video1 -c exposure_auto=0*
[COLOR=#FF0000]*VIDIOC_S_CTRL: failed: Input/output error*[/COLOR]
*exposure_auto: Input/output error*



Following are the settings dump of C920 connected to my ubuntu:
[IMG]http://i.stack.imgur.com/vRDaH.png[/IMG]

---

