---
title: "connecting to multiple networks"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by kapad on 2010-09-04
Have been trying unsuccessfully to connect to two networks and have them working together. 

My setup is such that I have a LAN which connects me to the campus network but doesn't provide internet.

I use a USB LAN connection through my phone to get online. 

Also i can use a static ip on my LAN connection but not on the USB(phone) connection. 

Both these networks dont always seem to work together. Actually some applications like filezilla and linuxdcpp have a major problem. if i use the browser for the ftp then there isn't any problem. 

what i really need working all the time is the net, filezilla(for ftp) and linuxdcpp.


thanx

---

### Post by kapad on 2010-09-04
I just got filezilla and linuxdcpp working by using a static ip and configuring a bind address for both. 

I wanted to know if there is any other method using iptables to configure both of my networks to work simultaneously.

---

### Post by BkkBonanza on 2010-09-04
You need to use the route command to set the correct routing options for the two networks. For more help, post here, your output from **route**, your LAN network ip range, your modem IP and output from **ifconfig** command. That should have all the info needed to fix the routing.

---

### Post by kapad on 2010-09-07
@bkkbonaza

sorry for the delayed reply. was having some trouble with grub and wasn't able to boot into linux. all sorted out now. 

here is the output from route

[HTML]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.42.0    *               255.255.255.0   U     1      0        0 usb0
10.3.3.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
default         10.3.3.1        0.0.0.0         UG    100    0        0 eth0[/HTML]

the iprange for my LAN network is 10.3.3.xxx

the modem ip is assigned on login and cannot be static. I connect my phone as a modem and the phone assigns an ip to the computer. it seems to always be 192.168.42.x

the ifconfig output is 

[HTML]eth0      Link encap:Ethernet  HWaddr 00:21:70:7c:57:8f  
          inet addr:10.3.3.14  Bcast:10.3.3.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe7c:578f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3903137 (3.9 MB)  TX bytes:478421 (478.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

usb0      Link encap:Ethernet  HWaddr a2:77:e2:4a:3d:be  
          inet addr:192.168.42.192  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::a077:e2ff:fe4a:3dbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:747706 (747.7 KB)  TX bytes:132399 (132.3 KB)[/HTML]

thanx for the help

---

