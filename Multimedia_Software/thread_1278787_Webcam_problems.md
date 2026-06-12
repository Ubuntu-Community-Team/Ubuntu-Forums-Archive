---
title: "Webcam problems"
date: 2009-09-30
forum: Multimedia Software
---

### Post by briansykes on 2009-09-30
Hello everyone, i'm currently having some webcam troubles, i'm trying to get my logitech quickcam messenger to work, i've tried many drivers but they all fail to compile despite me having every single thing the requirements tell me to have, can anyone help me out on this?

I've tried the qc-messenger-1.8 driver and that was hours of time wasted.

Update:  I found a tutorial on how to build and compile the qc-usb-messenger-1.8 driver which worked, but now my problem is in the tutorial it says it should be located at /dev/video0 but its not, a reboot didn't solve the problem either, if anyone has any clues as to why this doesnt work, i'd really appreciate it.  I have the proper webcam for the tutorial as well here is my lsusb:

```
Bus 001 Device 005: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
```

tutorial Link: [http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/](http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/)

---

### Post by briansykes on 2009-09-30
Hey everyone, i got the qc-usb-messenger-1.8 driver to install and cheese says that my webcam input cannot be opened, and gives no other errors, this is as close as i have gotten, the driver is installed and loads at boot time thanks to a guide i found that explained how to do that but, this is bothering me, i'm so close yet i cant get the camera to show video. Below is a screenshot of my hardware drivers dialog.

[IMG]http://img32.imageshack.us/img32/8937/screenshothardwaredrive.png[/IMG]

---

