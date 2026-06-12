---
title: "Linksys WPC54G Driver Installed, Can't Connect"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by CaffeineTripp on 2011-12-16
Recently went over the install for the Linksys WPC54G PCI card driver, turned out just well.  Got the okay go from sudo.  I pick up plenty of wireless around my home, my own as well.  I know the key for it, obviously, but for some reason the password prompt for the wifi keeps popping up, not letting me connect to it.
Any suggestions?

---

### Post by praseodym on 2011-12-16
Hi,
which encryption mode is in use? Any strange letters/signs/whatever in the key or ESSID? How many characters does the key have? Please show:
```

iwconfig
sudo iwlist scan
lsmod
lspci -nnk | grep -iA2 net
```

---

