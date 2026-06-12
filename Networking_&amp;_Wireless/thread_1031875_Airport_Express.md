---
title: "Airport Express"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by Orangefromwin on 2009-01-05
Are there any working ubuntu drivers for Airport Express? Thanks.

---

### Post by pytheas22 on 2009-01-05
First, try going to System>Administration>Hardware Drivers and see if there's an option for enabling your wireless.  That may solve the problem.

If no wireless option is available, please post the output of these commands and I'll tell you how to make the card work:
```

lspci -nn
lshw -C Network
uname -rm
```

---

