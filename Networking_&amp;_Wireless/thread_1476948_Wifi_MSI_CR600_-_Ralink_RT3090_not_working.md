---
title: "Wifi MSI CR600 - Ralink RT3090 not working"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by ~stephan on 2010-05-08
Hello,

I just acquired a new MSI CR600 for my kids and decided to install Ubuntu 10.04 LTS.  Everything works great except WIFI and the latest version is amazing!

From what I can tell the MSI CR 600 uses a Ralink RT3090 WIFI chipset.  I apologize if there is a solution already posted but I have not been able to find something which seem related to this WIFI set up with 10.04 LTS.

**I installed the rutil package, but receive the following error when trying to run it:**

[B]Critical Error
Can't find any wireless network interface[/B]

Is there a package available for this driver?  

Any help is greatly appreciated.

morgan@morgan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:24:21:f6:03:8a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.108 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:23 memory:fae7d000-fae7dfff ioport:c080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network UNCLAIMED
       description: Network controller
     **  product: RT3090 Wireless 802.11n 1T/1R PCIe**
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff

---

### Post by chili555 on 2010-05-08
May we see the following in a terminal:```
dmesg | grep -i rt2
```If the output is what I think it is, we may find a solution here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

---

### Post by zebraneo on 2010-11-06
Anyone  that is having problems with Rt3090 driver try this link [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")
e=navclient-ff&shva=1#inbox/12c240d2b500bbfa

it worked for me and i was trying one and off for over a year

---

