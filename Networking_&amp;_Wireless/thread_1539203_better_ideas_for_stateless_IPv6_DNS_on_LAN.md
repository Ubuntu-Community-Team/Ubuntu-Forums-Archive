---
title: "better ideas for stateless IPv6 DNS on LAN?"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by abrahamsmith on 2010-07-26
In the IPv4 world, a DHCP server gives addresses to clients, and then records their hostname/IP locally.  This hostname/IP can then be passed on to the authoritative DNS server for a domain, so those hostnames can be addressed directly.  (On a LAN, this is often all handed by dnsmasq.  dnsmasq usually doesn't face the whole world, but it can.)

I want this effect for IPv6 using "stateless" radvd and not DHCPv6.
My quick question is:  to populate the DNS server, can anyone think of a better way than running this command every few minutes?

```

$ avahi-browse -at -d local  | grep Workstation | cut -d\  -f 4 | sort -u | while read a; do avahi-resolve -6 -n "${a}.local"; done;
albus.local     fe80::202:6fff:fe5b:5987
isis.local      2001:470:xxx:xxx::
laptop.local  2001:470:xxx:xxx:20b:5dff:fec5:45e4

```

or, watch this command

```

$ avahi-browse -r -p  _workstation._tcp | cut -d\; -f 7,8
albus.local;fe80::202:6fff:fe5b:5987
isis.local;2001:470:xxx:xxx::
laptop.local;2001:470:xxx:xxx:20b:5dff:fec5:45e4

```

Then, of course, grep for the addressable ones  (2001:...), stripping the ".local", and inserting them as AAAA records?

---

