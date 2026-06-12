---
title: "Problem with vpnc, gadmin-bind, /etc/resolv.conf"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by pbarada on 2010-05-12
I'm trying to setup a local DNS server on 9.10 to handle name services in my home office network, and I installed gadmin-bind to address my woeful knowledge of bind's syntax/semantics.

I've got my local name server configured enough to resolve external names and /etc/resolv.conf automagically now points to 127.0.0.1 for its nameserver.

So far, so good.

The problem is when I fire up vpnc through NetworkManager, I'd expect it to do what it did before, namely rewrite /etc/resolv.conf to have the nameservers internal to the VPN network listed, but instead, /etc/resolv.conf still has only 127.0.0.1 as the sole nameserver.

As a result I can't resolve any of the machines internal to the VPN.

How can I configure resolvconf/vpnc to update /etc/resolv.conf and add its nameservers ahead of 127.0.0.1?

Thanks in advance!

---

