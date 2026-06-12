---
title: "Webcam stops working after hard reset"
date: 2011-06-29
forum: Multimedia Software
---

### Post by tdelle on 2011-06-29
I already searched the forum and found some topics regarding this issue, however I did not find a solution. My problem is the following:

I'm using a desktop pc + logitech quickcam pro 9000 for camera surveillance. I'm using VLC to record the stream and to project the stream on a television. The version of ubuntu is 11.04 (32bit). Everything is working fine except for one thing.

When there is a power failure during the recording (for example someone wants to replace the pc) and the desktop is rebooted, i can't get the camera to work. It doesn't show up in /dev/video*. The only thing that works is to unplug the camera and plug it in again.

Things i have tried:
-add uvcvideo to /etc/modules
-tried 

sudo rmmod uvcvideo sudo modprobe uvcvideo (with and without quirks=2)
as posted in [http://ubuntuforums.org/showthread.php?t=1036819](http://ubuntuforums.org/showthread.php?t=1036819)

-tried restarting usb_storage 

I hope i can try the procedure with another webcam next week, but i hope somebody knows the solution to this problem..

---

### Post by no2498 on 2011-06-30
i seen this some time back and was said in the link you posted

BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)


sudo rmmod uvcvideo
sudo modprobe uvcvideo

---

