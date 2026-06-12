---
title: "Speeding up my internet"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Dobbie03 on 2009-07-21
Hi Guys,

I have recently returned from Windows Xp back to Ubuntu.  So far everything is going well except the speed of my internet has dropped.  Any ideas on how to speed it up? or maybe ideal router settings (like the ipv4 settings).  I am using a D-Link DS-502T connected via an ethernet cable.  I dont know what info to post so please just tell me what to do :)

Any info would help.

---

### Post by martinbaselier on 2009-07-21
Could you open a terminal and post the output of **sudo ethtool eth0**?

It would also help to know a bit more about the ethernet card

you can use lspci to get the right info. 

Example: 
```

**lspci | grep eth -i**
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

**sudo lspci -s 06:06.0 -v**
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0070
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at c8200000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Kernel driver in use: tg3
	Kernel modules: tg3

```

You can copy/paste from/to the terminal by selecting text with the mouse and using the right mouse button menu.

---

### Post by Dobbie03 on 2009-07-22
ok this is from my terminal:

Settings for eth0:
	Supported ports: [ TP MII ]
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
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

As far as the ethernet card goes:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

I hope that is enough info.

---

### Post by martinbaselier on 2009-07-22
Could you also tell the output of lspci -v -s 02:00.0

You don't need to send me a personal message. I'll try to look into the thread every now and then when I have time. But there will probably be others who will try to help too.

It would of course be most helpfull for you if someone with the same card could look into it. He/She might already have found a solution.

---

### Post by superprash2003 on 2009-07-22
could you post the results from [www.speedtest.net](www.speedtest.net)

---

### Post by Dobbie03 on 2009-07-23
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Packard Bell B.V. Device e015
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at febe0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


I tested from Auckland (New Zealand) to Brisbane

[[IMG]http://www.speedtest.net/result/523401732.png[/IMG]](http://www.speedtest.net)

The above results are extremely slow compared to before my ubuntu install.

---

### Post by superprash2003 on 2009-07-23
try selecting the nearest (recommended ) server.. that gives a more accurate result.. what speeds are you supposed to be getting?

---

### Post by Dobbie03 on 2009-07-23
[[IMG]http://www.speedtest.net/result/523420280.png[/IMG]](http://www.speedtest.net)

I generally get between 5.5 - 8.0 mbps, upload is average here in NZ, set at 128kbs.  But I still got really good speed with Windows.  Cheers.

---

### Post by superprash2003 on 2009-07-23
post output of ifconfig from the terminal , you could try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by Dobbie03 on 2009-07-24
> **superprash2003 said:**
> post output of ifconfig from the terminal , you could try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

eth0      Link encap:Ethernet  HWaddr 00:1e:90:22:8f:f2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe22:8ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9031475 (9.0 MB)  TX bytes:504366 (504.3 KB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Dobbie03 on 2009-07-24
> **jocoolguy said:**
> nice information,
also try this, clear cookies and delete all temp file..then  test your internet 
[speed]("http://www.ip-details.com/internet-speed-test/")

It sort of worked but not really:
[[IMG]http://www.speedtest.net/result/524179748.png[/IMG]](http://www.speedtest.net)

---

### Post by Dobbie03 on 2009-07-25
Anyone else?

---

### Post by Dobbie03 on 2009-08-05
I am getting desperate, anyone got any ideas?

---

### Post by irv on 2009-08-05
I am sitting in a Travelodge and I checked my speed with Speekeasy speed check and this is what I am getting. I get 12K download and 3K upload at home, but I pay for it. this reading I am getting in the motel is about standard. 
[ATTACH]123709[/ATTACH]

---

