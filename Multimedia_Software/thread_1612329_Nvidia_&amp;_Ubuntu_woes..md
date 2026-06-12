---
title: "Nvidia &amp; Ubuntu woes."
date: 2010-11-03
forum: Multimedia Software
---

### Post by MadMikeyB on 2010-11-03
Hi all,

Been having some trouble for some time (since 9.04) with my Nvidia GPU (drivers) and Ubuntu. I have a NVidia GeForce 9400 GT 512MB DDR2, and I am currently running 10.10. Here's the scenario.

I Followed the instructions here; [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Removed Noveau, Activated the latest (already installed previously) Nvidia drivers, and restarted.

Now, when I boot up, It loads into ubuntu, without any GUI. I've heard that maybe I should run sudo startx, this causes a 'no screen/display'(I forget the exact wording) or 'no driver' error.

To get to the desktop, I have to boot up, hold down shift, which brings up the GRUB bootloader, I then have a choice of kernels and recovery mode etc, I choose the second one down (latest kernel, recovery mode) and choose "FailSafeX" as the graphics option, it then loads in "Low Graphics Mode", and all is fine for around 15 minutes, and then after that, it just freezes up. (all the lights, caps lock, num lock and scroll lock on the keyboard start to flash and the computer becomes unresponsive.

Now, Everything was fine running on the Noveau drivers, except that I could NOT watch any video WITHOUT it being laggy and choppy as hell on fullscreen, but I can live without video for now, I would like to know if possible, how I can fix this, what steps to take, **OR** how to get back to noveau or whatever which was working before..

Appreciate any help! I've tried to be as detailed as I can.

---

### Post by r-mo on 2010-11-03
Try the command
```
sudo nvidia-xconfig
```
It should generate the correct X11 config file for you.

If it's not installed make sure you do actually have everything installed

```
sudo apt-get install nvidia-common nvidia-current nvidia-glx-185 nvidia-settings
```

HTH

---

### Post by MadMikeyB on 2010-11-03
Thanks for the answer, I've just tried that, and rebooted, and it booted into tty1 as CLI console, no GUI again. I log in and try "sudo startx" and the error is:
```

FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your systems kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

```

This is the same one as before :(

---

### Post by Mills00013 on 2010-11-03
I would personally add the xorg edgers PPA to your repositories list and then do a "sudo apt-get update && sudo apt-get upgrade" command. The PPA is ppa:xorg-edgers/ppa. Then just to double check, do "sudo apt-get install nvidia-current" and then the config command again. Then restart. See what happens.

---

### Post by f3nr1c on 2010-11-03
I have a standard protocol whenever I install Ubuntu (with an Nvidia 9600 GT). This is part of it. I used to have problems when I first started, but I have stuck to this, and have had none. 

> 
sudo apt-get --purge remove xserver-xorg-video-nouveau

Add proprietary driver from Jockey/Synaptic.(nvidia-current)

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

reboot


EDIT: as above, xorg-edgers ppa is good, but failing that ubuntu-x-swat.

---

### Post by SeijiSensei on 2010-11-04
I have never had a problem simply using the Hardware Drivers application (now called "Additional Drivers") to install the proprietary NVIDIA driver.  I have a 9500 GT card with essentially identical specs to yours.  It's worked perfectly whenever I install the driver using the built-in Ubuntu application.

---

### Post by inso_741 on 2010-11-04
> **SeijiSensei said:**
> I have never had a problem simply using the Hardware Drivers application (now called "Additional Drivers") to install the proprietary NVIDIA driver.  I have a 9500 GT card with essentially identical specs to yours.  It's worked perfectly whenever I install the driver using the built-in Ubuntu application.

yes, its better to use drivers provided by the ubuntu team unless you need a specific feature thats only available in the latest binary released by nvidia

---

### Post by MadMikeyB on 2010-11-05
> **Mills00013 said:**
> I would personally add the xorg edgers PPA to your repositories list and then do a "sudo apt-get update && sudo apt-get upgrade" command. The PPA is ppa:xorg-edgers/ppa. Then just to double check, do "sudo apt-get install nvidia-current" and then the config command again. Then restart. See what happens.

Done that, thanks, and it still boots into a tty with no graphical interface.

> **f3nr1c said:**
> I have a standard protocol whenever I install Ubuntu (with an Nvidia 9600 GT). This is part of it. I used to have problems when I first started, but I have stuck to this, and have had none. 



EDIT: as above, xorg-edgers ppa is good, but failing that ubuntu-x-swat.

I've done everything you said, and it still has the above error with the "No drivers available" error.

> **SeijiSensei said:**
> I have never had a problem simply using the Hardware Drivers application (now called "Additional Drivers") to install the proprietary NVIDIA driver.  I have a 9500 GT card with essentially identical specs to yours.  It's worked perfectly whenever I install the driver using the built-in Ubuntu application.

I always have problems with the drivers, every single time :(

Thank you everyone for your help, maybe it's something to do with the version of drivers I have?

---

### Post by YfoMp5QBh2 on 2010-11-05
Hi there, had the exact same issue as yourself and managed to get it sorted with the good help of the people in these forums. see the below thread.
 
[http://ubuntuforums.org/showthread.php?t=1565176](http://ubuntuforums.org/showthread.php?t=1565176)

---

