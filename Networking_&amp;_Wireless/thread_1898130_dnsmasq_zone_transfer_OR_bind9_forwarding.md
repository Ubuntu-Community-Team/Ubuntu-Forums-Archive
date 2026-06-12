---
title: "dnsmasq zone transfer OR bind9 forwarding"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by MichiGreat on 2011-12-20
**Hi!**

I currently have a configuration like this:

192.168.1.1 (DNS of the local network): dnsmasq forwards queries for specific local domains to 192.168.1.2, queries for an "ip6.arpa." zone to bind9 that runs on port 5301, and the remaining queries to my ISP's DNS.

My goal is to enable specific hosts to do a zone transfer from my DNS server. But dnsmasq refuses to do so.

So, there are two possibilities:

1. Configure dnsmasq to allow zone transfers to specific IP addresses (IPv4 and IPv6).
2. Get rid of dnsmasq and configure bind9 to ask 192.168.1.2 for the domains I specify.

Any ideas how to realise one of them?

Greetings

*Michael*

---

