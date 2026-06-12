---
title: "mythbuntu reinstall - how to import old recordings"
date: 2011-02-06
forum: Mythbuntu
---

### Post by davidstoll on 2011-02-06
I had to format and reinstall Mythbuntu.
I do have a backup of my / (for the most part).
My recordings were saved on a separate HDD, which has been remounted and is ready to go.
Mythtv is set to record to this other drive/path as it was before.

So, there are a bunch of mpg files that I need to bring back into mythtv, but I don't want to have to go through every single one..description, channel, etc.

Is there a database file somewhere from my backup that I can use that has info for brining them back?...and how do I actually import them?  With mythconverg-import.pl?  How do I do this so it can use the old database?

Thanks!

---

### Post by nickrout on 2011-02-06
Put the recordings in a storage group on the new setup.

Run the restore script from this page:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I assume you did back up your database before wiping the previous system?

If not, mythbuntu should have done a weekly backup, you will be missing data for the point between your last backup and the date you wiped.

If you are not sure where the backups were saved, try 

locate -r mythconverg.*gz

---

### Post by davidstoll on 2011-02-06
> **nickrout said:**
> Put the recordings in a storage group on the new setup.

Run the restore script from this page:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I assume you did back up your database before wiping the previous system?

If not, mythbuntu should have done a weekly backup, you will be missing data for the point between your last backup and the date you wiped.

If you are not sure where the backups were saved, try 

locate -r mythconverg.*gz

I said format...I'm sorry I actually put a new drive in.  The old drive all of a sudden had so many errors (not physical), but I had a hell of a time even booting it up.

I tried to run mythconverg_backup, but it said it is read only.  The latest backup file is like 7 months old...I don't know why it would have stopped.

Is there any way to get the live database, rather than a backup?

---

### Post by nickrout on 2011-02-06
What do you mean "live database"?

If you mean the binary files under /var/lib/mysql/mythconverg, then they are usually not portable from one version of mysql to another. The properly recognised way to do it is a text backup, such as created by the proper scripts.

But I think the backups _should_ be stored on the data disk, are you sure that they do not exist there?

---

### Post by davidstoll on 2011-02-06
> **nickrout said:**
> What do you mean "live database"?

If you mean the binary files under /var/lib/mysql/mythconverg, then they are usually not portable from one version of mysql to another. The properly recognised way to do it is a text backup, such as created by the proper scripts.

But I think the backups _should_ be stored on the data disk, are you sure that they do not exist there?

There are some mythconverg.sql.gz .0 .1 .2....
files in /var/backups/

But they seem to be 6 months old.

---

### Post by davidstoll on 2011-02-06
So, I'm booted after all the checking and fixing finished..

when I run /usr/share/mythtv/mythconverg_backup.pl
it tells me that /tmp/XXXXXXXXX: Could not create temp file /tmp/COTGs...: Read-only file system at ./mythconverg_backup.pl line 941

It seems /tmp is read only, but not a separate mount or anything, it's just a folder on / as far as I know.

Is it trying to use /tmp as a temp folder while it exports and then moves it to whereever?  Can I just have it use a different temp folder or write it directly somewhere else?

I tried the --directory option, but I get the same error.

---

### Post by davidstoll on 2011-02-06
Since mounting the old drive is a problem, can I run mythconverge_backup.pl if I use a live cd or if I put it in an external USB enclosure?

I tried using a live CD, but the backup file it created was 0 bytes...do you know the command to use to pull the data off a drive other than /  ?

Thanks

---

### Post by davidstoll on 2011-02-07
I re-bound my /tmp to a different physical drive and that seemed to help, but I still get an error and the output file is only 801 bytes.

```
Configuring environment:
  -    username: root
  -        HOME: /home/david
  - MYTHCONFDIR: /home/david/.mythtv

Parsing configuration files:
  - checking: /home/david/.mythtv/config.xml
     parsing: /home/david/.mythtv/config.xml
  - checking: /home/david/.mythtv/backuprc
     parsing: /home/david/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

No DBSchemaVer specified, querying database.
Found DBSchemaVer: 1254.

Database Information:
         DBHostName: localhost
             DBPort: 0
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 1254
  DBBackupDirectory: /recordings/tmp/backups/
   DBBackupFilename: mythconverg-1254-20110206235416.sql

Executables:
          mysqldump: mysqldump
           compress: bzip2

Attempting to use supplied password for mysqldump.
Any [client] or [mysqldump] password specified in the MySQL options file will take precedence.

Executing command:
'/usr/bin/mysqldump' --defaults-extra-file='/tmp/Kb4aev9OI1' --host='localhost' --user='mythtv' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick --add-drop-table 'mythconverg' 2>&1 1>'/recordings/tmp/backups//mythconverg-1254-20110206235416.sql'

mysqldump exited with status: 2
mysqldump output:
mysqldump: Got error: 144: Table './mythconverg/oldprogram' is marked as crashed and last (automatic?) repair failed when using LOCK TABLES
```

I still think I need to run the script from a properly booted machine on this drive after I mount it in an external USB drive...if anyone knows if it is possible and can help me.

:(

---

### Post by nickrout on 2011-02-07
looks like your old database is damaged. Try running up mythweb and using the repair functionality there. 

I am cautious to recommend this because I am not fully sure of the ramifications, but if oldprogram is the only crashed table, you could drop it and then make the backup. Given the description of the table in the wiki, it possibly will not affect operation, but I am no expert.

[http://www.mythtv.org/wiki/Oldprogram_table](http://www.mythtv.org/wiki/Oldprogram_table)

> The oldprogram table contains the titles of everything that has been in the program table (your listings) in the past 320 days. The cutoff is just short of a year so that it won't grow forever and so holiday specials will appear in the New Titles list next year

ie it **seems **to be used to work out what is a new program and what has screened before.

---

### Post by alien878 on 2011-02-09
If you are having troubles with mythweb, you can stop the backend (important) and run the following command:
```
mysqlcheck -r -umythtv -p<password> mythconverg
```I ran into this problem once and that command worked perfectly.

---

### Post by davidstoll on 2011-02-09
> **alien878 said:**
> If you are having troubles with mythweb, you can stop the backend (important) and run the following command:
```
mysqlcheck -r -umythtv -p<password> mythconverg
```I ran into this problem once and that command worked perfectly.

Well, I think the drive is too messed up now because mythweb isn't working and the boot process is excruciatingly long and laborious....somtimes I can't even get to a prompt.  It takes like an hour to *maybe* get it booted.

What have I learned from all this?
1) don't remove python!
2) make sure backup scripts are running
3) if this happens again, mythweb may be able to help
4) there are a lot of very nice and helpful people here

The drive is just toast as far as booting goes, but at least I can put it in an external USB case and pull my home dir off.

I moved the videos from my secondary drive to a different folder (so the new installation can resume its recordings of future shows) and I'll watch them with VLC over the coming days/weeks/months.

backup backup backup

Thanks so much to everyone.  At least if anyone else (or if it happens to me again), I'll have this thread to go back to for help.

:)

---

### Post by alien878 on 2011-02-10
> **davidstoll said:**
> What have I learned from all this?
1) don't remove python!
2) make sure backup scripts are running
3) if this happens again, mythweb may be able to help
4) there are a lot of very nice and helpful people here5) Don't backup to the same drive (default for the backup scripts)

Sorry you had no luck.

---

