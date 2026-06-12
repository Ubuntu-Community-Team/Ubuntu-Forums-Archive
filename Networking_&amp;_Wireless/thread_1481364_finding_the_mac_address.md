---
title: "finding the mac address"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by Garthhh on 2010-05-12
I'm setting up a static IP address & I need to know the mac address of my 2 unbuntu machines? [8.04 & 9.10]

---

### Post by acce on 2010-05-12
in terminal, have you tried: ```
lshw -c network
```

---

### Post by Garthhh on 2010-05-12
Never mind
I should have looked on help instead of the forum
Just in case someone else does the same here's the procedure:
open terminal
ifconfig
the mac address is labeled HWaddr

---

### Post by Garthhh on 2010-05-12
> **acce said:**
> in terminal, have you tried: ```
lshw -c network
```
that's interesting then I get choices I don't quite understand

---

