---
title: "DNS search suffix and DHCP"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by Djense on 2010-02-03
Hi,

My network uses DHCP from a Cisco router and internal DNS installed on 8.04 server with Bind9 for the static IPs.
I would like to set it up so that all clients getting their IP from the DHCP server automatically search the right domain suffix (similar to add 'search domain.com' in /etc/resolv.conf).

Should this be done on the DHCP server ? DNS server ?
I know it can be done manually on the machine itself, but I would prefer to avoid that if possible...

Thanks

---

### Post by Iowan on 2010-02-03
From **man dhcp-options**:> option domain-name text;
This  option  specifies  the domain name that client should use when resolving hostnames via the Domain Name System.
Dunno if this is the option you're looking for... the standard */etc/dhcp3/dhclient.conf* contains a "domain-name" in the request line...

---

