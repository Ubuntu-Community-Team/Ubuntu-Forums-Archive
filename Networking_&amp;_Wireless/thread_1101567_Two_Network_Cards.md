---
title: "Two Network Cards"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by javier__medina on 2009-03-20
Hi, this is my first post.

Here is the thing.....

Im have Ubuntu Desktop 8.04 as the main OS and as a guest i have Windows XP running on VirtualBox... 

The Host-> Ubuntu: Is the files and printers sharing, email, etc. 
The Guest-> Virtual Windows XP: Is the server for an accounting program.

The trafic was really slow because both servers were using the same network card, so i installed a 2nd network card. 

The ubuntu system recognize the cards as eth0 and eth2.

How can i make them connect at same time? 
Making Ubuntu use only one card for his tasks and leaving the other connected to.... 
When i configure both working at the same time, the lan and internet conexion freeze in both computers, so im using only one rigth now.

This is what i tryed to do:

```

axxis@CANSERVER:~$ sudo gedit /etc/network/interfaces

auto lo 
iface lo inet loopback

iface eth0 inet static
address 192.168.1.170
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

iface eth2 inet static
address 192.168.1.160
netmask 255.255.255.0
gateway 192.168.1.1

auto eth2



axxis@CANSERVER:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:06:91:68  
          inet addr:192.168.1.170  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe06:9168/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:23839563 (22.7 MB)  TX bytes:4398609 (4.1 MB)
          Memory:90380000-903a0000 

eth2      Link encap:Ethernet  HWaddr 00:80:ad:70:a1:9c  
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:571143 (557.7 KB)  TX bytes:571143 (557.7 KB)


```

Thank you in advance, waiting for some help.

---

