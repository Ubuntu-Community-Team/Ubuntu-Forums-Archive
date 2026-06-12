---
title: "64 bit vs. 32 bit Ubuntu 12.10 Compiz stability question"
date: 2012-11-14
forum: Multimedia Software
---

### Post by ARooster on 2012-11-14
I've been on Ubuntu for quite awhile now. Since the shift to Unity I was less than fully happy with the look and feel of the new Unity/Ubuntu desktop, but I have stuck with it and I grew used to it in spite of a few stability issues, mostly due to nVidia drivers, I suppose.

When the new 12.10 came out I went for a clean install of the 64-bit system (as I usually do). The stability's gotten even worse, Compiz keeps crashing and while using Oracle's VirtualBox to run an instance of Windows (yes, I do bloody need Windows to an extent, so back off :P) or Thunderbird mail client, the rather nice window selection feature you get by clicking on the active sidebar icon for the 2nd time keeps locking up, I am currently, after doing yet another fresh install, in the process of installing one or two alternative desktops which have proven to be more stable. This is rather unfortunate as Unity kind of grew on me (like some sort of persistent rash).

I was wondering, as I do seem to be one of the many facing these problems, have any of you noticed less problems with the 32 bit version or is it just more of the same? Is it worth going to 32-bit, will I gain more stability by it?

---

### Post by ARooster on 2012-11-15
For those of you who may be wondering (or possibly suffering the same problems), I just installed 32 bit Ubuntu 12.10. The graphics drivers issues seem to be the same from what I've seen so far. Opting for the proprietary nVidia driver in the Software sources menu brings up a low resolution desktop without the Unity interface and after ctrl+alt+F2 screen turns black without a prompt showing up. If you find yourself in this situation I find the easiest way to deal with it is bring up terminal with ctrl+T.

---

### Post by Paqman on 2012-11-15
Right so the issue is with driver support for your graphics card.

Which graphics card do you have?

This is a support issue btw, maybe a mod would like to move this out of the Cafe?

---

### Post by ARooster on 2012-11-15
nVidia GeForce 8800 GTS is the graphics card.

Yes, in retrospect I'd have posted this in support. Sorry about that.

---

### Post by oldos2er on 2012-11-15
Moved to Multimedia & Video.

---

### Post by juanmanuel78 on 2012-11-20
I found this article usefull to set up properly the privative nvidia drivers. Unfortunately it's in spanish but I write here the idea.

It seems to be a bug, Ubuntu 12.10 has been released without the "linux-headers-generic" package.  This isn't a problem, unless you have to compile a module of the kernel.  In that case you may have several problems, Xorg breaks, black screens, etc.

This bug has been reported in:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

To properly set up the privative drivers you have to:

1) Install de Header Generic:

sudo apt-get install linux-headers-generic

2) Install de privative driver you want:

sudo apt-get install nvidia-current
sudo apt-get install nvidia-current-updates
sudo apt-get install nvidia-experimental-304

(select the one you want, this can also be done in "software source")


In case you have installed the privative drives without the Headers Generic, you need to first uninstall the drivers, then install in the order descripted above and reboot.

This is the article in spanish, if it helps:

[http://www.ubuntu-guia.com/2012/10/instalar-controlador-nvidia-en-ubuntu.html](http://www.ubuntu-guia.com/2012/10/instalar-controlador-nvidia-en-ubuntu.html)

---

### Post by efflandt on 2012-11-21
One source I read said you also needed linux-source, but maybe not really.  But if you have already installed nvidia-current with everything related (I installed it from Software Center) and it does not work, you don't really need to "uninstall" nvidia drivers. You can add the kernel headers and "reinstall" nvidia-current or whatever version you need

```
sudo apt-get install linux-headers-generic
sudo apt-get --reinstall install nvidia-current
```Once you reboot after that, everything should fall into place.

Not exactly newbie friendly, but I guess if they stick with it, they can learn something new.

---

