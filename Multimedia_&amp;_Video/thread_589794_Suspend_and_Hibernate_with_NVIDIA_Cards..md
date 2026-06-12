---
title: "Suspend and Hibernate with NVIDIA Cards."
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by khurrum1990 on 2007-10-24
Hi, this tutorial is for Ubuntu 7.10 and it will help users of NVIDIA card using the drivers 100.14.19. Here is what u r supposed to do if u have NVIDIA drivers installed and running. The problem is actually with the agp module that loads up.

While u r in terminal type:
lsmod | grep agp
Some names such as intel_agp, sis_agp, via_agp etc will show up. Ignore agpgart here.

just remember exactly what show up and type in terminal:
sudo nano /etc/modprobe.d/blacklist
Now a file will open up and which shows black listed modules, go at the bottom of it and type:
# blacklist agp module
blacklist (the module which showed up such as sis_agp or intel_agp)
blacklist agpgart
Now press ctrl+o and press enter to save and exit with ctrl+x

Now u have to edit ur xorg.conf file:
sudo nano /etc/X11/xorg.conf
In the device section add the line after nvida and stuff:
Option     "NvAGP"    "1"
Save and exit and reboot ur computer. Once it starts open ur terminal again and type:
cat /proc/driver/nvidia/agp/status
This will show u which module is loaded and if u did everything right then only nvidia module should be loaded. Now u should be able to suspend to ram and suspend to disk as well. I am sorry if this is difficult to understand as its my first tutorial but it should work as it worked on many pc's I tried it with.
Good Luck and take care! Reply if this works for u as well.

---

### Post by K.Mandla on 2007-10-26
Moved to Multimedia and Video.

---

### Post by khurrum1990 on 2007-10-26
If anyone needs any modifications in this tutorial then please tell me.

---

### Post by jschneider on 2007-10-26
Hmm, doesn't work for me.

/proc/driver/nvidia only contains the followings dirs/files:

- cards
- registry
- version
- warnings

more version 
NVRM version: NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
GCC version:  gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Any suggestions?

Thanks.

---

### Post by duffrecords on 2007-10-26
Thanks.  This worked for my Dell Inspiron 8200 with an NVIDIA GeForce 440 card.

---

### Post by khurrum1990 on 2007-11-15
Hi, I also have to mention that the new kernel for Gutsy which is 2.6.22-14 breaks hibernate. Some people went back to 2.6.22-12 and it started working again. I did the same thing but with the recent updates to Gutsy kernel and the new nvidia-glx-new package hibernate is broken on all Gutsy kernels.

---

### Post by gerri on 2007-11-18
Hi,

it worked for me. Thank you for your help.

Is there a limit because of swap-space? When I do hibernate with many open application it does not work.

Greetings

---

### Post by fisting_mayfield on 2007-11-20
Worked for me (Dell XPS m1330 with Nvidia Geforce 8400M)

---

### Post by LML on 2007-11-20
Does not work for me (Dell xps m1330 nvidia 8400m gs)

lsmod | grep agp:
```
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp

```

I added the following to /etc/modprobe.d/blacklist:
```
# blacklist agp module
blacklist intel_agp
blacklist agpgart
```

And this is my new "Device" Section:
```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8400M GS]"
	Driver		"nvidia"
	Option		"NvAGP"			"1"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```

cat /proc/driver/nvidia/agp/status says:
```
cat: /proc/driver/nvidia/agp/status: No such file or directory
```

I used Envy to install the driver. what's wrong?

---

