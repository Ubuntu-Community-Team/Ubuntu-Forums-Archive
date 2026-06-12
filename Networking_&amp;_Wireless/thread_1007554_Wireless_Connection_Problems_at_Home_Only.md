---
title: "Wireless Connection Problems at Home Only"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by mdhicks1 on 2008-12-10
Thanks in advance. Yay, linux community! :D

**Problem**
Recently I installed Ubuntu 8.10 Intrepid Ibex on my laptop and on a friend's.

The wireless for both machines worked "out of the box" for a few days. But then I started having problems.

At my university, my computer connects easily, stays connected, and I experience good speeds.

At my home, however, I can connect initially and experience fast browsing, but after a period of time--as brief as under a minute or as long as half an hour--the Internet stops working. It still shows me as connected, but I can't browse, download, etc.

If I disconnect and reconnect, restart my network manager, or restart the computer, I can again browse for a short period of time before getting the same problem.

My friend's laptop, a different brand than mine, experiences this same problem.

**Solutions I've already tried**
I've hit the ubuntu forums pretty hard the last few weeks, but cannot resolve the problem.

1) I looked at the [Wifi Docs Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns") and followed the guide's ping test to see if the problem was a dns nameserver issue. As I could ping the router but could not ping an external site, I do not believe this is the problem--though I could be wrong. I went ahead and tried to find my Connection-Specific DNS suffix anyway on my windows partition, but that field was empty.

2) On the advice of another forum, I changed my network connection manager from gnome network manager to Wicd network manager, but this did not resolve my problem.

3) Another forum suggested that there could be something wrong with the router, but the router works for all of my roommates' Windows computers and for my girlfriend's ubuntu gutsy laptop using ndiswrapper for a broadcom card.

4) A forum suggested I change the beacon interval settings for my router, but I don't believe my router has these settings. :P

5) A forum suggested I change the channel my router broadcasts on, but when I did this, no computer could connect to it any longer (not the windows machines, not my girlfriend using ndiswrapper, or either of the intrepid laptops for even a second.)!

6) A forum suggested I disable ipv6 in Firefox in case that is triggering the problem and explains the variable drop-time, but after doing this and testing another browser--Opera--I experience the same problems.

7) On wondering if my router was just stupid, I took my laptop to my girlfriend's apartment, but experience the same problem--though she does have the same router.

**Hardware/Setup**
My laptop is a Gateway ML6732 dualbooting Ubuntu Intrepid and Windows Vista using an Integrated Realtek 802.11b/g Wireless Networking card.

My friend's laptop is an HP Pavilion dv6000. It's hard to track down the card type for this, becuase they have lots of model numbers, though a poster in another forum referred to this as "some crazy broadcom wireless card."

The wireless router at my home and at my girlfriend's apartment are both Belkin 4-port wireless routers.


Sorry this was so complicated and involves so much hardware! Feel free to ignore everything but my laptop and my router, if that helps. I gave all the additional information in case it would be of help in pinpointing the problem.

I didn't try ndiswrapper on these two laptops because I figured since the cards obviously work so well in other locations, it must not be a driver problem. My logic could be wrong here, though.

If you need more specific model numbers/etc., I will be happy to provide them.

---

### Post by mdhicks1 on 2008-12-13
Bump. :)

---

### Post by superprash2003 on 2008-12-13
during the time when you arent able to acces internet.. try pinging your wifi router.. also type ping google.com and post output.. also post output of ifconfig .. do all this when you have internet problem

---

### Post by mdhicks1 on 2008-12-13
Router:
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.6 icmp_seq=1 Destination Host Unreachable
From 192.168.2.6 icmp_seq=2 Destination Host Unreachable
From 192.168.2.6 icmp_seq=3 Destination Host Unreachable
From 192.168.2.6 icmp_seq=4 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3019ms
, pipe 3

google.com:
ping: unknown host google.com

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:8c:6e:ee  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7186 (7.1 KB)  TX bytes:7186 (7.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:d4:f7:6e  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fed4:f76e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:658202 (658.2 KB)  TX bytes:153376 (153.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-D4-F7-6E-37-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mdhicks1 on 2008-12-16
bump, please.:p

---

### Post by superprash2003 on 2008-12-19
open your router settings.. under DHCP settings.. what is the DHCP lease time given??try setting up static ip for wlan0 [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by mdhicks1 on 2008-12-19
The DHCP lease time is currently set to "Forever."

---

### Post by mdhicks1 on 2008-12-19
Also, I looked at the tutorial for setting up a static ip. Will doing this affect my ability to connect at school, work, and other places?

---

### Post by superprash2003 on 2008-12-21
well in a way yes.. as you would have to give a static ip differently for each network you connect.. depending on the way that network is.. like gateway ip etc ..

---

### Post by gordintoronto on 2008-12-22
It sounds like your computer is losing its DNS.  I assume when you ping your router, you use the IP address, so the DNS is not used, but when you ping an external site, you use the site's name.

To see your DNS:
```

 cat /etc/resolv.conf

```

If the result is not what you expected, the next step is to figure out why.

> **mdhicks1 said:**
> ...I can connect initially and experience fast browsing, but after a period of time--as brief as under a minute or as long as half an hour--the Internet stops working. It still shows me as connected, but I can't browse, download, etc.

If I disconnect and reconnect, restart my network manager, or restart the computer, I can again browse for a short period of time before getting the same problem.
...
1) I looked at the [Wifi Docs Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns") and followed the guide's ping test to see if the problem was a dns nameserver issue. As I could ping the router but could not ping an external site, I do not believe this is the problem--though I could be wrong. I went ahead and tried to find my Connection-Specific DNS suffix anyway on my windows partition, but that field was empty.

2) On the advice of another forum, I changed my network connection manager from gnome network manager to Wicd network manager, but this did not resolve my problem.
**Hardware/Setup**
My laptop is a Gateway ML6732 dualbooting Ubuntu Intrepid and Windows Vista using an Integrated Realtek 802.11b/g Wireless Networking card.

My friend's laptop is an HP Pavilion dv6000. It's hard to track down the card type for this, becuase they have lots of model numbers, though a poster in another forum referred to this as "some crazy broadcom wireless card."

The wireless router at my home and at my girlfriend's apartment are both Belkin 4-port wireless routers.


---

