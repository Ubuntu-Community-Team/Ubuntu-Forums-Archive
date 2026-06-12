---
title: "Intermittent slow connection after upgrade"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by killkoy on 2011-10-25
After upgrading to the lts version of ubuntu I have had trouble connecting to the internet. Some websites seem to load up fine, but others seem to hang intermittently.

I have tried disabling ipv6 and searching on here. Also tried upgrading to 11.04 to see if that helps but no luck.

Any help would be much appreciated

Regards

---

### Post by killkoy on 2011-10-26
Output from ifconfig```
ath0      Link encap:Ethernet  HWaddr 00:16:e3:aa:09:97  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:feaa:997/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88212836 (88.2 MB)  TX bytes:5065141 (5.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:d1:bc:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.4 KB)  TX bytes:1408 (1.4 KB)

```and iwconfig ```
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11bg  ESSID:"Swing-winged"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:11:50:EB:57:6B   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:36   Missed beacon:0

```

---

### Post by killkoy on 2011-10-27
I've just tried using a live cd of version 11.10 and still have this problem.

an example of a website where is occurs is news.bbc.co.uk/weather

I didn't have this problem with version 9.10, is it possible to revert to this?

---

### Post by killkoy on 2011-10-28
I've tried using trace-route to see if I can track down the problem.

traceroute news.bbc.co.uk takes too long to complete.

traceroute bbc.co.uk seems to work fine

---

### Post by killkoy on 2011-10-31
bump

---

