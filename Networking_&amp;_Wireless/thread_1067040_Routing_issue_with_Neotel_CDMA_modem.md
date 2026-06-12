---
title: "Routing issue with Neotel CDMA modem"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by potgietdl on 2009-02-11
Hi All,

I`m quite new to most of the routing things so i`m struggling a bit. 

My current setup:
internal(10.0.0.x) -> router(10.0.0.1) -> DSL Modem -> Internet

Internal Network
1 x windows
1 x DNS-323
1 x Linux Ubuntu 8.10

I`m trying to get the Ubuntu machine connected via a usb modem.

Info:
I`ve setup a ppp connection with a CDMA usb phone/modem using the usbserial gsm driver on the ubuntu machine. I can connect to the isp via "pon neotel" and it seems to work as i get my local ip and remote ip.

Route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.0.0.1        0.0.0.0         UG    100    0        0 eth0

syslog:
Feb 11 20:14:22 DC-ONLINE pppd[5230]: not replacing existing default route via 10.0.0.1
Feb 11 20:14:22 DC-ONLINE pppd[5230]: Cannot determine ethernet address for proxy ARP
Feb 11 20:14:22 DC-ONLINE pppd[5230]: local  IP address 41.174.6.111
Feb 11 20:14:22 DC-ONLINE pppd[5230]: remote IP address 2.2.2.2
Feb 11 20:14:22 DC-ONLINE pppd[5230]: primary   DNS address 41.160.0.36
Feb 11 20:14:22 DC-ONLINE pppd[5230]: secondary DNS address 41.160.0.37
Feb 11 20:14:22 DC-ONLINE pppd[5230]: Script /etc/ppp/ip-up started (pid 5244)
Feb 11 20:14:23 DC-ONLINE pppd[5230]: Script /etc/ppp/ip-up finished (pid 5244), status = 0x0

The problem:
Because of the existing eth0 card i have a default route to the gateway 10.0.0.1, which under normal conditions is perfect as i want to use the existing modem on the router for internet. But when i get the ppp connected, i want to use it as my default gw. 

Now....the fun part. 
i`m connected with a windows laptop to the ubuntu machine via ssh on the internal lan. I`ve added the following two commands to /etc/ppp/ip-up 

route del default
route add default gw $PPP_REMOTE

The problem here is that as soon as the connection is up the ubuntu pc loses sight of the internal lan and my ssh session is lost. Also i cant then connect to the local_ip assigned to me via an external connection. So the ppp seems to work fine.

I`m not sure how to achieve this type of setup. Please any help would be fantastic.

I figured it should work both ways to either add a route to the internal network and change the default route as long as the connection to the isp lasts and then switch back with ip-down. or add a route that dictates all internet traffic has to go to the new connection.

Thanks
Derick

---

### Post by potgietdl on 2009-02-18
First of all, let me start of and say thanks for the many reply`s i got on this thread. It really helped me solve nothing.

The Solution, add another default route which is equal to the ppp remote ip. so in my case 2.2.2.2.

I now have two default routes. one as 
10.0.0.1 on eth0
2.2.2.2 on ppp0.

It works like a bomb, and the great thing is that if the connection fails, my machine doesn't start to use the default 10.0.0.1 gateway, which in my case is perfect.

I can still access the box via the 10.0.0.0 lan and get it to connect outwards via the modem.

Thanks for all the help potgietdl, with out you this would not have been possible.

---

