---
title: "linksys router prolem"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by ohibohr on 2012-05-04
Hi,
I've a Linksys WAG160N router at home and ubuntu 10.10. The wifi connection has been working since yesterday, when I was not more be able to connect. The ethernet connection works and it also works the wifi connection at school. It seems to be a problem between my pc and my home's routers. I use dhcp instead of a static IP address. Can anyone help me? thanks!

---

### Post by Veloteuton63 on 2012-05-04
> **ohibohr said:**
> Hi,
I've a Linksys WAG160N router at home and ubuntu 10.10. The wifi connection has been working since yesterday, when I was not more be able to connect. The ethernet connection works and it also works the wifi connection at school. It seems to be a problem between my pc and my home's routers. I use dhcp instead of a static IP address. Can anyone help me? thanks!

Post some more info, by posting the results of the following commands:

ifconfig

have a look and see whether your router assigned an ip address.

---

### Post by ohibohr on 2012-05-04
the result of ifconfig is

ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:7e:ac:85  
          indirizzo inet:192.168.1.103  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::92e6:baff:fe7e:ac85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:1008487 (1.0 MB)  Byte TX:220476 (220.4 KB)
          Interrupt:28 Indirizzo base:0xc000 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:13574 (13.5 KB)  Byte TX:13574 (13.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:75:83:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21338 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:21957799 (21.9 MB)  Byte TX:4349048 (4.3 MB)
          Interrupt:17 Memoria:f8098000-f8098100 

I think my router assigns the default IP address 192.168.1.100 or .101,102... and so on if you connect more computers to it

---

