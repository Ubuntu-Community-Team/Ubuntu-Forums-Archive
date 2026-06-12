---
title: "Broadcom Wireless Issues?"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by Noah0504 on 2006-07-02
I was previously using Ubuntu 6.06 as my only operating system on my Toshiba Tecra 8200.  Last week that computer died.  I made it an opportunity to buy a new notebook computer.  Office Depot was having some crazy rebate offers, and I was able to walk away with a Compaq Presario V2615US for $499.  Anyway, I noticed that it has a Broadcom internal wireless adapter.  I'm on vacation right now, and plan to install Linux when I get back home.  However, I'm concerned that I'll have trouble getting my wireless adapter to work -- I've noticed many posts regarding Broadcom wireless cards.  What trouble should I expect to have.

---

### Post by KB3MKD on 2006-07-02
got my acer aspire w/ broadcom wireless working w/o WPA using ndiswrapper + winXP driver.  Still working on the WPA thing.

---

### Post by MarkSheely on 2006-07-03
Noah,  do you know off hand which Broadcom card you have?  I can try to point you in the right direction.

---Mark

---

### Post by Noah0504 on 2006-07-03
[QUOTE=MarkSheely]Noah,  do you know off hand which Broadcom card you have?  I can try to point you in the right direction.

---Mark[/QUOTE]
No, I can't seem to come across a model number.

---

### Post by ubunturules on 2006-07-04
run this command.
```
lspci | grep Broadcom\ Corporation
```

---

### Post by Geekbeard on 2006-07-04
There should come bundled with your laptop one CD or more labelled "Driver Recovery CD" or something like that. Usually, you'll find the Broadcom .inf file you need in Disc 1. It will be named something like "bcmwl*". When I had my Compaq laptop (before I stupidly gave it away to a family member who didn't have a computer), I used the bcmwl5.inf file in ndiswrapper (through ndisgtk) and it worked fine.

---

