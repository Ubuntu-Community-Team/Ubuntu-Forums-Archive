---
title: "dnsmasq problem"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by solidwinter on 2010-02-04
I setup a dnsmasq server, configured it, and so forth but cannot resolv names on any other computer except for the computer its running on...

I checked the dnsmasq.conf to make sure its running on the right interface and checked netstat to make sure it was listening, all seems fine.

Only settings enabled in dnsmasq.conf are
domain-needed
bogus-priv
expand-hosts

the rest beyond that are commented out.

My resolv.conf is default with
nameserver 127.0.0.1

edit: and all the clients have there dns set to dnsmasq server, which is 10.0.0.1

---

### Post by Iowan on 2010-02-04
Looks pretty much like mine - you mentioned having the **interface=** line with the right interface. My server also has the **domain=** line active - and my domain is listed in the **search** line of */etc/resolv.conf*. 
Are you also using it as DHCP Server?

---

### Post by solidwinter on 2010-02-05
Na, I use DHCP3-Server as my dhcp.

I've never had to worry about the domain line and this configuration usually works.  I feel that it might be caused by have a NAT setup with two interfaces, and one of those gets its dhcp settings from a router (internet)

---

### Post by solidwinter on 2010-02-06
bump

---

