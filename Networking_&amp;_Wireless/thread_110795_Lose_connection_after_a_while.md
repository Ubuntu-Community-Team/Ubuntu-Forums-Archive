---
title: "Lose connection after a while"
date: 2005-12-31
forum: Networking &amp; Wireless
---

### Post by EEPS on 2005-12-31
I have a Netgear WG311 v2 with the Ti ACX 111 chipset. It uses the acx_pci driver. It connects fine, but after a while, I lose the connection, while iwconfig still has the MAC of the router, and ifconfig shows I still have an IP. But, I can't ping the router, the only way I have found to reconnect is to restart. Any help?

-thanks

---

### Post by vasudevank on 2005-12-31
i have the same problem, what is you wireless card mine is a dwl-g630

---

### Post by Jeff12088 on 2005-12-31
Same problem, but as long as I keep using the connection, it'll stay alive.

---

### Post by EEPS on 2006-01-03
I have resorted to using ndiswrapper, and it is in fact MUCH more stable than the native driver. It connects instantly and does not lose the connection. I guess the native driver is just to unstable atm. Any way, it works great now.

---

