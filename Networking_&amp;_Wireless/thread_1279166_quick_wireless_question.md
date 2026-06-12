---
title: "quick wireless question"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by accol on 2009-09-30
Hello all!  Ubuntu recognizes my wireless perfectly but when I try running backtrack its not even detected.  I have no idea if what I need it 'ndiswrapper' or anything like that.  If you can please point me in the right direction in to what to look for that would be awesome.

---

### Post by Ayuthia on 2009-09-30
We need a little more information.  Which wireless card are you using and which version of backtrack are you using?

---

### Post by accol on 2009-09-30
Im trying version 3 since the usb install is already set.  My wireless card (when I pulled it out to check) is an arimus.  Noob question:  which command tells me specifically what wireless card i have installed?

---

### Post by Ayuthia on 2009-09-30
> **accol said:**
> Im trying version 3 since the usb install is already set.  My wireless card (when I pulled it out to check) is an arimus.  Noob question:  which command tells me specifically what wireless card i have installed?

If it is a pci card:
```
lspci -nn
```

If it is a USB version:
```
lsusb
```

---

