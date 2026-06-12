---
title: "Wired network woes"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by noffle on 2009-11-20
Hello good people of the internet,
I have just made a fresh install of Karmic on a computer than was previously running windows. The computer is connected directly to a modem and the internet works just fine. It is also connected to a network switch which connects it to two other computers - one running Windows and the other Arch Linux. The internet connection is not being received by either of those computers, as it does automatically under Windows (so it can't be a connection problem). Upon booting, Ubuntu tells me that there is a disconnected wire - or something to that extent. Here is the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:19:db:6a:ed:85  
          inet6 addr: fe80::219:dbff:fe6a:ed85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7596 (7.5 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:23 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:e1:a7:76:76:81  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e1:a7ff:fe76:7681/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3155 errors:45 dropped:0 overruns:0 frame:45
          TX packets:3071 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3032289 (3.0 MB)  TX bytes:427356 (427.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```
So it would seem that eth1 is the internet connection and eth0 the network. Any ideas would be much appreciated, thank you (there seems to be a lack of wired networking literature on wired networking - or maybe I'm a bad Googler).
Merci.

---

### Post by dandnsmith on 2009-11-20
Under Windows, I'm willing to bet, you've set up to share the internet - it's those settings you have to replicate.
Have a look at the routing tables to see what is set up (*route print* I think), but there may also be a need to set up forwarding of packets (having sorted them out via NAT - which I don't know how to set up).

---

### Post by Iowan on 2009-11-20
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for connection sharing that may be useful.

---

### Post by dandnsmith on 2009-11-21
That's certainly helpful to me - I'll bookmark it for reference.

---

