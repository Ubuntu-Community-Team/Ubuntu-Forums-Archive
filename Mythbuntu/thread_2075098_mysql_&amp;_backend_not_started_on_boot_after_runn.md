---
title: "mysql &amp; backend not started on boot after running Ubuntu Tweaks"
date: 2012-10-23
forum: Mythbuntu
---

### Post by dheianevans on 2012-10-23
Just ran the software Ubuntu Tweaks to clean up some cruft after moving from mythbuntu 11.04 to mythbuntu 12.04.

Went to start myth again and got the frontend country/language screen and the message that it couldn't find the backend.

Just looked and noticed that mysql and mythbackend didn't get started on boot. Just so I don't mess things up too much, is there a script I can run that will get the boot setup the way mythtv expects to find it?

update: running 'sudo start mysql' gets me start: Job failed to start

Any idea why the backend and mysql suddenly failed to start on boot?

---

### Post by dheianevans on 2012-10-23
Update: according to [https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/986892](https://bugs.launchpad.net/ubuntu/+source/mysql-5.5/+bug/986892) cruft removal deleted /etc/apparmor.d/local/usr.sbin.mysqld


As suggested I created a dummy one and everything launched fine at boot.

---

