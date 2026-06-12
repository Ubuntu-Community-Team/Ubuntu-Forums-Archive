---
title: "Second NIC sees gateway but not other boxes"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by schlagle on 2011-04-13
I have 10.04 Server setup with dual NICs. The first one works great on the public network. The second one only connects to the gateway. It simply can't get past the gateway. I'm assuming this is a routing problem but need some help figuring it out. Here's some output to mull over. Note that "x.x" are used simply to hide the IP address of the machine. It's eth1 that i'm having the problem with.

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:fb:33:23  
          inet addr:x.x.1.1  Bcast:x.x.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21c:c0ff:fefb:33f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:116835031 (116.8 MB)  TX bytes:14259736 (14.2 MB)
          Memory:e3200000-e3220000 

eth1      Link encap:Ethernet  HWaddr 00:04:76:38:d5:43  
          inet addr:192.168.10.111 Bcast:192.168.10.255 Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe38:d5e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8535426 (8.5 MB)  TX bytes:2100493 (2.1 MB)
          Interrupt:11 Base address:0xa800 


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    192.168.10.2    255.255.255.0   UG    0      0        0 eth1
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
x.x.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         x.x.254.252  0.0.0.0         UG    100    0        0 eth0

---

### Post by gareththered on 2011-04-14
You seem to be running two networks on one LAN segment.  The first (eth0) and second (eth1) will reach the gateway by using ARP, therefore everything that's local will work.

When you attempt to go further with eth1, traffic will get as far as the gateway and stop as eth1 is on a private IP address range - unless you have NAT configured on your gateway.

As eth0 is in a public address range (x.x.0.0) then that will route in/out of your gateway, which is why you can see that working properly.

Unless your gateway can be configured to run both networks; one directly connected and the other via NAT then I can't see how this will work.

If you are running a server and need the outside world to access it, you could always configure eth0 to also be in the private address space (192.168.x.x) and configure port forwarding on the router.

---

