---
title: "Logitech webcam stx does not work with intrepid  8.10"
date: 2009-03-23
forum: Multimedia Software
---

### Post by revelationman on 2009-03-23
I was looking all over the forums for this issue if has been discussed or posted apologies.

Webcam does not work in Intrepid just want to know the status of it in terms will it be corrected.

here is my hardware information on the Webcam

Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:3016 Dell Computer Corp.
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

can anyone tell me the status of this issue or is there some solution that does not require major brain surgery

Thanks

---

### Post by yahs on 2009-03-23
I have a logitech Quickcam STX and I am still using Ubuntu 8.04.2 because 8.04 uses Video for linux driver 1(v4l1) while intrepid uses v4l2.
I have intrepid installed on a separate partition and I can get pictures from camorama  or cheese, but it gives a green screen if I try and use it with skype.
This issue is well documented on the launchpad and there are varous fixes suggested, not sure if they all work.
On a separate point when I used the STX webcam in Windows XP it took up a huge amount of resources, often 80% ( under control panel, hardware, devices, usb controller, bandwith) and if it was plugged into a USB1 point, the quality over Skype or MSN was poor.I had to run it through USB2 to get good quality.
In 8.04.2 I get very good quality using Skype. Hope this is useful

---

### Post by revelationman on 2009-03-24
Since I have 8.10 installed and working fine it will be a pain in the *** to go back reinstall 8.04 
I still have Windows Vista on the other partition so until they get this fixed I will just have to use Windows. 
I really do not believe in all these quick fix schemes to be honest just in case it messes up my system.

---

### Post by bedhead75 on 2009-03-24
That's odd because my Logitech Communicate STX works right out of the box with Skype in Ubuntu 8.10.  I'm using 64-bit.  The "on-light" never turns on though.  The cam also worked in Cheese without any problems in both 8.04 (32-bit) and 8.10, but I never tried Skype in 8.04.

---

### Post by yahs on 2009-03-24
Quick fix for Skype, which works for me in Intrepid. Open a terminal and run this command

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
(or depending on library) 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

NB: Closing the terminal closes Skype, so just minimise.

If this works there are more permanent solutions to try.

---

