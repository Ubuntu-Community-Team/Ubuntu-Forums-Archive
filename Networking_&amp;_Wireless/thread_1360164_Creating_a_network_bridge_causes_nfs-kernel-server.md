---
title: "Creating a network bridge causes nfs-kernel-server to stop working"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by ronzo on 2009-12-20
When I change /etc/network/interfaces from

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.13
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1

```

to

```
# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

# The primary network interface
auto br0
iface br0 inet static
	address 192.168.1.13
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	bridge_ports eth0
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off

```

and restart networking, nfs-kernel-server stops working. If I try to restart it, nfs-kernel-server does not come up anymore.

I am using Karmic (all updates installed).

Any hints?

---

