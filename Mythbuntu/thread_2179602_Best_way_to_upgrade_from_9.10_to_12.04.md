---
title: "Best way to upgrade from 9.10 to 12.04?"
date: 2013-10-09
forum: Mythbuntu
---

### Post by roinane on 2013-10-09
Hi!

I have outdated Mythbuntu and now wondering, what is the best - or least painful way to take a leap over couple releases?
All my media and recordings are on separate physical disk and I want to keep them, as well my settings and recording schedules.

Is it possible just take a backup of the database, install Mythbuntu 12.04 from scratch and restore the database to the brand new Mythbuntu?
Are there any database changes between the releases 0.22 and 0.27 which could prevent this?

-r

---

### Post by Kirboosy on 2013-10-09
I looked on the MythTV wiki and it looks like they have some perl scripts you can run to backup the databases.

[Database Backup and Restore -- MythTV Wiki]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")

They have two perl scripts, one called [backup]("https://raw.github.com/MythTV/mythtv/master/mythtv/programs/scripts/database/mythconverg_backup.pl") and one called [restore]("https://raw.github.com/MythTV/mythtv/master/mythtv/programs/scripts/database/mythconverg_restore.pl")
> 
Save them to a location where you'll be able to find them and make them executable```
chmod a+x mythconverg_backup.pl mythconverg_restore.pl
```
Detailed help is available by executing either script with the --help argument. 
By saving the scripts to a directory in the user's PATH, you can  execute them without specifying a full path.  If you do not save them to  a directory in the PATH, you should execute the scripts from the  current directory as: ```
./mythconverg_backup.pl --help
```

Both scripts require several pieces of information, much of which can be  determined by looking at the MythTV configuration file, ~/.mythtv/config.xml.   However, the backup directory must be specified.  While the directory  can be specified with the --directory command-line argument, since it's  likely to be the same value for every run, it makes sense to add the  backup directory to a backup resource file (~/.mythtv/backuprc).  Do so by running the following command from a shell (not in MySQL), replacing the directory, /home/mythtv, with the desired backup directory path:

```
echo "DBBackupDirectory=/home/mythtv" > ~/.mythtv/backuprc
```
If you do not specify the directory as above, the backups will be  stored to a directory defined in the DB Backups storage group, falling  through to the Default storage group. 
At this point, creating a backup should be as easy as running: ```
mythconverg_backup.pl
```



Now for the upgrading part of Ubuntu. If you want to go the upgrade route you could upgrade the box to Ubuntu 10.04. From there you could jump to the next LTS release, 12.04. 

Personally I would recommend doing a fresh install of Ubuntu 12.04. However, I would test the database backup and restore funtionality before you commit to wiping the box down. Maybe stand up a VM of Mythbuntu 12.04 and see if it will restore the database to it. 

There might be a bug upon restoring the database since you will be importing a older MythTV database into a  newer system. They say online thought that MythTV will handle everything automatically.

It would be terrible to lose all those recordings!


Hope that helps!
~Caboose

---

### Post by Bucky Ball on 2013-10-09
Not sure how you'd upgrade it to 12.04 LTS. 10.04 LTS no longer supported.

Backup, clean install I'd say.

@Caboose885: Just noticed you've edited your post. Yep, clean install easiest, and possibly only, way to 12.04 from 9.10. ;)

---

### Post by Kirboosy on 2013-10-09
> **Bucky Ball said:**
> Not sure how you'd upgrade it to 12.04 LTS. 10.04 LTS no longer supported

Backup, clean install I'd say.

I just did a fresh 9.10 install in a VM and I launched the Update Manger  and selected "upgrade to 10.04". It installed without a hitch and I  upgraded it finally to 12.04. All over the internet and no CDs required.

In my test enviroment it worked beautifully but considering your system has years of use on it your "mileage may vary"

> **Bucky Ball said:**
> 
@Caboose885: Just noticed you've edited your post. Yep, clean install easiest, and possibly only, way to 12.04 from 9.10. ;)

Edited my post? Since when? ;)


Hope that helps!
~Caboose

PS. Even though it is possible to upgrade I would still recommend a clean install

---

### Post by Bucky Ball on 2013-10-09
Edited one minor detail when you were doing it cos it changed. Anyway, no matter. Too long ago now and inconsequential and you've since discovered some other magic so good luck with it. Well in hand and leave it to you.

---

### Post by Kirboosy on 2013-10-16
OP, Any update on your upgrade?

---

### Post by roinane on 2013-11-01
Thanks for the comments! I think I'll go for backup + fresh install of 12.04, testing it with another box before doing it in 'live'. Upgrade is now waiting for a suitable "maintenance window", i.e. wife & kids being away for a weekend ;)

---

