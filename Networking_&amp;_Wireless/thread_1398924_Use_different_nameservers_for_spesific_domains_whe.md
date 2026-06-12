---
title: "Use different nameservers for spesific domains when connected to VPN"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by geirgp on 2010-02-05
I use Networkmanager to connect to our corporate network using OpenVPN. When I do so, the corporate nameserver is added to the top of /etc/resolv.conf and this means that normal browsing goes slower for other web sites because that nameserver is slower to respond than my ISP's.

I could of course disable the corporate nameserver, but then I am unable to use a lot of the intranet services. All these services are under the domain *.company.local. I am wondering if I can configure /etc/resolv.conf to only use the corporate nameserver for *.comperio.local lookups, and use my ISP's for all other lookups?

Thanks,

Geir

---

