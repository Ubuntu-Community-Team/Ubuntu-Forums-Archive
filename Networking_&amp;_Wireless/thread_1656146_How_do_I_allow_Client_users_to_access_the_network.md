---
title: "How do I allow Client users to access the network?"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by Cotopaxi on 2010-12-30
Hi,

The question is related to one single desktop machine, with 3 users.

1) the superuser (me)
2) My elder son
3) My younger son.

As superuser, I can access the network (internet router) via "Wicd" perfectly well.

Both Client users can't.

Do I have to give them special user priviledges? If yes, which ones?

Thanks!

---

### Post by Cotopaxi on 2010-12-30
Bump.
;)

---

### Post by spiky001 on 2010-12-30
If you go System/Administration/users select user properties then make sure connect to wireless eth0 networks is ticked under User Privileges

---

### Post by Cotopaxi on 2010-12-30
Thanks for your help, that one is checked.

It is the first time this happens since 8.10!

Anyhow, thanks for your help!

---

### Post by spiky001 on 2010-12-30
I presume that in network manager that eth0/wlan0 is ticked all users

---

### Post by Cotopaxi on 2010-12-30
Also ticked, thanks again! :popcorn:

I will, most probably, re-install version 9.10 tomorrow, version 10.04 and 10.10 are working great on my laptop, but they are horrible on the family's desktop!

Thanks again for your help!

---

### Post by Cotopaxi on 2010-12-30
Ok, I managed to solve it:

I opened the package manager and typed in: “network-manager”.

If Wicd is installed, EVERYTHING related to “network-manager” must be thrown out, sorry: removed!

Once I did that, both Client users (from their respective sessions) can now access the internet via Wicd.

Spiky again, Thanks very much indeed for your help! :popcorn:

---

