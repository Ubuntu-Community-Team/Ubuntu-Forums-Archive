---
title: "SIMPLE folder share"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by ilna on 2010-09-21
Hi!

I have two PC in my home net (in fact, wifi AP and STA under Kbuntu Maverick testing, but it doesn't matter - just having pings to each other). The aim is to share a folder (with read-write rights) on one PC for another one. Client must be able just to mount remote folder. Basic authentification will be sufficient (say, password + MAC address).

Probably, there are plenty of ways to accomplish this task. But I have never met with any of them earlier. Please, point me right direction, taking in mind the demands listed above. Also, reliable and simple variants win. I mean I'd be happy to avoid such monsters as samba is :-) Of course, a decision must be CLI-oriented.

I see, too many demands... Nevertheless, I'm sure you have plenty of hints for me :)

---

### Post by marc.verwerft on 2010-09-22
Seems you've already got some command line experience. Good. Ever had a look at sshfs ? Or maybe NFS ?

Happy hunting ;-)

Regards,

Marc
[]("http://www.google.com/search?client=ubuntu&channel=fs&q=file+sharing+ubuntu+10.04&ie=utf-8&oe=utf-8")

---

### Post by ilna on 2010-09-22
> **marc.verwerft said:**
> Ever had a look at sshfs ? Or maybe NFS ?Now I'm evaluating NFS. Thanks for pointing me to sshfs! - I'll take it for my next iteration.

---

