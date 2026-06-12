---
title: "Restart networking manually to get connected"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by ThomWilhelm on 2011-03-29
I have a server which is the DMZ assigned server for the network, the server has 2 network cards, one to connect to the ADSL router, the other for a local network.

A couple of days ago I had to reboot the server, when I started it again it was not accessible from outside the local network. I spent some time trying to diagnose the issue, it had correctly been assigned the DMZ ip address and all the setup was correct, the server could not send/receive connections to the internet. To get it working I found I simply have to run:

sudo /etc/init.d/networking restart

Everytime the server starts and then everything work fines. Then the server can load web pages as well as receive connections. I have posted the results of "ip route" below before and then after I run the above command, there is a slight difference in the ordering, not sure if this makes a difference:

root@webserver1:~# ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.200 
169.254.0.0/16 dev eth1  proto kernel  scope link  src 169.254.202.245 
default via 169.254.202.245 dev eth1  scope link  metric 100 
default via 192.168.0.1 dev eth0  metric 100 

root@webserver1:~# ip route
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.200 
169.254.0.0/16 dev eth1  proto kernel  scope link  src 169.254.202.245 
default via 192.168.0.1 dev eth0  metric 100 
default via 169.254.202.245 dev eth1  scope link  metric 100

For reference here is the results of my ifconfig (it is the same before and after, eth0 is the internet connection, eth1 is the local network):

root@webserver1:/etc/init.d# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:ee:01:93:8d  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:eeff:fe01:938d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:266458 (266.4 KB)  TX bytes:1713445 (1.7 MB)
          Interrupt:17 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:18:37:08:4b:2c  
          inet addr:169.254.202.245  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::218:37ff:fe08:4b2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1237949 (1.2 MB)  TX bytes:228659 (228.6 KB)
          Interrupt:18 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25992 (25.9 KB)  TX bytes:25992 (25.9 KB)

Any ideas why restarting the network would fix this issue I have?

---

