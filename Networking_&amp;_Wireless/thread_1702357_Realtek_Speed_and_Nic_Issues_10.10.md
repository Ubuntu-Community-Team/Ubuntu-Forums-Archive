---
title: "Realtek Speed and Nic Issues 10.10"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by caleberx on 2011-03-07
I have been having some issues with my NIC, it is stuck at 10Mb/s even though it supports Gig.  I have checked all my wiring and that is not the issue. I did follow this [http://ubuntuforums.org/showthread.php?t=1480328&highlight=nic+speed+issue]("http://ubuntuforums.org/showthread.php?t=1480328&highlight=nic+speed+issue") to see if it would fix it, and it has not.  Below is my nic info. If you need more do not hesitate to ask.


```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```


```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 6c:62:6d:0a:5c:ce
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=129.21.145.197 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:c800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fe8e0000-fe8fffff
rahlxcb@ritkit:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 6c:62:6d:0a:5c:ce
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=129.21.145.197 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:c800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:fe8e0000-fe8fffff
```

---

### Post by bkratz on 2011-03-07
Here is a thread that may help

[http://ubuntuforums.org/archive/index.php/t-1480328.html](http://ubuntuforums.org/archive/index.php/t-1480328.html)

---

### Post by caleberx on 2011-03-07
> **bkratz said:**
> Here is a thread that may help

[http://ubuntuforums.org/archive/index.php/t-1480328.html](http://ubuntuforums.org/archive/index.php/t-1480328.html)

That is the link I linked in mine. I already tried that one.

---

