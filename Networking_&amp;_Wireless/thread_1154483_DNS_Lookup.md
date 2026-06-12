---
title: "DNS Lookup"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by drt1245 on 2009-05-09
I have a DNS Sever running on my dd-wrt router (DNSmasq). On 2 Macs and 1 Ubuntu computer (using NetworkManager) on my network, I can use the configured hostnames instead of IP addresses. However, on my 8.10 Ubuntu Sever, I cannot use hostnames.

I have my router's IP specified in */etc/resolv.conf* (nameserver 192.168.1.1).

Running *host* or *nslookup* returns the correct information about the hostnames, but when I try and actually use it (with *ping*, *ssh*, *elinks*, etc) it fails.
i.e.:```
$ ping hostname
ping: unknown host hostname
```Any ideas?

---

