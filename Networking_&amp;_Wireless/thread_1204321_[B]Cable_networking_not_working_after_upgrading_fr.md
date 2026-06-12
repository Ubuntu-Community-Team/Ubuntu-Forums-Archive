---
title: "[B]Cable networking not working after upgrading from 8.10  to 9.[/B]"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by SilverBridge on 2009-07-04
sorry[/B] if i sound a bit dumb , but after upgrading from ubuntu 8.10 to ubuntu 9 my cable network did not work , whenever i log in into ubuntu , it tells me connection established but no internet working , i also lost the wireless internet , and the driver is not identified by the machine , and also the 3d desktop effect , but i am keen now to fix the cable network , so i manage to find out fixes for the other issues using the ubuntu instead of switching between it and vista each 5 minutes , 
 i am using Acer Extensa , Dual boot with Vista 
these are the info i managed to get , i am a bit dumb with Ubuntu 


Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes



Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0f:06.0 



modjoo@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:c4:7a:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.97 firmware=5787m-v3.23 ip=10.0.0.6 latency=0 module=tg3 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:97:33:8b:dd:a5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes








so any help over there ?******[B][B]**[/B][/B]

---

### Post by wojox on 2009-07-04
Open Synaptic and search for Broadcom.
See if there's a driver.

---

### Post by SilverBridge on 2009-07-04
and how would i do that ?

---

### Post by cariboo on 2009-07-04
You have a driver istalled for your nic. What is the output of:

```
ifconfig
```

If you say your are connected, I suspect it is a dns issue. Two things you can try to troubleshoot the problem. Open a terminal and type:

```
ping 74.125.53.99
```

if you get a response type:

```
ping www.google.com
```

If you don't get a response when you ping by name, you have a dns issue.

---

### Post by SilverBridge on 2009-07-04
well, before i post this thread , i was getting connected to eth0 , now after trying to log into ubuntu again to check the connection , it is telling me i am not connected , and the ipconfig plus the ping are not working to , i managed to print screen this .... so any suggestions ?

---

### Post by Iowan on 2009-07-04
Try **ifconfig** instead of *ipconfig* (the Windows version). Second, open the pulldown and check for eth0 instead of lo (loopback device). Then, on to **cariboo907**'s suggestions.

---

