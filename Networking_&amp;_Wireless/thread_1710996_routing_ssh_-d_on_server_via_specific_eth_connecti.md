---
title: "routing ssh -d on server via specific eth connection"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by gfenton on 2011-03-20
Hi all

I have a dedicated server that has 1 IP and 3 failover IPs:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr x:x:x:x:x:x  
          inet addr:91.121.x.x  Bcast:91.121.x.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:222106164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221379491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:189049171577 (189.0 GB)  TX bytes:205359291984 (205.3 GB)
          Interrupt:40 Base address:0x4000 

eth0:0    Link encap:Ethernet  HWaddr x:x:x:x:x:x  
          inet addr:94.23.x.215  Bcast:94.23.x.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:40 Base address:0x4000 

eth0:1    Link encap:Ethernet  HWaddr x:x:x:x:x:x  
          inet addr:94.23.x.88  Bcast:94.23.x.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:40 Base address:0x4000 

eth0:2    Link encap:Ethernet  HWaddr x:x:x:x:x:x  
          inet addr:94.23.x.94  Bcast:94.23.x.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:40 Base address:0x4000
```I have sshd listening on the server and can connect from the client using ssh -d (socks).

I want the data passed over the socks tunnel to exit via a set IP address (such as eth0:1) rather than the default of eth0 so that it appears as eth0:1's IP on sites such as wimi.com.

Is this possible?

If so, how?

---

