---
title: "After upgrade to 9.1 unable to change mysql to old passwords"
date: 2009-11-19
forum: Mythbuntu
---

### Post by nunrgguy on 2009-11-19
Need old passwords to allow xbmc to connect to the database. Attempted to edit the my.cnf files but has no effect.

Attempting to run mysqld --old-passwords gives the following message:
arning: World-writable config file '/etc/mysql/my.cnf' is ignored
091119 11:33:09 [Warning] Can't create test file /var/lib/mysql/MythTV.lower-test
091119 11:33:09 [Warning] Can't create test file /var/lib/mysql/MythTV.lower-test
091119 11:33:09 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
091119 11:33:09 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
091119 11:33:09  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.

mysql_upgrade has already been run to fix another issue previously.

cheers

---

### Post by nunrgguy on 2009-11-19
BTW I have changed permissions and it does have access rights to the files

---

### Post by vanyinet on 2010-02-25
> **nunrgguy said:**
> BTW I have changed permissions and it does have access rights to the files

Can you tell me which file permission have you changed? I've the same issue with MySQL.

---

