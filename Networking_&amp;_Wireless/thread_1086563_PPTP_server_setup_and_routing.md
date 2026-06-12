---
title: "PPTP server setup and routing"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by RayVad on 2009-03-04
Trying to get my PPTPServer running i got some issues, which are hard to figure out.

My setup is like this:
> 
--- dsl-p4 -- vpn eth1 -- PPTPserver -- lan eth0 -- dsl-p1---

eth0 = 192.168.6.10 (gateway 192.168.6.1)
eth1 = 10.10.0.10  (gateway 10.10.0.254) this subnet is in DMZ
dsl-p1 = router port 1 configured for local lan (192.168.6.0/24)
dsl-p4 = router port 2 configured for vpn connections (10.10.0.0/24)
VPN clients will have ipadresses in the range 192.168.6.150-159

The routing is default like this on the server.
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.6.150   *               255.255.255.255 UH    0      0        0 ppp0
192.168.6.0     *               255.255.255.0   U     0      0        0 eth0
10.10.0.0       *               255.255.255.0   U     0      0        0 eth1
default         dsldevice.lan   0.0.0.0         UG    100    0        0 eth1
default         dsldevice.lan   0.0.0.0         UG    100    0        0 eth0

1) There seems to be somwething wrong with routing, since i cant make connections to internet from the server itself over eth0. Lan connection over eth0 is no problem en works fine. How should the network be configured? Should every nic has its own gateway configured? Bringing down eth1 results in a good connection to internet over eth0.
My nic setup:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# LAN side NIC of POPTOP Server
auto eth0
iface eth0 inet static
        address 192.168.6.10
        netmask 255.255.255.0
        network 192.168.6.0
        broadcast 192.168.6.255
        gateway 192.168.6.1

# WAN side NIC of POPTOP Server
auto eth1
        iface eth1 inet static
        address 10.10.0.10
        netmask 255.255.255.0
        broadcast 10.10.0.255
        gateway 10.10.0.254



Do i need for both nics a gateway?
It seems that if i don't configure the gateway for eth1, it doesn't accept connections.

---

