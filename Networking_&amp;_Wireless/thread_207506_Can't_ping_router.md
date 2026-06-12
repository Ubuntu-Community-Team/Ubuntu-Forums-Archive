---
title: "Can't ping router"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by scollyp on 2006-07-02
Networking is completely broken on my new Kubuntu installation.  I can't even ping my router.  The same machine works fine dual-booted to XP.

Here's output from ping, ifconfig -a, and route.  Any ideas?

```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.5 icmp_seq=2 Destination Host Unreachable
From 192.168.0.5 icmp_seq=3 Destination Host Unreachable
From 192.168.0.5 icmp_seq=4 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5000ms
, pipe 3


eth0      Link encap:Ethernet  HWaddr 00:08:A1:24:5B:AE  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:54 dropped:0 overruns:0 frame:0
          TX packets:21 errors:2 dropped:0 overruns:1 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:4253 (4.1 KiB)  TX bytes:2390 (2.3 KiB)
          Interrupt:201 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1292 (1.2 KiB)  TX bytes:1292 (1.2 KiB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


```

---

### Post by mips on 2006-07-02
What network card do you have, full details ?

Use lspci -v to get the info.


Tried disabling IPv6 ?

---

### Post by scollyp on 2006-07-03
Card details:
```

0000:02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
	Subsystem: Unknown device 4554:434e
	Flags: bus master, medium devsel, latency 64, IRQ 201
	I/O ports at e800 [size=256]
	Memory at fe1fec00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 20000000 [disabled] [size=256K]
	Capabilities: [50] Power Management version 2

```

I disabled ipv6 in the aliases file, but that doesn't seem to help either.

Thanks
Scott

---

### Post by Tamsco on 2006-07-03
What type of router? Do you have a static IP set up or are you using the router's DHCP server?

It's a long shot but I once had a router whose DHCP server didn't like linux (Gentoo to be specific) but when I set a static IP I had no problems.

---

### Post by scollyp on 2006-07-04
The router is an Actiontec GT701-WG.  

Thanks for the suggestion.  Unfortunately, the exact same problem happens with a static address, so DHCP isn't the problem.

I'm kind of at a loss on how to troubleshoot this.  Could it be some kind of driver problem?

---

### Post by scollyp on 2006-07-04
Here is the solution.  The Davicom adapter doesn't work with the tulip kernel module Ubuntu loads by default.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by scollyp on 2006-07-04
By the way, thanks for your help!  I wouldn't have been able to figure this out without the lspci command you suggested.

Posting happily from kubuntu...
Scott

---

### Post by mips on 2006-07-05
Sorry, only read this today. Had I seen/read your reply with the Davicom Tulip chipset I would have pointed you to that thread.

Also saw you have a Actiontec router which some people in the past have had problems with.

As long as it works all is great !

---

