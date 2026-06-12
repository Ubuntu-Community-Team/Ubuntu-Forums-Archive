---
title: "Checking/Upgrading AMD drivers on Linux 12.04"
date: 2014-02-19
forum: Multimedia Software
---

### Post by benmcneil102 on 2014-02-19
How do I check which driver I'm currently using for my graphics card and how would I upgrade the driver if it wasn't up to date


I have an AMD radeonhd 7770

---

### Post by Bucky Ball on 2014-02-19
*Thread moved to **Multimedia & Video**.*

Unsure what this has to do with ***Gaming & Leisure***. :-k

You could try looking in Additional Drivers and see if there is anything enabled in there. You can also try Catalyst Control Centre if you have it installed. That has all the details.

---

### Post by Yellow Pasque on 2014-02-20
```
lspci -k
```

> how would I upgrade the driver if it wasn't up to date
Assuming you're using proprietary fglrx/Catalyst driver,  you can get a very recent version if you enable proposed repo: [https://launchpad.net/ubuntu/+source/fglrx-installer-updates/2:13.125-0ubuntu0.0.1](https://launchpad.net/ubuntu/+source/fglrx-installer-updates/2:13.125-0ubuntu0.0.1)
Just disable the proposed repo after you get that package because you generally don't want to upgrade everything to the proposed version..

---

