---
title: "Prosavage KM266/KL266 Resolution Problems"
date: 2009-10-13
forum: Multimedia Software
---

### Post by 96OldsAurora on 2009-10-13
I just did a fresh install of Kubuntu 9.04 with KDE4. Installation was successful. However, the resolution is not correct. I have a max of 800x600. I would prefer to have 1024x768.

**Video Card:**
> 
# lspci|grep VGA
# 01:00.0 VGA compatible controller: S3 Inc. VT8375 [Prosavage KM266/KL266]
I have tried using the following commands with no avail:

> # sudo dpkg-reconfigure xserver-xorg> # sudo dpkg-reconfigure -phigh xserver-xorg
I know this video card is capable of displaying a resolution of 1024x768. As that was the default while running Windows.

Any help greatly appreciated! Thanks in advance!

---

### Post by 96OldsAurora on 2009-10-14
I was able to fix the resolution by doing the following:

1. Logged into console from login menu
2. Removed the package xserver-xorg-video-vesa
[INDENT]sudo apt-get remove xserver-xorg-video-vesa
[/INDENT]3. Rebooted
[INDENT]sudo reboot
[/INDENT]4. Reinstalled xserver-xorg-video-vesa
[INDENT]sudo apt-get install xserver-xorg-video-vesa

[/INDENT]5. Reconfigured X
[INDENT]sudo dpkg-reconfigure xserver-xorg
[/INDENT]6. Rebooted into KDE4 and was able to change the resolution to 1024x768

---

### Post by 96OldsAurora on 2009-10-14
I spoke to soon!

Let me start over and say I am setting up a desktop pc to be used with my hdtv. Now, usually the tv does not recognize an 800x600 resolution. The recommended is 1024x768.

Since it does not recognize 800x600 means I have to use a separate monitor to do the install.

With steps I used above in post #2 I immediately just plugged the vga cord in for the hdtv once I got the monitor set up to display 1024x768.

However, once I rebooted it reverted back to using 800x600 resolution. The option for 1024x768has disappeared.

I need some help guys! Thanks in advance!

---

### Post by 96OldsAurora on 2009-10-15
BUMP! C'mon someone knows how to help!:P

---

