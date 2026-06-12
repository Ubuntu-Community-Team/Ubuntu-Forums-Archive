---
title: "Problem with two subnets seeing each other (two NICs)"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by kasparof on 2013-03-16
My network configuration looks like the attached image.
I am using a switch that connects to an ADSL modem running DHCP for the 192.168.2.0 network.
On the server pc that has two network interfaces, eth0 has statically assigned 192.168.2.3 IP
and eth1 192.168.1.1. 

After using firestarter i was able to share internet connection and the pc with IP 192.168.1.100 
is able to "see" every other pc on the network but any pc on 192.168.2.0 network cannot "see" 
this one, except server pc that is physically connected on both subnets.

Any ideas on how to route traffic from 192.168.2.0 subnet to 192.168.1.0 subnet?
And if possible, without having to touch the ADSL modem-router.

my /etc/network/interfaces 

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.2.3
    netmask 255.255.255.0
 network 192.168.2.0
 gateway 192.168.2.1
        dns-nameservers 192.168.2.1
        
auto eth2
iface eth2 inet static
    address    192.168.1.1
    netmask    255.255.255.0
        network 192.168.1.0
        gateway  192.168.2.1
        dns-nameservers 192.168.2.1

and my routing table ( route -n )

> Kernel IP routing table
 Destination              Gateway                 Genmask                 Flags   Metric   Ref     Use   Iface
 192.168.2.0             0.0.0.0                   255.255.255.0      U          0               0           0       eth0
 192.168.1.0             0.0.0.0                   255.255.255.0      U          0               0           0       eth2
 0.0.0.0                       192.168.2.1         0.0.0.0         UG                    100          0           0       eth0

Thanks!

---

