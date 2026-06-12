---
title: "Static Ip problem in Jaunty"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by spidermaniac2 on 2009-04-30
Hi,
I cant set static IP(local) for my pc.
In 8.10, changing etc/network/interfaces file was enough? wasnt it?
I upgraded 8.10 to 9.4, and all configurations are default now.
So I changed my interfaces file. but still cant
It looks like;
```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.254
auto lo
iface lo inet loopback

```
my ifconfig outputs;
```
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:d0:4e:06  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fed0:4e06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6812763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4650926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1556797997 (1.5 GB)  TX bytes:363551413 (363.5 MB)
          Interrupt:251 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10772810 (10.7 MB)  TX bytes:10772810 (10.7 MB)

```

I want to change my ip to 192.168.1.100
And I connect my routers page by typing 192.168.1.254
What should I do? Do I have remove network-manager?
I dont think so because I had not removed any stuff from 8.10, and It was working..

---

### Post by Iowan on 2009-04-30
As I recall, 8.10 was (at least initially) somewhat of a bear to get static IP to work properly.  It wasn't as simple as editing */etc/network/interfaces*. There were several How-To's/workarounds, but I don't remember if I ever saw a bullet-proof, cure-all fix.

---

