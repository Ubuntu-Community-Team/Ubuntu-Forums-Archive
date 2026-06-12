---
title: "Myth TV backup problem with LOCK TABLES"
date: 2013-11-02
forum: Mythbuntu
---

### Post by linuxhippy on 2013-11-02
I'm trying to copy my backed up mythubuntu 12.04.2 to a new install of mythbuntu 12.04.3 using the instructions here for scripts:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Backup)

However, I am getting a bad backup using that backup script.  I used the verbose option so I could see what was happening and got this:

/usr/share/mythtv/mythconverg_backup.pl --verbose

Configuring environment:
  -    username: tux
  -        HOME: /home/tux
  - MYTHCONFDIR: /home/tux/.mythtv

Parsing configuration files:
  - checking: /home/tux/.mythtv/config.xml
     parsing: /home/tux/.mythtv/config.xml
  - checking: /home/tux/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

No DBBackupDirectory specified, querying database.
Found DB Backups directory: /var/lib/mythtv/db_backups/.

No DBSchemaVer specified, querying database.
Found DBSchemaVer: 1299.

Database Information:
         DBHostName: localhost
             DBPort: 3306
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 1299
  DBBackupDirectory: /var/lib/mythtv/db_backups/
   DBBackupFilename: mythconverg-1299-20131102131805.sql

Executables:
          mysqldump: mysqldump
           compress: gzip

Attempting to use supplied password for mysqldump.
Any [client] or [mysqldump] password specified in the MySQL options file will
take precedence.

Executing command:
'/usr/bin/mysqldump' --defaults-extra-file='/tmp/DOuOwaSkwp' --host='localhost' --port='3306' --user='mythtv' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick --add-drop-table 'mythconverg' 2>&1 1>'/var/lib/mythtv/db_backups//mythconverg-1299-20131102131805.sql'

mysqldump exited with status: 2
mysqldump output:
mysqldump: Got error: 144: Table './mythconverg/programgenres' is marked as crashed and last (automatic?) repair failed when using LOCK TABLES

***************************************************************************************************

Any ideas how to get a good backup file in 12.04.2 to put into 12.04.3?

---

### Post by aelfric55 on 2013-11-03
The error message was straightforward enough: the database has a crashed table. Mysqldump can't back up the database until it's fixed.

Usually you do this manually with mysqlcheck
```
$ mysqlcheck -u mythtv -p -A -e --auto-repair
``` (where -p will ask for the mysql password) is usually enough to do it. Takes about 20 minutes to run. Then you should be able to use a mysqldump-based backup script.

---

### Post by linuxhippy on 2013-11-05
That worked well-thanks for the help!

---

### Post by dannyboy79 on 2013-11-08
care to use the thread tools and mark it solved that way other users can find the solution. thanks

---

### Post by linuxhippy on 2013-11-08
done

---

