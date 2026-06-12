---
title: "Upgraded Ubuntu 11.04 and my wireless won't work. Don't want to go back to Windows."
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by jthompson99 on 2011-04-30
I already tried the following:
 
Synaptic Package Managers > Search Firmware-b43-lpphy-installer > click mark > click install
 
sudo lshw -c network
sudo lspci -vvnn | grep 14e4
 
Synaptic Package Managers > search Broadcom > Mark the 3 unmarked packages
 
System Admin > Hardware > Additional Drivers > STA
 
 
None of this worked.
 
I need some help getting this worked, I've been off Windows and On Ubuntu for about 6 months now and I don't want to go back.
 
Thanks.

---

### Post by chili555 on 2011-04-30
> sudo lshw -C networkThat's an upper case C. So what was the result?

---

### Post by jthompson99 on 2011-05-01
> **chili555 said:**
> That's an upper case C. So what was the result?
 
Ok, so I did it again with an uppercase "C" and this is the result.
This is really, really annoying, I've been using Ubuntu for 6 months now and I "upgrade" to the latest version and now I can't use my computer, this is pathetic. I can't believe they released this "upgrade".
 
*-network UNCLAIMED   
  description: Network controller
  product: BCM4311 802.11b/g WLAN
       
  vendor: Broadcom Corporation
  physical id: 0
  bus info: [EMAIL="pci@0000:06:00.0"]pci@0000:06:00.0[/EMAIL]
  version: 01
  width: 32 bits
  clock: 33MHz
  capabilities: pm msi pciexpress bus_master cap_list
  configuration: latency=0
       
  resources: memory:60400000-60403fff
  
*-network
       description: Ethernet interface
  product: RTL-8139/8139C/8139C+
  vendor: Realtek Semiconductor Co., Ltd.
  physical id: 8
  bus info: [EMAIL="pci@0000:08:08.0"]pci@0000:08:08.0[/EMAIL]
  logical name: eth0
       version: 10
       
  serial: 00:16:d4:9e:7d:ef
  size: 10Mbit/s
  capacity: 100Mbit/s
  width: 32 bits
  clock: 33MHz
  capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 
  duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
  resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff

---

### Post by northd_tech on 2011-05-01
> **jthompson99 said:**
> 
sudo lshw -c network
sudo lspci -vvnn | grep 14e4
 
Synaptic Package Managers > search Broadcom > Mark the **3 unmarked** packages
 
System Admin > Hardware > Additional Drivers > STA
 
Your Broadcom 4311 is one that is specifically recommended with the STA driver:

> These packages contain Broadcom's IEEE 802.11a/b/g/n hybrid Linux® device driver for use with Broadcom's** BCM4311-**, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware. There are different tars for 32-bit and 64-bit x86 CPU architectures. Make sure that you download the appropriate tar because the hybrid binary file must be of the appropriate architecture type. The hybrid binary file is agnostic to the specific version of the Linux kernel because it is designed to perform all interactions with the operating system through operating-system-specific files and an operating system abstraction layer file. All Linux operating-system-specific code is provided in source form, making it possible to retarget to different kernel versions and fix operating system related issues.
 NOTE: You must read the LICENSE.TXT file in the lib directory before using this software.
 [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

So which 3 Broadcom packages do you currently have installed under the Synaptic Package Manager?

My working STA wireless connection with a "4328" Broadcom lists these only under Synaptic Package Manager:

> bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source
b43-fwcutter
bcmwl-modaliases
It might be helpful to post the results of these terminal commands:

```
lsmod

cat /etc/modprobe.d/blacklist.conf
```

EDIT:  It also might be worth watching this [likely related] Broadcom 4313 "STA" thread:

[B]Ubuntu 11.04 - Broadcom STA Wireless Driver Install fail - Broadcom BCM4313
**[http://ubuntuforums.org/showthread.php?t=1742091](http://ubuntuforums.org/showthread.php?t=1742091)**
[/B]

---

### Post by ndefontenay on 2011-05-01
I don't know if you considered it or if you can't, but I've had no wireless as well.

I've backed up my data and did a clean install. Problem fixed.

---

### Post by collisionystm on 2011-05-01
> **jthompson99 said:**
> I already tried the following:
 
Synaptic Package Managers > Search Firmware-b43-lpphy-installer > click mark > click install
 
sudo lshw -c network
sudo lspci -vvnn | grep 14e4
 
Synaptic Package Managers > search Broadcom > Mark the 3 unmarked packages
 
System Admin > Hardware > Additional Drivers > STA
 
 
None of this worked.
 
I need some help getting this worked, I've been off Windows and On Ubuntu for about 6 months now and I don't want to go back.
 
Thanks.

Here you go buddy. Follow these directions and the run the driver program that comes with ubuntu. It worked for me.

[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

---

### Post by jthompson99 on 2011-05-02
> **collisionystm said:**
> Here you go buddy. Follow these directions and the run the driver program that comes with ubuntu. It worked for me.
 
[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)
 
 
Thanks for the help man, but I tried it and it didn't work.
 
This is unreal to me that they release an update that basically cripples your computer.

---

### Post by jthompson99 on 2011-05-04
I guess I am going to have to reinstall Ubuntu because there is no fix for the upgrade disabling your wireless adapter. That is really, really sad. Maybe this is part of the reason why Windows is still dominating.

---

