---
title: "2 NICs, one cable modem, one router, zero success"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-08-13
Recently my Internet connection began dying at random, several times per day.  Boy did that get old quickly.

My problem seems to lie in the router, a Netgear WNR 3500 v2.  For now, I am connecting directly to the cable modem (Motorola SB6120 via eth1) to get to the Internet.  My machine has two wired, 1 gigabit NICs built in, so I am trying to use the other NIC (eth0) to connect the router. 

For some reason, I cannot access the router, even though it is physically plugged into the second NIC and the NetworkManager applet shows a live connection on both eth0 and eth1.

For example, if I direct Firefox to the router's address, which was always 192.168.1.1, I get a "Loading..." message for a long time, and eventually the "The connection has timed out" error page.  Similarly, pinging 192.168.1.1 at the command line results in 100% packet loss.

I currently have eth0 configured as "Link-Local Only."  Results are the same if I try "Shared" or "Automatic (DHCP)".  Right-clicking on the NetworkManager icon in the notification area, then selecting Connection Information, shows both connections as active.  But clearly the eth0 connection is not working.

I know someone will ask for it sooner or later, so here is the output of **ifconfig -a** and **sudo lshw -C network**:

```
objekt910@objekt910-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          inet addr:169.254.3.107  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::222:15ff:fe2f:4f11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1485627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1313830 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:757824238 (757.8 MB)  TX bytes:1314447484 (1.3 GB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet addr:174.56.116.159  Bcast:174.56.119.255  Mask:255.255.252.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18064781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13381392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14618997087 (14.6 GB)  TX bytes:5106880051 (5.1 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1572645 (1.5 MB)  TX bytes:1572645 (1.5 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

objekt910@objekt910-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 12
       serial: 00:22:15:2f:4f:11
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=169.254.3.107 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:285 memory:fe9fc000-fe9fffff ioport:d800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 12
       serial: 00:22:15:2f:4e:b5
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=174.56.116.159 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:286 memory:fe8fc000-fe8fffff ioport:c800(size=256) memory:fe8c0000-fe8dffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

So what's the deal?

This router worked fine from when I bought it this February until the last week or two.  It's had the same firmware all that time, so I don't think a firmware upgrade is going to fix it.  That is, assuming I can ever get to the router's Web interface to try a firmware upgrade!

I have found a few references to this router dropping wireless connections with earlier firmwares, but nothing about it dropping wired connections.  I only use its wireless capabilities with 1 of our 3 machines, anyway.

---

### Post by confusedstingray on 2010-08-15
just an idea try to have your machine in the same subnet as the router 
if router is 192.168.1.1 set you ip of your machine to 192.168.1.5 
then try to get to the router.

from the ifconfig  it looks like you are trying to  use your machine as a router?
is this what your are trying to do ?

if you want to by pass the router temporarily
set your machine to DHCP it will get a address from the modem

if you do by pass the router you might want to setup gfw and clamav 
these are a gui firewall and antivirus

---

### Post by Iowan on 2010-08-15
I haven't (yet) really studied **link-local**, but [this]("http://en.wikipedia.org/wiki/Link-local_address") suggests they are only for local communication.

You've probably already done so, but make sure a static address is outside the range used by the DHCP server.

---

