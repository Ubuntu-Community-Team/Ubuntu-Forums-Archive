---
title: "List of allocated IPs"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by abasel on 2012-03-20
I am Using Server 10.04. How do I get a list of the IP's currently being used or allocated by the DHCP server?

---

### Post by collisionystm on 2012-03-20
> **abasel said:**
> I am Using Server 10.04. How do I get a list of the IP's currently being used or allocated by the DHCP server?


/var/cache/dhcp maybe dhcp3

I think

Not on my system right now ;)

---

### Post by raja.genupula on 2012-03-20
may be this ?
```
tail -n 15 /var/lib/dhcp3/dhclient.*.leases
```

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

---

### Post by collisionystm on 2012-03-20
There you go.....


/var/lib/dhcp3/dhcpd.leases

---

### Post by abasel on 2012-03-20
Excellent... from here I can see that the DHCP is not getting in hostnames which means they don't resolve... and ideas where I can look?

---

### Post by collisionystm on 2012-03-20
> **abasel said:**
> Excellent... from here I can see that the DHCP is not getting in hostnames which means they don't resolve... and ideas where I can look?

Your DHCP server needs to be using the same DNS as your machines

---

