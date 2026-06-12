---
title: "Wireless Bridge no DHCP"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by akester on 2011-03-30
I have a bit of a weird problem.  I am trying to configure an external wireless bridge for a few systems to replace a very long, duct taped cable.

I have it set up and it is connecting, at least I can see the pfsense router on the other side and ping any machine in the network.

Here's the issue, I cannot get dhcp to work across the link. I set a static address (dns servers and all) but when I try to ping google i get "Network is Unreachable"

I'm not sure where to look for the problem.

Thank you for any help

---

### Post by patryk77 on 2011-03-30
Please post the output of the following two commands:

```
ifconfig

route -n

```


Cheers!

---

