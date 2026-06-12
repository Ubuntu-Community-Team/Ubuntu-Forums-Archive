---
title: "Tap/Virtual servers Dropping"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by Meatetarian on 2008-12-09
Hi guys,

I think I've got a good one.

We're running 7.10 Desktop with Virtualbox and several 7.10 servers (modularized so we've got one for hosting, one for DBs, etc) and a Smoothwall firewall directing the bunch.

The problem we're running into is that all of our hosted sites will, intermittently, drop off the face of the earth.

This is based purely on observation, but it seems to go down more often when we're SSH'd into one of the servers from the outside (at which point, we get disconnected from our SSH session and get "Connection Refused" messages until thing come back up).

For a while now, we've thought that Smoothwall was locking everything down, but this seems unlikely, because the connection attempts don't register in any of Smoothwall's logs (or on any of the other virtualized servers).  We're starting to think we may have set things up in a funny way, or that there's some instability in our network, but I have no idea where to start tracking this down from.

Maybe someone here could proof my network/interfaces file and see if there are any obvious flaws?

Any advice would be greatly appreciated.  Thanks!

```

# The loopback network interface
auto lo
iface lo inet loopback

auto tap0
iface tap0 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap4

auto tap1
iface tap1 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap4

auto tap2
iface tap2 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap4

auto tap3
iface tap3 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.0.15
	uml_proxy_ether eth0

auto tap4
iface tap4 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap4

auto tap14
iface tap14 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap14

auto tap15
iface tap15 inet manual
	tunctl_user phoenix
	uml_proxy_arp XX.XX.XX.XX
	uml_proxy_ether eth1

auto tap5
iface tap5 inet manual
	tunctl_user phoenix
	uml_proxy_arp XX.XX.XX.XX
	uml_proxy_ether eth1

auto tap6
iface tap6 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap4

auto tap7
iface tap7 inet manual
	tunctl_user phoenix
	uml_proxy_arp 192.168.10.15
	uml_proxy_ether tap4

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet static
	address 192.168.0.15
	netmask 255.255.255.0
	gateway 192.168.0.5
	bridge_ports eth0 tap3
	bridge_maxwait 0

auto br1
iface br1 inet static
	address XX.XX.XX.XX
	netmask 255.255.255.0
	gateway XX.XX.XX.XX
	bridge_ports eth1 tap5 tap15
	bridge_maxwait 0

auto br2
iface br2 inet static
	address 192.168.10.15
	netmask 255.255.255.0
	gateway 192.168.10.1
	bridge_ports tap4 tap14 tap2 tap7 tap0 tap1 tap6
	bridge_maxwait 0

up route add -net 192.168.10.0 netmask 255.255.255.0 br2

```

---

### Post by Meatetarian on 2008-12-11
Update:

This is definitely a Networking issue.  Either our bridge or tap adapter (br1 or tap5 in the interfaces file) is dying when things go down and eth1 is taking over (not passing packets to tap5).

We can't find any log messages reporting this, or saying what the exact issue is, though.  Does anyone know where to start troubleshooting this?  Do I need to do some reading on how to recompile the network drivers with debug enabled?  Will that tell us anything?

I can post how we determined where the problem lies if anyone's interested, but it was sorta convoluted.

---

