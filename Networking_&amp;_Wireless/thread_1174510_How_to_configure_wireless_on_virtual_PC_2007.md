---
title: "How to configure wireless on virtual PC 2007"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Surendra on 2009-05-31
I installed Ubuntu Desktop 9.04 on virtual PC 2007.  Now i am able to get the network through wire. I am not able to configure the wireless.

I am using IBM Think pad T42.


[PHP]
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[/PHP]

[PHP]cat /etc/network/interfaces
auto lo
iface lo inet loopback

[/PHP]
[PHP]
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:ff:44:4e:ec
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fe44:4eec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:418407 (418.4 KB)  TX bytes:101314 (101.3 KB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



[/PHP]
Can anybody suggest how to configure wireless connection ubuntu 9.04.

Thanks in Advance

---

### Post by Surendra on 2009-06-01
Does anybody have any idea on this?

Thanks in Advance

---

