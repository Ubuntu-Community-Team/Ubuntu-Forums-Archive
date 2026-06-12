---
title: "No video signal after Nvidia Driver install"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by xECK29x on 2007-05-10
I just finished installing Ubuntu 7.04 on my desktop which is running a GeForce 7900GT. I just installed the drivers using the installation guide in this months Maximum PC (using Synaptic Package Manager and choosing nvidia-glx package)

When i restart i get no video signal to the monitor....has to be a refresh rate problem, so I looked at this guide ([http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1_-_OFFLINE_INSTALLATION](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1_-_OFFLINE_INSTALLATION)) and in the problems section #10 has a fix for my problem, but when I do sudo nano /etc/x11/xorg.conf no text is there for me to edit, and I cannot edit this file using the live boot cd either.

is there another command I can run from recovery mode to help fix my problem?

Thanks guys and Ubuntu Owns!

---

### Post by kamillozo on 2007-05-10
> **xECK29x said:**
> but when I do sudo nano /etc/x11/xorg.conf no text is there for me to edit
That's true because there is no directory named x11 but X11. As you see It really maters for Unix systems wheather you use capital letters or not. Remember about it. So if you want to edit xorg.conf execute:
sudo nano /etc/X11/xorg.conf

> **xECK29x said:**
> When i restart i get no video signal to the monitor....has to be a refresh rate problem
You propably get signal but it is out of range of your monitor. I would propose another way of solving this problem.
Edit xorg.conf and add lines with proper values of horizontal and vertical refresh ranges in section monitor. You should find info about proper ranges for your monitor in its manual or on producers website.

Here is example of how should it look:
```
Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 85.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection
```

Sorry for my english.

---

### Post by xECK29x on 2007-05-10
still not getting a signal input even when I play around with the values (the user manual for this monitor does not list all the resolutions and refresh rates so I guessed.

Anything else I can play around with, such as the mode settings or resolutions? Can I lock it to one resolution?

---

### Post by xECK29x on 2007-05-14
...grr any updates on this I really wanna dump Vista!

---

