---
title: "Need help restoring database using mythconverg_restore.pl"
date: 2010-09-22
forum: Mythbuntu
---

### Post by yonkiman on 2010-09-22
Well, came home today to a blank screen and my 1.5TB Seagate Barracuda LP system drive clicking away.  It's a goner...

Fortunately I had an image of the system on another drive, so I'm already back up and running, but the image is months old, so I need to restore the MythTV database.  I've got the automatic backups (the latest is mythconverg-1254-20100918074830.sql.gz), so it's almost looking like everything's gonna be OK, but when I run mythconverg_restore.pl, it says "ERROR: Unable to do a full restore. The database contains data."

So I go [here]("http://www.mythtv.org/wiki/Database_Backup_and_Restore") and it says "When restoring, you're simply restoring the database schema and data, so the database itself must be created first."

Now my database is already created, it's just out of date.  Do I really need to proceed as if I have no database?  The link it sends me to says this is as easy as typing "$ mysql < mc.sql", but nothing I've ever done to mysql directly has ever been easy.

Can anyone tell me what's my next step?  I don't want to screw up the database I have - even though it's months old, it's better than losing the info for ALL my 300+ programs.

Thanks,
Fred

---

### Post by ian dobson on 2010-09-23
Hi,

Have a look here [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

extra this bit:- 
mythconverg_restore.pl --drop_database --create_database --filename mythconverg-1214-20080626150513.sql.gz

Hope this helps
Regards
Ian Dobson

---

### Post by yonkiman on 2010-09-23
> **ian dobson said:**
> Hi,
Have a look here [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

extra this bit:- 
mythconverg_restore.pl --drop_database --create_database --filename mythconverg-1214-20080626150513.sql.gz


Hi Ian,

Thanks for the tip!  Unfortunately the script returns "Unknown option: drop_database".  

At least I have something to look into now...

Thanks again.

---

### Post by ian dobson on 2010-09-23
Hi,

Then maybe you can just drop the database yourself with mysqladmin then run the restore script without the drop-database option.

From the help text:-
To do a full restore:
Ensure you have an empty database. If you are replacing an existing database,
you must first drop the old database. You may do this using the mysql client
executable by issuing the command:

# mysql -umythtv -p mythconverg -e "DROP DATABASE IF EXISTS mythconverg;"

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-09-23
> **yonkiman said:**
> Hi Ian,

Thanks for the tip!  Unfortunately the script returns "Unknown option: drop_database".  

At least I have something to look into now...

Thanks again.

That is a new feature in a newer version of mythtv. If you enable 0.23.1 auto-builds it should be available to you.

---

### Post by yonkiman on 2010-09-23
> **tgm4883 said:**
> That is a new feature in a newer version of mythtv. If you enable 0.23.1 auto-builds it should be available to you.

Hmmm...  So I did enable 0.23.1 autobuilds and updated everything, but I still get the same error.  I checked the version of the script:
```

$ mythconverg_restore.pl --version
MythTV Database Restore Script
mythconverg_restore.pl
version: 1.0.8

```

Is 1.0.8 the right version?

---

### Post by yonkiman on 2010-09-23
> **ian dobson said:**
> Hi,
Then maybe you can just drop the database yourself with mysqladmin then run the restore script without the drop-database option.


Thanks again Ian.  I'll try that if upgrading to 0.23.1 doesn't work (which it doesn't seem to so far).  But the fact that the drop_database option doesn't work makes me a little suspect of the rest of the script...

---

### Post by ian dobson on 2010-09-23
Hi,

I'm running 23.1 and have version  1.0.13 of the script.

Note the script is in /usr/share/mythtv/ which is not on my path so I have to start it with /usr/share/mythtv/mythconverg_restore.pl  --version

They seemed to have afew problems with the weekly builds server last night (8 hours ago) so maybe try an apt-get update/upgrade now.

Regards
Ian Dobson

---

### Post by yonkiman on 2010-09-24
> **ian dobson said:**
> 
Note the script is in /usr/share/mythtv/ which is not on my path so I have to start it with /usr/share/mythtv/mythconverg_restore.pl  --version


Yep, found it there.  Thanks!

---

### Post by yonkiman on 2010-09-25
> **ian dobson said:**
> Note the script is in /usr/share/mythtv/ 

Worked perfectly - thanks everyone!

---

