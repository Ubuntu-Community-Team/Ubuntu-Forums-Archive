---
title: "Nvidia problems"
date: 2010-01-15
forum: Multimedia Software
---

### Post by Raijin8 on 2010-01-15
I had a couple of problems with graphics recently. I'm not sure if they're related, but both of them need to be solved in any case.

First, I recently installed Karmic on this computer. After everything was up and running, I tried installing the recommended nvidia driver (version 185) through jockey-gtk, but it got stuck and froze up (I later found that envy-ng had the same problem). After trying to get that to work for a while, I gave up and tried downloading a driver from nvidia.com and installing manually. It wasn't my preferred way to do it, but it worked.

Next:
A few days later, ubuntu did an update that included a kernel update. Because I installed the nvidia driver manually, of course it didn't work when I booted with the new kernel. So I reinstalled the driver for the new kernel and got it working. However, now when I run 3d games like sauerbraten and quake live, the fps is at around 2-3. Even after I went back to the old kernel and reinstalled the nvidia driver, I still had the same problem.

In summary:
1. Why can't jockey-gtk or envy-ng install drivers? **[solved]**
2. What is making 3d games, etc. run so slow?

If it makes any difference, my card is an Nvidia GeForce 6200.
btw, the driver I installed manually was actually version 190

---

### Post by Raijin8 on 2010-01-24
This hasn't magically fixed itself yet... any help would be appreciated.

---

### Post by Raijin8 on 2010-01-24
Ok I got something to work. :D
By randomly messing around, I was able to figure out that jockey-gtk *will* install the driver, but only if the karmic live CD is in the drive. So I assume it's downloading from the CD rather from the repository. I don't know why it would do that, or why it wouldn't at least give some message that it needed the CD, but that's ok as long as it works now (if anyone knows why it did that, please explain).
So problem #1 is (sort of) solved.

However, now that jockey-gtk has installed nvidia driver version 173, 3D graphics are still slow (about 15 fps). Better, but still unusable.
I'm gonna see if I can install the ubuntu recommended driver and if that will fix things (if it does, I will humbly admit that I have absolutely know idea why).

---

### Post by llawwehttam on 2010-01-24
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

works for me.
If you manually install the nvidia driver on a kernel update you have to compile the module to the new kernel. Script will do it automatically. To fix your current problem simply re-run the nvidia installer.

I have had nothing bit problems from the recommended driver.

---

### Post by Raijin8 on 2010-01-24
Thanks for the reply.
I knew that you had to had to recompile manually installed drivers after kernel updates, but I didn't want to bother with the script, so I recompiled manually.
In any case, that's not the problem I'm having.

Also, I installed the nvidia driver version 185 using jockey-gtk and 3D graphics are actually worse.
**Edit: it was at around 5 fps this time.**

---

### Post by llawwehttam on 2010-01-24
I am using the nvidia driver version 190.53 and I have had no problems. Have you tried manually downloading a new one directly from nvidia's website?

---

### Post by Raijin8 on 2010-01-25
That's a great idea. I'll do that.
Ok. Now I'm back where I started with less than one frame per second in games with 3D graphics.

Seriously though,
I guess it doesn't really matter which driver I use. If newer is better, fine. I'll use version 190.53. Unfortunately the problem doesn't seem to have anything to do with the driver version *or* the kernel version. If that were the case, this would be easy. However, I've tried every combination of kernel and driver versions available, and everything always works fine except the 3D graphics.

All I know is that before I had an update last week (that happened to include a kernel update) and now 3D graphics run at anywhere between <1 fps and ~15 fps depending on the driver version.

(Hopefully that simplifies things)

---

### Post by Linuxforall on 2010-01-25
Turn off compiz when playing games and see if it gets any better. I am on latest 195xx drivers and never faced any issues, that too with a cheap no name 8400GS.

---

### Post by VertexPusher on 2010-01-25
> **Raijin8 said:**
> I was able to figure out that jockey-gtk *will* install the driver, but only if the karmic live CD is in the drive. So I assume it's downloading from the CD rather from the repository. I don't know why it would do that, or why it wouldn't at least give some message that it needed the CD, but that's ok as long as it works now (if anyone knows why it did that, please explain).
It seems that the install CD is still listed as a package source in your /etc/apt/sources.list file. When installing packages, APT will prefer local media if available.

However, I have no idea why there was no prompt to insert the CD.

---

### Post by rsrohitrs on 2010-01-25
Hi,
I am new to Ubuntu but I have everything working on it perfectly but there is one problem.
I am using Dell Inspi 1720 with Nvidia 8600M GT 256MB card and the resolution I am getting is 1920x1200.
I cannot change it to lower using the Nvidia settings or anything.
I opened my xorg.conf file and it has the following output:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig: version 1.0 (buildmeister@builder63) Fri Aug 14 17:54:58 PDT 2009


Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection


Everything looks very small in this resolution so I want to lower it. 
Please help me.


Thank you.

---

### Post by Raijin8 on 2010-01-25
@Linuxforall
K I tried that. No difference. Anyway I had it on before with no problems. Thanks for the idea though.

@VertexPusher
Thank you! It bugs me beyond reason to make something work without knowing how.

@rsrohitrs
What were you using to change your resolution? If you use Ubuntu's default program it doesn't give you all the options supported by your driver (I don't know why, but I would like to.) If you use nvidia's settings program it doesn't always have permission to change the xorg.conf file. I have to do this:
```
gksudo nvidia-settings
```
Then the settings window should come up as normal only with administrator privileges.

---

### Post by Raijin8 on 2010-02-01
Ok I have more information. I don't know if this is related or if it helps at all, but one of the games I've been using as a benchmark throughout this process (sauerbraten) gives this warning whenever it starts up:

WARNING: no vertex_buffer_object extension! (geometry heavy maps will be SLOW)
Rendering using the OpenGL fixed-function path.

I've done some searching for causes and solutions for this, but every other case I've seen comes with a bunch of other warnings and errors and is caused by a missing package. This doesn't match my situation at all.

If this actually doesn't have anything to do with my problem, please tell me so I can avoid a wild goose chase. This warning *did* show up after all my problems began though.
Also note that though all of the 3D games I have tried have the same problem, this is the only one that gives any such warning.

---

### Post by saidh4ndra on 2010-02-01
for notebook ASUS UL80VT cnfigure XORG.conf can't be useful please helpe ASUS UL80VT have two graphical intel and nvidia for installed nvidia in ubuntu not working that isue ubuntu dosent suport with dual grapical like ASUS UL80 VT

---

### Post by Raijin8 on 2010-02-10
There has been another kernel update. The script I just installed that was supposed to automatically recompile the module didn't work, even when I ran it in terminal (it froze up). So I uninstalled and reinstalled the driver manually as before.
When I tried playing 3D games I had the same 5 or less fps as before.

I'm really starting to think this doesn't have anything to do with the kernel now, but I don't know what could cause this problem or why it would happen after a kernel update.

---

