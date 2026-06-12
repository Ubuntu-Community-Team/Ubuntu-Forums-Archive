---
title: "Bare error.  Can I import tables from backup?"
date: 2010-12-05
forum: Mythbuntu
---

### Post by Chunk of Earth on 2010-12-05
I'm getting an error when restoring a backup from Mythbuntu 10.10/Myth 0.24 to Mythbuntu 10.10/Myth 0.24. (I upgraded,[COLOR=Blue] [had a problem]("http://ubuntuforums.org/showthread.php?t=1632963")[/COLOR], backed up, reinstalled and attempted to restore.) The error is as documented in [COLOR=Blue][bug number 661976]("https://bugs.launchpad.net/mythbuntu/+bug/661976")[/COLOR].
I'd really rather not restore all the configuration data, anyway, because I think there may be some cruft in the old database that was brought in from previous upgrades. All I'd really like to bring in are the old recordings table, current recordings table, and recording schedule. I can reconfigure the rest of it. Is there a way to use the backup file to import only those tables into my new database? (I have the actual recordings restored already, btw.)
Thanks.

---

### Post by tgm4883 on 2010-12-05
> **Chunk of Earth said:**
> I'm getting an error when restoring a backup from Mythbuntu 10.10/Myth 0.24 to Mythbuntu 10.10/Myth 0.24. (I upgraded,[COLOR=Blue] [had a problem]("http://ubuntuforums.org/showthread.php?t=1632963")[/COLOR], backed up, reinstalled and attempted to restore.) The error is as documented in [COLOR=Blue][bug number 661976]("https://bugs.launchpad.net/mythbuntu/+bug/661976")[/COLOR].
I'd really rather not restore all the configuration data, anyway, because I think there may be some cruft in the old database that was brought in from previous upgrades. All I'd really like to bring in are the old recordings table, current recordings table, and recording schedule. I can reconfigure the rest of it. Is there a way to use the backup file to import only those tables into my new database? (I have the actual recordings restored already, btw.)
Thanks.

If that bug is similar to what you are experiencing, can you attach the backup file to the bug report? You can open a new bug and mark it private if you prefer. 

The sql file on the bug report you specified didn't have a single piece of data in it. 

The tool itself cannot do what you want (partial restores). You may be able to check out this site and get the information you want. Bare uses the scripts here to backup/restore the database, but it's a full restore.
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup)

---

### Post by Chunk of Earth on 2010-12-06
> **tgm4883 said:**
> The tool itself cannot do what you want (partial restores). You may be able to check out this site and get the information you want. Bare uses the scripts here to backup/restore the database, but it's a full restore.
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Partial_restore_of_a_backup)

Thanks. That documentation talked me into doing a full restore, which I was able to perform using the mythconverg backup embedded in the bare backup. The full restore demonstrated that the original problem that pushed me into a reinstall was contained in the database -- probably the settings table. All the problems returned. That's why I wanted to do a partial restore.
After the full restore messed up the system I did a partial restore using the --drop_database and --create_database options. That gave me great results as far as getting my recording data back but it broke a bunch of other stuff including the plugins. That was a real bummer when mythweb gave me a blank screen.
So I decided to go with a hybrid restore -- a full restore followed by a partial restore. I had the uncharacteristic presence of mind to use bare to make a full backup of my new install immediately before I attempted to restore anything to it, so I had a good clean full backup to work with. I wiped out the mythconverg database, this time as recommended in the mythconverg_restore.pl help documentation (the sql  drop database statement) and then created a new database, also as recommended.
You know how it says to run the mc.sql script to create the new mythconverg database? Yeah, don't do that. It changed the password of the MySQL mythtv user so I spent a bunch of time trying to figure out why I couldn't restore or even log in to sql as mythtv (my dba fu is admittedly weak.) For the record, the MySQL commands that allowed continuance were```
UPDATE user SET Password=PASSWORD('*mypassword*') WHERE user='mythtv';
FLUSH PRIVILEGES;
```After creating the empty database (and resetting the mysql user password) I attempted to do a full restore using bare. I again received the python runtime error which surprised me since it was from the exact same installation that it was backed up on. As a workaround, I extracted the mythconverg backup embedded in the bare backup and did a full restore using the mythconverg_restore.pl script. That gave me a working but blank mythbuntu box again.
Then I did the same partial restore as before and this time I got a working mythbuntu installation with all my recording and scheduling data. I still had to manually add tuners and scan channels but that's not a huge deal.
I would recommend this hybrid method as a general system upgrade. After a few in-place upgrades your database can get a little wacked as mine did. I'm going to keep a small hard drive handy and do a fresh install of new mythbuntu versions on it, then make a full backup of its database to apply to in-place upgrades in case they get squirrelly.
I still have two other bugs in the new system. X is still dropping me out to the gdm occasionally and the mythfrontend crashes with an "Illegal Instruction" every time I attempt to adjust a running playback's time stretch to anything other than none.

> If that bug is similar to what you are experiencing, can you attach the backup file to the bug report?Done.

---

### Post by tgm4883 on 2010-12-06
What version of mythbuntu-common do you have installed?

```
dpkg -l mythbuntu-common
```

---

### Post by Chunk of Earth on 2010-12-07
> **tgm4883 said:**
> What version of mythbuntu-common do you have installed?

```
dpkg -l mythbuntu-common
```

mythbuntu-common       0.54-0ubuntu1

---

