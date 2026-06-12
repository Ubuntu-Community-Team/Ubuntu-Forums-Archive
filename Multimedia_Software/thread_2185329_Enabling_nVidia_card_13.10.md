---
title: "Enabling nVidia card 13.10"
date: 2013-11-02
forum: Multimedia Software
---

### Post by Stephen_Gibson on 2013-11-02
Hi,

I have an Asus N550L Laptop with an Intel chip and a GT745M. I am currently trying to get this card to work but nothing seems to be working.

I have installed bumblebee and configured it and get this error when trying to run optirun:

```
[39840.534457] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:4:0:0.  Please


[39840.534530] [ERROR]Aborting because fallback start is disabled.

```

I have tried googling this and came up dry, one post suggested I ensure that the PCI address is correct, I done this and it was 04:0:0 has stated above. This was some weeks ago so can't remember what else I have done, besides complete reinstall of drivers and everything.

I really want to get this working, I am moving away from Windows entirely and plan on removing it from my dual boot, only Windows apps I use is EVE, some Minecraft and Terraria, I don't play or run anything else and Ubuntu has everything I need for my Java development.

---

### Post by protoss96 on 2013-11-02
Are you trying to enable graphics card?

If so, can you post output of this command? Thanks.
```
lspci | grep VGA
```

---

### Post by Bucky Ball on 2013-11-02
*Thread moved to **Multimedia & Video**.*

---

### Post by Stephen_Gibson on 2013-11-02
```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

```

is the outcome of the above code

---

### Post by Yellow Pasque on 2013-11-02
Make sure you have a recent nvidia driver (319.xx or later) and also see: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting)

---

### Post by Stephen_Gibson on 2013-11-03
> **Temüjin said:**
> Make sure you have a recent nvidia driver (319.xx or later) and also see: [https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting](https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting)

Well that went horribly :D

I tried to install the drivers from the nvidia website, obviously that was just stupid since now I have 2 drivers (i think) installed.

I have lost the unity launcher and the top panel, as well as all my configurations (theme, compiz etc etc)

So yeah, best approach would be?

So far I have removed that driver I install using:

```
sudo nvidia-uninstall
```

Now what? lol

---

### Post by Yellow Pasque on 2013-11-03
> **Stephen_Gibson said:**
> I tried to install the drivers from the nvidia website
Not what I had in mind...
I wanted you to add ppa:ubuntu-x-swat/x-updates to your sources and let bumblebee install the nvidia-319 driver. This used to be documented in the bumblebee wiki, but I guess someone took it out now that Ubuntu 12.04.x and 13.10 have the nvidia 319 driver in the repo. Sigh...

> Now what?
Well, first step is to get the intel GPU working again, so drop to terminal (Ctrl+Alt+F1) and:
```
sudo apt-get purge nvidia* bumblebee bumblebee-nvidia virtualgl
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now reboot and make sure Unity is working properly (i.e. intel driver functions). If so, then have another crack at bumblebee, using the nvidia-319 driver this time:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia virtualgl
```

---

### Post by Stephen_Gibson on 2013-11-03
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package virtualgl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'virtualgl' has no installation candidate



```

This is the outcome of:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install bumblebee bumblebee-nvidia virtualgl[/FONT][/COLOR]
```

---

### Post by Stephen_Gibson on 2013-11-03
Omg i'm an idiot, i'll edit the thread title. I forgot I moved to 13.10 couple days ago...fail.

So yeah, this problem is with 13.10, I managed to get my Unity back but not with the stuff you posted.

I purged the nvidia drivers, rebooted and then Unity was still broke but it turned out the unity plugins had all disabled in CCSM, so that fixed that.

However, I still can't use my nVidia card so lets start fresh again lol!

Sorry :( I am very bad at this hehe

Also to note, on 13.04 I was using my Intel card just fine, on 13.10 it feels slow and sluggish. For instance I used Desktop Cube and animations with wobbly windows just fine, now it seems to run about 10-15 fps, especially when rotating the cube.

---

### Post by Yellow Pasque on 2013-11-03
Pastebin the /var/log/Xorg.0.log

---

### Post by Stephen_Gibson on 2013-11-03
> **Temüjin said:**
> Pastebin the /var/log/Xorg.0.log

[http://pastebin.com/GXTf14r1](http://pastebin.com/GXTf14r1)

I am also constantly getting "Internal Errors" and Program Errors and the keyboard keeps changing back to US! lol

---

### Post by Yellow Pasque on 2013-11-03
The log looks okay for the Intel graphics. Not really sure what to tell you in regards to the nvidia graphics...
Check dmesg for mo more specific errors, as bumblebee troubleshooting FAQ suggests.

---

### Post by Stephen_Gibson on 2013-11-03
> **Temüjin said:**
> The log looks okay for the Intel graphics. Not really sure what to tell you in regards to the nvidia graphics...
Check dmesg for mo more specific errors, as bumblebee troubleshooting FAQ suggests.

OK, i'll have a look but in the meantime, thanks and bump :D.

---

