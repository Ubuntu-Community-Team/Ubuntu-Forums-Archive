---
title: "Dvico Hybrid (again)"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Sumatie on 2008-01-05
Hi, again, I can't get Dvico Hybrid working in Gutsy...tried all common fixes such as adding to modules. The card seems to be there but the system won't access it.

Here is what is coming up, MythTV can find the card but not identify what it is just says generic. When I try to scan for chanels it tries and comes up with nothing no matter what I set the region to.

Code:

 ls -l /dev/dvb/adapter*
ls: /dev/dvb/adapter*: No such file or directory

Code:

 dmesg | grep dvb
[   64.782453] cx2388x dvb driver version 0.0.6 loaded
[   64.782457] cx8802_register_driver() ->registering driver type=dvb access=shared

Help please..

Anybody??

---

