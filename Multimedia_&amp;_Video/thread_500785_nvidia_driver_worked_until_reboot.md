---
title: "nvidia driver worked until reboot"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by 3408 on 2007-07-14
I'm trying to install the nvidia driver for my 8600GT, but can't get it work. I've been reading for hours on this forum on how to get it installed, but I can't get to work.
At a certain point I thought I had it working because I could finally run the app "nvidia x server settings" allowing me to set my resolution to 1440x900. 
However, it did tell me that not all changes could be applied and that this required a reboot. I did so, and after the reboot ubuntu didn't want to start X anymore.

What I did:
1. I downloaded the NVIDIA-Linux-x86-100.14.11-pkg1.run file from the nvidia website.
2. I stopped the xserver using "sudo /etc/init.d/gdm stop"
3. I ran the downloaded file using "sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run"
4. It told me that it couldn't find a kernel interface, so it had to compile one    (What is a kernel interface?)
5. It made some change changes to the xorg.conf
6. I restarted the xserver using "sudo /etc/init.d/gdm start"
7. It still didn't work, but I found that a new app called "nvidia x server settings"
8. I started "nvidia x server settings", it didn't work because I wasn't using the NVIDIA driver and had to run nvidia-xconfig as root and restart the xserver
9. I opened a terminal and started the app and restarted the xserver
10. Now I could use "nvidia x server settings" application, so I changed my resolution and applied the changes.
11. It immediately switched to the correct resolution, but told me to reboot.
12. I rebooted, but after the reboot xserver didn't want to start anymore.

I copied the original xorg.conf file and now it works as before (without the nvidia driver).

The initial xorg.conf looks like this:
> Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

> After running nvidia-xconfig it look like this:
Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Please help.

---

### Post by kiepmad on 2007-07-14
which kernel are you using?
Try the whole thing again with .15.
have you tried this: [http://ubuntuforums.org/showthread.php?p=2791480](http://ubuntuforums.org/showthread.php?p=2791480)

---

### Post by 3408 on 2007-07-14
I forgot to say that I'm using version .15.
If I use .16 it doesn't work at all (as mentioned in the thread you provided me).

I have tried what was mentioned in the thread, but it gave the same result.

I've been looking in the logs as well. It states:
> (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***

I looked in the README, and have also read about it in multiple forums.
Unfortunately, I don't understand what to do. It seems I'm too newbie.

---

### Post by avik on 2007-07-14
I've had issues with the .run package from NVIDIA.  Try getting rid of it and using the nvidia-glx-new package:

```
sudo apt-get install nvidia-glx-new
```

I think I could use the .run package before by running the installer (though not actually installing) each time I booted up.

---

### Post by 3408 on 2007-07-14
I've tried
> sudo apt-get install nvidia-glx-new
but it didn't help.

Is it possible that due to my many attempts , I have made a mess of my system? If so, how can I clean it up?

---

### Post by kansei on 2007-07-14
> **3408 said:**
> I forgot to say that I'm using version .15.
If I use .16 it doesn't work at all (as mentioned in the thread you provided me).

I have tried what was mentioned in the thread, but it gave the same result.

I've been looking in the logs as well. It states:


I looked in the README, and have also read about it in multiple forums.
Unfortunately, I don't understand what to do. It seems I'm too newbie.

Exactly the same issue I was having after some updates (including a new kernel) that I install this morning.

I was running the NVIDIA driver from nvidia direct (the .run package) for a day or two, working great. I tried using the 'old school' nvidia-glx-new package (it's pretty outdated at this point) and it wouldn't work either.

I'm back to using 'nv' (with some wonderful 16-bit colour depth) for now. The system still works fine of course, just doesn't look pretty.

---

