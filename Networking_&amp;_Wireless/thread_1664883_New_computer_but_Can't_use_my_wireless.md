---
title: "New computer but Can't use my wireless"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by jonpon on 2011-01-11
I bought a new computer but the Wlan card won't work!
I tried downloading the driver from the Edimax website but still having no joy,
can anyone help me out?   please..?

get this with:lspci -nn
```
03:06.0 Network controller [0280]: RaLink Device [1814:3060]

```
so it seems to be there
but just won't work

---

### Post by PatchesTheCaveman on 2011-01-11
You can download the driver from Ralink's website:
[http://ralinktech.com/support.php?s=2](http://ralinktech.com/support.php?s=2)

You'll need to know the exact chipset of your card.  This command should give you that information:
```
lspci -vnn
```

---

### Post by jonpon on 2011-01-13
Got it sorted I found [SIZE="3"][this]("http://ubuntuforums.org/showthread.php?t=1615304&page=5")[/SIZE]

Hee hee I'm online

---

