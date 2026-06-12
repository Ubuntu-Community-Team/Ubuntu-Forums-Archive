---
title: "can't access server using domain name"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by cybercity@localhost on 2012-04-26
i cannot access my server using domain name on local network. i have configured my /etc/hosts file but yet it's not working this is how my hosts file looks,

```

127.0.0.1    qambrani.net    qambrani localhost.localdomain localhost    localhost4

::1        qambrani.net    qambrani    localhost6.localdomain    localhost6

```i can access this server by it's ip address but in browser whenever i type qambrani.net it shows server not found. :(

---

### Post by chrtr on 2012-04-26
> **cybercity@localhost said:**
> i cannot access my server using domain name on local network. i have configured my /etc/hosts file but yet it's not working this is how my hosts file looks,

```

127.0.0.1    qambrani.net    qambrani localhost.localdomain localhost    localhost4

::1        qambrani.net    qambrani    localhost6.localdomain    localhost6

```i can access this server by it's ip address but in browser whenever i type qambrani.net it shows server not found. :(
You need DNSMasq or a DNS Server in order to be able to use the hostname on any other computer other than the local one. The hosts file only applies to the local computer.

---

### Post by cybercity@localhost on 2012-04-27
how do i setup dns or MasqDns to resolve hostname of my server?

---

### Post by cybercity@localhost on 2012-04-27
one more thing i would to tell that the DNS nameservers are retrieved dynamically from DHCP and PPoE server from my isp.

---

