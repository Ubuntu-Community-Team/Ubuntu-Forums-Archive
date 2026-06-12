---
title: "Eth  interface Disabled"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by kanjah on 2013-02-12
Hi guyz, i have hp z800, running on ubuntu 12 amg64, wth two onboard NIC (eth1 and p1p1), the problem is that pinging p1p1 gives high latency and after a restart the p1p1(as shown when i run lshw -C network) is disabled, so i have to reconfigure it again. Running 
lspci -nnk | grep -iA2 eth, shows its present, but missing in /etc/udev/rules.d/70-persistent-net.rules, only eth1 is present. This is really dragging my network, is there a way around this?

---

### Post by Bucky Ball on 2013-02-12
*Thread moved to **Networking & Wireless**.*

---

