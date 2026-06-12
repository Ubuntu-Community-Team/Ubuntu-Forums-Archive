---
title: "Realtek 8111E Gigabit LAN controller"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by wdh1974 on 2011-10-07
This is a re-post but i wanted to ask aobut fixing my LAN drivers if they vanish again.

Last time i had ubuntu installed it was fine till the next morning when the build in network card stopped working.

It's a Realtek 8111E Gigabit LAN controller and i have limited to no net access aside from this computer.

Are there simple steps to fix this since it's working on the fresh install but stopped the next day?

I can copy and paste any commands to a flash drive, as it seems this will be a simple fix.

---

### Post by praseodym on 2011-10-07
Hi,

please show:

```
lspci -nnk | grep -iA2 net
uname -a
lsmod
```

---

