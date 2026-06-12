---
title: "Struggling to migrate 0.21 database info to 0.22"
date: 2009-10-31
forum: Mythbuntu
---

### Post by yonkiman on 2009-10-31
I'm trying to use the scripts and follow the instructions described here: [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I believe I backed up my old 0.21 database successfully, and the restore script finds the backed up data.  But if I run it with a mythconverg database in place (using "sudo dpkg-reconfigure mythtv-database" to create it), it always ends with:
[INDENT]Found 94 tables in the database.
WARNING: Database not empty.
ERROR: Unable to do a full restore. The database contains data.[/INDENT]

but if I delete the database using:
[INDENT]mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'[/INDENT]

I get: 
[INDENT]Unable to connect to database.
ERROR: The database does not exist.[/INDENT]

So I'm stuck.  I want a new 0.22 database with all my old recordings and other show info.  The script isn't happy if the database is there, and it's not happy if the database isn't there.  What am I missing?  

FYI, I have no info or data in the 0.22 system yet - I wanted to first get my recordings transferred successfully and then I'd start configuring the new system.

---

### Post by SFromley on 2009-10-31
I'm no expert, but have you tried it with a blank empty database (like just the tables, no actual items in them)?

Maybe it doesn't like to overwrite existing data, and doesn't know how to create the tables.

Don't worry, I'm sure a grown-up who knows the real answer will be along shortly. In the meantime, try that or make a cup of tea.

---

### Post by yonkiman on 2009-10-31
> **SFromley said:**
> I'm no expert, but have you tried it with a blank empty database (like just the tables, no actual items in them)?

Maybe it doesn't like to overwrite existing data, and doesn't know how to create the tables.

Just like me!  :-)  I'd be happy to try to create just the tables, but I have no idea how to do that...

---

### Post by SFromley on 2009-10-31
You don't want my advice - I just totally hosed mine and had to recreate the db from scratch using the backend setup.

after you have done:

```
mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'
```

you have to create a new database from the schema provided. mine went like:

```
mysql -uroot -p < /usr/share/mythtv/sql/mc.sql
```

That basically does this: 

```
CREATE DATABASE IF NOT EXISTS mythconverg;
GRANT ALL ON mythconverg.* TO mythtv@localhost IDENTIFIED BY "mythtv";
FLUSH PRIVILEGES;
GRANT CREATE TEMPORARY TABLES ON mythconverg.* TO mythtv@localhost IDENTIFIED BY "mythtv";
FLUSH PRIVILEGES;
ALTER DATABASE mythconverg DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;

```

Which if you're not too up on mysql, creates a db called mythconverg for user mythtv at localhost with password mythtv - you will need to know those in case you have to tell mythtv how to reconnect to its own db, such as in my case where I had to run the setup again.

Once you have created the db using the schema mc.sql as above, you should be able to restore your backup into it.

Good luck. :)

---

### Post by yonkiman on 2009-11-01
SF,

I followed the two steps you showed (exactly), and the commands executed with no errors (is there a verbose mode?).

But when I executed the restore script (mythconverg_restore.pl --verbose), it ended with "Unable to connect to database.  ERROR: The database does not exist."  Here's my full dump:

```
fred@mythtv:~$ mythconverg_restore.pl --verbose

Configuring environment:
  -    username: fred
  -        HOME: /home/fred
  - MYTHCONFDIR: /home/fred/.mythtv

Parsing configuration files:
  - checking: /home/fred/.mythtv/config.xml
     parsing: /home/fred/.mythtv/config.xml
  - checking: /home/fred/.mythtv/backuprc
     parsing: /home/fred/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

No filename specified. Attempting to find the newest database backup.
Using database backup file:
/media/storage/mythtvbackup/mythconverg-1214-20091031163635.sql.gz

Database Information:
         DBHostName: localhost
             DBPort: 0
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: /media/storage/mythtvbackup
   DBBackupFilename: mythconverg-1214-20091031163635.sql.gz
    create_database: 

Executables:
       mysql_client: mysql
         uncompress: gzip -d

Miscellaneous:
    partial_restore: no
   restore_xmltvids: no
    change_hostname: no

Checking database.
Unable to connect to database.

ERROR: The database does not exist.
```

You say you're no expert, but you sure know more than me - I'm totally over my head here!  Thanks for the support!

---

### Post by kja999 on 2009-11-01
As per the instructions you mentioned, under the database restore section, did you follow this part:  If you do not create the database before running the restore script and you did not specify the --create_database argument to the script, the script will exit with the error, &quot;ERROR: The database does not exist.&quot;      I had issue with the update as the schema wouldn't upgrade past version 1230. My solution was to use my old .21 database dump, and take the INSERT sections out for the tables I wanted. These were similar to you being, all the music_* ones and the recorded* ones. Effective but a pain ...

---

### Post by yonkiman on 2009-11-01
> **kja999 said:**
> As per the instructions you mentioned, under the database restore section, did you follow this part:  If you do not create the database before running the restore script and you did not specify the --create_database argument to the script, the script will exit with the error, &quot;ERROR: The database does not exist.&quot;      I had issue with the update as the schema wouldn't upgrade past version 1230. My solution was to use my old .21 database dump, and take the INSERT sections out for the tables I wanted. These were similar to you being, all the music_* ones and the recorded* ones. Effective but a pain ...

Would you mind showing a step-by-step example of whatever it is you just said?  I'm totally lost, only have a vague idea what a schema is, don't know what INSERT sections are, and really have no idea what to even try to do next.  Although I think I like the ability to pick and choose what parts of the database get imported.

I suppose this is happening because I'm trying to use these new scripts.  I have successfully migrated a database before using the old
```
mysqldump -h 192.168.1.105 -u mythtv -pxxxxxxxx mythconverg record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek | mysql -u mythtv -pxxxxxxxx mythconverg
```
command...  Would I be more or less likely to shoot myself in the foot with that?

You could put all I know about mysql into a mysql database that would comfortably fit inside an Intel 4004's on-board cache...

---

### Post by SiHa on 2009-11-01
> **yonkiman said:**
> 

I suppose this is happening because I'm trying to use these new scripts.  I have successfully migrated a database before using the old
```
mysqldump -h 192.168.1.105 -u mythtv -pxxxxxxxx mythconverg record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek | mysql -u mythtv -pxxxxxxxx mythconverg
```
command...  Would I be more or less likely to shoot myself in the foot with that?


That's how I just did it, worked like a charm.

> You could put all I know about mysql into a mysql database that would comfortably fit inside an Intel 4004's on-board cache... 
Me too.

---

### Post by yonkiman on 2009-11-01
That did it!

Thanks to everyone for the support!

---

