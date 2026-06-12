---
title: "How to print DNS zone information in BIND?"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by malice930 on 2011-02-06
Hello,

Is there a way to show \ print all zones and associated records in BIND?

Thank You

---

### Post by SeijiSensei on 2011-02-07
You mean other than simply listing the contents of named.conf and the zone files?  It's easy to list the zones 
```
grep 'zone' named.conf
```

If you want just the domains, use
```
grep 'zone' named.conf | awk '{print $2}' | sed 's/"//g'
```

I don't know any way to enumerate all the hosts in a domain by a single command.  "host -t any domain.name" will return SOA, MX, and NS records, but no A or CNAME records for individual hosts.  The "dig" utility seems to work the same way.

---

