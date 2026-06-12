---
title: "My IP address reverts to IPV6 when restart, even when i have a static IPV4 address co"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by rohitmp on 2008-12-03
HI Guys,

Current OS:Ubuntu8.04
kernel: 2.6.24-22-rt

The problem is, i have installed VirtualBox2.0.2 so to allow the guest os connect to outside world,
i created host interface (bridging mode)
set up a bride on host. (ipaddress being 192.168.1.249)
I gave the static ip address (192.168.1.250) for host network card.

Now when i restart the host OS, everytime my HOST ipv4(192.168.1.250) address vanishes. It picks up a IPV6 address (i dont know from where) for the network card at the restart.

how do i make my host n/w card use 192.168.1.250 even after restart.

my /etc/network/interfaces is as follows

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1

auto br0
iface br0 inet static
    address 192.168.1.249
    netmask 255.255.255.0
    gateway 192.168.1.1
    bridge_ports eth0 vboxeth0 vboxeth1 vboxeth2

my /etc/vbox/interfaces is as follows

# <interface name> <user name> [<bridge>]
vboxeth0 rohitmp br0
vboxeth1 rohitmp br0
vboxeth2 rohitmp br0

please let me know how to fix the issue. Any help would be much appreciated.

Thanks,
rohitmp

---

