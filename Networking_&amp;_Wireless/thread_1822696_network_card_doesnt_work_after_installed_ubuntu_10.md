---
title: "network card doesnt work after installed ubuntu 10.04"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by xmagixx on 2011-08-10
Hello guys and girls
here's the thing : My Onbod netcard wont get that it has a cable in it
i mean it wont work at all. and after i installed it now wont work in windows either :(

here's some info

ubuntu 10.04
Desktop 
Wired
 
```

uname -r
2.6.32-33-generic

```

```

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 90:e6:ba:bc:9c:51
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:36 ioport:d800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8ff8000-f8ffbfff(prefetchable) memory:fbdf0000-fbdfffff(prefetchable)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: bnep0
       serial: 00:15:83:19:16:c2
       capabilities: ethernet physical
       configuration: broadcast=yes ip=172.20.10.4 multicast=yes

```

```

sudo ethtool eth0
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
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: no

```
```

lspci -vv
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 83a3
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 36
	Region 0: I/O ports at d800 [size=256]
	Region 2: Memory at f8fff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f8ff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at fbdf0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8168

```
```

dmesg | grep eth0
[    1.043203] eth0: RTL8168d/8111d at 0xf80ac000, 90:e6:ba:bc:9c:51, XID 083000c0 IRQ 36
[   12.522128] r8169: eth0: link down
[   12.522205] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by lkjoel on 2011-08-10
> ...
[   12.522128] r8169: eth0: link down
[   12.522205] ADDRCONF(NETDEV_UP): eth0: link is not ready

Bad news...

Could you give me the output of these Terminal commands?
```
sudo /etc/init.d/networking restart
iwconfig
sudo ifconfig
uname -a
sudo nm-tool
sudo rfkill list all

```

---

### Post by dineshs on 2011-08-11
The lshw -C network output says 
> product: RTL8111/8168B PCI Express Gigabit Ethernet controller
driver=r8169
link=no

Thease links may help 
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) (ref :[http://ubuntuforums.org/showpost.php?p=10402720&postcount=2](http://ubuntuforums.org/showpost.php?p=10402720&postcount=2))
[http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-8111-8168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-8111-8168-issue-615047/#post3029998)
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)
here is a bug report 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)
> and after i installed it now wont work in windows eitherWill it be a hardware problem?

---

