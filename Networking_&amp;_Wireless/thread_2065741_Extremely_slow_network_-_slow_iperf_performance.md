---
title: "Extremely slow network - slow iperf performance"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by James2012 on 2012-10-02
Hi all,

This is my first post to these forums. I've been playing with Ubuntu for a while now and have used these forums to help me out with many problems, unfortunately I cant seem to fix my current problem.

I've setup a box (HP Proliant Microserver N36L) running Ubuntu Server 64bit 12.04.1 LTS to act mainly as NAS and I'm experiencing extremely slow network speeds.

I know the various file sharing protocols will be slower than raw speed but my problem seems to stem from the raw speed.

Firstly my hardware: HP N36L has onboard gigabit lan. Using cat 6 cable connected to 10/100Mb capable router, then wireless to Apple Macbook.

Right so my network interface is reduced to 100Mb(router) but surely I should still be getting better results with iperf than this:

iperf:
```
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.69 port 5001 connected with 192.168.1.64 port 56451
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  13.6 MBytes  11.4 Mbits/sec

```

In fairness this result is pretty good I'm usually hitting around 5Mbits/sec

Here is some more information I think is relevant (cant find any problems in any of it):

ethtool eth0:
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes

```

dmesg | grep eth0:
```
[    2.714157] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address 3c:4a:92:74:2c:2c
[    2.714222] tg3 0000:02:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.714271] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.714317] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   22.348755] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.196436] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.784099] tg3 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex
[   30.784105] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX
[   30.784336] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   40.880052] eth0: no IPv6 routers present

```

UPDATED - this might help aswel!

sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5723 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 3c:4a:92:74:2c:2c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5723-v3.35 ip=192.168.1.69 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:fe9f0000-fe9fffff

```

I'm sure there's something I've missed. At the moment I'm using netatalk to share with my macbook as I understand it's faster than samba but it's pretty much useless to stream videos from at these speeds.

I very much hope someone out there can help. Every other post out there seems to be someone with good iperf results and poor smb speeds. I've just got terrible iperf results!!!

---

### Post by houstonbofh on 2012-10-02
You are connecting to the MAC book and it is on WiFi, correct?  That is your bottleneck.  Since you said 10/100 router, that probably means not N, so 54gig in bast case, and WiFi is never best case.  And if it is a junk 2Wire, it could be far worse than best case...  Plug the Mac in with a cable and see if it improves.

---

### Post by Sergius14 on 2012-10-02
I think that your issues are related to the WiFi.

Do you have many other SSID in your area? Signal Quality? Specification (.G, .N), etc.

In your case I will firt test everything without WiFi, so then you can fully discard your Ubuntu NAS and focus on the WiFi side. Depending in what you find out, of course.

11mbit could perfectly at WiFi.


Be Advice: Specificacions (54mbps, 110mbps, etc.) are the maximum traffic at layer 1 (bits level), on top of that you have to add layers 2, 3, 4...and 7 (OSI model). The usuable bandwith is far far less.


At my Apt I get also about true http 11mbps due to many other SSID's in the same channels. Also my mouse is using bandwith (interference) and (depending on the wifi channel) when I do a full speed test the mouse gets locked and unresponsive.

---

### Post by James2012 on 2012-10-03
Thanks guys,

It's always the most obvious solution. Actually I feel pretty stupid, plugged the mac in via ethernet and iperf runs at about 93-97Mb as it should.

I know actual transfer speeds will be lower. I was concerned that if iperf was getting bad results I had problems somewhere on the tcp layer - anyway thats not the case!

Next stage is tuning my NFS, AFP config to get the most out of it.

Your right of course, I am using a crappy 2wire router. I'm actually testing the system for installation in my house, I'll be using a much more modern router there, so hopefully WiFi speeds will be better there. Either way my HTPC set top box will be connected via ethernet.

It's a shame though I was hoping to use a wireless range extender to avoid running cables through my house but it looks like thats a bad idea. I really didn't think WiFi was that much of a bottleneck!!

Anyone with any ideas would be greatly appreciated!!

---

