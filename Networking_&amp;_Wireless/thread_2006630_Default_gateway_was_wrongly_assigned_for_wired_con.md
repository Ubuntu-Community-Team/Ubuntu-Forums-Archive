---
title: "Default gateway was wrongly assigned for wired connection"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by hello5678 on 2012-06-19
Hello there,

i'm a newbies to Ubuntu .... recently i installed Ubuntu 12.04 LTS on my old Dell notebook ... everything work fines with wireless connection.
but when i connected to the router using wired connection, i found that the default gateway was wrongly assigned ... therefore i can't connect to the Internet or ping it from other PC !!

I've tried setting the default gateway by using the "route add default gw" command but it response with "RTNETLINK answers: No such process" ....
I've also tried to manually setup the IP address, but still no luck (can't connect to internet nor ping from other PC).... 

Would someone pls. help me out for the problem, many thanks !!!  
Sorry for the long story !!

---------------------------------------
Here is the info of route and ifconfig for eth0 (wired connection):

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         setup.net       0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.8.0     *               255.255.255.0   U     1      0        0 eth0

eth0      Link encap:Ethernet  HWaddr 00:12:3f:82:22:6e  
          inet addr:192.168.8.2  Bcast:192.168.8.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76183 (76.1 KB)  TX bytes:382221 (382.2 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:204130 (204.1 KB)  TX bytes:204130 (204.1 KB)

---------------------------------------
Here is the info of route and ifconfig for eth1 (wireless connection):

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         dir-605         0.0.0.0         UG    0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.0.0     *               255.255.255.0   U     2      0        0 eth1

eth1      Link encap:Ethernet  HWaddr 00:13:ce:1c:30:f0  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe1c:30f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1052640 errors:185 dropped:185 overruns:0 frame:0
          TX packets:869156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:993991879 (993.9 MB)  TX bytes:662861003 (662.8 MB)
          Interrupt:10 Base address:0x2000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:235879 (235.8 KB)  TX bytes:235879 (235.8 KB)

---

### Post by rukiaEnix on 2012-06-19
Hello, what do you mean by gateway wrongly assigned? Are you getting an error message somewhere?

And what is your network configuration for wired connection, DHCP or manual?

And if it's manual how are you configuring the network settings?

---

### Post by hello5678 on 2012-06-19
Thanks rukiaEnix !!
 
I connected using DHCP.
 
The IP for my router is 192.168.0.1 (dir-605), it was correctly assigned when i connected using Wifi (i can connect to Internet & ping from other PC).
 
However, when i connected using wired connection, it gave me 192.168.8.2 (setup.net) which I have no idea why this IP was assigned.
 
I did try to set the IP manually as below:
IP: 192.168.0.103
subnet mask: 255.255.255.0
default gateway: 192.168.0.1
 
It seems Ok, the IP was successfully set, however I still can't connect to the Internet nor ping from other PC .....

---

### Post by rukiaEnix on 2012-06-19
Did you also configure your DNS settings correctly?

Try pinging Ubuntu forums IP and post please the result:

```

ping 91.189.94.12

```

---

