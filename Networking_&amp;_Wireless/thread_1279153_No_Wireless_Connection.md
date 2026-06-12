---
title: "No Wireless Connection"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by komatsu100 on 2009-09-30
I upgraded to Ubuntu 9.04 and now I don't have Wireless Internet connection.  What happened, do I need to try to reinstall 9.04 or can I changes something to get it back.

---

### Post by wobin77 on 2009-09-30
First, please post your exact hardware you re using.

Feedback on the output of those commands: (in terminal)

```
lspci
```
```
lsusb
```

---

### Post by Iowan on 2009-09-30
**lshw -C network** is another command that will provide info about your networking hardware. Invest some time in troubleshooting before you re-install.

---

