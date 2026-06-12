---
title: "How to remove Samba4 Daemon"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by xenogia on 2009-07-27
I removed Samba4 by using doing the standard apt-get remove command

sudo apt-get remove samba4

But I have noticed that the daemon is still being enabled during boot up, how do I remove this?

---

### Post by charos1978 on 2013-03-11
Hi xenoia,

I would try to go to the source folder where you did your make && make install and do a :

make uninstall

---

