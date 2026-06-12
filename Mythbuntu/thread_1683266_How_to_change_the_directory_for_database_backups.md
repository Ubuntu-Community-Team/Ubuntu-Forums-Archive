---
title: "How to change the directory for database backups?"
date: 2011-02-07
forum: Mythbuntu
---

### Post by anaximandro22 on 2011-02-07
by default is in /var/lib/mythtv/db_backups. And I want to put it in /home/mythtv/db_backups.

I've changed the directory in the backend - Storage directories - DB Backups
and also, in a terminal I've executed:
mythconverg_backup.pl --mysqldump /home/mythtv/db_backups

Then I can make a backup executing mythconverg_backup.pl. But from the backend, when I change something in the configuration, when I exit the backend, It suggest to me to run mythfilldatabase, I do it but it don't make a database backup file.

I don't understand what happens.
Could anybody tell me when make the backend a new database file backup?.

---

### Post by vanadium on 2011-02-07
The easiest approach would seem to replace /var/lib/mythtv/db_backups with a symlink to the directory where you want the data to be actually stored. No change in configuration in your software would be needed.

---

### Post by tgm4883 on 2011-02-07
> **anaximandro22 said:**
> by default is in /var/lib/mythtv/db_backups. And I want to put it in /home/mythtv/db_backups.

I've changed the directory in the backend - Storage directories - DB Backups
and also, in a terminal I've executed:
mythconverg_backup.pl --mysqldump /home/mythtv/db_backups

Then I can make a backup executing mythconverg_backup.pl. But from the backend, when I change something in the configuration, when I exit the backend, It suggest to me to run mythfilldatabase, I do it but it don't make a database backup file.

I don't understand what happens.
Could anybody tell me when make the backend a new database file backup?.

mythfilldatabase doesn't make a database backup, it fills the database with scheduling information. IIRC, DB backups happen on a schedule, although I don't recall if that is weekly or monthly

---

### Post by nickrout on 2011-02-07
The default in mythbuntu is to make a database backeup every week, via /etc/cron.weekly/mythtv-database

My practise is to shift this into the /etc/cron.daily directory so that it gets executed every day, and make a file ~/.mythtv/backuprc with the line ```
rotate=21
``` so I have 21 days or three weeks of backups.

---

### Post by anaximandro22 on 2011-02-09
I understand. It was configured weekly as nickrout says, but I didn't know. I thought that was mythbackend who did it when I changed something in the configuration.

Thanks a lot.

---

