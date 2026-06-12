---
title: "DELL Vostro 1000 cannot connect to internet"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by FlavoFraz on 2013-05-12
Hi,

I have a dell vostro 1000 with Ubuntu 12.04. I cannot connect to the internet wirelessly or with the Ethernet cable.
I have tried different methods found on some Ubuntu threads without any results.

Could someone guide me with a step by step approach to fixing this problem?

Thank you in advance

some info that might be useful

```

ubuntu@ubuntu:~$ sudo lshw -class network
  *-network              
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:7c:ad:a0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff


```

---

### Post by sanderj on 2013-05-12
I can't help you really, but I can give some remarks / thoughts:

Which 12.04? The old 12.04, or 12.04.2? Check with "lsb_release -a"
Your output says "link=no". Can you check the cable is connected correctly, and the light on the switch (and maybe computer) lights up? Change the cable?
Is "linux-firmware" installed? Maybe it is needed? Check with "aptitude show linux-firmware"
What happens when you run Ubuntu 13.04? A live-boot from a USB/CD should be OK.

---

