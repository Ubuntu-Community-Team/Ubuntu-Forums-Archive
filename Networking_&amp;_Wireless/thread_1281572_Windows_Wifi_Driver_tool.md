---
title: "Windows Wifi Driver tool?"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by bantam59 on 2009-10-03
Is ndiswraper still used to install windows wifi drivers? i previouslt used linux mint and noticed there is a windows wireless drivers tool, but i dont see it in ubuntu. when i setup my wifi drivers using ndiswrapper i get a warning msg in a terminal saying:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

BUT when i used the windows wireless drivers tool in MINT i did not get that msg. is that wireless drivers tool a MINT only tool? if not where can i find it for ubuntu

---

### Post by chili555 on 2009-10-03
This warning is harmless. You can fix it with:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```Now does your Windows driver install work better for you?

---

