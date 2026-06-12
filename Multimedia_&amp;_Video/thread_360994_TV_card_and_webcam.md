---
title: "TV card and webcam"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by beartard on 2007-02-13
One thing that's been driving me nuts is getting my tv card to play well with my webcam.  Sometimes, after a reboot, it works fine.  Other times, no apps can see the webcam, but its light is on constantly.  In this situation, kopete defaults to using the tv card as a webcam.  I think it has to do with the order in which the drivers are loaded at boot.  Is there a way to make sure the webcam driver gets loaded before the tv card?

I have a Logitech Quickcam for Notebooks using the spca5xx driver (self-compiled in feisty) and a generic pcmcia tv card using the saa7134 driver.  I've had to add the tv card driver to modules.conf so that it loads with the proper options (evidently, generic cards cut costs by not including an EEPROM with the tuner and video chipset info).  I've also made it default to /dev/video1, since kopete and other apps want to get a webcam from /dev/video0.

I'm just stumped.  Anyone with a similar issue?  I think I've read just about every website out there on the issue and I still can only get them working right *sometimes.*

---

### Post by Stemp on 2007-02-13
Maybe it will help you : [Video devices and udev]("http://ubuntufr.free.fr/?p=28")

---

### Post by beartard on 2007-02-14
Thanks!  I did figure out that my problem was with a kernel update.  I forgot to install my self-compiled driver with the new kernel.  Everything seems ok now.

> **Stemp said:**
> Maybe it will help you : [Video devices and udev]("http://ubuntufr.free.fr/?p=28")

---

### Post by mhancoc7 on 2007-10-04
I have a similiar issue.

My Logitech QuickCam STX works great as long as I don't use my PCMCIA wireless card. My webcam is using a PCMCIA usb/firewire card. If I am using the wireless card then the camera freezes in all the programs that I have tried. The video will work for about 30 seconds. If I don not use the wireless card then the webcam works perfectly.

Jereme

---

