---
title: "how do i connect to DSL and eth0 simultaniously?"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by willem on 2009-04-29
I am running a dual boot Intrepid/XP system. I have two network connections: a telkom DSL connection for my internet and a normal ethernet connection to connect to our home lan. In XP, I can access the internet and the lan at the same time. In Ubuntu, I have to choose between one of my two network connections however. (I can select eithe eth0 or DSL from the network icon by clicking on one of the radio buttons, but not both). How can I enable both my eth0 and my DSL connection simultatiously?

---

### Post by coutts99 on 2009-04-29
What interface does your DSL show as? eth1?

I don't use networkmanager personally, prefer to use /etc/network/interfaces in which you can configure multiple interfaces.

---

### Post by willem on 2009-04-29
> **coutts99 said:**
> What interface does your DSL show as? eth1?

I don't use networkmanager personally, prefer to use /etc/network/interfaces in which you can configure multiple interfaces.

The DSL connection is listed as "DSL connection 1", and the lan as "eth0" in networkmanager. Using /etc/network/interfaces sounds like a better idea than networkmanager. My interfaces file currently looks like this:

> 
auto lo
iface lo inet loopback
address 10.0.0.79
netmask 255.255.255.0


what do i need to add?

ifconfig returns the following, if it helps:
> 

eth0      Link encap:Ethernet  HWaddr 00:1f:d0:90:73:5d  
          inet6 addr: fe80::21f:d0ff:fe90:735d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7791173 (7.7 MB)  TX bytes:1255053 (1.2 MB)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16272 (16.2 KB)  TX bytes:16272 (16.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.247.71.49  P-t-P:41.242.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:9012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:7370606 (7.3 MB)  TX bytes:1061662 (1.0 MB)



---

### Post by coutts99 on 2009-04-29
Try -:

```
auto eth0
iface eth0 inet dhcp

auto pppp
iface ppp0 inet dhcp
```

The "sudo /etc/init.d/networking restart"

---

### Post by coutts99 on 2009-04-29
I might have the ppp stuff wrong (I only use ethernet here)

Try this instead for ppp -:

```
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
```

---

### Post by willem on 2009-04-29
I've got everything working now! Here's how:

I tried your initial solution, and it almost worked. We don't have a DHCP server - it's a small home network. (I'm building a linux DHCP and file server as soon as I scavenge enough spare parts. You'll be getting plenty of queries on that soon enough...) Anyway, *sudo /etc/init.d/networking restart* gave the following:

```


 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

ppp0: unknown hardware address type 512
ppp0: unknown hardware address type 512
Listening on LPF/ppp0/
Sending on   LPF/ppp0/
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1f:d0:90:73:5d
Sending on   LPF/eth0/00:1f:d0:90:73:5d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 * if-up.d/mountnfs[eth0]: waiting for interface pppp before doing NFS mounts
Ignoring unknown interface pppp=pppp.
                                                                         [ OK ]


```
I figured the problem was that we don't have a DHCP server - it's a small home network. (I'm building a linux DHCP and file server as soon as I scavenge enough spare parts. You'll be getting plenty of queries on that soon enough...) So, I after fiddling with /etc/network/interfaces to use a static ip address, I got eth0 to work by changing /etc/network/interfaces to:

```


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.79
netmask 255.255.255.0

auto pppp
iface ppp0 inet dhcp


```

DSL was still not working, so I started looking in the Ubuntu help system for answers. (Yes, if all else fails, RTFM!) I found a very convenient way to set up the DSL to run on the eth0 connection. I simply ran *pppoeconf* which sets everything up easily and quickly. Everything is working perfectly now. My /etc/network/interfaces now looks like this:

```


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.79
netmask 255.255.255.0


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


```

I would have been struggling with this for ages wihout your help. Thanks so much!

---

### Post by coutts99 on 2009-04-29
Yes I've just come across pppoeconf, glad you got it working :)

---

