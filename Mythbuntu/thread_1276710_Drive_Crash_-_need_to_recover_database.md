---
title: "Drive Crash - need to recover database"
date: 2009-09-27
forum: Mythbuntu
---

### Post by Billsputters on 2009-09-27
OK, had a major calamity here, the drive decided to crash and gave up the ghost after the many power outages etc. we have here.

All is not lost, I can boot into an Ubuntu Live CD and copy over the var/lib/mysql and all it's contents to a USB pen drive.

The question is, how do I get it back into a new install and have things back to the the way they were.

---

### Post by klc5555 on 2009-09-27
> **Billsputters said:**
> OK, had a major calamity here, the drive decided to crash and gave up the ghost after the many power outages etc. we have here.

All is not lost, I can boot into an Ubuntu Live CD and copy over the var/lib/mysql and all it's contents to a USB pen drive.

The question is, how do I get it back into a new install and have things back to the the way they were.

Since you can't run a mysqldump on your dead installation to produce a portable mythconverg_backup.sql file from your most current mythconverg, the easiest way might be to gather up any and all of the weekly automatic mythconverg backups that may have accumulated in /var/backups Then restore from one of these into your new myth installation by following the guidance here: [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#The_database](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#The_database)

---

