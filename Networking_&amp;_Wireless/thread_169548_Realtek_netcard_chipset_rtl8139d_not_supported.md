---
title: "Realtek netcard chipset rtl8139d not supported"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by julioboaro on 2006-05-02
Two netcards, chipsets rtl8139c and rtl8139d.

$ lspci
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:09.0 Ethernet controller: Unknown device 1904:2031 (rev 01)

Both Ubuntu 5.10 and Kurumin 6.0 don't detect the second chipset.

Anyone connects with rtl8139d and can help?

---

### Post by az on 2006-05-03
Go upstream:

[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

Look at the homepage and see if you can ask someone on the project's mailing list about support for that card.

---

