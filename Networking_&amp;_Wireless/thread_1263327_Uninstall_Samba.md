---
title: "Uninstall Samba"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by saidbakr on 2009-09-10
Hello,

How to completely remove Samba from the system in-order to be reinstall it again in ideal standard state?

I did some mistakes in its configurations files and folders and I want to assure that I start everything from the begining.

---

### Post by uylug on 2009-09-10
```
sudo apt-get remove samba
sudo apt-get install samba
```or

```
sudo dpkg-reconfigure samba
```

---

### Post by zwdev on 2009-11-05
**sudo apt-get purge samba**

---

