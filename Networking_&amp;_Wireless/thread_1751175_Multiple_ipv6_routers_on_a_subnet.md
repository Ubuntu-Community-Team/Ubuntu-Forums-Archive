---
title: "Multiple ipv6 routers on a subnet"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by jonsmirl on 2011-05-06
I have a 6to4 tunnel running on Ethernet (subnet 2002:ad4c:16cc:1) without problem. It runs radvd and announces a default route back to the Internet like this: "default via fe80::6a7f:74ff:fe0a:fbec dev br0"

On this same Ethernet I have a Linux plugbox (fe80::225:31ff:fe01:cc) which is a gateway to a network of IPv6 enabled sensors. I've assigned this second subnet 2002:ad4c:16cc:2.

How do I get the plugbox to announce "2002:ad4c:16cc:2 via fe80::225:31ff:fe01:cc" so that the hosts on the Ethernet (2002:ad4c:16cc:1) will automatically pick up the route? The route works if I add it to the boxes manually. 

I've tried getting radvd on the plugbox to do this but I've had no success.

---

### Post by Sef on 2011-05-06
Are you sure that your Linux plugbox supports IPv6? Unless it is specifically stated that it does, it probably does not.

---

### Post by jonsmirl on 2011-05-06
I am sure that plug box is running ipv6. If I setup all of the routes up by hand I can ping my sensor nodes over ipv6 from an external IPv6 site. The sensor nodes are IPv6 only.

I am just missing the part on how to get the plugbox ( fe80::225:31ff:fe01:cc) to announce the route ("2002:ad4c:16cc:2 via fe80::225:31ff:fe01:cc") onto the Ethernet LAN (2002:ad4c:16cc:2) such that hosts connected to the Ethernet LAN will automatically pick the route up. 

If I go around to the boxes on the Ethernet LAN and manually add the route it all works. But that is annoying every time tun6to4 changes my global ipv6 address.

---

### Post by jonsmirl on 2011-05-06
Plug box is running 2.6.31 from plugapps.com. I have all of the source and can rebuild the system. 


[root@Plugbox ~]# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:31:01:00:CC  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:ad4c:16cc:1:225:31ff:fe01:cc/64 Scope:Global
          inet6 addr: fe80::225:31ff:fe01:cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16971077 (16.1 Mb)  TX bytes:1605019 (1.5 Mb)
          Interrupt:40

---

