---
title: "Modem dials but can't browse"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by frank cox on 2009-11-23
When I connect it tells me:

 Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

Would someone tell me how to correct this problem?

TIA

---

### Post by _duncan_ on 2009-11-24
try this in a terminal:

```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```

replace [COLOR="Blue"]userID[/COLOR] with your actual user ID.

log out, then log back in for the changes to take effect.

---

### Post by frank cox on 2009-11-27
Thanks-  I will try it tomorrow!

I was already a user.
Thanks anyway.

---

### Post by _duncan_ on 2009-12-09
you probably forgot the word 'dip'. The command I posted is supposed to add your existing user to the dip group, not create a new user.

---

### Post by frank cox on 2009-12-09
> **_duncan_ said:**
> you probably forgot the word 'dip'. The command I posted is supposed to add your existing user to the dip group, not create a new user.

It said I was already a member of dip. I remember doing that before.
Thanks anyway.

---

