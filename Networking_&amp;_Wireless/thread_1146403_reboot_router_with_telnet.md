---
title: "reboot router with telnet"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by njb on 2009-05-02
Hello,

My object is to reboot my router everyday at 6 AM
I alredy succeed to do it with terminal and commands :

telnet <IProuter>
login
password
reboot

Is there a way to execute automaticaly this script everyday at 6AM with my ubuntu.

:P NjB

---

### Post by llemm on 2009-05-02
> **njb said:**
> Hello,

My object is to reboot my router everyday at 6 AM
I alredy succeed to do it with terminal and commands :

telnet <IProuter>
login
password
reboot

Is there a way to execute automaticaly this script everyday at 6AM with my ubuntu.

:P NjB


use cron

man cron

---

