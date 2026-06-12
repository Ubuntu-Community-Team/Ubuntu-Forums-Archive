---
title: "nVidia Driver issues..."
date: 2008-08-07
forum: Multimedia Software
---

### Post by Forlornity on 2008-08-07
Hello all, I've (these past few minutes) found that I am unable to boot into any X environment using the binary nvidia drivers, which kinda sucks as I'd rather like to have the real drivers working (I game on the machine).
I'm perfectly able to start an X session with any other drivers.
This came about immediately after I (rather foolishly) ran the command "sudo apt-get install nvidia-glx" as instructed by a guide, while attempting to set up twinview.
To my chagrin, upon restarting my X server immediately after this command (and some insignificant xorg.conf edits) it failed to load.
Naturally, I restored the file from a backup and attempted once again to start my x server, but it gave me the exact same error!
From this I believe my problem lies not in my x configuration but some freak of software which has stopped my nvidia drivers working.
The drivers were, I believe, originally installed using envyNG and I have tried a fresh install of the drivers using envy again, but to no avail. My issue remains and although I have a bootable, usable system (even a terminal is usable, of course, though I am able to start wmii, using the free drivers) I would much like to see the full potential of the computer.

The error thrown at me should I attempt to start x with the binary driver is similar to such:
Error: API mismatch: the NVIDIA kernel module has version 96.43.05,
but this NVIDIA driver component has version 173.14.09. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Failed to initialise the NVIDIA kernel module! Please ensure
that there is a supported NVIDIA GPU in this system, and
that the NVIDIA device files have been created properly.
please consult the NVIDIA README for details

This is running on an x86_64 machine, with the 64 bit edition of Ubuntu Hardy.

How on earth am I to fix this!?
Thanks, Forlornity

---

### Post by logos34 on 2008-08-07
EnvyNG installs the proprietary nvidia driver, but requires that the Ubuntu binary nvidia-glx(-new) be uninstalled first.  So if you accidentally installed the -glx, you need to remove it (use **apt-get remove --purge**) then if necessary uninstall and reinstall EnvyNG.

---

### Post by overdrank on 2008-08-07
Hi and have you tried to use Envy to remove the nvidia drivers and reboot and then install again?
You may remove the drivers and then try what is suggested by PmDematagoda 
```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```
Here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)
Edit as logos34 suggest :)

---

### Post by Forlornity on 2008-08-08
I believe the issue was in that I hadn't actually done a full reboot of the machine :P
I'm not entirely positive on this matter so if someone more knowledgable than I could clarify this, but I believe it was the kernel module/driver component version mismatch which was causing the issue and I hadn't restarted the machine, therefore the driver component was being reloaded with a new version and the kernel module was not.
That's just a guess of course, I don't really know enough to be sure.

Thanks for the assistance, you certainly helped get it working!
- Forlornity

---

