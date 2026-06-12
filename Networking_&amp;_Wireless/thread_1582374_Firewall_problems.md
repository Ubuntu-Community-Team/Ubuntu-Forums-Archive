---
title: "Firewall problems"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by canoemoose on 2010-09-26
Hi all.

I'm having some interesting issues on my network.  I have a Ubuntu box acting as a firewall and router, sharing its internet connection with the rest of my network.  The machine is running dnsmasq configured as a local DNS and DHCP server.
I've tried to use Firestarter to set up the connection sharing but have run into an interesting issue - when the firewall is running, my network gets Internet access (as expected) but the server itself can't - I can ping and do DNS lookups, but not actually visit any address in Firefox.  It's not browser-specific - nothing on this machine can access the Internet.  If I stop the firewall, the rest of the network loses Internet access (again, as expected) and the server gets it back.
I'm not using Network Manager as it doesn't play nicely with dnsmasq and have configured my devices in /etc/network/interfaces.

I know the "done thing" is to not use Firestarter, but as non-technically minded people have to administrate this machine when I'm not here, unfortunately it's necessary.

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.12.1
netmask 255.255.255.0
gateway 0.0.0.0
```

Output of route -n: (Firewall not running, server has Internet access - this doesn't change when the firewall is running)
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

The server connects to the local network on eth1 and to the Internet via eth0.

Any ideas?

---

### Post by canoemoose on 2010-09-26
Further to my post above, I've uninstalled Firestarter and have got the NAT working with the iptables rule:```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

However, this still leaves the problem of me having no easy way of editing my firewall rules.

I'd like to have some graphical program which allows me to see what on my network is using the Internet, easily allows certain traffic into my network (OpenVPN for example) and allows a non-technical user (my mother) to block a certain host's internet access.

Firestarter would seem to have all of these benefits, if it were to allow the gateway machine internet access while running.

](*,)

---

### Post by canoemoose on 2010-10-23
I solved it, and it's now working as intended.
It would appear the option "Block broadcasts from external network" should be relabelled "Stop everything working properly".

---

