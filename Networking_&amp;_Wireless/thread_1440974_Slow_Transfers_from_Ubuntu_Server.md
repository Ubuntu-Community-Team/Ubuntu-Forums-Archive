---
title: "Slow Transfers from Ubuntu Server"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by heen2001 on 2010-03-28
I have a gig-e network and transferring files from my ubuntu server running 8.10 is very slow, when I copy files from this server to my Mac (OS x 10.6.2) its taking over 7min to copy over a 600Mb file. The same file copied from the server to my Vista machine is done in a matter of seconds. Transferring the same file from my Mac to my Vista PC also takes a matter of seconds.

However if I am running an XP VM (using Parallels) on my Mac and copying over the same file from the ubuntu server to my mac, it takes seconds like it does between the other platforms.

So in short I am having problems transferring from my Ubuntu server to my Mac at anywhere close to gigiabit speeds; in fact its barely running at 10MB/s.

I'm sharing files using a SAMBA share, for all these transfers

from the ethtool output, it seems to  say that gigabit ethernet is supported, but not advertised. Could this be the problem?

Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes:  Not reported
Advertised auto-negotiation: No


I have tried setting advertise using the hex codes, for auto negotiation and full 1000Tx, but nothing seems to be working

sudo ethtool -s eth0 advertise 0x020

I've also tried including everything in a single command, but nothing seems to work. I am at a lotal loss, any help would be much appreciated!




here is the ethtool output,

heenesh@palais:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised auto-negotiation: No
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: puag
	Wake-on: g
	Current message level: 0x00000002 (2)
	Link detected: yes


the ifconfig output

heenesh@palais:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:63:f9:6f:6d  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:350671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1255317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26646422 (26.6 MB)  TX bytes:1871413679 (1.8 GB)
          Interrupt:28 Base address:0xec00 


the lshw output

heenesh@palais:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 82
       serial: 00:40:63:f9:6f:6d
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.14 duplex=full ip=192.168.1.67 latency=0 link=yes module=via_velocity multicast=yes port=twisted pair speed=1GB/s

---

