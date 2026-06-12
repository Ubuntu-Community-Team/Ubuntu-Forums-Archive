---
title: "Nvidia Card Messed Up"
date: 2010-06-26
forum: Multimedia Software
---

### Post by Zayfox on 2010-06-26
Alright, just another one of those "My card messed up" threads, but I've looked through various solutions, some mentioning a TV tuner (don't have, or if I do, don't use it), or allocating Vmemory (which I did, to no avail).

From boot, the NEC splash is messed up. Weird lines and stuff everywhere. I've noticed that text in the console is fine, it seems to almost have something in front of it, if you can picture that. Once I get to GDM loading, I get an error with the traditional Nvidia errors, telling me that there's no usable configuration for my monitor. However I did notice that emptying the config file leaves no error message, but I still have the really weird screen.

So, UF. What do? I'm open to any suggestions here 'cause I kinda need that machine. I've tried a LiveCD and reinstalled the Nvidia drivers just to see if it was something with the loaded drivers, but that didn't work either.

The model is Nvidia 9800GT, I'm on Ubuntu Lucid Lynx 10.04.

[B]Edit:
[/B]
I'll see if I can port the logs across to my laptop somehow, as I can't stand looking at that screen for more than five seconds or so.

---

### Post by Zayfox on 2010-06-26
Alright, here's the log for Xorg.

---

### Post by tommcd on 2010-06-26
> **Zayfox said:**
>  I've tried a LiveCD and reinstalled the Nvidia drivers just to see if it was something with the loaded drivers, but that didn't work either.
How did you install the nvidia driver? Is it the driver from the Ubuntu repos? Or did you install the driver from nvidia.com?

Has the nvidia driver been failing ever since you installed 10.04? Or was the driver running ok, and this is a new issue?
Here is your problem from the Xorg.0.log:
```

(EE) Jun 26 19:56:41 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Jun 26 19:56:41 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Jun 26 19:56:41 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jun 26 19:56:41 NVIDIA(0):     README for additional information.
(EE) Jun 26 19:56:41 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"

```
What happens if you try to load the nvidia module manually:
```
sudo modprobe nvidia
```

Also post your **xorg.conf** file.

---

### Post by gradinaruvasile on 2010-06-26
You have to blacklist the nouveau module and disable kms.
And after installing the proprietary driver, make sure you have a generated xorg.conf (you can re-generate it for the nvidia driver with "sudo nvidia-xconfig").

---

### Post by nss0000 on 2010-06-26
> **Zayfox said:**
> Alright, just another one of those "My card messed up" threads, but I've looked through various solutions, some mentioning a TV tuner (don't have, or if I do, don't use it), or allocating Vmemory (which I did, to no avail).

From boot, the NEC splash is messed up. Weird lines and stuff everywhere. I've noticed that text in the console is fine, it seems to almost have something in front of it, if you can picture that. Once I get to GDM loading, I get an error with the traditional Nvidia errors, telling me that there's no usable configuration for my monitor. However I did notice that emptying the config file leaves no error message, but I still have the really weird screen.

So, UF. What do? I'm open to any suggestions here 'cause I kinda need that machine. I've tried a LiveCD and reinstalled the Nvidia drivers just to see if it was something with the loaded drivers, but that didn't work either.

The model is Nvidia 9800GT, I'm on Ubuntu Lucid Lynx 10.04.

[B]Edit:
[/B]
I'll see if I can port the logs across to my laptop somehow, as I can't stand looking at that screen for more than five seconds or so.

ZF:

I'm running a similar Vidcard ( 9800gtx+ ) and x64LL_10.04 without issue or need for manual adjustment. NV driver 195.xx.xx was automagically installed with the OS. Scores in UNIGINE_Tropics/Heaven are reasonable. 

So --- I think your card should work just fine.

---

### Post by gradinaruvasile on 2010-06-26
The "NV" (actually this is called nvidia) 195.xx driver is NOT installed automagically (maybe you installed/activated it).

The driver that is installed in 10.04 by default for nvidia cards is the "nouveau" open source driver (it is NOT the older "nv" driver that was replaced by nouveau). This driver is a reverse-engineered nvidia driver and thus may not support correctly all functions of the various nvidia cards (for example i have an onboard 8200 and that just blacks out with nouveau) - it is also capable of KMS (kernel mode switching) meaning that all virtual terminals will have the monitors resolution and the vt switching is performed faster and seamlessly.
The downside is that the nouveau driver conflicts with the "nvidia" (proprietary) driver and it MUST be blacklisted or else it will load ahead of the "nvidia" module and prevent that too from working leading to disabled X server.
This is done by:

sudo nano /etc/modprobe.d/blacklist.conf

and appending to the end of the file the line:

blacklist nouveau

And then reboot.
Also, it might be necessary to disable kms from grub.cfg, but if the nouveau module is blacklisted, probably this step is not needed (on my rig i just blacklisted nouveau and it was enough).
The nvidia driver should load if properly installed (the xorg.conf is set up properly).

---

### Post by nss0000 on 2010-06-26
> **gradinaruvasile said:**
> The "NV" (actually this is called nvidia) 195.xx driver is NOT installed automagically (maybe you installed/activated it).

The driver that is installed in 10.04 by default for nvidia cards is the "nouveau" open source driver (it is NOT the older "nv" driver that was replaced by nouveau). This driver is a reverse-engineered nvidia driver and thus may not support correctly all functions of the various nvidia cards (for example i have an onboard 8200 and that just blacks out with nouveau) - it is also capable of KMS (kernel mode switching) meaning that all virtual terminals will have the monitors resolution and the vt switching is performed faster and seamlessly.
The downside is that the nouveau driver conflicts with the "nvidia" (proprietary) driver and it MUST be blacklisted or else it will load ahead of the "nvidia" module and prevent that too from working leading to disabled X server.
This is done by:

sudo nano /etc/modprobe.d/blacklist.conf

and appending to the end of the file the line:

blacklist nouveau

And then reboot.
Also, it might be necessary to disable kms from grub.cfg, but if the nouveau module is blacklisted, probably this step is not needed (on my rig i just blacklisted nouveau and it was enough).
The nvidia driver should load if properly installed (the xorg.conf is set up properly).


Perhaps in your installation ... or in most NV installations ( it was surely true for my "2nd" kit AMD5400/NV9400 install of x64LL10.04.) Yes, the nouveau driver is installed by default ... and an excellent one at that!

But, I assure you, on my **1st** kit ( AMD965/MSIgd70/9800gtx+ ) from the first "burn & learn" of beta_Lucid-Lynx three months(?) ago to my last update the automagically installed driver has been the NV_195.xx.xx

I have not-so-much as **touched** the NV_driver panel ... and I have had to do that before. No telling what your issue might be ... perhaps you are running an INTEL processor and the NV recognition software did not want to dirty-its-hands on borgish kit ??

---

### Post by Zayfox on 2010-06-26
From memory, the issue started just after I turned my PC on yesterday morning, the only thing I did regarding graphics the night before was install DirectX libraries for Wine.

As for that weird Nouveau thing, I uninstalled that, I believe. I'll look at that in a moment.

**Edit:**

Blacklisted Nouveau and restarted. No difference. :(

**Edit:**

> **nss0000 said:**
> ZF:

I'm running a similar Vidcard ( 9800gtx+ ) and x64LL_10.04 without issue  or need for manual adjustment. NV driver 195.xx.xx was automagically  installed with the OS. Scores in UNIGINE_Tropics/Heaven are reasonable. 

So --- I think your card should work just fine.
Mine used to work just fine. =\

---

### Post by Zayfox on 2010-06-26
> **tommcd said:**
> How did you install the nvidia driver? Is it the driver from the Ubuntu repos? Or did you install the driver from nvidia.com?

I installed it via the "Hardware Drivers" option back in Karmic. It's updated a few times but this just happened out of the blue.
> **tommcd said:**
> Has the nvidia driver been failing ever since you installed 10.04? Or was the driver running ok, and this is a new issue?
Here is your problem from the Xorg.0.log:
```

(EE) Jun 26 19:56:41 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Jun 26 19:56:41 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Jun 26 19:56:41 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jun 26 19:56:41 NVIDIA(0):     README for additional information.
(EE) Jun 26 19:56:41 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"

```What happens if you try to load the nvidia module manually:
```
sudo modprobe nvidia
```Also post your **xorg.conf** file.
The latter, it was working previously.

Loading it manually outputs this:
```
FATAL: Module nvidia not found.
```I'll get the Xorg config later.

---

### Post by Zayfox on 2010-06-27
Using DBAN on it now. I'm just gonna try going from scratch. Farewell, 40GB of games and 8GB of music!

---

### Post by gradinaruvasile on 2010-06-27
> **Zayfox said:**
> I installed it via the "Hardware Drivers" option back in Karmic. It's updated a few times but this just happened out of the blue.

The latter, it was working previously.

Loading it manually outputs this:
```
FATAL: Module nvidia not found.
```I'll get the Xorg config later.

Well you dont have the driver installed right (module nvidia not found). The Hardware drivers sometimes dont work right.
Install the nvidia-glx package manually and then run "sudo nvidia-xconfig".

I personally use the latest installer directly from nvidia's site - it is simple and straightforward (but when certain packages and the kernel are upgraded you need to run it again).

---

### Post by Zayfox on 2010-06-27
> **gradinaruvasile said:**
> Well you dont have the driver installed right (module nvidia not found). The Hardware drivers sometimes dont work right.
Install the nvidia-glx package manually and then run "sudo nvidia-xconfig".

I personally use the latest installer directly from nvidia's site - it is simple and straightforward (but when certain packages and the kernel are upgraded you need to run it again).
```
elliot@Hades:~$ sudo aptitude install nvidia-glx
[sudo] password for elliot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for nvidia-glx
No candidate version found for nvidia-glx

```

Also, attached is the Xorg.conf you requested.

---

### Post by tommcd on 2010-06-27
> **gradinaruvasile said:**
> 
The downside is that the nouveau driver conflicts with the "nvidia" (proprietary) driver and it MUST be blacklisted or else it will load ahead of the "nvidia" module and prevent that too from working leading to disabled X server.
This is done by:
sudo nano /etc/modprobe.d/blacklist.conf
and appending to the end of the file the line:
blacklist nouveau

This is a good point. However, I did not do this. How careless of me!!!
I installed the nvidia driver for my 8600GT card like this:
```

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```
A file named *nvidia-graphics-drivers.conf * was created in my /etc/modprobe.d/ directory which contains this:
```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```
 This file must have been created automatically, as I did not create it or edit it myself. So it seems that Ubuntu's installer for the nvidia driver will automagically blacklist nouveau.
I always prefer to install the nvidia driver directly from the terminal, rather than trusting the: system > administration > hardware drivers thing.

---

### Post by tommcd on 2010-06-27
> **Zayfox said:**
> From memory, the issue started just after I turned my PC on yesterday morning, the only thing I did regarding graphics the night before was install DirectX libraries for Wine.

Perhaps you could try removing these DirectX libraries then if everything was fine before that. 
Have you been running Wine as root? If so, this is a big no-no, and a potential security issue.

I am not all that familiar with Wine, since I have only briefly tried using it a while back to install some Windows games in Ubuntu. So I don't know if those DirectX libs would be a problem or not. I suspect not, but it is worth a try anyway.
Since you stated that you are using the nvidia driver from the Ubuntu repos, can you post the output of:
```
aptitude search nvidia
```
This will tell us exactly what nvidia packages you have installed.
 A "p" before a package name in the output means that the package is purged (i.e., not installed). An "i" before a package name means it is installed. An "i A" means that it was automagically installed, perhaps as a dependency for another package. A "c"  means that the package was removed, but it's config files remain. A "B" before a package name means it has broken dependencies.

---

### Post by gradinaruvasile on 2010-06-27
It seems i was mistaken about the nvidia drivers package - it is nvidia-common as tommcd pointed it out (i use Debian and here nvidia-glx is the package name).

Follow tommcd's instructions, they seem to be good.

---

### Post by gradinaruvasile on 2010-06-27
Double post. sorry

---

### Post by Zayfox on 2010-06-27
I used your method for installing the drivers and I got the blacklist config thing too.

I ran WoW again after a second DBAN and it crashed on me again, but this time I managed to not completely mess my computer up, so I still have it working fine. I'm guessing that the issue is based around the latest version of Wine (1.2-rc5).

---

### Post by Zayfox on 2010-06-28
Alright scratch that, it seems to occur when I allow wine apps to control the window then try to alt tab. Anyway, it's now screwed up beyond belief, I can't even login or get to terminal (CTRL+ALT+1) at the login screen.

This is ridiculous now. Why has it only just started happening?

**Edit:**

I've actually wiped the computer for the THIRD time using DBAN, yet I still can't use the LiveCD. The graphical trauma is still there even at boot!
This wasn't happening at all during the day when I temporarily had it working, what the hell is this?

---

### Post by tommcd on 2010-06-29
> **Zayfox said:**
> Alright scratch that, it seems to occur when I allow wine apps to control the window then try to alt tab. Anyway, it's now screwed up beyond belief, I can't even login or get to terminal (CTRL+ALT+1) at the login screen.

As I said previously I don't use Wine, so I can't test this. However, I do know that running Winows apps in Wine is often problematic. This may be a Wine issue, and not an Ubuntu or nvidia driver issue.
If you install Ubuntu from scratch, then install the nvidia driver as per my instructions in post #13 of this thread, are you then able to play 3D native linux games like Nexuiz or World of Padman?
After installing the nvidia driver from the Ubuntu repos, post the output of:
```
glxinfo | grep -i direct
```
It should report: **direct rendering: Yes**, with possibly some other stuff as well.
Are you able to run **glxgears** and get a decent frame per second rate?
I know glxgears is not a valid benchmarking app, but you should expect a good fps with your card though. For what it's worth, I get over 8000 fps on my 8600GT. I am running Salix at the moment, but it should be about the same with Ubuntu.

---

### Post by Zayfox on 2010-07-02
Turns out the card had actually had a component die. Got it replaced.

Solved, sorry for wasting your time. >_<

---

