---
title: "Darkstat log"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by bachor on 2011-01-05
could't find anywhere on how to clear all IPs in Darkstat,anyone knows?

---

### Post by mhgsys on 2011-05-03
yep; today I wanted to do just that.

found it out btw; 
first stop darkstat...
```
sudo service darkstat stop
```

then rm the database
```
sudo rm /var/lib/darkstat/darkstat.db
```
and then start darkstat again 
```
sudo service darkstat start
```

the new darkstat.db file will be in /var/lib/darkstat the next time you stop (or restart) darkstat.

---

