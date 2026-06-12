---
title: "Re: Thinkpad  wireless issue"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by G0dzzilla on 2012-08-05
> **genericuser8133 said:**
> I'm trying to get a Realtek 8172 network card to work on a Lenovo Thinkpad sl510. I have the latest kernel (Which according to this should solve the problem: [https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172]("https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172")). There are no new drivers available in "Hardware drivers" and no updates in "Update Manager".

Please, can anyone help me? I've been trying to get this to work for hours.

I have the same problem. Did anybody get the wireless to work on the Thinkpad SL510 ?

---

### Post by wildmanne39 on 2012-08-05
Thread moved to it own thread!

---

### Post by chili555 on 2012-08-05
> **G0dzzilla said:**
> I have the same problem. Did anybody get the wireless to work on the Thinkpad SL510 ?Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
lsb_release -d
```Thanks.

---

