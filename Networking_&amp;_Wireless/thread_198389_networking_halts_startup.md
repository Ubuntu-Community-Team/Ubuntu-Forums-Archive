---
title: "networking halts startup"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2006-06-17
/etc/init.d/networking seems to halt startup after I upgraded to dapper.

To get around this I have to do ```
alt+sysRq+e
``` to kill the task and then do ```
/etc/init.d/networking restart
``` when everything has loaded.

I have a wireless card but what I don't understand is why it works fine when the system is up.

Perhaps there is something else causing trouble on startup? But how do I find out?

---

