---
title: "DHCP don't connect at boot"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by rompstar on 2009-05-16
Hi,

I got Ubuntu 9.04 server installed.  Something weird has happened, from a restore. Now my network don't work.  When I type sudo dhclient, then a network space is assigned and I get this:

[B]ifconfig
eth2      Link encap:Ethernet  HWaddr 00:00:1a:1a:a9:e7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:1aff:fe1a:a9e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:399848 (399.8 KB)  TX bytes:99175 (99.1 KB)
          Interrupt:31 

eth3      Link encap:Ethernet  HWaddr 00:00:1a:1a:a9:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

eth3:avahi Link encap:Ethernet  HWaddr 00:00:1a:1a:a9:e8  
          inet addr:169.254.7.175  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4880 (4.8 KB)  TX bytes:4880 (4.8 KB)

pan0      Link encap:Ethernet  HWaddr 0a:d5:d4:1a:3a:4d  
          inet6 addr: fe80::8d5:d4ff:fe1a:3a4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5586 (5.5 KB)

pan0:avahi Link encap:Ethernet  HWaddr 0a:d5:d4:1a:3a:4d  
          inet addr:169.254.5.53  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
[/B]


inside my file here are it's contents:

sudo pico /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet dhcp




anyways, I am not sure what I am doing wrong, I want DHCP to work automatically, is there something else that I need to check ?

---

### Post by pbpersson on 2009-05-17
Apparently the server was given an address on eth2

Can you ping 192.168.0.1?

What exactly is the problem?  It appears that everything is setup okay.

What happens when you ping [www.ubuntu.com?](www.ubuntu.com?)

---

### Post by rompstar on 2009-05-17
The problem is that I have to type the command: sudo dhclient after I boot into the system to have a network, it won't work automatically, that's the problem :- )

Any ideas ?

Once I issue the command, everything works, but not until then.

):P

---

### Post by Iowan on 2009-05-18
Is eth3 connected to a different network (than eth2)? 
Eth3 does not appear in your */etc/network/interfaces *.

---

