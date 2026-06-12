---
title: "possible easy fix for flash works great for me."
date: 2010-12-11
forum: Multimedia Software
---

### Post by olympicsfan55 on 2010-12-11
[SIZE=4]I had tons of problems with flash with Linux mint and Ubuntu which kept me from deleting windows from my hard disk,flash on Linux has always been buggy and glitchy for me but mostly flash was just plain laggy and unusable i accidently found out how to fix my problem in Linux mint which is built from Ubuntu so it should work for Ubuntu too.Anyway what i found out is my proprietary video card drivers for the Nvidia Geforce 6150se are way better with stability and performance then the installable drivers it works perfectly with flash and all the other video formats i have tried and my computer in general is just way faster with the proprietary driver then the downloadable ones.So if you are having trouble with flash try using your proprietary driver it could just fix your problems with flash the only thing you will be missing is the desktop effects but you could gain a nice performance boost and it could fix flash and i don't know about you but  Linux to me still looks amazing even without the desktop effects.[/SIZE]

---

### Post by laithbsoul on 2010-12-11
Installing the nvidia proprietary driver shouldn't keep you from using desktop effects/compiz in fact it should enhance performance with the effects.

---

### Post by olympicsfan55 on 2010-12-11
[SIZE=4]No what i meant was i did not install any of the the recommended drivers i just kept the plain old proprietary driver installed.I was having all the problems with flash and Linux in general with the restricted drivers that you can install.[/SIZE]

---

### Post by ajgreeny on 2010-12-11
> **olympicsfan55 said:**
> [SIZE=4]No what i meant was i did not install any of the the recommended drivers i just kept the plain old proprietary driver installed.I was having all the problems with flash and Linux in general with the restricted drivers that you can install.[/SIZE]
Please use the standard font for your posts.  It is far too hard to read fonts the size of yours.

As for the driver problem you speak of, the driver you get with the installation, before you do anything to install an alternative, is the open source driver, not a proprietary driver, as you seem to think.

You are obviously getting rather muddled in your thoughts of what comes as the default, but don't worry about it; use whatever driver works best for you.  I thought I would just point this out for your information.

---

### Post by efflandt on 2010-12-11
It is difficult to tell which video drivers you are actually using.  Default drivers for nvidia are nouveau open source drivers.

Proprietary nvidia drivers are any drivers from nvidia, whether you installed them using "activate" in Hardware Drivers (or Additional Drivers in 10.10), or installed using Synaptic, or downloaded and installed from nvidia website.  The latter (downloaded directly from nvidia) are the most difficult to use because they do not update kernel modules automatically when kernels update. so they may need to be reinstalled after kernel updates.

The nvidia proprietary drivers packaged for Ubuntu (Hardware Drivers, Synaptic, or apt-get) or the default nouveau drivers update automatically.

---

### Post by olympicsfan55 on 2010-12-12
Thank you guys for pointing that out i did mean the open source drivers or whatever you call them.Not the drivers from the restricted drivers setting anyway thanks.

---

### Post by Dilutu on 2010-12-12
Yeah I also found out that the only driver working good for my old geforce 4000mx is the nv driver!

---

