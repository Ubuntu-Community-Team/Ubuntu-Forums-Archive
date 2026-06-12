---
title: "Broadcom Corporation BCM43XX problem has been solved!"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by mrefan on 2009-11-01
First you have to ensure that what your wi-fi card model is by using this command: 

mohsen@mohsen-ubuntu9:~$ lspci -nn | grep Net

If your net adaptor is from BroadCom BCM43XX family ; and still not working; then use this command :

mohsen@mohsen-ubuntu9:~$ sudo apt-get install bcmwl-kernel-source
( you have to be connected to the net via other NICs like your cable )

now ; you have to restart your laptop ... then you can connect to your local wireless lan :) 
try it :D

---

### Post by Torgas Prim on 2009-11-01
I get this message:
Couldn't find package bcmwl-kernel-source

The package got broken installing fresh copy of 8.04 and
after reconfiguring my package manager it will not enable the wireless now.

Any suggestions?

---

### Post by mrefan on 2009-11-01
download bcmwl-kernel-source package from here and then retry...


[http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

---

### Post by Torgas Prim on 2009-11-01
Thank you I will try that

---

### Post by reylafo on 2009-11-01
Solved same problem by removing restricted modules-backport with synaptic.
Re-installing with Hardware Drivers app and everything was loaded as supposed, modules and drivers.
The backport version of the modules may be causing the problems.
Hope this helps.

---

### Post by cheyingtan on 2009-11-10
mrefan,

I tried to install the bcmwl-kernel-source from the link u gave.

But it said Error:Wrong architecture ‘amd 64'

I google it, they said this is due to the file is built for 64 bits only not for 32 bits.
Is there any bcmwl-kernel-source that built for amd 32?

Actually I am running on AMD64 machine but I install ubuntu 32bits. Do i need to reformat it again and change it 64bits?

Any advice? Please.

Thanks.

---

### Post by mikeharris7 on 2010-05-15
cheyingtan - it sounds like you installed the 32 bit version of Ubuntu and are trying to install a 64 bit driver, which won't work. Try the 32 bit version of the driver.

---

### Post by mikeharris7 on 2010-05-15
> **mrefan said:**
> download bcmwl-kernel-source package from here and then retry...


[http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/admin/bcmwl-kernel-source)

I tried this but I still get nothing. Any ideas?

---

### Post by DJ Crossfire on 2011-03-16
I'm new to ubuntu and i also cant get wireless to work.

The light on my keyboard that is supposed to show wireless is on is not lighting up. i pressed it like a hundred times and it still didnt work. i tried the command u said but Ubuntu says Ipsci command cannot be found (or something like that).

BTW, im using a HP 210-1014. And Im using dual-boot. so right now im on Win 7.

HELP! please!

---

### Post by walt.smith1960 on 2011-03-16
> **DJ Crossfire said:**
> I'm new to ubuntu and i also cant get wireless to work.

The light on my keyboard that is supposed to show wireless is on is not lighting up. i pressed it like a hundred times and it still didnt work. i tried the command u said but Ubuntu says Ipsci command cannot be found (or something like that).

BTW, im using a HP 210-1014. And Im using dual-boot. so right now im on Win 7.

HELP! please!

Open a terminal:  applications-accessories-terminal and type "lspci". Post the output, especially the line that says "ethernet controller" or something like that.  If you were using a USB adapter you'd type "lsusb". This will tell everyone what chipset HP is using in your machine.  For instance, here's the relevant part of mine-not wireless.
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

Your wireless sounds like it's built into your machine so it'd be PCI.  For viewers' general fund of knowledge Here's the output of my lsusb:
```
Bus 002 Device 003: ID 0846:9030 NetGear, Inc.
```

Put that device I.D. into google and you can find out chipset etc.

---

### Post by bkratz on 2011-03-16
> **walt.smith1960 said:**
> Open a terminal:  applications-accessories-terminal and type "lspci". Post the output, especially the line that says "ethernet controller" or something like that.  If you were using a USB adapter you'd type "lsusb". This will tell everyone what chipset HP is using in your machine.  For instance, here's the relevant part of mine-not wireless.
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```Your wireless sounds like it's built into your machine so it'd be PCI.  For viewers' general fund of knowledge Here's the output of my lsusb:
```
Bus 002 Device 003: ID 0846:9030 NetGear, Inc.
```Put that device I.D. into google and you can find out chipset etc.



@walt.smith1960

Actually the wireless device will probably say network controller or have 802.11 in the description--the one label ethernet controller is the hardwired device.

---

### Post by walt.smith1960 on 2011-03-16
> **bkratz said:**
> @walt.smith1960

Actually the wireless device will probably say network controller or have 802.11 in the description--the one label ethernet controller is the hardwired device.

True.  The machine I was posting from didn't use the network controller phrase for whatever reason. Most do.

---

### Post by Sef on 2011-03-16
Locked. Necromancing.

---

