---
title: "no wireless - broadcom"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by ELD on 2011-10-15
Even after installing the additional drivers my wireless still doesn't seem to want to turn on.

I have a lenovo ideapad Z570

---

### Post by varunendra on 2011-10-17
The following outputs please:
```
sudo lshw -C network
lsmod
ifconfig -a
iwconfig
rfkill list all
```

---

### Post by ELD on 2011-10-17
Nevermind i ended up fixing it, needed to blacklist acer wireless...(even tho my unit is lenovo apparently acer_wireless is loaded on most laptops?)

---

