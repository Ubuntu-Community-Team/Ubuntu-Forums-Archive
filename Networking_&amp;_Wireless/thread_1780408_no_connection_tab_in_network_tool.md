---
title: "no connection tab in network tool"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by Navtronics on 2011-06-12
hi,
i recently installed ubuntu 10.04. And frm the day i installed it i'm not able to connect to wired network( to my modem).
in ubuntu help i found tht network-admin was installed,so i installed it.
guess what no connection tab in it!!!!!
so i've a problem in connecting to internet :( 
my network supports DHCP!
so can anyone tell me how to interface with wired network....

---

### Post by Iowan on 2011-06-12
Does your machine recognize the adapter?
**ifconfig -a ** from a terminal (Applications>Accessories>Terminal) should show available interfaces. 
If necessary, **lshw -C network** can provide more details about the networking hardware.

---

