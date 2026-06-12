---
title: "[Server 64bit] Troubles bridging the network"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by b3n0 on 2009-07-04
Hello all,

As a small project, I have decided to set up a web/file server. Using an old computer I had and a cd of Ubuntu 9.04 server 64bit, I'm.... er.... hmmm, well closer to reaching my goal than I was last week. :D

The server connects directly to the router. However I need another computer to connect through the server. The server has one onboard LAN port and a PCI gigabit LAN card.

I have patch Cat5E running to the router and crossover Cat6E running between the 2 machines (Just to cover the basics). 

Here is my interfaces file on the server.
```
# this file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface br0 inet dhcp
bridge_ports all
```

Currently my server cannot connect to the internet (tested with 'ping'). So I typed this interfaces file out manually, sorry if there are any typos.

The machine that is connecting through the server is running Vista 64 bit.

Please help me bridge my network.

Cheers.

---

