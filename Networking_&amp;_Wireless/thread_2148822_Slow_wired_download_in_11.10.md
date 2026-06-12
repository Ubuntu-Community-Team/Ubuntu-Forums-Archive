---
title: "Slow wired download in 11.10"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by ericOO on 2013-05-26
I am experiencing a rather slow download rate compared to what my ISP has promised me(~50Mbit/s). A speedtest gives:

Download : 5.96 Mbit/s
Upload : 27.10 Mbit/s

Some information that might be useful:

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:ac:93:c8  
          inet addr:213.113.115.213  Bcast:213.113.127.255  Mask:255.255.240.0
          inet6 addr: fe80::ca0a:a9ff:feac:93c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1823561 errors:107158 dropped:0 overruns:0 frame:107158
          TX packets:1321496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1551697513 (1.5 GB)  TX bytes:141275623 (141.2 MB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27436 (27.4 KB)  TX bytes:27436 (27.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:8a:4b:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo ethtool eth0
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes

ipv6 is not enabled. Thanks in advance for any help.

---

