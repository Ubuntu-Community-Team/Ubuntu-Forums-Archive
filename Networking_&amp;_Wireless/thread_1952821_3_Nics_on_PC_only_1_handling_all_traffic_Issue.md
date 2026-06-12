---
title: "3 Nics on PC only 1 handling all traffic Issue"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by banshee10000 on 2012-04-05
Hey guys, I have a strange Problem.

I have a Lucid LTS PC, with 3 Network cards installed. All of em are working
But here is the issue.

eth0 is my onboard.
eth1 is a pci DLink
eth2 is also a pci DLink 

Both D-Links are the same moddels
[B]
My /etc/network/interfaces file:[/B]
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.11
network 192.168.1.0
broadcast 192.168.1.255

auto eth1
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.11
network 192.168.1.0
broadcast 192.168.1.255

auto eth2
iface eth2 inet static
address 192.168.1.13
netmask 255.255.255.0
gateway 192.168.1.11
network 192.168.1.0
broadcast 192.168.1.255


```And my **/etc/udev/rules.d/70-persistent-net.rules**
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1969:0x1063 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="bc:ae:c5:32:ab:bb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1186:0x4300 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="14:d6:4d:11:0d:36", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x1186:0x4300 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="14:d6:4d:11:0c:94", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


```Now when I Unplug eth0 with address 192.168.1.11
i can still connect / ping 192.168.1.11 and connect to ssh but it goes through eth1

same with unplugging eth2 i can still ping 192.168.1.13 and connect to it.

But when i unplug eth1 (192.168.1.12) nothing works anymore

So it looks like all network traffic comes in through eth1 its like eth1 has 3 ip's assigned to it. How can i fix this ....

I would like for it to be:
eth0 = 192.168.1.11 apache, samba, dnsmasq and ssh only
eth1 = 192.168.1.12 only ptokax hub1
eth2  = 192.168.1.13 only ptokax hub2

This is to divide certain apps up on spread the load on certain Nics
if one nic goes down then that IP shouldn't be available anymore
in other words Binding static IPs to respected Nic's and not have them bleed over


My ptokax,  apache, ssh, dnsmasq and samba is already bound to the Nics i want but it still created like a failover or something

Any Help ?

P.S This is only for a LAN not internet use :)

---

### Post by banshee10000 on 2012-04-05
Nobody out there with an Idea on this issue ?

---

