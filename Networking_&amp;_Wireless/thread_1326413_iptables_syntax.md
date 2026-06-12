---
title: "iptables syntax"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by dvirdc on 2009-11-14
hey

```
ip route add $P0_NET dev $IF0 table T1 
```

does anyone know how do I check what '$P0_NET' and '$IF0' represent on my machine?

cheers

---

### Post by t0mppa on 2009-11-14
That's not from iptables, it's just the newer routing syntax.

> **dvirdc said:**
> ```
ip route add $P0_NET dev $IF0 table T1 
```

does anyone know how do I check what '$P0_NET' and '$IF0' represent on my machine?

For my machine, here are the routes of the main table:```
$ ip route list
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.100  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.0.254 dev wlan0  proto static
```

$P0_NET would be the subnet, like 192.168.0.0/24 and $IF0 the interface used for it, wlan0.

Alternatively you can check **route** or **netstat -r**, but they tell exactly the same thing, just slightly differently.

---

