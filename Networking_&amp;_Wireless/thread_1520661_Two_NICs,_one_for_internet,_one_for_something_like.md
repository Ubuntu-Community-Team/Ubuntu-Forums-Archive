---
title: "Two NICs, one for internet, one for something like local link"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by ambivalentduck on 2010-06-29
I need to get networking working for the following layout:

2 NICs.
One connects to the internet
One connects using a crossover cable to an xPC target machine.
-IP address 192.168.0.2, port 22222, all communication over UDP.


How do I set this up so that all requests for that address are routed through one NIC while everything else goes through the other?

---

### Post by ambivalentduck on 2010-07-06
Solved using info from here: [http://ubuntuforums.org/showthread.php?t=812222](http://ubuntuforums.org/showthread.php?t=812222)

Basically, network manager is completely unsuitable for this since when it sees eth0 and eth1, it assumes both should have a default gateway which leads to "where do I send it?"

Knock out both of these and instead edit /etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.252
network 192.168.1.0
broadcast 192.168.1.255

To save you some time, you'll probably want the netmask 255.255.255.0.  The 252 on the end of mine is specific to the case where you only want 2 computers on the subnet.  Everything else should be braindead substitution.  Oh, and ubuntu automatically tries to tie a nic card to a eth#.  So don't worry about doing anything fancy there.

---

