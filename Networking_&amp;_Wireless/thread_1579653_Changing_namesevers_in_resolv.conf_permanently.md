---
title: "Changing namesevers in resolv.conf *permanently*?"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by wombatvvv on 2010-09-22
Hi guys,

My Internet connection runs slow and jerky, but can be fixed by using the Google public nameservers instead of the default one in this file. Problem is, the changes keep being reverted, even when I chmoded the file to have read-only permissions by everyone.

How can I change the nameserves permanently?

---

### Post by kerry_s on 2010-09-22
right click the network icon-> edit connections

---

### Post by SlugSlug on 2010-09-22
One of the first things I do on a ubuntu install is remove network-manager

then edit /etc/resolv.conf & /etc/network/interfaces  manually

---

### Post by kerry_s on 2010-09-22
> **SlugSlug said:**
> One of the first things I do on a ubuntu install is remove network-manager

then edit /etc/resolv.conf & /etc/networking/interfaces  manually

why? if you use it right life's easy.

---

### Post by SlugSlug on 2010-09-22
> **kerry_s said:**
> why? if you use it right life's easy.


I find it a lot easier editing those two files than I do clicking a load of buttons in network-manager.

and once I've set the files I know nothing will make them change

---

