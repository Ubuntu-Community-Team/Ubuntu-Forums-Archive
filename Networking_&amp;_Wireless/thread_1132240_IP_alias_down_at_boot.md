---
title: "IP alias down at boot"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by gecka on 2009-04-21
Hello, 

I use jaunty server. Here is my /etc/network/interface

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 202.0.0.6
	netmask 255.255.255.0
	network 202.0.0.0
	broadcast 202..0.0.255
	gateway 202.0.0.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 202.0.1.28
	dns-search com

auto eth0:0
iface eth0:0 inet static
	name ns2.myhost.com
	address 202.0.0.5
	netmask 255.255.255.0
	network 202.0.0.0
	broadcast 202..0.0.255
	gateway 202.0.0.254

After each boot I need to do "ifup eth0:0". How can I have it up after reboot?

Regards

---

