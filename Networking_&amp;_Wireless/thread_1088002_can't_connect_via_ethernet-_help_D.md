---
title: "can't connect via ethernet- help :D"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by Fenris_rising on 2009-03-05
Hi all

Recently obtained an ethernet cable so that i can hookup to the router direct rather than using the wireless. Well I get lights at both ends
but am unable to connect to the net. I am using Wicd as my network manager.
here are the results of some terminal entries.

```
*-network:1 
                description: Ethernet interface 
                product: LNE100TX 
                vendor: Lite-On Communications Inc 
                physical id: 9 
                bus info: pci@0000:05:09.0 
                logical name: eth0 
                version: 20 
                serial: 00:c0:f0:57:1c:6d 
                width: 32 bits 
                clock: 33MHz 
                capabilities: bus_master ethernet physical 
                configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 module=tulip multicast=yes 

eth0      Link encap:Ethernet  HWaddr 00:c0:f0:57:1c:6d  
          inet6 addr: fe80::2c0:f0ff:fe57:1c6d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:629 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:93327 (91.1 KB) 
          Interrupt:21 Base address:0xe800 
```

Can I establish if my NIC just isn't linux friendly or are there further
terminal enquiries I can do to see whats wrong? The Router modem is a belkin54g which I can connect with the cable to my eeepc successfully.

regards

Fenris

---

### Post by Iowan on 2009-03-05
I'm not really familiar with wicd... if it uses */etc/network/interfaces*, or keeps information elsewhere.  Post */etc/network/interfaces*.  I'd ask about **lshw -C network**, but it looks like you've already provided that information.

---

### Post by Fenris_rising on 2009-03-06
Hi there

Yes the info is from the lshw input. This is my etc/network/interfaces
which does seem a little empty. Any thoughts? 

```
auto lo
iface lo inet loopback
```

I will have a look round and see if I can find the code I could put in. I have a vague Idea what it looks like :D

Thanks for looking

regards

Fenris

---

### Post by Fenris_rising on 2009-03-06
Hi again

Found the string to add which was;

```
auto eth0

iface eth0 inet dhcp
```

A restart of the network brought up this old chestnut;

```
fenris@Odhinn:~$ sudo /etc/init.d/networking restart
[sudo] password for fenris: 
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:f0:57:1c:6d
Sending on   LPF/eth0/00:c0:f0:57:1c:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
```

Any clues?

regards

Fenris

---

