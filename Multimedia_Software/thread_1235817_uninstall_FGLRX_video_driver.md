---
title: "uninstall FGLRX video driver"
date: 2009-08-09
forum: Multimedia Software
---

### Post by gseward on 2009-08-09
I am running Ubuntu 9.04 with a onboard Ati Radeon HD 3300 video card, and I have installed the Proprietary FGLRX video driver, now when I boot I get the screen with the  word Ubuntu and the colored moving graphic below it, then a black screen. I cannot get into my Ubuntu installation. Is there a way to uninstall the FGLRX driver from the Install cdrom?  Or I just have to bite the bullet and re install Ubuntu?

AsRock AOD790GX/128


Gil

---

### Post by efgevh on 2009-08-09
> **gseward said:**
> I am running Ubuntu 9.04 with a onboard Ati Radeon HD 3300 video card, and I have installed the Proprietary FGLRX video driver, now when I boot I get the screen with the  word Ubuntu and the colored moving graphic below it, then a black screen. I cannot get into my Ubuntu installation. Is there a way to uninstall the FGLRX driver from the Install cdrom?  Or I just have to bite the bullet and re install Ubuntu?

AsRock AOD790GX/128


Gil


perhaps from the live-cd, mount your system and replace xorg.conf with backup

---

### Post by gseward on 2009-08-09
> **efgevh said:**
> perhaps from the live-cd, mount your system and replace xorg.conf with backup

How do I mount my system from the live-cd?  Would xorg.conf have been backed up when I installed the proprietary driver?
Thanks

---

### Post by smdeep on 2009-08-11
Boot your computer again. Wait for sometime and see if you can get shell access by typing ctrl+atl+f1. If you get a login prompt login to the shell and remove the driver and reboot.

---

### Post by gseward on 2009-08-25
> **gseward said:**
> I am running Ubuntu 9.04 with a onboard Ati Radeon HD 3300 video card, and I have installed the Proprietary FGLRX video driver, now when I boot I get the screen with the  word Ubuntu and the colored moving graphic below it, then a black screen. I cannot get into my Ubuntu installation. Is there a way to uninstall the FGLRX driver from the Install cdrom?  Or I just have to bite the bullet and re install Ubuntu?

AsRock AOD790GX/128


Gil

Tried all the suggestions here with no luck.  I have reinstalled Ubuntu 9.04 and tried the same FGLRX video driver again, with (Surprise!!!) the same result.  I really don't want to reinstall again, I would really like to fix this, as with the default driver I only get a maximum of 1024*768, and I would like higher res.  Maybe I should be going to ATIs web site. Does anyone know if I can install a video card and have it configured automatically?
Any help appreciated.

---

### Post by Struki on 2009-08-25
I had similar problems with the drivers (I have radeon hd 3200), I dont know how to help with uninstalling the drivers, but...
After I installed ubuntu for the second time(same reason as you), I didn't install the proprietry drivers, instead I went directly to the ATI official[ site ]("http://http://support.amd.com/us/gpudownload/Pages/index.aspx")and downloaded drivers directly from there. You have them under: Linux >Radeon >3xxx
There is also a pdf "how to install" guide, but there is a whole lot of stuff that you don't realy need you just have to navigate your way tru terminal to the drivers and then run them with the command:

*sudo sh ./ati-driver-installer-9-8-x86.x86_64.run*

Reboot, and all should work well!

GL!

P.S. You should run the command as root

---

### Post by cadwill on 2009-08-25
I'm having the same problem with the ATI 2400 pro card, and had to re-install ubuntu a couple times before I tried booting in the repair mode and trying
sudo apt-get remove --purge xorg-driver-fglrx
or 
sudo apt-get remove xorg-driver-fglrx fglrx-kernel-source

then sudo apt-get update
and run
sudo dpkg-reconfigure xserver-xorg

It gets me back into safe graphics mode, so I can try something else (still working on getting the graphic card to work!) at least and saves me from the entire reinstall. I'm sure others know more about this, but good luck.

---

### Post by SteveONCSU on 2009-08-25
> **Struki said:**
> I had similar problems with the drivers (I have radeon hd 3200), I dont know how to help with uninstalling the drivers, but...
After I installed ubuntu for the second time(same reason as you), I didn't install the proprietry drivers, instead I went directly to the ATI official[ site ]("http://http://support.amd.com/us/gpudownload/Pages/index.aspx")and downloaded drivers directly from there. You have them under: Linux >Radeon >3xxx
There is also a pdf "how to install" guide, but there is a whole lot of stuff that you don't realy need you just have to navigate your way tru terminal to the drivers and then run them with the command:

*sudo sh ./ati-driver-installer-9-8-x86.x86_64.run*

Reboot, and all should work well!

GL!

P.S. You should run the command as root
I might add that ATI just released updated drivers on their site.

---

### Post by LordFlick on 2012-11-06
I have a similar problem. I can get to the ati catalyst install but I need to remove the original driver first. I have no Idea how to do that

---

### Post by oldos2er on 2012-11-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

