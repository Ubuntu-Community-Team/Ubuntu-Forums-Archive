---
title: "Realtek rtl8192se disappears on ubuntu 11.04"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by Poliseno on 2011-05-24
After having installed ubuntu 11.04 my laptop's wireless device (realtek rtl8192se on a packard bell laptop) disappears on ubuntu 11.04. Before, with ubuntu 10.10, I had no problems.
Now, when I start ubuntu 11.04, sometimes the wireless card work, but most of times it doesn't: the wireless led is off, and with the lspci command I got no line about wireless card. If I restart the laptop and I start win7, the wireless card doesn't work there too! only after many reboots and/or shutdowns wireless card appears again.
Can you help me?
Thanks

---

### Post by chili555 on 2011-05-24
> with the lspci command I got no line about wireless card.Please show me:```
lspci -nn
rfkill list all
```Thanks.

---

