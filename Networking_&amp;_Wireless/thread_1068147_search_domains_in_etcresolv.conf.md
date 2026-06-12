---
title: "search domains in /etc/resolv.conf?"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by chengt on 2009-02-12
I currently use:

```

supersede domain-name "foo.com bar.com";

```

in /etc/dhcp3/dhclient.conf to get

```

search foo.com bar.com

```

in my /etc/resolv.conf

Does anyone know the equivalent for this in dhcp6c.conf?
I can't seem to find any way to set this.

---

