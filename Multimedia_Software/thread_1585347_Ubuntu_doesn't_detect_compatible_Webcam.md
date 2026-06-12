---
title: "Ubuntu doesn't detect compatible Webcam"
date: 2010-09-30
forum: Multimedia Software
---

### Post by sneek on 2010-09-30
Hey guys, 
first of all, I'm from Germany, so please excuse if I may have a bad English, but I'll do my best :)
Second, I hope I choose the right section.

My problem is, that Ubunutu doesn't detect a compatible webcam.
Here are the outputs from dmesg and lsusb:

lsusb:
```
Bus 006 Device 004: ID 0595:4343 Zoran Microelectronics, Ltd Digital Camera EX-20 DSC
```dmesg:
```
[14402.925347] zr364xx 6-2:1.0: Zoran 364xx compatible webcam plugged
[14402.925351] zr364xx 6-2:1.0: model 0595:4343 detected
[14402.925356] usb 6-2: 320x240 mode selected
[14402.925421] usb 6-2: Zoran 364xx controlling video device 1
[14403.600909] usb 6-2: Failed sending control message, error -110.
[14403.600916] usb 6-2: error during open sequence: 5
[14440.024332] usb 6-2: Failed sending control message, error -71.
[14440.024340] usb 6-2: error during open sequence: 0
```In the folder /dev are two Files, video0 (intern Notebookcam, detected) and video1 (USB webcam, doesn't detected).

With "doesn't detected" I mean especially that I can't use the cam in aMSN, because the cam is not listed there, only the intern webcam is listed :/

Do you guys know how I can fix the problem?

---

