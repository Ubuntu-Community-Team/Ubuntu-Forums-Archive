---
title: "Wireless breaks off"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by gtorem on 2012-12-18
I am new. I tried installing ndiswrapper and it didn't work. I also tried going to Sofware Sources, Additional Drivers, but it fails to accept "using SmartLink software modem daemon from sl-modem-daemon". It says "A proprietary driver has private code that Ubuntu develpers can't review or improve. Security and other updates are dependent on the driver vendor."

I add this, in case it is useful to you:

truly1@laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:91:14:64:33
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 multicast=yes port=twisted pair
       resources: irq:41 memory:d0100000-d0103fff ioport:a000(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:be:04:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.34 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
       resources: irq:22 memory:d0207000-d0207fff


Thanks

---

