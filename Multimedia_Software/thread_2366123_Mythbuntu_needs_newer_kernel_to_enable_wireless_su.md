---
title: "Mythbuntu needs newer kernel to enable wireless support for NUC6CAYH"
date: 2017-07-14
forum: Multimedia Software
---

### Post by BigGeoff on 2017-07-14
Hi all
The recent demise of my aged Shuttle-K45 prompted the purchase of a NUC6CAYH and HDHomerun Connect, but when I tried to install my Mythbuntu 16.04.1 dvd the wireless  is not recognised.

> 02:00.0 Network controller: **Intel Corporation Device 24fb (rev 10**)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
geoff@mythbox:~$ uname -a
Linux mythbox **4.4.0-83-generic #106-Ubuntu** SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


After rooting around I understand that:-

a) Mythbuntu support has ceased (boohoo but massive thanks to the developers for their efforts - very much appreciated)
and
b) After an hour+ of installing updates last night and more trawling through forums, that this newer wireless device is not supported until (I think)  kernel 4.8.

I have never had to 'manually' install a kernel before so I have a couple of questions:-

As the update manager has only updated the kernel to 4.4.0 is there going to be a problem going to 4.8 (surely there's a reason for stopping at 4.4)?

Can someone please possibly walk me through the process so I can get on with arguing with MythTV about connecting to the Homerun, folder ownership and db passwords :-D

Sorry to sound like such a wimp but this is taking me out of my comfort zone (been spoilt with 10 years of Linux and never having a WiFi problem before)

---

### Post by deadflowr on 2017-07-14
You can upgrade to the newer 4.8 kernel smoothly by installing the linux-generic-hwe-16.04 package.
However please note that this places you in the hardware stack enablement group and as such the kernel will be upgraded to a newer version every 6 to 9 months until July/August of 2018 when it will then freeze at whatever version Ubuntu 18.04 uses.

Currently if use install the package it would upgrade to the 4.8 kernel series which is the version used in Ubuntu 16.10, then soon it would upgrade you to the version used in Ubuntu 17.04 (4.10-XXXXX-something)
then in 6 to 9 months after that it would update to whatever is used for Ubuntu 17.10 and then one last time 6 or 9 months later for whatever version is used in Ubuntu 18.04.
Then it will run the last version for the remaining 3 years of support for Ubuntu 16.04.

Maybe a better explanation here:
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack")

Sorry for my ramblings...

---

### Post by BigGeoff on 2017-07-14
Thanks for the quick reply deadflowr, would that be a simple **sudo apt-get install linux-generic-hwe-16.04**?

---

### Post by deadflowr on 2017-07-14
> **BigGeoff said:**
> Thanks for the quick reply deadflowr, would that be a simple **sudo apt-get install linux-generic-hwe-16.04**?

yep.
for the new kernel.

If on system is just a server then that would be all you need to do.
If the system is a desktop then you might want to also install the upgraded xserver packages too.
```
sudo apt-get install linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 
```
 Well explained here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by BigGeoff on 2017-07-15
Sorry deadflowr had to sleep. Updated this morning - it's worked a treat and has sorted the WiFi without any problems. On to arguing with MythTV :-D

Thank you for the help - oh and your original explanation was just fine not rambling at all.

---

