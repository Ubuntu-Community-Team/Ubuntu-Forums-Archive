---
title: "Privoxy+Polipo = dns bug ?"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by ploum on 2008-12-08
Hello,

I've followed the nice and short tutorials there :
[https://help.ubuntu.com/community/DnsmasqPolipoPrivoxy](https://help.ubuntu.com/community/DnsmasqPolipoPrivoxy)

But I've one concern : often, a website will take a lot of time to render and even fails after a timeout.

I've reported the bug here :
[https://bugs.edge.launchpad.net/ubuntu/+source/polipo/+bug/306241](https://bugs.edge.launchpad.net/ubuntu/+source/polipo/+bug/306241)

It really makes polipo unusable so is there anyone that can confirm the bug and/or has an explanation for that ?

Thanks in advance,

Lionel

---

### Post by Alibloke on 2009-01-21
Simply disable ipv6 dns lookups in the config:

```
dnsQueryIPv6 = no
```

Restart polipo and you'll find it working much quicker.

---

### Post by ploum on 2009-01-21
Indeed. Thank you very much :-)

---

