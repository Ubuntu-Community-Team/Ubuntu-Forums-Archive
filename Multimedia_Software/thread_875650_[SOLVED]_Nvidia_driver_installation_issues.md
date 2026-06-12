---
title: "[SOLVED] Nvidia driver installation issues"
date: 2008-07-31
forum: Multimedia Software
---

### Post by tyler87 on 2008-07-31
I'm having difficulties installing the latest version of NVIDIA's drivers. The drivers I'm using are the 64bit restricted release from NVIDIA. I believe the specific driver is 173.14.05. 

I start by Ctrl+Alt+F1

sudo /etc/init.d/gdm stop         to stop xserver

sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run 

I run the installer and everything works just fine. At the end it asks me if it can replace the x config file so it will be used when I restart X. So I say yes and restart x with 

sudo /etc/init.d/gdm start

Hooray! Everything works as intended! Until I restart my machine. As soon as I hit restart or shutdown I hear my system beep. The system hangs when booting up, looping about five times until I'm brought into the "low resolution" mode. It tells me it can't detect my video card... which is an 8800gt by the way. 

I can run Xfix and it fixes the problem.. but the new driver isn't utilized. 

Any suggestions?

The only reason I really want to update my drivers is because of flash.. For whatever reason, it works a LOT better with the latest drivers from NVIDIA. Its still garbage but it works better. With the new drivers I can actually go fullscreen on most videos. The only game I really play is WoW and the driver updates haven't done much for performance there.

---

### Post by overdrank on 2008-07-31
> **tyler87 said:**
> I'm having difficulties installing the latest version of NVIDIA's drivers. The drivers I'm using are the 64bit restricted release from NVIDIA. I believe the specific driver is 173.14.05. 

I start by Ctrl+Alt+F1

sudo /etc/init.d/gdm stop         to stop xserver

sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run 

I run the installer and everything works just fine. At the end it asks me if it can replace the x config file so it will be used when I restart X. So I say yes and restart x with 

sudo /etc/init.d/gdm start

Hooray! Everything works as intended! Until I restart my machine. As soon as I hit restart or shutdown I hear my system beep. The system hangs when booting up, looping about five times until I'm brought into the "low resolution" mode. It tells me it can't detect my video card... which is an 8800gt by the way. 

I can run Xfix and it fixes the problem.. but the new driver isn't utilized. 

Any suggestions?

Hi and welcome, you may try what  PmDematagoda suggested here
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
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

---

### Post by tyler87 on 2008-07-31
I'll make sure to give that a try when I get home. Thanks! Updates to follow...

---

