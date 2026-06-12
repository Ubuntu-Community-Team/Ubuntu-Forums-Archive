---
title: "Domain Resolving"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by kazza on 2013-02-19
Hi,

Im having a strange issue with domains. I have just set up ubuntu 12.10 on a domain, but I am having issues when resolving local fqdn's.

For instance, when I ping intranet.X.local I get an error message saying that the host is unknown. Yet when I do 'host intranet.X.local' it resolves it to the correct ip address.

When I do 'hostname -fqdn' it yields the correct name, i.e. pcxyz.X.local.

Yet when I do domainname I get (null).

Is there something obvious that I have overlooked, perhaps with configuring the resolver?

Thanks,
kazza

---

### Post by kazza on 2013-02-19
ah, I forgot to mention that I have no problem ping'ing the unqualified names. 

In the example above 'ping intranet' works ok.

---

