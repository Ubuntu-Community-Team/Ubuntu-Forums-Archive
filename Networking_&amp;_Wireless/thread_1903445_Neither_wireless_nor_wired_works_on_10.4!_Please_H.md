---
title: "Neither wireless nor wired works on 10.4! Please Help!"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by Livinhoca on 2012-01-02
Can't go online! I've tried wired and wireless and none of them work. What should I do? It stopped working after I tried downloading STA drivers while I had my Dell Inspiron 1420 on B43 drivers and was running 11.10. I couldn't get STA do download and my internet just died on me. Now I can't get it to work anymore. Can anyone help me?

---

### Post by chili555 on 2012-01-02
Please open a terminal and run and post:```
lspci -nn | grep -e 0280 -e 0200
lsmod | grep -e wl -e b4 -e ssb
```Thanks.

---

