---
title: "VLAN forwarding"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by shingalated on 2010-08-03
I have a DAAP server with multiple VLAN interfaces.  I would like to get traffic forwarded on all of the VLANs.  Forwarded from eth0 to eth1.010*  I've got the switch configured to be a trunk port with the correct VLANs, and I enabled 
```
/proc/sys/net/ipv4/ip_forward 
``` 

But that doesn't seem to be doing the trick.
Is there anything else I need to do?  

Here is my ifconfig results, as you can see the VLAN interfaces aren't really getting any traffic:

```
eth0      Link encap:Ethernet  HWaddr 00:14:d1:10:ca:fc  
          inet addr:192.168.1.20  Bcast:172.21.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:264232 (258.0 KiB)  TX bytes:37425 (36.5 KiB)
          Interrupt:20 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1c:c4:31:28:22  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225213 (219.9 KiB)  TX bytes:47118 (46.0 KiB)
          Interrupt:17 

eth1.0101 Link encap:Ethernet  HWaddr 00:1c:c4:31:28:22  
          inet addr:172.17.1.20  Bcast:172.17.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9076 (8.8 KiB)

eth1.0102 Link encap:Ethernet  HWaddr 00:1c:c4:31:28:22  
          inet addr:172.18.1.20  Bcast:172.18.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9076 (8.8 KiB)

eth1.0103 Link encap:Ethernet  HWaddr 00:1c:c4:31:28:22  
          inet addr:172.19.1.20  Bcast:172.19.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9076 (8.8 KiB)

eth1.0104 Link encap:Ethernet  HWaddr 00:1c:c4:31:28:22  
          inet addr:172.20.1.20  Bcast:172.20.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9076 (8.8 KiB)

eth1.0105 Link encap:Ethernet  HWaddr 00:1c:c4:31:28:22  
          inet addr:172.21.1.20  Bcast:172.21.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9076 (8.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20777 (20.2 KiB)  TX bytes:20777 (20.2 KiB)

```

Here is my interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Automagically configured network interfaces
auto eth0
auto eth1.0101
auto eth1.0102
auto eth1.0103
auto eth1.0104
auto eth1.0105

iface eth0 inet static
   address 192.168.1.20
   netmask 255.255.0.0
   gateway 192.168.1.3
   network 172.21.0.0
   broadcast 172.21.255.255

iface eth1.0101 inet static
   address 172.17.1.20
   netmask 255.255.255.0


iface eth1.0102 inet static
   address 172.18.1.20
   netmask 255.255.255.0


iface eth1.0103 inet static
   address 172.19.1.20
   netmask 255.255.255.0


iface eth1.0104 inet static
   address 172.20.1.20
   netmask 255.255.255.0


iface eth1.0105 inet static
   address 172.21.1.20
   netmask 255.255.255.0
```

Thank you for any help, I've been working on this for quite a while.

---

