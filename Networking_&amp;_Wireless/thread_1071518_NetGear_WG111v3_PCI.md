---
title: "NetGear WG111v3 PCI"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by anjanesh on 2009-02-16
Hi

I have a wired connection on my Ubuntu 8.10 64-bit PC which is fine.
I've now inserted a WLAN card to connect to another LAN. The WLAN card is a Netgear WG111v3 PCI (not USB).
But when I goto System > Administration > Network, I dont see a Wireless Connection row. It shows 2 Wired Connections though - dont know why.
```
anjanesh@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:c7:73:69  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fec7:7369/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:236040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:316920816 (316.9 MB)  TX bytes:17889708 (17.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8005389 (8.0 MB)  TX bytes:8005389 (8.0 MB)

anjanesh@ubuntu:~$ 
```
[IMG]http://img11.imageshack.us/img11/7636/gnomenetworkmanagerum0.png[/IMG]

I even installed ndiswrapper-utils & Windows Wireless Drivers from Repo, but no luck.
Is there any way to get this working ?

Thanks

---

