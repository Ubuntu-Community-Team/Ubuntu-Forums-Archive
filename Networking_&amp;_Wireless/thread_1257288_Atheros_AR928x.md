---
title: "Atheros AR928x"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by killians31 on 2009-09-03
I recently installed Ubuntu 9.04 on my Asus G50vm-x1. it seems that ubuntu doesnt want to recognize my wireless card which is an Atheros AR928x. This is kind of strange because when i boot into the live cd, i can pick up wireless, but as soon as i installed ubuntu onto my hard drive, it doesnt even want to recognize my card! i performed a search, but it seems like this issue hasnt been resolved yet...?

Any help is appreciated!

Thanks,
-Ben

---

### Post by Crafty Kisses on 2009-09-03
What are the results of the following?
```
lspci
lsusb
lshw -C network
```

---

