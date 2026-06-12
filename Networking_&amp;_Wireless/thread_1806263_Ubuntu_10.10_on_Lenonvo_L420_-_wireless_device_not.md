---
title: "Ubuntu 10.10 on Lenonvo L420 - wireless device not detected"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by yatendragoel on 2011-07-17
I have purchase one Lenovo L420. It has Windows 7 installed. I have installed Ubuntu 10.10 also (dual boot).

The wireless is not working in Ubuntu but working in Windows 7.

I think that the wireless device is not detected in Ubuntu.

I searched on internet also but didn't find any solution.

---

### Post by Bucky Ball on 2011-07-17
Welcome. Have you plugged in a cable and gotten any available updates? Check System>Administration>Additional Hardware (or Hardware Drivers depending on release).

Open a terminal (Applications>Accessories>Terminal) and paste this in:

```
 sudo lshw -C network
```

Post the output back here. ;)

---

### Post by yatendragoel on 2011-07-17
> **Bucky Ball said:**
> Welcome. Have you plugged in a cable and gotten any available updates? Check System>Administration>Additional Hardware (or Hardware Drivers depending on release).

Open a terminal (Applications>Accessories>Terminal) and paste this in:

```
 sudo lshw -C network
```Post the output back here. ;)

I got the following output:

PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: 6000 Series Gen2
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: e8:9a:8f:33:03:dc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:3000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff

---

### Post by Bucky Ball on 2011-07-17
System>Administration>Additional Hardware (or Hardware Drivers depending on release)?

Which release are you using? It appears this is not working 'out of the box' in earlier kernels. See second post here:

[http://ubuntuforums.org/archive/index.php/t-1735416.html](http://ubuntuforums.org/archive/index.php/t-1735416.html)

In a terminal, could you paste:

```
uname -r
```

If an earlier kernel it is doable by the looks, but it will require a bit of tweaking in the terminal. ;)

---

### Post by yatendragoel on 2011-07-17
> **Bucky Ball said:**
> System>Administration>Additional Hardware (or Hardware Drivers depending on release)?

Which release are you using? It appears this is not working 'out of the box' in earlier kernels. See second post here:

[http://ubuntuforums.org/archive/index.php/t-1735416.html](http://ubuntuforums.org/archive/index.php/t-1735416.html)

In a terminal, could you paste:

```
uname -r
```If an earlier kernel it is doable by the looks, but it will require a bit of tweaking in the terminal. ;)

I don't have "Addition Hardware" and "Hardware Drivers.." under System>Administration.

I have "Additional Drivers" and when I clicked on it, it searched for a while and displayed a message "No proprietary drivers in use on this system"

Are you asking for the version of Ubuntu? I am using Ubuntu 10.10

---

### Post by Bucky Ball on 2011-07-17
```
uname -r 
```

... will give us the kernel version ...

---

### Post by yatendragoel on 2011-07-17
> **Bucky Ball said:**
> ```
uname -r 
```... will give us the kernel version ...

It's 2.6.35-30-generic

---

### Post by Bucky Ball on 2011-07-17
Thanks. That is an older kernel which doesn't support this card 'out of the box.' To get it working in that kernel, try this (the second option below is probably easier, though):

Download  [THIS]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2") file. (from post #27 [HERE]("http://ubuntuforums.org/showthread.php?t=1739047&page=3")).

Then open a terminal, get into the directory where you have downloaded the file and add these commands one by one:

```
tar xjvf  compat-wireless-2011-03-31.tar.bz2
cd  compat-wireless-2011-03-31
sudo make
sudo make install
shutdown -r now
```From post #28 in the above link. Let me know if you need a hand.
[B]
*** TRY THIS FIRST[/B]: This is apparently fixed in the 2.6.36-xx kernels so the other possibility is to upgrade the kernel. I would perhaps try this first. In a terminal:

```
sudo add-apt-repository ppa:kernel-ppa/ppa
```... then open Synaptic Package Manager and the image and headers will be there. Look for these three files:

linux-headers-2.6.36-1
linux-headers-2.6.36-1-generic
linux-image-2.6.36-1-generic

Install, reboot, choose the .36 kernel from your menu list and hopefully your wireless will be recognised and you can log on.

Info from [HERE]("http://ubuntuforums.org/archive/index.php/t-1631900.html"). ;)

---

### Post by yatendragoel on 2011-07-17
> **Bucky Ball said:**
> Thanks. That is an older kernel which doesn't support this card 'out of the box.' To get it working in that kernel, try this (the second option below is probably easier, though):

Download  [THIS]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2") file. (from post #27 [HERE]("http://ubuntuforums.org/showthread.php?t=1739047&page=3")).

Then open a terminal, get into the directory where you have downloaded the file and add these commands one by one:

```
tar xjvf  compat-wireless-2011-03-31.tar.bz2
cd  compat-wireless-2011-03-31
sudo make
sudo make install
shutdown -r now
```From post #28 in the above link. Let me know if you need a hand.
[B]
*** TRY THIS FIRST[/B]: This is apparently fixed in the 2.6.36-xx kernels so the other possibility is to upgrade the kernel. I would perhaps try this first. In a terminal:

```
sudo add-apt-repository ppa:kernel-ppa/ppa
```... then open Synaptic Package Manager and the image and headers will be there. Look for these three files:

linux-headers-2.6.36-1
linux-headers-2.6.36-1-generic
linux-image-2.6.36-1-generic

Install, reboot, choose the .36 kernel from your menu list and hopefully your wireless will be recognised and you can log on.

Info from [HERE]("http://ubuntuforums.org/archive/index.php/t-1631900.html"). ;)

It worked :)

Thanks a lot... cheers

---

### Post by Bucky Ball on 2011-07-17
Excellent news and you're welcome. Enjoy, please mark thread as 'Solved' from 'Thread Tools,' and post a new thread with any future issues. ;)

FYI: Have a look at the output of 'sudo lshw -C network' now and you will see the Network Controller is now enabled and you will also be able to see what driver has been loaded in the new kernel (if you did it that way).

---

