---
title: "Samsung R580 laptop camera not working in Ubuntu 10.10"
date: 2010-11-07
forum: Multimedia Software
---

### Post by lightningfox on 2010-11-07
Hi 

I just upgraded from Ubuntu 10.10 (64 bit) from Ubuntu 10.04 (64 bit) on my Samsung R580 laptop  
[http://www.samsung.com/au/consumer/pc-peripherals/notebook-pc/notebook/NP-R580-JS02AU/index.idx?pagetype=prd_detail&tab=specification](http://www.samsung.com/au/consumer/pc-peripherals/notebook-pc/notebook/NP-R580-JS02AU/index.idx?pagetype=prd_detail&tab=specification).

So far all my hardware seems to be working except the laptop's integrated camera.

In 10.04 the camera worked and I could use the program "Cheese" to take photos and videos with the camera.


In 10.10 I installed Cheese and tried to use my laptop's camera but it didn't work.

I installed all the available updates for 10.10 but still the camera wouldn't work.


The only information about the camera on the laptop's webpage is that it is a 1.3 MP Web Camera.



Please help me get the camera working in Ubuntu 10.10.

---

### Post by no2498 on 2010-11-08
type lsusb in a terminal click enter
that gives you more info on the cam

now with gstreamer you need to have installed gstreamer good,bad,ugly,and 10

look in the package manager for them

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

hope this helps

---

### Post by lightningfox on 2010-11-10
Hi

This is the output for lsb:

```
Bus 002 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0a5c:219b Broadcom Corp. Bluetooth 2.1 Device
Bus 001 Device 003: ID 0ac8:c342 Z-Star Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


I have all the gstreamer packages installed.



I opened gstreamer-properties through terminal.




I tried v4l1 but it didn't work and gives this error: ```
Video for Linux (v4l): Could not get/set settings from/on resource.
```


When v4l1 is selected there is no device in the device field.



I tried v4l2 and I could use my camera.





v4l2 worked and could use my camera.

When v4l2 is selected in the device field it shows: "WebCam SCB-1900N"

I think that is my camera.



I changed Default video output from the default 
"X window system (No Xv)"  to X window system (X11/XShm/Xv).

When changing the above the Default output device field showed NV17 Video Texture, which is not there when the default is selected.


After doing the above changes I tried Cheese but it still didn't work.

I also followed everything in the Cheese faq but Cheese still didn't work.



Please help me get my laptop camera working.

---

