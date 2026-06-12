---
title: "Mythtv database backup help"
date: 2010-10-15
forum: Mythbuntu
---

### Post by goffa on 2010-10-15
Hi, I'm trying to get daily backups of my mythtv database, I have tried to follow the instructions at [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)
>   **Quick Start**

Both scripts require several pieces of information, much of which can be determined by looking at the MythTV configuration files (~/.mythtv/config.xml or the MythTV mysql.txt file(s)). However, the backup directory must be specified. While the directory can be specified with the --directory command-line argument, since it's likely to be the same value for every run, it makes sense to add the backup directory to a backup resource file (~/.mythtv/backuprc). Do so by running the following command from a shell (not in MySQL), replacing the directory, "/home/mythtv", with the desired backup directory path: 

It is the first line that I am stuck at, what is the information I need from the confirguration files and what am I to do with this information. I tried using the --help --help but could not find any clear instruction.

---

### Post by tgm4883 on 2010-10-15
The script will scan those files for the proper information it needs. The only thing not in those files is the storage directory you want the DB to be saved to. You set that by running the following command

```
echo "DBBackupDirectory=/home/mythtv" > ~/.mythtv/backuprc
```

---

### Post by goffa on 2010-10-16
thanks tgm4883

After running mythconverg_backup.pl --verbose i get the following.

> htpc@htpc-desktop:~$ /home/htpc/.mythtv/mythconverg_backup.pl --verbose

Configuring environment:
  -    username: htpc
  -        HOME: /home/htpc
  - MYTHCONFDIR: /home/htpc/.mythtv

Parsing configuration files:
  - checking: /home/htpc/.mythtv/config.xml
     parsing: /home/htpc/.mythtv/config.xml
  - checking: /home/htpc/.mythtv/backuprc
     parsing: /home/htpc/.mythtv/backuprc

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
  DBBackupDirectory: /media/Backups/Database/Mythtv23
   DBBackupFilename: mythconverg-20101016144201.sql

Executables:
          mysqldump: mysqldump
           compress: gzip

Executing command:
'/usr/bin/mysqldump' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick --add-drop-table 'mythconverg' 2>&1 1>'/media/Backups/Database/Mythtv23/mythconverg-20101016144201.sql'

mysqldump exited with status: 2
mysqldump output:
mysqldump: Got error: 1045: Access denied for user 'htpc'@'localhost' (using password: NO) when trying to connect

htpc@htpc-desktop:~$ 

its checking the config.xml file which exists but contains not data, does not seem to want to continue and check the mysql.txt file.

---

### Post by tgm4883 on 2010-10-16
> **goffa said:**
> thanks tgm4883

After running mythconverg_backup.pl --verbose i get the following.



its checking the config.xml file which exists but contains not data, does not seem to want to continue and check the mysql.txt file.

That file contains no data? odd. Try deleting that file or moving it to see if the script will pick it up from mysql.txt

---

### Post by goffa on 2010-10-16
I was thinking the same, deleted the config.xml file and ran the script without error.

After rebooting a new config.xml file existed, this time with data. The script successfully ran again. 

Thanks for you help, this is now solved.

---

