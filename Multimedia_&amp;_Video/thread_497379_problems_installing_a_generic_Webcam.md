---
title: "problems installing a generic Webcam"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by nika22 on 2007-07-10
Hi,

I get new webcam as a present and I wanted to use it with ubutu 7. I think that is a generic webcam because when I do lsusb it doesn't appear its name (I think that is the one on device 005)

/dev$ lsusb
Bus 001 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 007: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 005 Device 005: ID 1b17:6111  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d62:001c Darfon Electronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

I've followed this instructions on this section :

[http://ubuntuforums.org/showthread.php?p=2009418](http://ubuntuforums.org/showthread.php?p=2009418)

and finally when I type the dmesg I get this:

[  887.429131] Linux video capture interface: v2.00
[  887.448289] usbcore: registered new interface driver gspca
[  887.448299] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

that I think it's correct, and if I look my modules (lsmod) I have this:

gspca                      616272  0 
videodev                 29824    1 gspca
v4l2_common        28800    1 videodev
v4l1_compat          14980    1 videodev


that I think it's correct too. But it says nothing about a quickcam...I'm not sure if it have to be on the modules information as I saw on some forums..

Well, then, when I try to test de webcam with xawtv I get this error:

This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.20-16-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


I've been googling but I can't find what could it be.

I'll be very gretefull if someone could hep me because I don't want to change to windows every time I need the webcam.

thanks in advance.

Nika

---

### Post by linuxwizard on 2007-07-10
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by nika22 on 2007-07-10
Thanks, but I've visited this page before. The problem is that I don't know which camera I have so I don't know which driver I need to install and look for. 

With a detection hardware on windows it says USB2 PC CAMERA and in linux the only way I know is use the command lsusb, but it says nothing about the name, so I followed the way of compiling the sources from :

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

and is what I've explained in my first post.

thanks

---

### Post by linuxwizard on 2007-07-10
Did you try this


Driver installation

Many cameras work out-of-the-box. If needed, try EasyCam, a tool for installing webcam drivers. 

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)
EasyCam is a software for an automated webcam installation. Thanks to the autodetection it will install the needed driver for your webcam.

---

### Post by Ancient1 on 2007-07-12
[COLOR="Sienna"]Hi[/COLOR] 

Same (almost) problem . 
  
Noob 
Feisty 64bit , Logitech ClickSmart510 ( supported by SPCA )  
I have a bt848 TVtuner which works basically, (if webcam connected at boot TVapp  sees the webcam only) 

_LSUSB_  
Bus 003 Device 004: ID 046d:0901 Logitech, Inc. ClickSmart 510 

_LSMOD_ 
usbcore               154416  6 usbhid,xpad,gspca,uhci_hcd,ehci_hcd      (Thats the only mention of SPCA in the output)  
v4l2_common            28800  4 tuner,bttv,compat_ioctl32,videodev
v4l1_compat            14980  1 videodev

_Tried :  _
[COLOR="Blue"]https://help.ubuntu.com/community/Webcam[/COLOR] 
[COLOR="Gray"]This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.20-16-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
[/COLOR]
[COLOR="Blue"]https://help.ubuntu.com/community/EasyCam[/COLOR]  
[COLOR="Gray"]"E: Couldn't find package easycam2", "easycam" too[/COLOR]
[COLOR="Gray"]No idea how to install manually[/COLOR]

[COLOR="Blue"]https://help.ubuntu.com/community/Spca5xx#head-48b871e312b6c98ba31970d0545d73b7f2fec9af[/COLOR]
[COLOR="Gray"]Troubleshooting : .. you still might not have it and need to install the driver...  HOW ? All I have is sources for gspca and scpa5xx [/COLOR] 

[COLOR="Sienna"]Thanx for any help[/COLOR]

---

### Post by judits on 2008-07-06
Hi!

I have a generic USB webcam (it was a cheap gift). I think its model is JL2005A, but I don't know the manufacturer.

The webcam came with a driver CD for Windows, but I'd like to use it with Ubuntu.

When I do lsusb I get this (the Logitech device is the mouse):
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c019 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

The webcam is connected, but I guess Ubuntu is unable to recognise it. Is there a solution to get the webcam work, or maybe should I buy a better webcam?

Thanks!

---

