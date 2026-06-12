---
title: "No Internet at all."
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by TMW12 on 2010-03-06
I just got Ubintu 9.10 because one of my friends put in a good word for it to me and I decided to try it. I booted it up for my Netbook and there's no Internet connections at all. Is there anything I can do?

---

### Post by wojox on 2010-03-06
Open your terminal and run this to tell us what your Network Card is:

```
lspci | grep -i net
```

---

### Post by TMW12 on 2010-03-06
Are you talking about the Network controller? If so: Atheros Comm. Inc. AR9285 Network Adapter (PCI- Express) (rev 01)
If not: Ethernet- Realtek Semiconductor Co. , Ldt.

---

