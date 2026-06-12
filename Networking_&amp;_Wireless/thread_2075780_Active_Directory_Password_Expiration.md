---
title: "Active Directory Password Expiration"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by sergiofm on 2012-10-24
HI,

I joined Ubuntu to AD and need to know wen must I change my password.

Tanks,
Sérgio Marques

---

### Post by thebeest on 2012-10-24
It depends on the AD server's configuration. Normal values are 28-42 days but values range between those specified in: [http://technet.microsoft.com/en-us/library/cc875814.aspx](http://technet.microsoft.com/en-us/library/cc875814.aspx)

If you have access to the server you could set the maximum age to 0 so that the password never expires.

---

### Post by sergiofm on 2012-10-25
Hi,

I know that, but what I wont is to be notified to change my password.

Tanks

---

### Post by thebeest on 2012-10-26
As far as I am aware this is notification is not possible. When the password expires you will get a incorrect password warning and have to change it at that point. If you can find out the number of days til the password expires you could simply make a reoccurring calendar event to remind you to change the password.

---

