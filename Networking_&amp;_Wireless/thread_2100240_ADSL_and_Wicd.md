---
title: "ADSL and Wicd"
date: 2013-01-01
forum: Networking &amp; Wireless
---

### Post by Infinite Indefinite on 2013-01-01
Upon initially installing Wicd, I found that the wired network would not automatically connect on my system, unless I plugged in my ADSL modem at the login screen (as opposed to plugging it in before I put on the power).  

I managed to solve this problem by simply adding the line:

**sleep 1m** 

above the line 

**pon adsl**

in the file _/etc/rc.local_.

---

