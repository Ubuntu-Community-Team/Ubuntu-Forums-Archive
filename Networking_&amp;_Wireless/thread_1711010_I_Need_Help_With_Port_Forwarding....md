---
title: "I Need Help With Port Forwarding?..."
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by rainbowagent7 on 2011-03-20
Hi all. I've gotten so far as to set up my new router and connect all of the other computers on my network, however the download rate for my machine is hovering around 5 kbps (or some ridiculously low number like that). I just did a fresh install of Lucid and everything else is running very smoothly. I have been awake for three days working on this and am so close I can taste it. I could finish this myself, but I would like someone who is well skilled in networking to check what I have and possibly put an end to this dilemma for me because I just want sleep! Anyway, here is my current router settings, ifconfig, route -n, and iwlist.
So to summarize I just need to determine what is holding up my download rate. I'm sure it's something simple, but ultimately I'm still slightly noobish and don't Know for sure:-k. Thanks in advance to anyone who can help:-] 


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
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe2e:96e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7280686 (7.2 MB)  TX bytes:1286087 (1.2 MB)
          Interrupt:27 Base address:0x2000 
```route -n:
```
william@RAINBOWDATASTORAGE:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```iwlist:
```
william@RAINBOWDATASTORAGE:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
```Oh, I'm not sure if it makes any difference but I access Internet via satellite.

---

