---
title: "Setting up WAP through bridged laptop wlan"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by Nevon on 2009-01-03
(Very confusing topic, I admit)

I've got a small home wlan setup with wpa2 encryption. Currently there are three laptops on the wlan and an xbox on a wired connection through the same router, all with DHCP. It works fairly well after some fiddling around (getting Vista to be able to access the shared printer was a bitch), however, I would like to set up a second wlan with WEP or no encryption at all. This is because I want to be able to connect my DS and my brother's Wii, since they both lack support for WPA2. Of course I could just change the encryption on the wlan, but I'm currently staying at my mom's house, and she'd go berserk if I happened to mess up her network ("mess up" meaning any kind of change). 

I've never really been into networks, so I don't know much about it. But I know that I should be able to bridge wlan0 (my laptop wireless network device) - I just don't know how. 

In short, I want to set up a second wireless network by bridging my existing wireless network connection through my laptop. 

Is this possible at all? Also, is there any way that I could still access the network on my laptop while it acts as a switch? 

I also have another question. Can I also bridge my wireless connection to connect another desktop through the standard ethernet port? Would a standard ethernet cable work for that?

If you need any more information, just ask.

Thank you!

Here's the output of ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:90:f5:80:65:03  
          inet6 addr: fe80::290:f5ff:fe80:6503/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:3447600338 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3828 (3.8 KB)  TX bytes:3888 (3.8 KB)
          Interrupt:218 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120640 (120.6 KB)  TX bytes:120640 (120.6 KB)

pan0      Link encap:Ethernet  HWaddr 6a:bc:ac:34:88:0a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:47:3b:75  
          inet addr:192.168.55.99  Bcast:192.168.55.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe47:3b75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31084643 (31.0 MB)  TX bytes:14183401 (14.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-47-3B-75-62-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Nevon on 2009-01-07
Bump.

---

