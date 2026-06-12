---
title: "Bonding Wlan And 3g Modem in Ubuntu 9.10"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by Binx on 2010-02-27
Reading this other topic -> [http://www.ubuntu-es.org/?q=node/107394](http://www.ubuntu-es.org/?q=node/107394) i've tried to bond the wireless interface (wlan0) and the modem connection (ppp0), with no success, (did the ip route thing in there,and seemed to work, but looking at the traffic transmitted by each interface with ifconfig, i think only the wlan connection was used, besides, the download speed was the same as the wifi's bandwidth, so the bond wasn't working).. 

the thing is that when i try 

```
sudo ifenslave bond0 wlan0 ppp0
```

the result is:

```
Master 'bond0', Slave 'ppp0': Error: Enslave failed
```

Any Ideas Why?

Some info that could help:

```
**$: sudo cat /proc/net/bonding/bond0**

Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: wlan0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:1c:bf:xx:xx:xx 

**$: ifconfig**

bond0     Link encap:Ethernet  HWaddr 00:1c:bf:xx:xx:xx  
          inet6 addr: fe80::21c:bfff:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:4033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2630543 (2.6 MB)  TX bytes:770912 (770.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:736 (736.0 B)  TX bytes:736 (736.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xx.xx.255.33  P-t-P:xx.xx.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:13395 (13.3 KB)  TX bytes:801 (801.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:xx:xx:xx  
          inet addr:xx.xx.0.101  Bcast:xx.xx.0.255     Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2630543 (2.6 MB)  TX bytes:770912 (770.9 KB)
```

---

