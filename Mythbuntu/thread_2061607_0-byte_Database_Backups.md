---
title: "0-byte Database Backups"
date: 2012-09-23
forum: Mythbuntu
---

### Post by jamoody on 2012-09-23
Something is causing 0-byte database backups but I can't seem to identify what is doing it.  The empty files are of the form mythconverg-20120922223343.sql.  I've run all scripts in /etc/cron.daily and none of them seem to be doing it.  I suspect BARE but I haven't been able to prove it.  

Ideas?

---

### Post by nickrout on 2012-09-23
> **jamoody said:**
> Something is causing 0-byte database backups but I can't seem to identify what is doing it.  The empty files are of the form mythconverg-20120922223343.sql.  I've run all scripts in /etc/cron.daily and none of them seem to be doing it.  I suspect BARE but I haven't been able to prove it.  

Ideas?logs?

---

### Post by klc5555 on 2012-09-23
The heart of the backup script is mysqldump, which produces the actual backup file. mysqldump errors out if it finds a crashed table or other significant database problem. So perhaps try running mysqlcheck to see whether a one or more crashed tables are found which need to be repaired.

---

### Post by tgm4883 on 2012-09-23
BARE just uses the MythTV provided backup script for the DB backup, and places the .sql file in a temp directory before gzipping it. If you are seeing the .sql file outside of /tmp then it isn't BARE.

---

