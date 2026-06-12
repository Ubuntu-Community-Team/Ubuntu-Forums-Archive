---
title: "Belkin wireless driver"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by Bolshy on 2012-10-21
Hi I am trying to locate a wireless driver for a Belkin wireless card F5D700UK v1133uk for Ubuntu can anybody help please?
Thanking you all in advance

---

### Post by chili555 on 2012-10-21
I believe this is a PCI card. Please open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep rt
iwconfig
```The pipe symbol | is on the right side ofmy US keyboard on the same key with \. Thanks.

---

### Post by Bolshy on 2012-10-21
Thanks I will try that now and let you know how I get on

---

### Post by Bolshy on 2012-10-21
are all of the| on the text pipe symbols?

---

### Post by chili555 on 2012-10-21
> **Bolshy said:**
> are all of the| on the text pipe symbols?I don't understand your question. Just type in the line and press Enter. Please see attached. You can just copy and paste the result here.

---

### Post by Bolshy on 2012-10-21
Sorry I was using l for lima and not i for india  so will let you know how it goes thanks

---

