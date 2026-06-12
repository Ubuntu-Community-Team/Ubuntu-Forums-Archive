---
title: "Logitech Quickcam Fusion issue with Jaunty"
date: 2009-05-17
forum: Multimedia Software
---

### Post by GooblyWoobly on 2009-05-17
Installed Jaunty, and my Logitech Fusion Webcam didn't get recognized as a video device (only audio). I looked at the hacks and patches, and installed gspca, which loaded fine. But I don't see any /dev/video0 (or any /dev/videox)

Any pointers?

---

### Post by korleon on 2009-05-31
I've had the same problem with a Logitech Cam It's the e2500 model which has a model code of:

```
@kuber-desktop:~$ lsusb
Bus 003 Device 002: ID 046d:089d Logitech, Inc.
```

When the cam is connected I get nothing:

```
@kuber-desktop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory
```

I searched the web extensively and tried to get the gspca driver to install.  
I tried this Blog I found listed here on the forums:
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/]("http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/")

Here's the logitech forums:
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/]("http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/")

No luck on either count. Finally I just got the .deb packages for a newer kernel and the cam works fine with the updated kernel and gspca module already part of the kernel. I found the link to the kernel .deb files here:
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/]("http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/")

WARNING: since I have an Nvidia card I have to boot this kernel in recovery mode because it isn't complied for my video card, but Cheese, and skype both work once it's loaded.

Beyond that, I'm stuck Does any one have a better solution or know how to make this work on my current kernel?

---

