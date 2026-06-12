---
title: "VPN Kills DNS on Normal Network Connection"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by jbrice on 2009-12-12
This is on a laptop using Jaunty that has a couple of pptp VPN connections that get used once in a while. Yesterday after I had  used the VPN, DNS failed on the regular network connection.

On investigation, the VPN connection is re-writing resolv.conf to set up DNS sources via the VPN tunnel and removing the local DNS. On disconnecting from VPN the original configuration is not being restored.

These VPN connections worked fine when I used them in the past, so what's going on? A bug introduced by updates?

I can re-edit resolv.conf after using VPN to put the correct DNS source back in, but would prefer a proper fix to the problem. Would appreciate any help to resolve this.

---

### Post by iponeverything on 2009-12-12
Might not be the ideal solution, but this link might help:

[http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks](http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks)

---

### Post by jbrice on 2009-12-13
> **iponeverything said:**
> Might not be the ideal solution, but this link might help:

[http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks](http://www.cyberciti.biz/faq/dhclient-etcresolvconf-hooks)

Thanks for the suggestion - but I would prefer to keep my installation as "standard" as possible. However it looks useful and I'll bear it in mind if nothing else comes up.

Surely this must be a bug in Jaunty - I have done nothing other than install the VPN modules,  and set them and use them under the standard network manager?

---

