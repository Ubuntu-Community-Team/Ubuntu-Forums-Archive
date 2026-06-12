---
title: "upgrade from 8.10 to 9.04: soundblaster pci 128 not working any more"
date: 2009-05-31
forum: Multimedia Software
---

### Post by fonzman on 2009-05-31
After installing Ubuntu 9.04 my Soundblaster PCI 128 does not work any more.
It did work fine in Ubuntu 8.10

When starting, Ubuntu writes this message:
```
0000:06:0c:0 unknown header type 0e, ignoring device
```

aplay -l says
```
aplay: device_list:217: no sound device found ...
```

lspci does not list the card.

any ideas?

---

