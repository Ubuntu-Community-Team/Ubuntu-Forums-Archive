---
title: "webcam stopped working"
date: 2010-02-09
forum: Multimedia Software
---

### Post by wolfgangpauli on 2010-02-09
Hi,

I just upgraded to karmic the other week and now my webcam isn't working anymore. 

here is my dmesg output
[ 1369.080502] pwc: Philips webcam module version 10.0.13 loaded.
[ 1369.080505] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[ 1369.080507] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[ 1369.080509] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[ 1369.465918] pwc: Logitech QuickCam Notebook Pro USB webcam detected.
[ 1369.465948] pwc: Registered as /dev/video0.
[ 1369.479354] input: PWC snapshot button as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/input/input8
[ 1369.479419] usbcore: registered new interface driver Philips webcam
[ 1396.679726] pwc: isoc_init() submit_urb 0 failed with error -28
[ 1396.679734] pwc: isoc_init() submit_urb 1 failed with error -28

the last two lines are added whenever I try to run mplayer or skype on the webcam. 

We are currently using uname -r: 2.6.31-19-generic (64 bit), but the problem was the same on 2.6.31-17-generic

any ideas?

---

### Post by no2498 on 2010-02-09
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button

get programs ( cheese and wxcan )

getdeb has wxcam you have cheese

---

### Post by wolfgangpauli on 2010-02-10
Thanks, i get the same error msgs in dmesg if I do this.

---

### Post by no2498 on 2010-02-11
you saying it did not come on ?

---

