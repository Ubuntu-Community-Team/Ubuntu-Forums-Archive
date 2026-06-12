---
title: "New network adapter name on restart"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by cchase88 on 2010-07-09
Hey everyone, I just recently replaced a network card on my ubuntu desktop and now I cannot connect to the internet anymore. Each time I start up ubuntu, my network adapter gets assigned a new name. Right now I have Auto eth5 listed when I click on the networking icon that is on the task bar. I've tried modifying the /etc/network/interfaces file, but like I said, after each restart, the file just reflects the old adapter name (right now it still says auto eth4 for the first line). Any ideas?

---

### Post by Iowan on 2010-07-09
You can edit */etc/udev/rules.d/70-persistent-net.rules* to get rid of extras, but dunno if that'll stop it from happening...

---

