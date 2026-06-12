---
title: "Vuplus duo ethernet connection problem"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by phd7 on 2011-02-06
Hi.
Anyone here have a VU+ connected to Ubuntu box (Ubuntu 10.10 64bit)? I am looking to confirm the correct network settings for the ethernet connection

I have a VU+ duo linux satellite receiver connected directly to the computer by cable. I used to be able to connect to it via telnet and filezilla but cant anymore. get "connection refused by server"

eth0      Link encap:Ethernet  HWaddr 00:25:64:eb:ec:b2  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:feeb:ecb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25632 (25.6 KB)  TX bytes:46353 (46.3 KB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46072 (46.0 KB)  TX bytes:46072 (46.0 KB)



I can see it in network/Windows network via nautilus and the vu+ can also connect to the internet via the computer.

A final point, just for full informatio... I have had trouble lately with that .ICEauthority file. When logging on , I get "could not update" same. I have no idea if this has anything to do with the problem.
Thanks in advance

---

