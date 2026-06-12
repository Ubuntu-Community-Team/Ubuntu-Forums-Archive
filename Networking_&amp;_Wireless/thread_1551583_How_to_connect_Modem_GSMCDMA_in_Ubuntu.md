---
title: "How to connect Modem GSM/CDMA in Ubuntu"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by jhent on 2010-08-12
English :I'm a newbie please help me??? How to connect Modem GSM(3g-hsdpa) / CDMA in Ubuntu??

Indonesia : Aku newbie, tolong bantu saya??? Bagaimana mengkoneksikan GSM Modem (3g-HSDPA) / CDMA di Ubuntu?


Modem : Option Icon322 / GlobeTrotter Icon322

:(

---

### Post by dineshs on 2010-08-12
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab,mobile broadband -add,then proceed(tick available to all users while configuring)
If it is not working post the results of ```
lsusb
```and```
dmesg | grep -e "modem" -e "tty"
```

---

### Post by jhent on 2010-08-13
> **dineshs said:**
> Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab,mobile broadband -add,then proceed(tick available to all users while configuring)
If it is not working post the results of ```
lsusb
```and```
dmesg | grep -e "modem" -e "tty"
```


ok... thanks.. i will try now:popcorn:

---

### Post by corysquires on 2010-10-05
Does this modem work? I am looking at getting one...

---

