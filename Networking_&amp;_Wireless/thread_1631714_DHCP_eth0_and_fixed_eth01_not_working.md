---
title: "DHCP eth0 and fixed eth0:1 not working"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by markosjal on 2010-11-27
I followed the guide here:

[http://www.liberiangeek.net/2010/04/how-to-quickly-create-multiple-virtual-network-interfaces-in-ubuntu/](http://www.liberiangeek.net/2010/04/how-to-quickly-create-multiple-virtual-network-interfaces-in-ubuntu/)

All appears to have gone well except that I can not ping anything on the virtual adapter network 192.168.1.X


My interfaces file looks like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth0:1
iface eth0:1 inet static
address 192.168.1.11
netmask 255.255.255.0


Ifconfig gives me this:

eth0      Link encap:Ethernet  HWaddr 00:30:65:e6:bb:52  
          inet addr:10.11.84.164  Bcast:10.11.255.255  Mask:255.255.0.0
          inet6 addr: fe80::230:65ff:fee6:bb52/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:281161 (281.1 KB)  TX bytes:171229 (171.2 KB)
          Interrupt:41 Base address:0x2000 

eth0:1    Link encap:Ethernet  HWaddr 00:30:65:e6:bb:52  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5184 (5.1 KB)  TX bytes:5184 (5.1 KB)

I figure that maybe I can not have a DHCP thh0 and a fixed eth0:1 or that The DHCP IP range/netmask is somehow in conflict with that of the fixed range/netmask??

This is ubuntu 10.04 PPC on a 350 Mhz imac

---

