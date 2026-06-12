---
title: "On board Network Wont work"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by Bananasdoom on 2010-12-27
I have recently built a HTPC with a GA-G41m Combo and it has worked well with Ubuntu 10.04, however last week some time the on board network stopped working. I have tried different routers and different cables, but the network light wont come on. What Can I doo?

---

### Post by dineshs on 2010-12-27
Please post result of ```
sudo lshw -C network
```

---

### Post by Bananasdoom on 2010-12-27
> **dineshs said:**
> Please post result of ```
sudo lshw -C network
``` 

I have had to put a network card in so that I can connect to the Internet and I cold work on that forever but I want to know if it is a hardware error (so that i can claim warranty) and I need the PCI slot for my TV tuner :( 

```
htpc@htpc-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:fdec0000-fdefffff ioport:bf00(size=128)
  *-network
       description: Ethernet interface
       product: 3cSOHO100-TX Hurricane
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth0
       version: 30
       serial: 00:04:76:8c:a6:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.64 latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:df00(size=128) memory:fddff000-fddff07f memory:80600000-8061ffff(prefetchable)
```

---

### Post by cariboo on 2010-12-27
It looks like you have two network interfaces, is it the Atheros device that's not working? It looks like the 3Com device is set up as eth0 and working.

---

### Post by Bananasdoom on 2010-12-28
> **cariboo907 said:**
> It looks like you have two network interfaces, is it the Atheros device that's not working? It looks like the 3Com device is set up as eth0 and working.

correct I have had to add a PCI network card to get connectivity.

---

### Post by dineshs on 2010-12-28
> network UNCLAIMED I think it is a driver issue
See if [this]("http://ubuntuforums.org/showthread.php?t=1476231") can help

---

