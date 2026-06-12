---
title: "dual boot networking doesn't work... unless"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by clowkun on 2009-07-22
so my ubuntu 8.04 dual boot vista will not configure the network device correctly and i'm stuck without a connection to the WWW but if I go to System->Administration->Network and configure the properties of my wired connection from DHCP to IP4 and back to DHCP then the network interface gets reconfigured and i'm online, why is that and what can I do to have permanently working

---

### Post by cariboo on 2009-07-22
What do your /etc/network/interfaces and /etc/resolv.conf look like. If you don't like using the command line, press Alt-F2 and type:

```
gksu gedit /etc/network/interfaces
```

and

```
gksu gedit /etc/resolv.conf
```

Paste the output of the above to commands into your next post.

---

