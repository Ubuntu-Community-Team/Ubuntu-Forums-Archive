---
title: "Slow wireless connection"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by Cheetah05 on 2011-07-09
System:
Samsung Q430 Laptop
Ubuntu 11.04 (fully updated with drivers enabled)
Chipset: Broadcom

I have a 50Mbps Virgin service which I get close to full speed with within Windows on wireless. When I do the same speed test in Ubuntu I barely get 1Mbps.

How do I fix this issue?

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  ESSID:"virginmedia"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:3F:0E:FE:78:88   
          Bit Rate=5.5 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=-6 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18  Invalid misc:0   Missed beacon:0


```

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:24:54:b1:8e:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr e8:39:df:11:f7:cd  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea39:dfff:fe11:f7cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34727 errors:0 dropped:0 overruns:0 frame:23404
          TX packets:34072 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33158439 (33.1 MB)  TX bytes:5728246 (5.7 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

```

Thank you.

---

