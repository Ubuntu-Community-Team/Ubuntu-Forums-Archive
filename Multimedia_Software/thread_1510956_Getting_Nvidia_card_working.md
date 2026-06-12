---
title: "Getting Nvidia card working"
date: 2010-06-16
forum: Multimedia Software
---

### Post by fallenshadow on 2010-06-16
I used to have Ubuntu working perfectly with the Nvidia driver until I got an update to: 

195.36.24-0ubuntu1~10.04

Which made Ubuntu stall on bootup. I did a fresh install and installed the driver. Same thing happened.

Would anyone have the older one in their cache?

(located in "/var/cache/apt/archives")

I would like if somebody could send me the packages for the older Nvidia release.

195.36.19-0ubuntu1~10.04   ... I think

Also im on 64bit so it would help if they were packages from a 64bit machine.

---

### Post by dino99 on 2010-06-16
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

add this ppa to your synaptic repo, then update

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by fallenshadow on 2010-06-16
I installed Nvidia current from this repo.

Was this what you wanted me to do? :confused:

---

### Post by fallenshadow on 2010-06-16
Installing Nvidia current from this repo had no effect.

---

### Post by fallenshadow on 2010-06-16
I downloaded and installed all the updates sent from that repo.

Do you want me to try installing the latest official driver? (the one from "Hardware Drivers")

or what should I do?

---

### Post by fallenshadow on 2010-06-16
Installed official driver... Ubuntu froze again at same point.

Beginning yet another fresh install...  :mad:  ](*,)

---

### Post by fallenshadow on 2010-06-16
Fresh install complete... struggling for ideas here.

Don't know will I ever be able to have 3D support back. :(

Please help me if you can!

---

### Post by mrowth on 2010-06-16
> **fallenshadow said:**
> I used to have Ubuntu working perfectly with the Nvidia driver until I got an update to: 

195.36.24-0ubuntu1~10.04

Which made Ubuntu stall on bootup. I did a fresh install and installed the driver. Same thing happened.

Would anyone have the older one in their cache?

(located in "/var/cache/apt/archives")

I would like if somebody could send me the packages for the older Nvidia release.

195.36.19-0ubuntu1~10.04   ... I think

Also im on 64bit so it would help if they were packages from a 64bit machine.

[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

---

### Post by fallenshadow on 2010-06-16
Thanks for the link... I downloaded and installed that version which worked before.

However I still don't have any 3D functionality. Gonna reboot a few times to see if anything changes.

---

### Post by fallenshadow on 2010-06-16
Rebooted and nothing has changed yet.

Got this message from Nvidia settings:

> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

However the Nvidia driver is installed! :rolleyes: As it is listed in "Hardware Drivers"..

---

### Post by fallenshadow on 2010-06-16
OMG!! I just realized something. The last time I had trouble with drivers not working was when my graphics card broke!

Is there anyway to check on its health? (without trying it in a different PC)

---

### Post by petellgra on 2010-06-16
I have the same trouble as well with Ubuntu studio and as I have both Ubuntu10.04 and Ubuntu Studio loaded I use Ubuntu10.04 and did'nt do the Nvidia update. I think I'm lucky I boot the computer I can choose which OS I want to use and can load the older version before the update in Grub. 
Pete

---

### Post by fallenshadow on 2010-08-29
I think the only fix for my graphics card is to upgrade to 10.10 when it comes out. Just like I had to upgrade from 8.04 to 8.10.

I would love to stay with LTS releases but they always seem to have broken graphics drivers. (Or working ones which break after an update)

---

