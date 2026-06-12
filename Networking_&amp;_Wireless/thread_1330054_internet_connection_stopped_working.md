---
title: "internet connection stopped working"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by blandwa on 2009-11-18
My wired internet connection in Ubuntu 9.10 stopped working.  It worked perfectly from the first time I ever booted Ubuntu, but now I don't think it's even being recognized.  I don't know what changed.  The connection works in Windows.  How do I fix this?

The output of ifconfig:

[INDENT]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62526 (62.5 KB)  TX bytes:62526 (62.5 KB)[/INDENT]


The output of ifconfig eth0 up:

[INDENT]eth0: ERROR while getting interface flags: No such device[/INDENT]


The output of ipconfig in Windows:

[INDENT]Windows IP Configuration


Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : McMaster.CA
   IPv6 Address. . . . . . . . . . . : 2002:8271:2c6f:8:f54a:bac9:4430:e5b3
   Site-local IPv6 Address . . . . . : fec0::8:f54a:bac9:4430:e5b3%1
   Temporary IPv6 Address. . . . . . : 2002:8271:2c6f:8:e8ae:d36d:5617:c3bc
   Link-local IPv6 Address . . . . . : fe80::f54a:bac9:4430:e5b3%8
   IPv4 Address. . . . . . . . . . . : 130.113.44.191
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::d964:47f2:8e52:be71%8
                                       130.113.44.5

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter Local Area Connection* 9:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:38a7:21a0:7d8e:d340
   Link-local IPv6 Address . . . . . : fe80::38a7:21a0:7d8e:d340%10
   Default Gateway . . . . . . . . . : ::

Tunnel adapter Local Area Connection* 14:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : McMaster.CA[/INDENT]

---

### Post by crucialhoax on 2009-11-18
In the terminal type: lspci -vv

Look for your ethernet card to make sure its being recognized by Ubuntu.

---

### Post by blandwa on 2009-11-18
My ethernet card seems to be there:

[INDENT]03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
	Subsystem: Dell Device 01f2 
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 64 
	Interrupt: pin A routed to IRQ 10 
	Region 0: Memory at fe5fe000 (32-bit, non-prefetchable) [size=8K] 
	Capabilities: <access denied> 
	Kernel modules: b44[/INDENT]


I was surprised to see that my wireless card also seems to appear since I have never been able to use it:

[INDENT]0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
	Subsystem: Dell Device 0007 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Interrupt: pin A routed to IRQ 17 
	Region 0: Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: b43-pci-bridge 
	Kernel modules: ssb[/INDENT]

---

### Post by lvlint67 on 2009-11-18
I feel like I have dealt with this problem on a friend's laptop... what's your /etc/network/interfaces look like?

---

### Post by blandwa on 2009-11-18
etc/network/interfaces contains only:

[INDENT]auto lo
iface lo inet loopback[/INDENT]

---

