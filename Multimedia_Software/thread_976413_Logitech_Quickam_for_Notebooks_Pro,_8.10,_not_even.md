---
title: "Logitech Quickam for Notebooks Pro, 8.10, not even starting."
date: 2008-11-09
forum: Multimedia Software
---

### Post by bishounen on 2008-11-09
Ok, here's my issue;

I have a Logitech Quickcam for Notebooks Pro  ([This one]("http://www.logitech.com/index.cfm/435/204&cl=us,en"), if you want the specific model).

This camera worked PERFECTLY under 7.10, and 8.04.  For some reason it has completely quit working.  I have been searching the forums for DAYS now and while I can find plenty of people with this issue, NONE of the proposed solutions seems to work.  I think this is because for each solution, the camera actually STARTS, but the software won't run it.  In my case, the camera won't START.  Here is my data:

LSUSB:

>  lsusb
Bus 005 Device 007: ID 046d:08c3 Logitech, Inc. Camera (Notebooks Pro)
Bus 005 Device 006: ID 04b3:310c IBM Corp. 
Bus 005 Device 002: ID 04b3:4485 IBM Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



The dmesg is so long it runs off the buffer, so I'll just include the USB camera pertinent section.
DMESG:
> [45658.484179] usb 5-6.1: new high speed USB device using ehci_hcd and address 7
[45658.770245] usb 5-6.1: configuration #1 chosen from 1 choice
[45658.772293] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)
[45659.772218] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[45660.772249] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[45660.772265] uvcvideo: Failed to initialize the device (-5).
[45661.738426] 7:3:3: cannot set freq 16000 to ep 0x86



Ok, so while my system can SEE the camera, it can't actually START the camera.

Interestingly, while it didn't work initially after I upgraded from 8.04 to 8.10, after the first major update it did work.  Once.  Then Cheese crashed and it hasn't worked since, in any application.  *(Incidentally, Camorama has NEVER worked for me, with ANY camera I've tried, on ANY machine I've tried it on in ANY version of Ubuntu, from Hoary on up.  Worst cam program EVER!)*

I need this camera to work for Skype, but before I can get there I need the system to actually initialize the dang thing.  Anyone have any idea what is going on here?

---

### Post by forkandles on 2008-11-09
Webcams designed for Windows are the biggest pain in the backside in Linux, bar none, as people on this forum and others will testify. Like you, I spent days trying to get my webcam to work but in the end I decided that there were just not enough hours in the day.

I then purchased a Logitech Vision Pro which works in Mac, Linux and Windows. There is a review here:
[http://www.aselabs.com/articles.php?id=268&asesessid=aa58de41ab3433ec951eba636a7e4a3c5b546fe4](http://www.aselabs.com/articles.php?id=268&asesessid=aa58de41ab3433ec951eba636a7e4a3c5b546fe4)

According to this site:   [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

your webcam &#8220;works with issues&#8221;, but give it a good try first before binning it or selling it to a Windows user. Good luck.

---

### Post by bishounen on 2008-11-13
The thing is, it worked without a SINGLE issue in both 7.10 and 8.04.  I just want to know what changed?  Is it a kernel incompatibility with the UVC driver?  Some kind of change in the driver itself?  Or a part of the upgrade process that failed out?

There has to be a reason WHY it won't work, beyond "well, those things are kinda flaky".  Particularly since it worked so well in the previous version of Ubuntu.

Still hoping someone can help me out here.

---

### Post by forkandles on 2008-11-26
See if this is any help.

[http://ubuntuforums.org/showthread.php?t=983574](http://ubuntuforums.org/showthread.php?t=983574)

---

