---
title: "Networking Problems After Upgrade to 8.10"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by kw1502 on 2009-01-06
I’m having networking problems since upgrading to 8.10. The problem is that I cannot ping any other computers on my LAN. I have a laptop with  wired and wireless NICs. 

After some experimentation, I found that if both NICs are enabled, I cannot ping anything. If I disconnect the Ethernet cable to the wired NIC, the wireless connection will work and if I turnoff the wireless NIC (via on/off switch on the laptop) the wired connection works. The problem appears to be Network Manager having problems when both NICs are enabled. Any help on solving this problem would be greatly appreciated.
 

I’m including the contents of /etc/network/interfaces and output of the ifconfig commands. Note, everything worked fine in 8.4 so I know my NICs are supported.

/etc/network/interfaces:
	auto lo
	iface lo inet loopback

Ifconfig:
	eth0      Link encap:Ethernet  HWaddr 00:0e:35:3c:77:3e  
		  UP BROADCAST MULTICAST  MTU:1500  Metric:1
		  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		  TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
		  collisions:0 txqueuelen:1000 
		  RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
		  Interrupt:11 Memory:cffff000-cfffffff 

	eth1      Link encap:Ethernet  HWaddr 00:0e:7b:1f:c6:13  
		  inet addr:10.57.59.213  Bcast:10.57.59.255  Mask:255.255.255.0
		  inet6 addr: fe80::20e:7bff:fe1f:c613/64 Scope:Link
		  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		  RX packets:163 errors:0 dropped:0 overruns:0 frame:0
		  TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
		  collisions:0 txqueuelen:1000 
		  RX bytes:112022 (112.0 KB)  TX bytes:37144 (37.1 KB)

	lo        Link encap:Local Loopback  
		  inet addr:127.0.0.1  Mask:255.0.0.0
		  inet6 addr: ::1/128 Scope:Host
		  UP LOOPBACK RUNNING  MTU:16436  Metric:1
		  RX packets:2 errors:0 dropped:0 overruns:0 frame:0
		  TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
		  collisions:0 txqueuelen:0 
		  RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

---

### Post by utnubuuser on 2009-01-06
Hi --  I don't have the answer for you, but did you Google this? Like "network problems after upgrade ubuntu".

I'm only mentioning it because I've seen this same issue on several posts, and though I'm not too fond of the forums search function, I usually manage to find the right posting through a google query.

---

### Post by oygle on 2009-01-06
It's bugs in Network Manager, see [http://ubuntuforums.org/showthread.php?t=1022569](http://ubuntuforums.org/showthread.php?t=1022569)

---

### Post by superprash2003 on 2009-01-07
your eth0 doesnt have an ip!!try static ip for both interfaces..

---

### Post by oygle on 2009-01-08
> **superprash2003 said:**
> your eth0 doesnt have an ip!!try static ip for both interfaces..

Don't know if you are replying to 'kw1502' or myself.  :confused:

Anyway, my eth0 does have a static, but that makes little difference for me, as I can't use eth0 at all (it has to be disabled to get the ppp0 connection going).

Oygle

---

### Post by superprash2003 on 2009-01-08
that was to kw1502 as he posted his ifconfig output

---

