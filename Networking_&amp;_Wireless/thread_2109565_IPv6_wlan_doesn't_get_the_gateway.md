---
title: "IPv6 wlan doesn't get the gateway"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by jalalmint on 2013-01-27
hi
I have a wireless router configured with IPv6
my linux connects well but it does not get a gateway
thus no internet connection is available
my windows 8/7 connects well
any help?
):P

---

### Post by lemming465 on 2013-01-30
In IPV6 the only way to get a native gateway is from the link-local address of the router in an ICMPv6 router advertisement; it's not an option inside RA's or via DHCPv6.  Try running *rdisc6 wlan0* (or whatever your network uplink is), and see if you can provoke any RA's by sending router solicitations to ff02::2 (all-routers multicast).

Windows since Vista will aggressively use tunnels to get IPv6.  If you visit somewhere like *[http://ipv6.he.net/](http://ipv6.he.net/)* which will tell you your source IP, is it a 2001:0::/32 Teredo series address or a 2002::/16 6to4 series address?  Those are tunneled, not native.

---

