---
title: "Gusty Beta Upgrade Binary Nvidia Driver Problems"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by CharlieM on 2007-10-01
I have an ubuntu server (although with a few X packages installed, & rat poison). The servers main role is as a mythtv back and front end. To be able to use the mythbuntu packages, I upgraded my server to Gusty Beta from Feisty using the do-release-upgrade method.

It went fairly well, although I have to rebuild the initrd image as my machine requires some non-free raid drivers. My problem is no matter what I try I cannot get the  Nvidia propriety drivers to work. I can't use the NV driver as I need the tv-out on the graphics card. 

I have tried to avoid using the nvidia installer and stuck with ubuntu methods. Although in previous versions I may have used the nvidia installer as I have found a copy of the NVIDIA installer lying around.  

The graphics card is an AGP Geforce 2 MX (so it needs the nvidia-glx driver). It seems unable to load the nvidia kernel module.

	modprobe -v nvidia

	install /sbin/lrm-video nvidia
	FATAL: Error running install command for nvidia

However I am unable to find out what the fetal error actually is. There is nothing in dmesg that relates to nvidia.

If have tried to purge nvidia-glx -> reboot -> install nvidia-glx but that didn't help.

I have read so many posts about how to install and trouble shoot these drivers, but nothing seems to help. Does anyone have any ideas what to try next, or where to look to find out what this “FATAL” error actually is.

Any help would be greatly appreciated.

---

