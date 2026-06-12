---
title: "[Ubuntu 12.04] Wired connection"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by enezx on 2013-05-01
I have Dell Inspiron 5420 and I cannot connect to ethernet. I am able to use wireless though.

Strange thing is that a while ago nothing - (wired and wireless) worked. So I had to install drivers for that. Then my LAN worked and after I made my wireless working, LAN stopped working. Why is that?

Help

---

### Post by Hadaka on 2013-05-02
Hi,please post the output of..
```
lspci -nn | egrep '0200|0280'
```
thanks

---

### Post by enezx on 2013-05-02
```

02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

```

---

### Post by enezx on 2013-05-03
Anyone?

---

