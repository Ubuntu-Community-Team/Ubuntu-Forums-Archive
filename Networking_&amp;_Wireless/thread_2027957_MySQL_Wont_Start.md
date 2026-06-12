---
title: "MySQL Wont Start"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by gdl on 2012-07-17
Hi,

I moved my ubuntu server install from dynamic to static IP.  Ever since, I can't get MySQL to start.

If I do:

sudo service mysql start

I get:


start: Job failed to start


dmesg says:


[  506.342347] type=1400 audit(1342533691.633:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1387 comm="apparmor_parser"
[  506.399019] init: mysql main process (1391) terminated with status 1
[  506.399123] init: mysql main process ended, respawning
[  507.417889] init: mysql post-start process (1392) terminated with status 1
[  507.440656] type=1400 audit(1342533692.733:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1415 comm="apparmor_parser"
[  507.497708] init: mysql main process (1419) terminated with status 1
[  507.497808] init: mysql main process ended, respawning
[  508.514626] init: mysql post-start process (1420) terminated with status 1
[  508.537787] type=1400 audit(1342533693.829:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1443 comm="apparmor_parser"
[  508.594837] init: mysql main process (1447) terminated with status 1
[  508.594941] init: mysql respawning too fast, stopped


Any ideas what I messed up!?  If it makes any difference, I am using cntlm...

Thanks, Geedle.

---

### Post by gdl on 2012-07-17
Found the problem!

If the /etc/mysql/my.cnf file's formatting had gone all wrong: lines had wrapped all over the place: all non-commented lines had wrapped.  I logged into the server a couple of times from Windows machines using PuTTy.  Worthwhile noting!

Cheers, Geedle.

---

