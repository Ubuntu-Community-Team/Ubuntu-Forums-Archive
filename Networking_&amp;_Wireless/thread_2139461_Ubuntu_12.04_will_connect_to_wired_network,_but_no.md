---
title: "Ubuntu 12.04 will connect to wired network, but not to internet when using static IP"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by lawschooldan on 2013-04-26
Running Ubuntu 12.04 on a wired connection. When using the network tools, if I switch to a static IP address, the internet connection will not work. I can ping my router, so I know the machine is connected to the network. I can access the router itself, but I can't get online. When I switch to a dynamic address, all of a sudden the internet works again.  I want to use a static IP so that I can use xbmc remote through the network to control the player. O/P of ifconfig, after switching to static IP follows:

eth0      Link encap:Ethernet  HWaddr 00:11:d8:37:26:89  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe37:2689/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2247119 (2.2 MB)  TX bytes:319735 (319.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77534 (77.5 KB)  TX bytes:77534 (77.5 KB)


Thanks in advance for your help.

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by lawschooldan on 2013-04-26
Thanks. I did end up going the router side, must have forgotten that I could set a reservation on the router side of things. Thanks.

-Dan

---

### Post by nerdyme on 2013-04-27
> **lawschooldan said:**
> Thanks. I did end up going the router side, must have forgotten that I could set a reservation on the router side of things. Thanks.

-Dan

How can I always get a static IP address via DHCP? It will change depending on lease time. Please tell me the maening of DHCP reservation on the router side of things?

---

### Post by ahallubuntu on 2013-04-27
~

---

