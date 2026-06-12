---
title: "Rx errors with large number of connections"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by alecm3 on 2011-04-10
I have a server with 2.6.32-30-server 10.04.2 LTS, that has two BroadCom 5709C Ethernet Controllers.

When the network load is medium, everything works fine. When the load becomes higher, I get hundreds of RX errors. 
Under a high network load (large number of connections, high new connection rate), I get

# ifconfig eth0
eth0 Link encap:Ethernet HWaddr e4:1f:13:69:a9:6c 
 inet addr:72.172.224.18 Bcast:72.172.224.127 Mask:255.255.255.128
 inet6 addr: fe80::e61f:13ff:fe69:a96c/64 Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets:2099602338 errors:**1131715** dropped:**1131715** overruns:0 frame:**1131715**
 TX packets:2113886295 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000 
 RX bytes:136611725547 (136.6 GB) TX bytes:240926946746 (240.9 GB)
 Interrupt:28 Memory:92000000-92012800

After this, the network connection crashes, and WAN becomes disconnected.
The bandwidth when this happens is moderate, about 100Mbps. There are about 30000 connections to the server at any time. When I try to reproduce and crash the network with iperf, I can do 20 connections with 750Mbps total throughput, and it does not crash the network. 

There is nothing in /var/log/messages or in the BMC controller hardware logs. I replaced the cable and plugged it into a different switch port: the problem is still 100% reproducible.

The port setting match that of on the switch:
# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: g
        Link detected: yes

Has anyone experienced this?

---

