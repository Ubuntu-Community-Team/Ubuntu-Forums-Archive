---
title: "Broadcom BCM5709 not working"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by knaj on 2012-03-27
Hi. I have a problem that I hope someone can help me with... I bought two new Broadcom Netxtreme BCM5709 Dual port 1Gb pcie-cards for my server. Everything seems to be recognized but I can't get the card to transmit anything...  
Here's the output from ethtool
```
Settings for eth5:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Link detected: no
```
And lshw
```
*-network:0             
       description: Ethernet interface
       product: NetXtreme II BCM5709 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth5
       version: 20
       serial: 00:10:18:8c:de:1c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.1.6 firmware=bc 5.2.2 ip=192.168.1.67 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:f8000000-f9ffffff
```
And dmesg
```
dmesg|grep eth
[    1.719782] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.720196] forcedeth 0000:00:11.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    1.720205] forcedeth 0000:00:11.0: setting latency timer to 64
[    1.864479] bnx2 0000:06:00.0: eth0: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f8000000, IRQ 16, node addr 00:10:18:8c:de:1c
[    1.879477] bnx2 0000:06:00.1: eth1: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f6000000, IRQ 16, node addr 00:10:18:8c:de:1e
[    2.245178] forcedeth 0000:00:11.0: ifname eth2, PHY OUI 0x5043 @ 1, addr 00:0e:a6:f1:cc:2a
[    2.245185] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    2.249235] forcedeth 0000:00:12.0: PCI INT A -> Link[AMC1] -> GSI 21 (level, low) -> IRQ 21
[    2.249243] forcedeth 0000:00:12.0: setting latency timer to 64
[    2.773180] forcedeth 0000:00:12.0: ifname eth3, PHY OUI 0x5043 @ 1, addr 00:0e:a6:f6:00:09
[    2.773187] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[   17.293981] udevd[369]: renamed network interface eth2 to rename4
[   17.385765] udevd[370]: renamed network interface eth3 to rename5
[   17.520223] udevd[368]: renamed network interface eth0 to eth5
[   17.547192] udevd[369]: renamed network interface rename4 to eth0
[   17.562736] udevd[371]: renamed network interface eth1 to eth4
[   17.601359] udevd[370]: renamed network interface rename5 to eth1
[   17.765090] bnx2 0000:06:00.0: eth5: using MSIX
[   17.765357] ADDRCONF(NETDEV_UP): eth5: link is not ready
[   17.825101] bnx2 0000:06:00.1: eth4: using MSIX
[   17.825355] ADDRCONF(NETDEV_UP): eth4: link is not ready

```
And ifconfig
```
eth5      Link encap:Ethernet  HWaddr 00:10:18:8c:de:1c  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3749 errors:0 dropped:3239 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254049 (254.0 KB)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f8000000-f8012800 

```
I've tried everything I can think of.. 
I've switched ethernet cable to others that work
Compiled new drivers from broadcom's webpage
I've switched pcie port
I've tried another switch (altough same model and brand, Netgear GS108)
Reinstalling doesn't work, because installer complains about no network connection
Turning autonegotiation off and switch speed to 100

Both cards gets the same result - link is not ready, and it receives packages but it's not transmitting any.. Am I missing something? It doesn't seem likely that both cards have the same fault. Any help or tips are appreciated.. Oh, and I'm running Ubuntu Server 11.10..

---

### Post by knaj on 2012-03-28
I've solved it.. For everyone else who's having the same problem, for some strange reason the card only works on my top pcie port. My board has 3 16x pcie and I tried the bottom two several times.. No go.. Then I tried moving my graphics card to the bottom one and put the NIC at the top, and lo and behold - it worked. Odd considering that it's a SLI-board and one would assume that at least the top two pcie ports are identical..

---

