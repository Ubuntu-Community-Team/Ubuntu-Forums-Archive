---
title: "Screen resolution not available"
date: 2008-09-03
forum: Multimedia Software
---

### Post by andrewkirk on 2008-09-03
I have ubuntu 8.04 installed on four computers, three with great success. But on the fourth I have been unable to get the screen resolution right.
Screen is LG Flatron L1811S with max and native resolution 1280 x 1024.
But the maximum resolution offered to me by any of the config utilities is 1024 x 768, unless I count 1280 x 800 which is vertically distorted and rather blurry. 

I have tried using System>Preferences>Screen Resolution, and also following the xrandr and displayconfig-gtk terminal commands set out in the following howto post:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I have also tinkered with the /etc/X11/xorg.conf file, with no success.
In some of these adventures the available screen resolutions have been reduced to two very low res ones. I'm now back where I started where there are eight resolutions offered, the biggest non-distorted being 1024x768 and the biggest distorted one 1280x800.

Can anybody help please?

Here is some system info:
o/s ubuntu 8.04 (Hardy) as downloaded c.25 August 2008 with about 107 updates since then that it asked to be allowed to install today
Gnome 2.22.3
Motherboard Asus P5GC-MX
CPU Intel Pentium 4 3GHz (System Monitor says there are processor 0 and processor 1 both with these specs. I don't know if that means there's two of them)
2GB RAM
Graphics card Invidia Geforce 8500 GT
Monitor LG Flatron L1811S max res 1280x1024
Additional relevant packages installed:
linux-restricted-modules 2.6.24.19-generic
nvidia-glx-legacy

Screen refresh rate currently showing in System>Preferences>Screen Res is 60Hz.

I have attached my current xorg.conf file (I added a .txt on the end to get the forum to accept it). I've been through several but none of them worked.

Thanks very much for any help anyone can provide. :)

---

### Post by wolfen69 on 2008-09-03
try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot.

---

### Post by andrewkirk on 2008-09-03
> **wolfen69 said:**
> try ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot.

Thanks wolfen69. I tried this, but all it did was revert the xorg.conf to an entirely generic version (attached) and System>Preferences>Screen Res still offers only the same restricted set of resolutions.

FWIW the system reply to the command was 
xserver-xorg post-inst warning: overwriting possibly customised configuration file; backup in /etc/X11/xorg.conf.20080903183744

---

### Post by andrewkirk on 2008-09-06
I found a fix. I installed the proprietary Nvidia drivers for the graphics card, as described on the following website:

[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) 

Then I rebooted and went into the Screen Resolution utility and voila, there was the 1280 x 1024 resolution, available to be chosen. Yippee!! :)

I had also inserted lines specifying Horizsync and Vertrefresh in the xorg.conf file, because I had read that could be a problem, but that on its own hadn't been enough to fix it.

Anyway, attached is my xorg.conf file, in case this is of any use to anyone else.

---

