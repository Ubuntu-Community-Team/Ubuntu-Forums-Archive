---
title: "Almost There, Please Help!..."
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by rainbowagent7 on 2011-03-21
Hi all. I've gotten so far as to set up my new router and connect all of  the other computers on my network, however the download rate for my  machine is hovering around 5 kbps (or some ridiculously low number like  that). I just did a fresh install of Lucid and everything else is  running very smoothly. I have been awake for three days working on this  and am so close I can taste it. I could finish this myself, but I would  like someone who is well skilled in networking to check what I have and  possibly put an end to this dilemma for me because I just want sleep!  Anyway, here is my current router settings, ifconfig, and route -n.
So to summarize I just need to determine what is holding up my download  rate. I'm sure it's something simple, but ultimately I'm still slightly  noobish and don't Know for sure:-k. Thanks in advance to anyone who can help:-] Also, sorry for re-posting, my first post was misleading and made me sound like an idiot, plus I couldn't figure out how to change the title!


Router Stats: 
     
     ```
Linksys/ Cisco E3000
Connection Type: DHCP
IP: 75.107.12.171
Subnet: 255.255.255.0
Gateway: 75.107.12.1
DNS 1: 75.104.96.61
DNS 2: ---------------
DNS 3: ---------------
MTU: 1500
Firmware is up to date. 
```ifconfig:
    ```
william@RAINBOWDATASTORAGE:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 70:71:bc:2e:96:e7  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe2e:96e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11434084 (11.4 MB)  TX bytes:1457824 (1.4 MB)
          Interrupt:27 Base address:0x6000 

```route -n:
     ```
william@RAINBOWDATASTORAGE:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```[/CODE]Oh, I'm not sure if it makes any difference but I access Internet via satellite.

---

### Post by garvinrick4 on 2011-03-21
5 kbps with a cisco e3000 you are just screwing around with us are you not.

---

### Post by rainbowagent7 on 2011-03-21
sorry for the time warp. And no I'm not screwing with you, somethings awry! Anywho, I'm in it for the long haul, got any suggestions?

---

