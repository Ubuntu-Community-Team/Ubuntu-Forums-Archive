---
title: "Ip4 &amp; ip6"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by tomski on 2009-07-22
Hi there,

was hoping you guy's could help me out
i have been trying to find some info/howto on configuring 1 single interface with IP4 & IP6 addresses concurrently just like you can with vista & xp

some people call this a 'Dual Stack'

but when i google the question all i see is advice on either setting up a 6to4 tunnel or just using either ip4 or ip6 

i want to use both at the same time on the same interface!

yes i have already setup a tunnel but my endpoint for that is my m0n0wall box, the tunnel i have is via hurricane electronics & i have my own /48 routed down that tunnel (all for free@ [http://www.tunnelbroker.net](http://www.tunnelbroker.net))

---

### Post by Brandon Williams on 2009-07-24
I think that you can make this work by simply adding the necessary entries in /etc/network/interfaces. I believe that it will accept and properly handle multiple intries for a single interface, provided that they specify different network types.
```
auto eth0
iface eth0 inet static
  options for ipv4 address go here ...
iface eth0 inet6 static
  options for ipv6 address go here ...
```
If that doesn't work, then you might be able to use an alias interface for one or the other.
```
auto eth0 eth0:0
iface eth0 inet static
  options for ipv4 address go here ...
iface eth0:0 inet6 static
  options for ipv6 address go here ...
```

For more information, check 'man interfaces' and 'zless /usr/share/doc/ifupdown/network-interfaces.gz'.

---

### Post by gombadi on 2009-07-24
```

human@ds2-uk:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 96.39.83.70
	netmask 255.255.255.0
	network 96.39.83.0
	broadcast 96.39.83.255
	gateway 96.39.83.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 75.75.4.58
	dns-search example.com
iface eth0 inet6 static
	address 2001:3f8a:0:6:5d59:5046:2b8a:1d4b/64
	netmask 64
	gateway 2001:3f8a:0:6::1

```

---

### Post by tomski on 2009-08-06
thnx for this guys
i'll try tonight & post back results
:D

---

### Post by tomski on 2009-08-10
yep that worked thnx for this

---

