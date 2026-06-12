---
title: "[SOLVED] mythfrontend.log problems"
date: 2008-11-18
forum: Mythbuntu
---

### Post by frego on 2008-11-18
My /var/log/mythtv/mythfrontend.log seems to get automagically recreated everyday with different user:group than what I expect.  Everything else in that directory gets created with frego:mythtv as user:group.  That is as I expect, but nightly it recreates itself with syslog:adm.  I think this behavior started with some updates a few weeks back.  Could anyone running Mythbuntu 8.04 with updates check ownership on your mythfrontend.log file and let me know what you have. Today's log is there but sometimes it's a zero byte file that can't get written to.  My permissions are:  -rw-rw-r--.

---

### Post by ian dobson on 2008-11-18
Hi,

Looks as if logrotate is getting abit confused, have a look at the /etc/logrotate.d/ directory for the myth-frontend configuration file.

Regards
Ian Dobson

---

### Post by frego on 2008-11-19
It wasn't updates that caused my problems with the mythfrontend.log ownership at all.  It was due to the fact that I had installed webmin and from within that interface added mythfrontend.log to the syslog module so I could look at the log from webmin.  Simply removing mythfrontend.log from that module seems to have fixed things up. :)

---

