---
title: "Since 1 week all my linux boxes can't access the internet (?!)"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by mauricep on 2010-07-12
I hope someone can help me with this bizarre Wifi problem. I have searched and searched and cannot find a solutions. Unfortunately this affects 3 computers in my household. And as the resident amateur Linux tech support/Linux advocate, I will be held responsible if I don't figure out how to fix this quick. Help, please!

After some extensive playing around, this is the situation. I have this problem on Ubuntu 9.10, Mint 9 (based on Ubuntu 10.04) and PC Linux OS 2010.:

- About a week ago the wireless network I use stopped working. There was a major power failure on our block during this period. No idea if there was a connection. Since then, I have been able to connect, but I am no longer able to access the internet. I can ping my own IP and my router, but no website (niether by IP not URL).
- When I booted my computer in Windows, it connected to the internet. My neighbours (whose network I am using) are also windows users, and are able to access the internet without problems.
- I have found exactly the same problem on my wife's laptop running Ubuntu 9.10 and on a Live CD of PC Linux OS 2010
- I am still able to log into all other wireless networks without problems.

I am perplexed. Is it possible for a wireless network to prevent internet access to linux computers? And inadvertently?

I tried disabling IPv6 (which wasn't being used anyhow), but this didn't make a difference.

I also tried manually entering an IP address and other network details into the network settings. Again, this didn't help.

My Mintwifi output is below:

-------------------------
* I. scanning WIFI PCI devices...
-- Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
==> PCI ID = 168c:002a (rev 01)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:"Nina's Network" 
Mode:Managed Frequency:2.457 GHz Access Point: 00:22:75:20:5E:EE 
Bit Rate=0 kb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=44/70 Signal level=-66 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

-------------------------
* IV. querying ifconfig...
eth0 Link encap:Ethernet HWaddr 00:24:8c:50:a7:ec 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:27 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2018 errors:0 dropped:0 overruns:0 frame:0
TX packets:2018 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:97429 (97.4 KB) TX bytes:97429 (97.4 KB)

wlan0 Link encap:Ethernet HWaddr 00:22:43:78:cf:d8 
inet addr:192.168.2.3 Bcast:192.168.2.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1
RX packets:2664 errors:0 dropped:0 overruns:0 frame:0
TX packets:3597 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:767474 (767.4 KB) TX bytes:603363 (603.3 KB)

-------------------------
* V. querying DHCP...
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:8c:50:a7:ec
Sending on LPF/eth0/00:24:8c:50:a7:ec
Listening on LPF/wlan0/00:22:43:78:cf:d8
Sending on LPF/wlan0/00:22:43:78:cf:d8
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 10.5.50.184 on wlan0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPOFFER of 192.168.2.3 from 192.168.2.1
DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.3 from 192.168.2.1
bound to 192.168.2.3 -- renewal in 868510052 seconds.
-------------------------
* VI. querying nslookup google.com...
;; connection timed out; no servers could be reached
mauricep
Level 1

 
Posts: 6
Joined: Thu Jun 03, 2010 3:57 am

---

### Post by km0r3 on 2010-07-12
Are you running a linux box as your router? Please, tell us more about your it. (Model, OS, Specifications, etc.)

Well, as far as I can see there are no problems in establishing a connection between router (the wireless connection) and the client machine (your computer).

> * VI. querying nslookup google.com...
;; connection timed out; no servers could be reached
mauricep
Level 1

The problem seems to consist of the router not being able cannot connect to the internet. Have you configured your DNS nameservers correctly?
You say there was a mayor power failure in your block. Maybe the router made a reset of its configuration? Have you checked if all the configuration made is still intact?

If that's the case then there's no reason to debug your computers.

---

### Post by TechBeastie on 2010-07-12
Try pinging an actual external IP (91.189.94.12, for instance, which is the address of ubuntuforums.org).  If that seems to work, your router is failing to push out correct DNS information, which you can get around entirely by configuring your computers to use OpenDNS or Google DNS servers instead.

---

### Post by mauricep on 2010-07-12
Part of my problem is that I share my neighbour's network and the router is in their appartment. I will need to find a moment when they are home and free and then get back to you.

> The problem seems to consist of the router not being able
> cannot connect to the internet. Have you configured your DNS
> nameservers correctly?

How do I check if my DNS nameservers are configured correctly?

I think the problem is not with the router not connecting to the internet: When I boot my computer in Windows, I can connect to the internet without problems.

---

### Post by mauricep on 2010-07-12
> **TechBeastie said:**
> Try pinging an actual external IP (91.189.94.12, for instance, which is the address of ubuntuforums.org).  If that seems to work, your router is failing to push out correct DNS information, which you can get around entirely by configuring your computers to use OpenDNS or Google DNS servers instead.

That would have been a neat solution. Unfortunately, that ping gives me nothing:


pigaht-mint@Maurice-Laptop ~ $ ping -c 4 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.

--- 91.189.94.12 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms

---

### Post by renkinjutsu on 2010-07-12
He has stated in the OP that pinging an IP address doesn't work either.. so a faulty DNS is out of the question. He just can't connect to the internet. This case has me scratching my head too

facts:
.. He's associated to the wifi ap
.. He's assigned an IP address (via dhcp?)
.. Can see other machines on the local network.
.. No internet connectivity

just making the information clearer so other people smarter than me can look at that list and come up with an answer

---

### Post by renkinjutsu on 2010-07-14
After connecting to the AP, and doing your DHCP thing, show us the output of ```
route
```

I don't think it's correctly configuring your gateway
From what i see from your DHCP output, i think the IP of the router is 192.168.2.1 ... .. right?

so open up a terminal and do this
```
sudo route add default gw 192.168.2.1
```

---

