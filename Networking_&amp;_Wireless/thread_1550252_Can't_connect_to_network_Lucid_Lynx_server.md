---
title: "Can't connect to network Lucid Lynx server"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by eddawg128 on 2010-08-10
As stated, I can't seem to connect to the network.  I am using ssh to log into a new install of Lucid Lynx Server Edition, and everything was working fine, until I tried to make a static IP address.  I assume I broke something.  Unfortunately this is my first Ubuntu install so I don't know where to turn.  I hope that i can get some help here, and will be able to finish with this VPN Server install. Thanks for the help in advance, and again sorry for the completely new noob question.

ifconfig
> eargumedo@HSI-Network:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:dc:6f:18
          inet addr:192.168.3.20  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fedc:6f18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:370553 (370.5 KB)  TX bytes:234382 (234.3 KB)
          Interrupt:19 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:29792 (29.7 KB)  TX bytes:29792 (29.7 KB)



I seemed to have solved the problem. Apparently a reboot did not reconfigure the network adapter.  

sudo /etc/init.d/networking restart

solved it.  Thanks.

---

