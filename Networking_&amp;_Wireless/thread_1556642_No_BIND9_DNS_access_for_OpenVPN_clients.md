---
title: "No BIND9 DNS access for OpenVPN clients"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by sbw87 on 2010-08-19
Hi,
I have configured a BIND9 DNS server for my local zone 192.168.100.0, as well as an OpenVPN server that gives clients IP addresses in the range 10.8.0.0.
When Ubuntu clients connect to the VPN, they get the address of the BIND DNS server via the "push" option. But the DNS server obviously doesn't work for those VPN clients.

Instead of proper records the VPN client gets:

```
;; WARNING: recursion requested but not available
```

This is independent of whether the VPN clients ask for a record the DNS server is authoritative for (i. e., my local clients) or for some other server in the world.

I simply can't figure out where the problem is and am looking forward to your answers.
Thanks so much!

---

