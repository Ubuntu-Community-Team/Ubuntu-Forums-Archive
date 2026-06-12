---
title: "Webcam not working"
date: 2009-02-09
forum: Multimedia Software
---

### Post by jamesbeat on 2009-02-09
I'm at the end of my tether with a new webcam that I just bought.
I have tried for ages now, but I can't seem to get it to work, so I need help!
I'm a bit of a noob, so go easy on me...

THe camera is an A4 Tech Flexicam PK-5, and I just don't seem to be able to find much info about it.

Here's the output of lsusb:

```
 Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 05af:0408 Jing-Mold Enterprise Co., Ltd 
Bus 001 Device 001: ID 0000:0000  


```
 and dmesg gave this:

```
[ 3897.411901] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 3897.664934] usb 4-2: configuration #1 chosen from 1 choice
[ 3897.670348] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[ 3897.729601] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
[ 3898.013808] usbcore: registered new interface driver zc0301

```


I followed the advice here:
[http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html](http://www.ubuntugeek.com/tip-getting-your-webcam-to-work-in-ubuntu.html)

and although it improved things because the camera seemed to be detected, I just get a black screen in Cheese and Camorama.

So now I'm stuck. Any ideas?

---

### Post by markusf21 on 2009-02-09
try ekiga its in your menu under internet. that way you can check to see if it works or not. AFAIK cheese is broken. I thought my cam didnt work, because i couldnt pull it up on cheese. but it works with ekiga.

---

### Post by jamesbeat on 2009-02-09
Sorry, forgot to add that during the initial Ekiga setup, when it looks for the cam, I get the error message 'Failed to open the device' 'error while opening /dev/.static/dev/video0'

---

### Post by jamesbeat on 2009-02-09
I feel like such an idiot. The lens has a cover.....
:lolflag::lolflag::lolflag::lolflag::lolflag:

So it's working in camorama, but Ekiga still won't recognise it

---

### Post by markusf21 on 2009-02-09
That is funny. We all have those "Brain Farts". I seem to have the opposite problem of yours. camorama doesn't work, ekiga does. Best of luck to you.

---

