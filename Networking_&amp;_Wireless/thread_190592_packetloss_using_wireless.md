---
title: "packetloss using wireless"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by SL0MO on 2006-06-06
I followed the HOWTO for my broadcom 4318.
Got it working now (after setting my router to B only ), but my connection is very slow, most of the time I only get timeout when trying to get on the web.
Wired connection works ok, same wireless nic works great in winXP on same pc.

```

bert@desktop:~$ ping 192.168.123.254
PING 192.168.123.254 (192.168.123.254) 56(84) bytes of data.
64 bytes from 192.168.123.254: icmp_seq=1 ttl=127 time=33.9 ms
64 bytes from 192.168.123.254: icmp_seq=2 ttl=127 time=10.1 ms
64 bytes from 192.168.123.254: icmp_seq=2 ttl=127 time=11.2 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=3 ttl=127 time=16.2 ms
64 bytes from 192.168.123.254: icmp_seq=3 ttl=127 time=16.8 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=3 ttl=127 time=17.8 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=4 ttl=127 time=31.2 ms
64 bytes from 192.168.123.254: icmp_seq=4 ttl=127 time=32.3 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=4 ttl=127 time=33.8 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=6 ttl=127 time=16.6 ms
64 bytes from 192.168.123.254: icmp_seq=6 ttl=127 time=17.5 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=7 ttl=127 time=14.0 ms
64 bytes from 192.168.123.254: icmp_seq=7 ttl=127 time=15.1 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=8 ttl=127 time=352 ms
64 bytes from 192.168.123.254: icmp_seq=8 ttl=127 time=353 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=8 ttl=127 time=355 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=8 ttl=127 time=357 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=11 ttl=127 time=57.4 ms
64 bytes from 192.168.123.254: icmp_seq=11 ttl=127 time=58.1 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=11 ttl=127 time=59.2 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=12 ttl=127 time=12.1 ms
64 bytes from 192.168.123.254: icmp_seq=12 ttl=127 time=13.0 ms (DUP!)
64 bytes from 192.168.123.254: icmp_seq=13 ttl=127 time=28.0 ms
64 bytes from 192.168.123.254: icmp_seq=13 ttl=127 time=29.3 ms (DUP!)

--- 192.168.123.254 ping statistics ---
13 packets transmitted, 10 received, +14 duplicates, 23% packet loss, time 12006ms
rtt min/avg/max/mdev = 10.189/80.980/357.529/123.222 ms

```

192.168.123.254 is the ip of my router.
That's not really what it should be.. Any ideas?

nic : Belkin pci  (Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02))
driver : wl_apsta.o  (from HOWTO)
Router : USR8054

---

### Post by jawrat on 2006-06-07
I just noticed the same thing on my dell 5150/broadcom 4306 card.  i moved closer to the access point and voila, problem solved.  damn signal reception on this built in card is teh suck.  anyone know how to boost the receptivity of the broadcom chipsets?  i've got a netgear 802.11b card that gets WAY better reception....:???:

---

### Post by LunarTech on 2006-06-08
I'm also experiencing a lot of packet loss (although using an Atheros PCI card). I'm dual-booting into XP where it works fine.

The signal strength is sitting at about 70% which should be fine. The problem can be quite variable, with the connection working well for short periods then going bad.

When I ping the router I get something like 40% packet loss.

Does anyone have any suggestions for diagnosing this? Any help would be greatly appreciated. Cheers :)

---

### Post by mvaranda on 2006-06-24
I have same problem with my daughters (two) toshibas M50-MX2 with Atheros AR5005G.
Both work fine running XP (dual boot) but looses UDPs under Ubuntu (Both machines hangs for a while during ping requests as described). My wife's Compac R4000 with Ubuntu running the experimental driver for Broadcom works perfectly. Same 100% OK rate for my Thinkpad T42p with Intel ipw2200.

It is clear that the driver that comes with Ubuntu/Debian (MADWiFi I guess) has a problem for Atheros.



There is a post from a quite while ago describing the same:
[http://www.linuxquestions.org/questions/showthread.php?t=402673](http://www.linuxquestions.org/questions/showthread.php?t=402673)

---

### Post by SL0MO on 2006-09-04
Sorry for bringing up this old thread.
Just wanted to let you know that I fixed my problem by using the drivers
from [this]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318") thread.

---

