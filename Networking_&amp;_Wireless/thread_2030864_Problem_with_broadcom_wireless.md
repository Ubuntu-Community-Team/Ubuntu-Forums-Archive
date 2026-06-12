---
title: "Problem with broadcom wireless"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by tontis on 2012-07-21
Hello,
I am quite a noob at Ubuntu but I have this problem and been trying everything I could find internet but it still remains and therefore I need some help!

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I have installed Ubuntu 12.04 and since I installed it, my wireless have stopped working. Wired internet on my ubuntu machine doesn't work either because the cable exit is broken.
Before Precise Pangolin I had solved the problem with ndiswrapper yet it doesn't seem to be working anymore.

I have tried the following:
[LIST]
[*]uninstalling ndiswrapper
[*]installing/uninstalling the STA additional driver (bcmwl-kernel-source from the ubuntu 12.04 cd) it is currently installed but not activated for some reason)
[*]installing ndiswrapper again
[*]installing the b43-fwcutter
[/LIST]

I looked through other posts but mostly it just confuses me more and seems like it should be working by now. Any help is greatly appreciated.

---

### Post by praseodym on 2012-07-21
Install the package "linux-firmware-nonfree" from here:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by kc1di on 2012-07-21
The problem is without an internet connection the Jockey tool has no way of downloading the correct proprietary driver for you card and install it. 

you can download it directly from broadcom from another machine that is connected and mannually install it your card uses the STA driver not the b43xx one. If you have the b43 firmware installed remove first. 

you can get the driver [here]("http://www.broadcom.com/support/802.11/linux_sta.php/") 

Make sure you down load and read the text file also as it tells you how to build the driver.

It is the hard way but it can be done.   

It may be easier to get the cable connector fixed though :) 

good luck.

---

### Post by tontis on 2012-07-22
thanks for the advice, i'll check it out and get back to you.

---

### Post by tontis on 2012-07-22
> **kc1di said:**
> The problem is without an internet connection the Jockey tool has no way of downloading the correct proprietary driver for you card and install it. 

you can download it directly from broadcom from another machine that is connected and mannually install it your card uses the STA driver not the b43xx one. If you have the b43 firmware installed remove first. 

you can get the driver [here]("http://www.broadcom.com/support/802.11/linux_sta.php/") 

Make sure you down load and read the text file also as it tells you how to build the driver.

It is the hard way but it can be done.   

It may be easier to get the cable connector fixed though :) 

good luck.

I downloaded and tried to build it, though it doesn't work. 

```
agne@Bixo:~/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  CC [M]  /home/agne/hybrid_wl/src/wl/sys/wl_linux.o
/home/agne/hybrid_wl/src/wl/sys/wl_linux.c:388:2: error: unknown field ‚Äòndo_set_multicast_list‚Äô specified in initializer
/home/agne/hybrid_wl/src/wl/sys/wl_linux.c:388:2: warning: initialization from incompatible pointer type [enabled by default]
/home/agne/hybrid_wl/src/wl/sys/wl_linux.c:388:2: warning: (near initialization for ‚Äòwl_netdev_ops.ndo_validate_addr‚Äô) [enabled by default]
make[2]: *** [/home/agne/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/agne/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic'
make: *** [all] Error 2

```

three packages are required for the making, according to the instructions in the readme file. It seems like I have the first two but not the last:

```
agne@Bixo:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for agne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

```
agne@Bixo:~$ sudo apt-get build-dep linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-meta' as source package instead of 'linux'
E: Unable to find a source package for linux-meta
```

Any suggestions?

praseodym: i missed your post before, i shall try it now and get back to you.

---

### Post by tontis on 2012-07-23
it would be great if someone could try and help me.
cheers.

---

### Post by bkratz on 2012-07-23
> **tontis said:**
> it would be great if someone could try and help me.
cheers.



The info given in post 2 should have taken care of you (make sure you remove all the other stuff again). Perhaps you couldn't find it in the listings ( it isn't easy!) Anyway, here is a more direct link

[http://packages.ubuntu.com/precise/linux-firmware-nonfree](http://packages.ubuntu.com/precise/linux-firmware-nonfree)

---

### Post by tontis on 2012-07-25
> **bkratz said:**
> The info given in post 2 should have taken care of you (make sure you remove all the other stuff again). Perhaps you couldn't find it in the listings ( it isn't easy!) Anyway, here is a more direct link

[http://packages.ubuntu.com/precise/linux-firmware-nonfree](http://packages.ubuntu.com/precise/linux-firmware-nonfree)

Well, I found it, installed it, it didn't do any difference. Perhaps I did something wrong. I'll try it again and get back to you. You say I should uninstall all the rest - fwcutter, bcmwl-kernel-source and ndiswrapper?

Cheers, Anton

---

### Post by bkratz on 2012-07-25
> **tontis said:**
> Well, I found it, installed it, it didn't do any difference. Perhaps I did something wrong. I'll try it again and get back to you. You say I should uninstall all the rest - fwcutter, bcmwl-kernel-source and ndiswrapper?

Cheers, Anton


Yes, remove the other stuff the link [praseodym]("http://ubuntuforums.org/member.php?u=1411497") gave you earlier will install the b43 driver which is right for your card.

---

### Post by praseodym on 2012-07-25
Remove the others via:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk bcmwl-kernel-source
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
Download this .deb:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb)

and install it with dpkg

---

