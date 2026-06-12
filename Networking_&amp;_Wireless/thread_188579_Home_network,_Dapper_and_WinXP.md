---
title: "Home network, Dapper and WinXP"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by Prism on 2006-06-04
Hi there,

I've installed Ubuntu Dapper a long time ago, and configured a home network with my other WinXP machine. The network hasn't been connected for a while, and when I established it again today, it didn't work.

My Dapper machine is connected to the Internet in ADSL, via eth1 and ppp0. It has another network card, eth0, which is connected to the Windows machine in a crossed cable.

It isn't a cable problem, since the network works when I boot into Windows (double-boot in my computer).

My Ubuntu machine runs the Shorewall firewall. I thought that this might be the problem, but even after canceling it the network doesn't work.

When I write "the network doesn't work", I mean that the Windows machine gets an IP via DHCP, but I can't ping the other computer. Pinging from my Ubuntu machine to the Windows machine doesn't work either.

What did I miss here?
Thanks in advance. :)

---

### Post by Prism on 2006-06-08
Anyone, please?

I checked more and found that in both of my network cards, the IP is 168.192.0.1. I tried to change eth1 (the one which is connected to the ADSL modem) to 168.192.0.2, but it still doesn't work. Does this IP make any difference?

The output of ifconfig on my machine is:

```
tomer@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:2E:38:17:1D
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185

eth1      Link encap:Ethernet  HWaddr 00:13:D4:C7:36:1A
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fec7:361a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9409420 (8.9 MiB)  TX bytes:21609905 (20.6 MiB)
          Interrupt:193 Base address:0xa800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6450480 (6.1 MiB)  TX bytes:6450480 (6.1 MiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:217.132.105.17  P-t-P:212.143.205.235  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:25440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:8836549 (8.4 MiB)  TX bytes:20884267 (19.9 MiB)
```

---

### Post by Slim Odds on 2006-06-08
[quote=Prism]Anyone, please?

I checked more and found that in both of my network cards, the IP is 168.192.0.1. I tried to change eth1 (the one which is connected to the ADSL modem) to 168.192.0.2, but it still doesn't work. Does this IP make any difference?
[/quote] 
If eth0 is 192.168.0.1 and eth1 is 192.168.0.2, that means they are on the SAME network. You don't want that.

eth1 should be more like 192.168.1.1

---

### Post by Prism on 2006-06-09
Thanks, it did it! :)

---

### Post by Slim Odds on 2006-06-09
[quote=Prism]Thanks, it did it! :)[/quote]

Glad to hear it. \\:D/

---

