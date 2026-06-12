---
title: "auto kill Gnome-PPP"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by sandipan on 2009-07-28
Hi All,
I need script(or teminal command) which will kill GnomePPP at 5:55 AM everyday, if it's running.
Can anyone help me ?

Thanks
Sandipan Ghosh:(

---

### Post by superprash2003 on 2009-07-28
you could use cron for this.. there is a command called killall to kill instances of applications.. like for example typing kilall pidgin would kill pidgin.. and kilall firefox would kill firefox.. im not sure if killall gnomeppp would work , but it maybe under a different process name..you could use cron for this
 in your terminal type **crontab -e** and add the following line

**55 5 * * * killall gnomeppp**

---

