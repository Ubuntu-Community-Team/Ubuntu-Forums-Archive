---
title: "Working eth1 cannot be found"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by AKviking on 2009-04-02
I have an ethernet card ETH1 that has been working great, and still is, however when I installed WireShark tonight, it won't let me select an interface to monitor.  

I go to System > Preferences > Network Configuration and get nothing. *(I actually have two cards and it sees neither)*

If I run IFCONFIG, I get the following:

> lance@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:04:5a:83:d0:ad  
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe83:d0ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4073069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4094718 errors:26 dropped:0 overruns:0 carrier:26
          collisions:0 txqueuelen:1000 
          RX bytes:1382839872 (1.3 GB)  TX bytes:1411737942 (1.4 GB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43177297 (43.1 MB)  TX bytes:43177297 (43.1 MB)


Any ideas how to get UBUNTU to recognize my card in GNOME?

---

