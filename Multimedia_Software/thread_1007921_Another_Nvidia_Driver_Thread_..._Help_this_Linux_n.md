---
title: "Another Nvidia Driver Thread ... Help this Linux newb"
date: 2008-12-10
forum: Multimedia Software
---

### Post by Housh on 2008-12-10
First off, I am brand new to Linux so I apologize ahead of time for any newb questions or remarks. Anyway, I have been trying for about a week now to get my Nvidia drivers to function properly. I really want to get this to work, but I fear I might end up downgrading to windows if i can't get this fixed soon.

I have been through the forums and tried "solutions" found there to no avail (granted a lot of it is another language to me). I have tried both 8.10 and 8.04, I have tried downloading/installing the drivers through Envy, System>Administration>Hardware Drivers, and the Nvidia website.

Generally what happens after I install the driver is I reboot and it comes back as a blackscreen. I am able to get my GUI up and running again by using Ctrl-Alt-F1, running [sudo nano -w /etc/X11/xorg.conf], and changing "nvidia" in the Drivers section to "nv". Also, when I try to run NVIDIA X Server Settings, I always get the result:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Currently I have just finished a fresh install of 8.04, went through the long upgrade, and installed the Nvidia driver from the Nvidia website using a tutorial found on another thread.

It has been a long, frustrating week, so any help at all is greatly appreciated.

---

