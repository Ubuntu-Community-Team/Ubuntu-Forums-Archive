---
title: "mythconverg_backup.pl reports 1045: Access denied for user 'laffi'@'localhost' (using"
date: 2009-11-20
forum: Mythbuntu
---

### Post by laffinet on 2009-11-20
I've been using the mythconverg_backup.pl script (via cron) for a while to backup my database and only just noticed that it hasn't produced any backups in 2 months or so :eek:

I tried running it manually and the error is:

```
mysqldump: Got error: 1045: Access denied for user 'laffi'@'localhost' (using password: NO) when trying to connect
```

The full output is:

> Configuring environment:
  -    username: laffi
  -        HOME: /home/laffi
  - MYTHCONFDIR: /home/laffi/.mythtv

Parsing configuration files:
  - checking: /home/laffi/.mythtv/config.xml
     parsing: /home/laffi/.mythtv/config.xml
  - checking: /home/laffi/.mythtv/backuprc
     parsing: /home/laffi/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

WARNING: DBName not specified. Using mythconverg

WARNING: DBHostName not specified.
         Assuming it is specified in the MySQL options file.

WARNING: DBUserName not specified.
         Assuming it is specified in the MySQL options file.

WARNING: DBPassword not specified.
         Assuming it is specified in the MySQL options file.

Database Information:
         DBHostName: 
             DBPort: -1
         DBUserName: 
         DBPassword: 
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: /var/lib/mythtv/drive3/backups
   DBBackupFilename: mythconverg-20091120173242.sql

Executables:
          mysqldump: mysqldump
           compress: gzip

Executing command:
'/usr/bin/mysqldump' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick --add-drop-table 'mythconverg' 2>&1 1>'/var/lib/mythtv/drive3/backups/mythconverg-20091120173242.sql'

mysqldump exited with status: 2
mysqldump output:
mysqldump: Got error: 1045: Access denied for user 'laffi'@'localhost' (using password: NO) when trying to connect

I can't recall changing anything so I have no idea why it stopped working or how to fix this. All I could find so far is things to do with database permissions, etc. but I can't figure it out.
Any ideas ?
Thanks.

---

### Post by laffinet on 2009-11-20
I managed to solve this, but why did it break in the first place...???

I added 

```
DBUserName=mythtv
DBPassword=<mymythvonvergpassword>
```

to the file 

```
/home/laffi/.mythtv/backuprc
```


and everything is working ok now.

Still puzzled why it stopped working...

---

### Post by earlneath on 2010-06-03
Thanks for this I was struggling until I found your post!

---

### Post by tgm4883 on 2010-06-03
Odd, I'm not sure why it broke. It is entirely possible that upstream changed how the script works and it now needs that file. That would get updated during regular system updates if you have auto-builds installed.

---

