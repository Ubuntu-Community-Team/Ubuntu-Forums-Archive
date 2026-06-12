---
title: "NVIDIA GT240 driver issue noob ubuntu user PLEASE HELP"
date: 2010-05-26
forum: Multimedia Software
---

### Post by locally.grown on 2010-05-26
Hi, 
 
I am completely new to ubuntu and linux, I was a long time hateful windows user and decided to give old bill gates the boot. However, now I am stuck on the first minor problem I encounter! 
 
I just downloaded and installed ubuntu 8.04 on my AMD64 pc. First thing I needed was a driver for my Nvidia geforce GT240 card, I downloaded the driver (NVIDIA-Linux-x86_64-195.36.24-pkg2.run) it appeared on my desktop, after double clicking it, it showed an error message (gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a different character coding and try again) so I selected the only other option of the drop down menu of the character coding which was Western, and the same error message appeared, then went to system -> admin -> hardware drivers and NOTHING shows up in any of the columns. 
 
Forgive me if this is a very basic problem, I am extremely fresh to this OS and have no idea about the coding behind it, or what any of these error messages mean. Please, please could someone help me install my graphics card drivers using lamens terms rather than jibberish, your help would be greatly appreciated.
 
At the moment the screen resolution is on the highest setting (800x600) which is heinous when your monitor is a 40" LCD HDtv, I am looking to get the 1080p perfection. Also, the sound does not work, but I am assuming it is all part of the same drivering seeing as it was on the windows equivelent. 
 
 
Cheers in advance!

---

### Post by rhinert on 2010-05-26
> **locally.grown said:**
> Hi, 
 
I just downloaded and installed ubuntu 8.04 



Are you running 8.04 or 10.04?  

I just installed the same vid card in Kubuntu 10.4 by going to K-menu -> System -> hardware drivers and enabling the proprietary drivers.  I assume you have something similar in Ubuntu?

BTW, this vid card is seriously sweet.  It appears to be the best value right now......

---

### Post by realzippy on 2010-05-26
...yep,install 10.04 since it is the new LTS...

---

### Post by spinoza666 on 2010-05-26
Hmmm a bit unsure if I'm getting this, but I'll give it a go.

The easiest solution to getting nvidia to work would be to use the Ubuntu driver tool, which will normally install and configure everything for you:

System ->  Administration -> Hardware Drivers

Is this what you did? Or have you downloaded an installer from somewhere, eg. the Nvidia-website?

I would first try the driver tool, before trying to install this .run file. You will need to enable the restricted repository (System -> Administration -> Software Sources), and run:

sudo apt-get update

in the terminal before you use the driver tool. In my experience you often need to reboot before the driver will be available.


If you need to do the latter, I believe you need to make the file executable and run it, see this for how to:

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

---

### Post by spinoza666 on 2010-05-26
With regards to the sound issue, I would try the easiest thing first, put the volume up:)

Right click on the volume icon up to the right, and click on 'Sound preferences'. Then make sure the volume is up.

If that's okay, enter this in the terminal, make sure all the volumes are up here too. Use the keyboard up/down to set the volume:

alsamixer

Hopefully that will sort it.

---

