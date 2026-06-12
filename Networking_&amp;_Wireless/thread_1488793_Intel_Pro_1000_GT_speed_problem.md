---
title: "Intel Pro 1000 GT speed problem"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by Toube on 2010-05-20
Hi,

I went out to store and purchased an Intel Pro 1000 GT nic because I couldn't get my integrated nic to a 1 Gb speed. Though I have the same problem with this nic, it will not work when I set it from ethtool to a 1000 Mb speed with autoneg off. It only works when I use the autoneg on or set to full duplex 100. When I try to set it to full duplex 1000 speed it either gives an error or then it accepts it but I loose the whole network connection. I updated with intels latest driver but no still same problem.

I'm using ubuntu 10.04 LTS, please help me get this up to 1000 speed.

Regards,

-Toby

---

### Post by Toube on 2010-05-20
Here,s the out put from: lshw -C network

  *-network               
       description: Ethernet interface
       product: 82541PI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth1
       version: 05
       serial: 00:1b:21:5d:cf:4f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=192.168.100.5 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:fbee0000-fbefffff memory:fbec0000-fbedffff ioport:ec00(size=64) memory:7d000000-7d01ffff(prefetchable)

---

### Post by Toube on 2010-05-20
Darn.. my bad I was using a cat 5e cable instead of cat6 cable. This fixed my problem.

---

