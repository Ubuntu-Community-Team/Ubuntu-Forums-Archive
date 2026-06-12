---
title: "Wifi not turned on at Ubuntu 8.10 startup - please help"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by brodymcd on 2009-05-22
To all:

I had 8.10 working well - the upgrade to 9.04 KILLED my wireless... don't know why. Don't have time to figure THAT one out now, so went BACK to 8.10, but NOW wireless doesn't come on at boot. I have to go to restricted drivers, turn the Broadcom driver ON then OFF to get my wifi working.

I'm running a Dell Inspiron 1526 with Ubuntu 8.10 - can someone help me so my wifi is enabled on startup rather than my tedious workaround?

Thanks,

Brody

---

### Post by t0mppa on 2009-05-23
Next time you do that, run 'lshw -C network' from the terminal before and after applying your workaround and post the results here. Sounds more like your interface is getting the wrong drivers assigned to it during the boot up rather than being powered off.

---

### Post by brodymcd on 2009-05-26
before workaround

brodymcd@brodymcd-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network UNCLAIMED     

       description: Network controller

       product: BCM4312 802.11b/g

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:0b:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: latency=0

  *-network

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 7

       bus info: pci@0000:03:07.0

       logical name: eth0

       version: 10

       serial: 00:1d:09:4d:7a:8e

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

  *-network DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: pan0

       serial: 26:e4:fc:2c:d4:7b

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

brodymcd@brodymcd-laptop:~$ 








after workaround

brodymcd@brodymcd-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:10:6f:9b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.27.12 ip=192.168.1.7 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:09:4d:7a:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:06:9c:62:c0:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
brodymcd@brodymcd-laptop:~$

---

### Post by t0mppa on 2009-05-26
Ok, looks like there are actually no drivers associated with your wireless interface after booting.

That should be easy to fix. Open up a terminal and run the following command: ```
echo wl | sudo tee -a /etc/modules
```
What it will do, is add the wl module (that gets associated after your workaround) to the /etc/modules file, which is a list of modules that get autoloaded during boot time.

---

### Post by brodymcd on 2009-05-28
that worked - THANKS  SO MUCH!

---

