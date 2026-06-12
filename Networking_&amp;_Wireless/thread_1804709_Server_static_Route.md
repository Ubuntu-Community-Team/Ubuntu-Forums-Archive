---
title: "Server static Route"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by jadeye on 2011-07-15
Hey guys....

Working my way through understanding LINUX.

I still consider myself a newbie.
I recently installed a 10.04 server with LAMP and others onit.

**I wish to get it surfing the net:** apt-get update and install webmin.

My SETUP:
Ubuntu 10.04 PC
Ubuntu 10.04 SERVER

**_PC connects to www through WiFi:_**

**netstat -r**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   Iface
10.0.0.0        *               255.255.255.0   U       wlan0
192.168.122.0   *               255.255.255.0   U       eth0
link-local      *               255.255.0.0     U       eth0

**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:c1:20:48  
          inet addr:192.168.122.100  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fec1:2048/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3654 (3.6 KB)  TX bytes:3666 (3.6 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:568917887 (568.9 MB)  TX bytes:568917887 (568.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:3c:f5:37  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe3c:f537/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:594104219 (594.1 MB)  TX bytes:43179501 (43.1 MB)

**_SERVER connects:_**
Destination     Gateway         Genmask         Flags   Iface
192.168.122.0   *               255.255.255.0   U       eth0
default         192.168.122.100 0.0.0.0         UG      eth0

WHEN I PING FROM SERVER:
ping 10.0.0.4 - GOOD
ping 192.168.122.100 - GOOD
ping -b 192.168.122.253 OR 0 - GOOD

**in /etc/network/interface:**
I defined Gateway as 192.168.122.100

What am I doing wrong?
I am not that great with networks...

Does anyone have any idea how to get the SERVER to get to the internet through the PC?
They see each other, the server sees the ip given by the WWW router to the PC but he does not exit through it...

I did some experimenting here trying to replace the gateway with all sorts but with no luck...

Tried:
up route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.122.253 (=router static ip)

How to fixit?

Thanx.

---

### Post by jadeye on 2011-07-15
Guys I need help....

I am sure there is someone here that know the solution no problem.

Please see thread:

[http://ubuntuforums.org/showthread.php?t=1804709]("http://ubuntuforums.org/showthread.php?t=1804709")

---

### Post by szs on 2011-07-19
i think you need to use the Internet Connection Sharing (ICS) option.
read [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)) for instructions.

hope it'll solve your prob.
have a great day dude.

---

