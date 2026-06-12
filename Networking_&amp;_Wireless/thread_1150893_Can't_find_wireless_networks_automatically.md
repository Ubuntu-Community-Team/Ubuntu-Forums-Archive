---
title: "Can't find wireless networks automatically"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by M.Sisco on 2009-05-06
I just installed Ubuntu on my laptop with an internal linksys card. However, it won't automatically find the wireless network. I went to the drivers and it says the card is active and in use. Is there a way to have it find wireless networks in the area automatically?

---

### Post by codysoyland on 2009-05-06
Take a look at network-manager or iwconfig.

---

### Post by aparigraha on 2009-05-06
... or lwlist to scan for networks.

```
iwlist [your interface] scanning
```

e.g iwlist eth0 scanning

more iwlist functions:

```
man iwlist
```

or [http://gd.tuwien.ac.at/linuxcommand.org/man_pages/iwlist8.html]("http://gd.tuwien.ac.at/linuxcommand.org/man_pages/iwlist8.html")

---

