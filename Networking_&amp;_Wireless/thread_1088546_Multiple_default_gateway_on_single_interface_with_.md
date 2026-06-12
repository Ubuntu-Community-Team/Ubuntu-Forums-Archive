---
title: "Multiple default gateway on single interface with failover?"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Turbo Donkey on 2009-03-06
Is there any way I can have a single interface (eth0, 192.168.254.254) with 2 default gateways, say 192.168.254.1 and 192.168.254.2, and have failover working on these gateways?

Cheers :)

---

### Post by puppywhacker on 2009-03-06
If you want to do it in an advanced way use "tc" traffic control. If you want some whacky script solution look at the link

[http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/](http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/)

---

