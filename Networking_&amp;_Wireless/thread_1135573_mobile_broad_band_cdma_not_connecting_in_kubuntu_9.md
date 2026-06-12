---
title: "mobile broad band cdma not connecting in kubuntu 9.04"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by rbhatt on 2009-04-24
I installed kubuntu 9.04 today. No problems there. But connecting to the internet through mobile broad band is a no go. The network widget is recognising the mobile broadband cdma device but is not connecting to the internet. clicking on the mobile broadband icon produces no result. The cdma device is working fine in ubuntu 9.04.  can any body help me. Thank you. :)

---

### Post by jepong on 2009-04-28
same problem here... workaround is to use wvdial.

---

### Post by zhitomir on 2009-05-12
You may use kppp, I think it is more KDE interface friendly. But in firefox you will need select File -> Work Offline to Off manually each time you start it.

---

### Post by digitalhead on 2009-08-05
> **zhitomir said:**
> But in firefox you will need select File -> Work Offline to Off manually each time you start it.

A workaround/fix that I found for this is to open **about:config**, locate **toolkit.networkmanager.disable**, and double click it to change it to **true**. Hope this helps.

---

