---
title: "Lost Settings Table"
date: 2016-02-18
forum: Mythbuntu
---

### Post by Raptor Ramjet on 2016-02-18
Hello,

Following an apt-get update last Saturday my mythconverg database has "lost" its settings table.  No idea what happened but its gone.

However I have managed to mostly restore the database from a dump I created just prior to running the upgrade but this dump is also missing the settings table (strange really as it was all working fine of Friday night)  Unfortunately all 4 other backups I have are also missing the settings table too so now I'm slightly stuck.

I'd therefore be very grateful if someone could be kind enough to generate a MYSQL script which has the necessary SQL to create the "settings" table and relationships etc.  Once I get the table back into the database I should be able to recover as the other tables appear to be there.

Thank you in advance.

---

### Post by wpcprez on 2016-02-18
> **Raptor Ramjet said:**
> Hello,

Following an apt-get update last Saturday my mythconverg database has "lost" its settings table.  No idea what happened but its gone.

However I have managed to mostly restore the database from a dump I created just prior to running the upgrade but this dump is also missing the settings table (strange really as it was all working fine of Friday night)  Unfortunately all 4 other backups I have are also missing the settings table too so now I'm slightly stuck.

I'd therefore be very grateful if someone could be kind enough to generate a MYSQL script which has the necessary SQL to create the "settings" table and relationships etc.  Once I get the table back into the database I should be able to recover as the other tables appear to be there.

Thank you in advance.
you sure it's lost and not just needing to be repaired?

[https://dev.mysql.com/doc/refman/5.6/en/rebuilding-tables.html](https://dev.mysql.com/doc/refman/5.6/en/rebuilding-tables.html)

---

### Post by Raptor Ramjet on 2016-02-18
Yup.  100% sure.  Already tried repairing and using the "optmise_mythdb" script to check the database.

The settings table is gone, dead, muerte, no more, it has ceased to be.  It is absent and is not coming back without me manually recreating it.

---

### Post by wpcprez on 2016-02-23
> **Raptor Ramjet said:**
> Yup.  100% sure.  Already tried repairing and using the "optmise_mythdb" script to check the database.

The settings table is gone, dead, muerte, no more, it has ceased to be.  It is absent and is not coming back without me manually recreating it.


well default table is basic


CREATE TABLE `settings` (
  `value` varchar(128) NOT NULL DEFAULT '',
  `data` varchar(16000) NOT NULL DEFAULT '',
  `hostname` varchar(64) DEFAULT NULL,
  KEY `value` (`value`,`hostname`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


Actually,
Use this file in your system

/usr/share/mythtv/sql/mythtv_0.27.0.sql

Just edit it and you will see this table creation then the insert statement you need to run afterward to populate the table. (version of file could be different depending on what you are running)

---

