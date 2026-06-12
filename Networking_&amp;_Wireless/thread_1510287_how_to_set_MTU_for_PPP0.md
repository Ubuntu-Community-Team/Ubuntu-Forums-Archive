---
title: "how to set MTU for PPP0"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by spandey on 2010-06-15
Hi,
My internet works with MTU=1460  for ppp0. I set this up manually using ifconfig. What changes are required so that it is done by default when PPP0 connects or at boot?

---

### Post by spandey on 2010-06-16
anybody help

---

### Post by sapeurcamembert on 2010-06-17
> **spandey said:**
> anybody help
look at file /etc/network/interfaces (root access) for the parameter iface related to your network card (could be eth0 or eth1 or else...) and add the parameter mtu parameter for static route..otherwise use parameter post-up (you must supply the full path of the command). The command executed will be ifconfig with mtu of your choice....

For more and example use man interfaces

---

### Post by Linuxforall on 2010-06-17
MTU can be set easily for your connection via network manager and its permanent setting.

---

### Post by spandey on 2010-06-17
In the Network Manager DSL tab. I changed the MTU value but it's not working. Is there any other way?

---

