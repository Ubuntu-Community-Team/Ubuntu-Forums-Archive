---
title: "Strange Dual NIC Issue"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by dolsson01 on 2011-06-10
I've been working on a strange issue for the last week that I'm hoping this community can help me with.

I have a Dell R210 server running natty (also seeing this same issue with maverick) with dual NICs.  I have one NIC in our DMZ (eth1) and the other (eth0) in our internal management network.  

I also have static routes to allow communication to our other 2 sites (connected via VPN).  The VPN has been up for months and my windows systems do not have this network issue. 

My current configuration works, but I'm seeing about 5 to 10 seconds where I cannot ping the management interface every 20 minutes.  Every 20 minutes there is 5 to 10 seconds of time where I cannot ping the management interface.  Repeated because it's so damn weird to say...

Here is my current configuration.  Do you guys have any ideas on what could be causing this?  

I've checked into the ARP flux issue, but I don't think that applies since the NICs are in different subnets (and physically separate).

```

eth0      Link encap:Ethernet  HWaddr bc:30:5b:d4:60:ca
          inet addr:192.168.40.21  Bcast:192.168.40.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4734593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6171794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1966423934 (1.9 GB)  TX bytes:6662167208 (6.6 GB)
          Interrupt:16 Memory:da000000-da012800

eth1      Link encap:Ethernet  HWaddr bc:30:5b:d4:60:cb
          inet addr:234.253.247.221  Bcast:234.253.247.255  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2744705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3687003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:309511483 (309.5 MB)  TX bytes:5109819033 (5.1 GB)
          Interrupt:17 Memory:dc000000-dc012800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6827591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6827591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11045008881 (11.0 GB)  TX bytes:11045008881 (11.0 GB)

		  
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
234.253.247.192 *               255.255.255.192 U     0      0        0 eth1
192.168.20.0    192.168.40.254  255.255.255.0   UG    0      0        0 eth0
192.168.50.0    192.168.40.254  255.255.255.0   UG    0      0        0 eth0
192.168.40.0    *               255.255.255.0   U     0      0        0 eth0
default         234.253.247.193 0.0.0.0         UG    100    0        0 eth1


auto eth0
iface eth0 inet static
        address 192.168.40.21
        netmask 255.255.255.0
        network 192.168.40.0
        broadcast 192.168.40.255
        post-up route add -net 192.168.20.0 netmask 255.255.255.0 gw 192.168.40.254 dev eth0
        post-up route add -net 192.168.50.0 netmask 255.255.255.0 gw 192.168.40.254 dev eth0

auto eth1
iface eth1 inet static
        address 234.253.247.221
        netmask 255.255.255.192
        network 234.253.247.192
        broadcast 234.253.247.255
        gateway 234.253.247.193

```

---

