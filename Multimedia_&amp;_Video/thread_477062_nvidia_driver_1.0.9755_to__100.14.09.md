---
title: "nvidia driver 1.0.9755 to : 100.14.09??"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by hecato on 2007-06-17
Hi there people.


OK, I must say I have been working in a sane 1.9775 installation, that is able to play a little with ogre3d and CGtutorial from nv, also glxinfo reported direct render yes.


the thing is taht I see the new 100.14.09 driver at nvidia, and because I know how to install in console mode (kill gdm) go to a console and enter as root, install nvidia, compile headers and things like that.... I say, **how hard this can be**???

I give it a try, but I forget to uninstall 9775 before, anyway, installation didnt say nothing about it... it has requested the headers, compiled and installated. After restart of the gdm it dosent work, if you whant to know the internals :KS [Ubuntu 1.0.9755 to : 100.14.09?? :KS]("http://www.nvnews.net/vbulletin/showthread.php?t=93407") I have attached some logs there.


Anyway, I thin that the correct way now is uninstall 9775 the first 2 packages get deleted OK they are **nvidia-glx-new** and [B]nvidia-glx-dev.

[/B]But in fact this isnt enought, because at start it say that thee is a mismatch between **nvidia-kernel-common** and the driver. If I try uninstall **nvidia-kernel-common** with synaptic, it also try to delete:
> 
Eliminating nvidia-kernel-common


nvidia-kernel-common                         will be eliminated with configuration
linux-generic                                will be eliminated
linux-restricted-modules-2.6.20-16-generic   will be eliminated
linux-restricted-modules-generic             will be eliminated


_** The question is**_: How do I eliminate nvidia-kernel-common without delete the others....

Also from: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)


> If you use Ubuntu, please also ensure that the *linux-restricted-modules* or *linux-restricted-modules-common* packages have been uninstalled. Alternatively, you can edit the [FONT=Courier New]/etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common[/FONT] configuration file and disable the NVIDIA *linux-restricted* kernel modules (*nvidia*, *nvidia_legacy*) via:[FONT=Courier New]
DISABLED_MODULES="nv nvidia_new"[/FONT]
Additionally, delete the following file if it exists[FONT=Courier New]
rm -f /lib/linux-restricted-modules/.nvidia_new_installed[/FONT] **Please note:** unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.

---

### Post by steveneddy on 2007-06-18
I used to  go through tis all of the time, but got tired of recompiling all the time when there was a kernel update.

---

### Post by hecato on 2007-06-18
A yey, I have finally managed, in fact you need let synaptic uninstall all the files that have marked, also delete all the linux-restricted* and other files that can be found in the [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) linked before in this thread. And then go other time to console without gdm running and install again the driver.

---

### Post by dabl on 2007-06-18
Thanks for posting this, hecato.  I have a -9755 installation that is working perfectly, with Beryl and the eye-candy.  I've been waiting to hear about others' experiences with the new driver -- I don't want to mess up a working installation, but I'd like to get the new one once I know for sure how to do it without breaking things.  :D

---

### Post by hecato on 2007-06-18
If this serve to you, here is the steps that I do:

**1)**
> Commit Log for Sun Jun 17 21:42:39 2007


Quitó completamente los siguientes paquetes:
**nvidia-glx-new**

Quitó los paquetes siguientes:
**nvidia-glx-new-dev**
**2)**
> Commit Log for Sun Jun 17 21:46:38 2007


Quitó completamente los siguientes paquetes:
**linux-restricted-modules-2.6.20-15-generic**
**3)**
> Commit Log for Sun Jun 17 22:55:46 2007


Quitó completamente los siguientes paquetes:
**linux-restricted-modules-2.6.20-16-generic**
**nvidia-kernel-common**

Quitó los paquetes siguientes:
**linux-generic**
**linux-restricted-modules-generic**
**4)**
> Commit Log for Sun Jun 17 22:56:44 2007


Quitó completamente los siguientes paquetes:
**linux-restricted-modules-common**
Like you see I have deeted in "steps" because I dont know the impact o delete those modules... and in fact I frst delete them before... I also have tried tl install after only the 1st step, taht also didnt work, then I was deleting and also that didnt work... after I decide to delete all dosent matter that I trash teh system step 3 and 4, and also I do some extra delete of the files listed in the nvnews forum... and installed and it work now!.


The only impact I see in the system is that system->administration-> restricted drivers dosent work, becasue it need "linux-restricted-modules-2.6.20-16-generic", but if I install them, then it try install the things I have deleted ;)... and I will not let do that.


My suguestion is delete all from 1 to 4 completely.

---

