---
title: "Will installing compat-wireless remove other drivers?"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by Wiking on 2013-05-17
Hi, if I install compat-wireless drivers will it remove my iwlwifi drivers?

I need to install rtl8187 drivers for my adapter card but would also like to keep the iwlwifi driver as well, I need both.

---

### Post by praseodym on 2013-05-18
No, it will be updated, too.

---

### Post by chili555 on 2013-05-18
If you do driver-select rtl818x and try to *ONLY *update those drivers, then a conflict will be created and iwlwifi will no longer work. I suggest you do not use the driver-select mechanism and update all drivers.

---

