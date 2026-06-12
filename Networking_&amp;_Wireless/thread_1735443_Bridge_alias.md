---
title: "Bridge alias"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by gnagnibu on 2011-04-21
Hi guys.
My KVM Server has 2 eth interfaces and I've settep up 2 bridges, br0 and br1.
br0 uses eth0, br1 use eth1.
Every guest has its network interfaces on br1 and eth1 has no link.
Shorewall manage network policies between the two bridges.
I need to setup an alias on br0, so I've tried to edit /etc/network/interfaces in this way

auto br0
iface br0 inet static
        address 192.168.200.108
        netmask 255.255.255.0
        gateway 192.168.200.254
        bridge_ports    eth0
        bridge_stp      off
        bridge_maxwait  0
        bridge_fd       0

auto br0:0
iface br0:0 inet static
       address 10.0.4.6
       netmask 255.255.0.0

auto br1
iface br1 inet static
        address 172.16.200.254
        netmask 255.255.0.0
        bridge_ports    eth1
        bridge_stp      off
        bridge_maxwait  0
        bridge_fd       0


but guest can't reach 192.168.200.x network after this changes.

Any ideas?

---

