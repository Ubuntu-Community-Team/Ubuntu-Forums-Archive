---
title: "Firmware missing in Dell 1525"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by Nagesh Kumar Chauhan on 2011-04-25
Wilreless network disconnected ...

in Dell inspiron 1525:confused:

---

### Post by josephmills on 2011-04-25
hi there to further assist you could you please show us the following ```
lspci -nn
``` thanks

---

### Post by emperorsmokey on 2012-02-29
I had a problem on my Dell Inspiron E1505. Solved it using the attached file and following commands:

download b43.zip to Desktop, and extract it there.

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```

---

### Post by bigken on 2012-02-29
stick a nertwork cable in then install restricted drivers

---

