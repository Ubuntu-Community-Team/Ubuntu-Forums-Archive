---
title: "Netgear WNA1100 wireless connection times out alot?"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by BcRich on 2012-06-02
Hi
Since I installed 12.04 my wireless connection has become much slower, and often times out.
on 10.10 I was using the Aetheros compat-wireless driver [http://linuxwireless.org/en/users/Drivers/ath9k_htc](http://linuxwireless.org/en/users/Drivers/ath9k_htc) and I didn't have any issues with my wifi device
[SIZE=2]Netgear[/SIZE] [SIZE=2][WNA1100 ]("http://www.netgear.com/service-provider/products/wireless-adapters/wireless-n/WNA1100.aspx")[/SIZE][[SIZE=2]with a AR9271 chipset[/SIZE]]("http://www.netgear.com/service-provider/products/wireless-adapters/wireless-n/WNA1100.aspx")
is there a way of installing the same driver on 12.04, or is there a better solution?
I've got no idea how to fix this, so if you could help me that would be most appreciated :)
ifconfig says:
```
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:c1:a0:6f  
          inet6 addr: fe80::1e6f:65ff:fec1:a06f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4924 (4.9 KB)
          Interrupt:50 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139824 (139.8 KB)  TX bytes:139824 (139.8 KB)

wlan0     Link encap:Ethernet  HWaddr e0:46:9a:16:7c:59  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e246:9aff:fe16:7c59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26449932 (26.4 MB)  TX bytes:2137298 (2.1 MB)
```

---

