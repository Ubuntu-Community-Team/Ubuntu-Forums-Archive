---
title: "Webcams not working when upgraded to 8.04"
date: 2009-07-12
forum: Multimedia Software
---

### Post by pteja on 2009-07-12
Upgraded my FIT-PC (based on Geode) to 8.04. After the upgrade "webcams" stopped working (i.e. stopped showing any video).

Have tried with 2 webcams - Labtec Webcam & Logitech QuickCam Messenger.

Tried Cheese, Skype & Ekiga. In all programs, the error is:

> Failed to open video device /dev/video0: Device or resource busy

In cheese, get a picture with vertical colored bars.

Tried the LD_PRELOAD in thread: [http://ubuntuforums.org/showthread.php?t=997807]("http://ubuntuforums.org/showthread.php?t=997807") with no success.

Any ideas??

BTW: lsusb command hangs if any USB device unplugged.

---

### Post by no2498 on 2009-09-05
run this in the terminal gstreamer-properties
go to video try vl or vl4

---

