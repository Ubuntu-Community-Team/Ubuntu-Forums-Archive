---
title: "Can't obtain gigabit speed with Nvidia MCP79."
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by bogoliubov on 2011-07-27
Hello. I just bought a new router with gigabit ethernet.

However, my HTPC running Ubuntu 10.04 (32 bit) with a Zotac ION mainboard can't obtain gigabit speed. I have tested the cables by connecting my laptop and it gets gigabit speed. I also have a desktop computer that obtains gigabit speed in my network, this one with another Nvidia chipset and Linux Mint 11.

I have tried to boot the HTPC with Linux Mint 11 LiveCD, but it fails to get gigabit as well.
I have also tried 
```
sudo ethtool -s eth0 speed 1000
```
but it does not succeed in chaingin the speed.

Is there anything I can do to get gigabit speed? I have all my files on the HTPC, so network speed is important!

Here's some info that might be useful:

```
christian@htpc:~$ dmesg | grep eth
[    1.243230] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.244597] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    1.244615] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.312069] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:27:67:f5
[    1.312081] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[   31.256328] eth0: link down.
[   31.277864] eth0: link down.
[   32.635746] eth0: link down.
[   33.305541] eth0: no IPv6 routers present
[   48.190070] eth0: link up.
```





```
christian@htpc:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:27:67:f5
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.103 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:fae7c000-fae7cfff ioport:d080(size=8) memory:fae7e400-fae7e4ff memory:fae7e000-fae7e00f
```



```
christian@htpc:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 3
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```


```
christian@htpc:~$ sudo lspci -v
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
        Subsystem: ZOTAC International (MCO) Ltd. Device a108
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fae7c000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d080 [size=8]
        Memory at fae7e400 (32-bit, non-prefetchable) [size=256]
        Memory at fae7e000 (32-bit, non-prefetchable) [size=16]
        Capabilities: [44] Power Management version 2
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth

```

---

### Post by bogoliubov on 2011-07-28
Perhaps I should have posted this under the "Hardware" section...?

---

### Post by Perfect Storm on 2011-07-28
Moved to Other OS/Distro Talk.

---

### Post by bogoliubov on 2011-07-29
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

Why was it moved? I have problems with a computer running Ubuntu 10.04. I compared its behaviour to that of computers with RHEL and Linux Mint. But the question is about Ubuntu.

---

### Post by Perfect Storm on 2011-07-29
> **bogoliubov said:**
> Why was it moved? I have problems with a computer running Ubuntu 10.04. I compared its behaviour to that of computers with RHEL and Linux Mint. But the question is about Ubuntu.

ok, I'll move it back.

---

### Post by bogoliubov on 2011-08-03
bump...

---

