---
title: "TV card and USB webcam - devices keep changing"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by dilidon on 2006-10-27
Hi,

I have an internal tv card and a usb webcam which both technically work fine. However, not always. That is, they work if the programs using them know the right device to use. If both are plugged in, everything is fine. However, I  often remove the USB cam from the PC.
If the camera is unplugged and the PC booted the tv-card binds itself to /dev/video0 which is normally the device for the webcam. This leads to a problematic situation where tvtime, camera monitor etc etc etc stop functioning properly because the tv-programs expect to find the tv-card at /dev/video1 and the webcam-programs expect to find the camera at /dev/video0. I can temporarily solve this manually by editing the configuration files to use the other device. However, if I replug the camera and happen to reboot, it takes its previous address again rendering the editing of the configuration files useless. Hence, they have to be re-edited each time again.

Is there a way to fix the /dev/video* locations each physical device uses once and for all? :-k (The internal tv-card is the priority as I am not the sole person using it. The stability of the usb-camera is less important).
Thanks.

---

