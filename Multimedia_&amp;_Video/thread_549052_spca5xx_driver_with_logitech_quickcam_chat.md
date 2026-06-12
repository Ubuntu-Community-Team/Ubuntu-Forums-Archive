---
title: "spca5xx driver with logitech quickcam chat"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by crutch on 2007-09-12
Hi, I'm fairly new to Ubuntu, so have some patience.

 I recently picked up a Logitech quickcam chat webcam, and I have been able to get this going in  some programs, such as camorama (although this has no colour) and in mplayer (using instructions on webcam page in ubuntu community docs). I have been trying to make a recording, and got xawtv for this.

However when I run this (using -nodga, otherwise It won't run at all) I get the following message

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=7): Invalid argument
ioctl: VIDIOCMCAPTURE(frame=0;height=264;width=352;format=5): Invalid argument

Xawtv opens, but either with the bottom half of the screen blank, and some horozontal lines going up and down the top half (I do get half an image) or with fuzzy lines covering the bottom half of the screen. Has anyone seen this before?

---

### Post by Floker on 2007-11-23
I have the very same problem and no solution :(

---

### Post by crush157 on 2007-11-24
Just updated my system and have this web cam, forgot about setting parameters when loading the gspca module.

sudo modprobe gspca force_rgb=1

If the module is already loaded, you will need to remove it first by:

sudo rmmod gspca

This will fix the driver to display properly. There are some other settings for Gamma. To find the options, download the source from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) and look at the readme file.

---

