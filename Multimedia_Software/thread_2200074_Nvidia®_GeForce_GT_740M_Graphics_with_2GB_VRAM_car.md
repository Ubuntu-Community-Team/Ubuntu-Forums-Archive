---
title: "Nvidia® GeForce GT 740M Graphics with 2GB VRAM card drivers for ubuntu."
date: 2014-01-17
forum: Multimedia Software
---

### Post by Thaitransit on 2014-01-17
I have a Lenovo Thinkpad Edge E540 (20C6002SAU) notebook that has graphics card problems after installing Ubuntu 12.04 LTS.

The  issue is after installing ubuntu or Kubuntu on this machine I could not see my graphics card. I also had errors "chipset not reconised" and other broken pipe errors related to this graphics card. It appears ubuntu could not see my Nvidia® GeForce GT 740M Graphics with 2GB VRAM graphics card that is  installed inside my notebook. This notebook also has intergrated intel graphics (Intel® HD Graphics 4600).

The question I ask is this problem related to no current Ubuntu / Kubuntu drivers for this hardware?

If so where would I be able to locate drivers for the Nvidia® GeForce GT 740M Graphics with 2GB VRAM graphics card?

If they do exisit how would I install the drivers onto my notebook?

Thanks for the help

---

### Post by Bashing-om on 2014-01-17
Thaitransit; Hi !

The problem is that Nvidia does not support linux with switchable graphics.
Open source developers are working real hard on this. Depending on the kernel you are running(HES enabled ?) there may be a great deal of help available in the open source world.
For instance:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)
Also there is the BumbleBee project:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

This one may still have some relevance:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

The good news is that there are options; The bad news is that you have work to do and decisions to make.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by efflandt on 2014-01-18
It was my understanding that Ubuntu 13.10 had some things installed by default to be able to handle dual graphics (in this case integrated Intel and Nvidia graphics). So I installed 64-bit 13.10 (instead of 12.04) on my laptop that has i7-4700MQ cpu with Intel HD 4600 and GTX 765M graphics. You need to use **nomodeset** kernel boot parameter during install (which grub will then use automatically after install). You will need to install nvidia drivers using Software Center, or apt-get, or synaptic (if you installed it). And you will need to use "optirun " prefix for any program (games, etc.) that you want to use the nvidia graphics.

---

