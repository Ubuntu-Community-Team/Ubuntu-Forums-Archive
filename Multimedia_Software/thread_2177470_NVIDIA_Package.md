---
title: "NVIDIA Package?"
date: 2013-09-28
forum: Multimedia Software
---

### Post by chrs80 on 2013-09-28
Is there a package in the Ubuntu repositories for the NVIDIA GeForce GT 630M?

---

### Post by bcschmerker on 2013-09-28
The Ubuntu® Restricted repositories contain two matched pairs of driver and settings packages, Release 304 plus an updated version, for the nVIDIA® GeForce® 100 and later series video display adapters (packages: nvidia-304, nvidia-settings-304, nvidia-304-updates, nvidia-settings-304-updates).  Additional nVIDIA® driver and settings packages across Releases 96, 173, 310 (experimental), and 319 are available from the Ubuntu® X-Swat Team repository at Launchpad™:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudp apt-get update

```
Release 319 is probably the one needed for the GeForce® GT™ 630M (nVIDIA® GF108 or GF117 GPU, dep. on maufacture date).

---

### Post by deadflowr on 2013-09-28
nvidia-319 is available for precise and (dev branch)saucy.
Don't know about either quantal or raring.
I think raring has 310 or 313.
Clueless on what quantal has.

---

### Post by Bashing-om on 2013-09-28
chrs80;

Is not the NVIDIA GeForce GT 630M an Intel/Nvidia hybrid card ? ->Optimus
Is not the recommended procedure to try BumbleBee ?
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

[INDENT][INDENT]just pass'n by
[/INDENT][/INDENT]

---

### Post by chrs80 on 2013-10-23
Do I need to worry about overheating? I'm running Ubuntu 12.04.

---

### Post by Yellow Pasque on 2013-10-25
Well, if you install Bumblebee, it will save power (and heat) by disabling the nvidia card when not in use and using the lower power intel GPU.

---

### Post by Linuxisfast on 2013-10-25
If you are using nvidia-prime, remove it first along with the drivers with the --purge command to install bumblebee, bumblebee-nvidia, linux-headers-generic and nvidia-319-updates

---

