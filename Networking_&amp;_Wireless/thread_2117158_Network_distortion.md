---
title: "Network distortion"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by amalgamas on 2013-02-17
I run Ubuntu 12.04 kernel 3.2.0-37-generic x86_64 x86_64.  Atheros network card with ath9k driver.  

When another PC on the same workbench is turned on (same ubuntu, Broadcom BCM4313 with wl driver), my network goes down and is totally unstable.  It works without glitches when the other PC is off.

Have anyone had the same experience, and does anyone have any suggestion to solve this issue?

---

### Post by sanderj on 2013-02-18
Do you use DHCP on both PCs?

At the moment both PCs are on, check their LAN IP address (with 'ifconfig').

---

### Post by amalgamas on 2013-02-18
No DHPC, we use fixed ip.  If I let the other PC run, but turn off WIFI (hardware switch), my WIFI is ok.  When I turn it on again, my WIFI fails

---

