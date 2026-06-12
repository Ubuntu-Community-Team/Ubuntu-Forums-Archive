---
title: "dhclient -6 hangs"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by snowkinguk on 2012-06-30
I have IPv6 autoconfiguration configured on my router which also supplies IPv6 name servers.  This works fine on my Windows 7 box (I get both IPv4 & IPv6 nameservers) but I only see IPv4 server in /etc/resolv.conf on my 12.04 Ubuntu box.  I get assigned IPv6 addressing just no IPv6 name servers.

When I try:

dhclient -6 eth0 (Or br0) it just hangs

When I look at a network trace I see DHCP-SOLICIT and DHCP-ADVERTISE repeated over and over until I control-C

I can see the DNS name server in the Advertise.  Any ideas?

Thanks

---

### Post by lemming465 on 2012-10-16
I don't know if you have resolved this already, or not.  A couple of points, in case you haven't.

(1) what does **sudo rdisc6 eth0** show in the way of router advertisement flags?  If the *managed* flag is off and the *other* flag is on, you are in the autoconfigured address / static DHCP case and there isn't a DHCPv6 lease (Request and Reply messages), just DHCPv6 options.

(2) As of ubuntu 12.04, /etc/resolv.conf is being rewritten by *resolveconf*, which in turn is typically being fed from *dnsmasq*.  It's now normal for /etc/resolv.conf to only contain the IPv4 loopback address (over which IPv6 AAAA queries can be made just fine).  Check e.g. /var/run/nm-dns-dnsmasq.conf to get a better idea where the DNS queries are actually going.

(3) if you are in the static DHCP case, you could probably prevent *dhclient* from hanging indefinitely by using the -S option for sending information-request queries instead of solicit queries.

I'm not sure what the behavior of Ubuntu is in the presence of both DHCPv4 and DHCPv6 DNS server options.  It might only plan to use the v4 ones in that case.

---

