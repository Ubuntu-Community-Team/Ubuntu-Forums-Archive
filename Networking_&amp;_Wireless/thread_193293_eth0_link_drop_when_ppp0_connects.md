---
title: "eth0 link drop when ppp0 connects?"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by kryptosaint on 2006-06-09
I have two PC's with ethernet cards connected via a crossover cat5 cable (standard stuff) which appears to be working fine...:D 
[B]
guest@ubuntusystem1:~$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=64 time=0.182 ms[/B]

But as soon as USB modem connects to the internet the Ethernet link to my other PC...:confused: 

[B]64 bytes from 192.168.0.101: icmp_seq=69 ttl=64 time=0.213 ms
ping: sendmsg: Operation not permitted[/B]

Why does this happen? Have I incorrectly configured something? Still a linux newbie. 

I've included some details below. Any suggestions would be much appreciated.\\:D/ 

[B]guest@ubuntusystem1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:77:11:BD
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:24152 (23.5 KiB)  TX bytes:20329 (19.8 KiB)
          Interrupt:9 Base address:0xf800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:360222 (351.7 KiB)  TX bytes:360222 (351.7 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:87.113.2.122  P-t-P:195.166.128.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1710637 (1.6 MiB)  TX bytes:264829 (258.6 KiB)

Static IP Address config:
IP Address: 192.168.0.100 (PC1) 192.168.0.101 (PC2)
Subnet Mask :255.255.255.0
Gateway Address: 192.168.0.0
[-o<[/B]

---

