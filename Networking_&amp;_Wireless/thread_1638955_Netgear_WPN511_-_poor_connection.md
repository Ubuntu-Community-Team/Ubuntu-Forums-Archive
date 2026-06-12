---
title: "Netgear WPN511 - poor connection"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by hertzog on 2010-12-06
Just installed Xubuntu 10.10 onto a laptop using a chinese-made Netgear WPN511 wireless card to provide network connection. Drivers for card installed as part of Xubuntu installation process.

If you are finding that on a fresh install you get intermittant connection faults including pages only partially loading, sometimes fully loading on hitting refresh, some pages slow loading, and some sites completely inaccessible, it might be worth your while checking if the fault lies with the driver.

In my case,the default Atheros driver was causing the problem, and installing ndiswrapper and the original Netgear Windows 2000 version of WPN511.sys fixed everything.

---

### Post by pricetech on 2010-12-06
Mark your thread "solved" so more folks will see it as a solution.

---

### Post by hertzog on 2010-12-06
> **pricetech said:**
> Mark your thread "solved" so more folks will see it as a solution.

Thanks, pricetech - done!

---

