---
title: "dell inspron n4030 wireless driver"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by hani270 on 2011-04-12
hello

i have dell inspron n4030
but i can't connect to wireless network to download other drivers and programs,
that's easy in win7

 i need the network card driver for ubuntu 10.10
where i  found it?

thanks

---

### Post by josephmills on 2011-04-12
Please go to Applications--> Accessories--> Terminal
then type in ```
lspci
```
then paste here thanks

---

### Post by hani270 on 2011-04-12
```
han@haN4030:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68e1
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
13:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
han@haN4030:~$ 



```

---

### Post by josephmills on 2011-04-12
please make sure that you are plugged into your router and if you have an external wifi button please make sure that it is on.Then go to go to System-->Addmin-->Synaptic Package Manager. Then  once the package manager has opened go to, Settings-->Repositories. Now make sure that all of the ticks are checked (see pic). After that is done close out of the software center. if you changed your repositories then a pop up will show close it. After That reload the synaptic package manger(see pic) After reloading close out of your package manager. Then open your terminal and typed in ```
sudo apt-get update
```then ```
sudo apt-get upgrade
``` then ```
sudo reboot
``` after rebooting go to your wireless manager(see pic) and right click on it make sure that wireless is enabled if ot is still greyed out tell us

---

### Post by hani270 on 2011-04-12
```
Some index files failed to download
```

how to do this update without internet !!!!!!!!

---

### Post by josephmills on 2011-04-12
> **hani270 said:**
> ```
Some index files failed to download
```

how to do this update without internet !!!!!!!!

if you read my above it says make sure that you are connected to you router via cat5 cable that is the first step

---

### Post by hani270 on 2011-04-13
I can not access the router of the network via a wire, and also i don't know where the source of network
it's a free network in the yard mediates the city
I use it in Windows 7 with very easy

sorry for bad english and very thanks for your help



Is there an alternative way?

---

### Post by bkratz on 2011-04-13
> **hani270 said:**
> I can not access the router of the network via a wire, and also i don't know where the source of network
it's a free network in the yard mediates the city
I use it in Windows 7 with very easy

sorry for bad english and very thanks for your help



Is there an alternative way?




There are instructions for installation of your driver (with no internet access) on this page.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

