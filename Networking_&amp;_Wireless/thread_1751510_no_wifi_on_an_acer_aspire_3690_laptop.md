---
title: "no wifi on an acer aspire 3690 laptop"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by velt on 2011-05-06
Hi, I can get wired internet if i connect the laptop to the router, but no wifi since I think I dont have the drivers.
i dont see anything in aditional drivers. 

please help.

---

### Post by mkleber on 2011-07-18
same problem here !

No wifi working under 11.04

---

### Post by wildmanne39 on 2011-07-18
> **mkleber said:**
> same problem here !

No wifi working under 11.04Hi, run these commands in a terminal
```
lspci -nn
```
```
sudo lshw -C network
```
```
rfkill list All

```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

