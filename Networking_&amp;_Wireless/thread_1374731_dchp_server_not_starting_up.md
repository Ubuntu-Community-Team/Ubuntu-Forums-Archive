---
title: "dchp server not starting up"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by dwight on 2010-01-07
I recently bought a TV that, in theory, should be able to connect to my computer via DLNA and play back the media served from it. The problem is that my router seems to block the TV from accessing my computer. So instead, I thought I'd try to connect the tv directly to my ethernet port. And this is where I'm stuck right now.. I can't get dhcp server working on the laptop so that the tv could obtain an ip address. I've tried reading various networking tutorials, but haven't gotten much smarter. 
Right now I get this when trying to start the dhcp server
```

Jan  7 12:10:03 zabu dhcpd: No subnet declaration for eth0 (0.0.0.0).
Jan  7 12:10:03 zabu dhcpd: ** Ignoring requests on eth0.  If this is not what
Jan  7 12:10:03 zabu dhcpd:    you want, please write a subnet declaration
Jan  7 12:10:03 zabu dhcpd:    in your dhcpd.conf file for the network segment
Jan  7 12:10:03 zabu dhcpd:    to which interface eth0 is attached. **

```

My ifconfig is:
```

eth0      Link encap:Ethernet  HWaddr 00:1b:63:2f:b3:b3  
          inet6 addr: fe80::21b:63ff:fe2f:b3b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:437427 (437.4 KB)  TX bytes:315014 (315.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7906593 (7.9 MB)  TX bytes:7906593 (7.9 MB)


wlan0     Link encap:Ethernet  HWaddr 00:1b:63:c6:b2:87  
          inet addr:192.168.216.121  Bcast:192.168.216.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fec6:b287/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5782444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6191810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3708317071 (3.7 GB)  TX bytes:781886747 (781.8 MB)

```

Any ideas how I should go about this to get something running? Thanks

---

### Post by suseendran.rengabashyam on 2010-01-07
Hi,
   In order to run a DHCP server you need to assign an ip to your interface eth0.

The network configuration file is /etc/network/interfaces and the format would be  

auto eth0
iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
network x.x.x.x
gateway x.x.x.x


Let me know if this helps you.

---

