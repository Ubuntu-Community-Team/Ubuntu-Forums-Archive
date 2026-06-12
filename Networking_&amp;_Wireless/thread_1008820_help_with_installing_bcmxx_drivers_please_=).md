---
title: "help with installing bcmxx drivers please =)"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by soloengineer on 2008-12-11
hi! i accidentally installed the 64 bit and after a year of crashes (im not that smart!) i had my tech friend tell me to install the 32 bit. now that i have, i cant get my wifi working...? how do i get those drivers to work? i used something ndis or something before but i cannot get a fix on exactly how to make it work, im a layman so please be simple =) thanks yal!

---

### Post by Ayuthia on 2008-12-12
If you are using Hardy or Intrepid and have a working internet connection in Ubuntu, then you can go into System->Administration->Hardware Drivers and activate the Broadcom b43 driver.  Otherwise, can you go into a Terminal and post the results of:
```
uname -a
lspci -nn
lsb-release
```

---

### Post by superprash2003 on 2008-12-12
this might help too [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

