---
title: "DDNS-DHCP Hostname Registration"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by CraigWatson on 2010-02-19
I have a slight problem with my Karmic x64 installation - it doesn't register itself with a DNS lookup on my CentOS DHCP server. My Windows 7 installation on the same PC works fine (I have a dual-boot setup).



I can ping galileo.dominion.local (my desktop PC) from any machine on my network while booted into Windows, but not when booted into Linux.
 Also, for some reason my Linux install gets assigned a different IP (.250) than my Windows install (.249).

I'd assume this is at least part of the problem, but I'm not sure how to fix it.


Here is some debug output - if more is needed, let me know :)

**-------------- [From Desktop PC] ----------------**
```
[craig@galileo Desktop]$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:24:8c:48:4b:07  
          inet addr:10.0.100.250  Bcast:10.0.100.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe48:4b07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1600 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1483 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1359453 (1.3 MB)  TX bytes:267128 (267.1 KB)
          Interrupt:2

[craig@galileo Desktop]$ ping galileo
PING galileo (127.0.1.1) 56(84) bytes of data.
64 bytes from galileo (127.0.1.1): icmp_seq=1 ttl=64 time=0.027 ms
64 bytes from galileo (127.0.1.1): icmp_seq=2 ttl=64 time=0.014 ms
64 bytes from galileo (127.0.1.1): icmp_seq=3 ttl=64 time=0.014 ms
64 bytes from galileo (127.0.1.1): icmp_seq=4 ttl=64 time=0.020 ms

[craig@galileo Desktop]$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	galileo

[craig@galileo Desktop]$ hostname
galileo

[craig@galileo Desktop]$ hostname -a
[Blank Line]

[craig@galileo Desktop]$ nslookup galileo
Server:		10.0.100.3
Address:	10.0.100.3#53

Name:	galileo.dominion.local
Address: 10.0.100.249
```


-------------- [From Backup Server] ----------------

```
[backup@backup ~]$ ping galileo
PING galileo.dominion.local (10.0.100.249) 56(84) bytes of data.

--- galileo.dominion.local ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4009ms
```

Any help is appreciated :)

---

