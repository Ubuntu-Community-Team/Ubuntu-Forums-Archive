---
title: "WPA/WEP problems PLEASE HELP"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by _Smiler_ on 2008-12-13
[LIST=1]
[/LIST]

Can anyone please help? I want to add security to my wireless connection, but whenever I try to add a wep key either by logging into the router or through Network Configuration, it disconnects and refuses to reconnect unless I remove the security. In fact, even before I had tried anything with security settings, I was having insane problems getting it to connect anyway. It seems to be random trial and error getting it to connect. It will work if I connect it by cable to the lan port on the router, and will usually stay connected when I remove the cable. If I try to restart the computer, unplug the router (basically disconnect in whatever way) it's a nightmare trying to connect again. I'm using Ubuntu 8.10, router is Edimax br-6504n,I don't know how to find out which wifi card I use. Someone suggested that it may not support encryption, but I can rule that out as I've used encrypted connections on this laptop before. I know I haven't supplied enough information, so I'll follow any instructions on getting more info. I only know the basics to Ubuntu, so apologies for the patience that may be required :)

Thanks to anyone to tries to help me!

Paula

Here's the ifconfig I got while connected:

eth0      Link encap:Ethernet  HWaddr 00:23:54:17:89:2d  
          inet6 addr: fe80::223:54ff:fe17:892d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369373 (369.3 KB)  TX bytes:93758 (93.7 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14088 (14.0 KB)  TX bytes:14088 (14.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:21:33:39  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe21:3339/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:580366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:572380172 (572.3 MB)  TX bytes:71523552 (71.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-43-21-33-39-33-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by _Smiler_ on 2008-12-14
Some more concrete info:

_uname -a:_ gives me:

Linux Liar 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux

[U]
sudo ethtool eth0:[/U]
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
	Link detected: no

[U]
sudo mii-diag:[/U]
eth0: no link (I'm connected on the wireless now-for how long I don't know, it seems to disconnect at random)

_sudo lshw -C network:_
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:23:54:17:89:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full latency=0 link=no module=sis190 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:21:33:39
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.101 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:e2:87:6f:45:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

_lspci | grep Ethernet:_
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

Can someone please suggest something?! My only other option is to return with my tail between my legs to windows, and I *really* can't afford to be doing that. Also, should the wifi light on the router be flashing orange? It's never been another colour, and when I reset it, it stops flashing, then starts again. I hope this is okay, as it cost me 100euro and I can't return it...

Thanks again

---

