---
title: "Getting two network connections to play nicely together"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by valuntahr on 2011-06-12
Is there any way to turn off the load balancing that occurs when ubuntu detects two active network connections? To be more specific, I have two networks set up, one of which is supposed to be for regular web traffic while the other network is dedicated to streaming various things throughout the house. Whenever I try to connect my server to both networks at once ubuntu "load balances" traffic from the web network onto the streaming network, which completely defeats the segregation I was going for. So far all of my attempts to turn off that behavior haven't worked at all. I'm currently running Ubuntu 10.10, any help would be greatly appreciated.

---

### Post by blueridgedog on 2011-06-12
Is each interface on the same subnet?  Is the server the common gateway for the clients?

What is the output of ifconfig?

---

### Post by valuntahr on 2011-06-12
each interface is on a different subnet. The server's not a common gateway for the clients, and ifconfig is showing the correct subnets for each interface as assigned by DHCP.

Ifconfig output

eth0      Link encap:Ethernet  HWaddr   
          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:159875157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144381087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155702420343 (155.7 GB)  TX bytes:34471162341 (34.4 GB)
          Interrupt:51 

eth1      Link encap:Ethernet  HWaddr   
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3273048 (3.2 MB)  TX bytes:1343266 (1.3 MB)
          Interrupt:52 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4082397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4082397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1616788375 (1.6 GB)  TX bytes:1616788375 (1.6 GB)

---

### Post by blueridgedog on 2011-06-12
Can the server get to the outside via each subnet?  In order to load balance to an internal host, the host would need to be on the same subnet as each interface, also to load balance to the internet, then each interface would need a route out.  What is the routing that the server is using?

What is the output of 

```
route
```

The solution would be to setup a default route that applies only to the interface you are trying to setup.

---

