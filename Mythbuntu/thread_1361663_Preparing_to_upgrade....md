---
title: "Preparing to upgrade..."
date: 2009-12-22
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-12-22
I'm currently using Mythbuntu 8.10, and I'm minded to upgrade to 9.10. This is best done as a clean install, rather than upgrading to 9.04 and then to 9.10, right?

So, before I wipe my hard disk for the install, I want to make sure I haven't forgotten anything.

My media files are all nicely backed up, so I can get them back again easily enough by just copying them back from where they are backed up, right?

I have a couple of custom scripts for backup, which can also easily be restored from where they are backed up, right?

My biggest worry is the database. I take regular backups using the mysqldump command. Will it be easy enough to restore the database from one of those backups simply by following the instructions on [this page]("http://www.mythtv.org/wiki/Database_Backup_and_Restore")? Is that a foolproof process or are there things that can go wrong?

I've made a note of the configuration settings that I've tweaked since my original installation. (I did this manually, but if there is a way to export all my configuration settings to a file, that would make sure I didn't miss anything).

Am I ready to wipe my hard disk and go for a fresh installation, or have I forgotten anything? I'm only using the machine for its MythTV functions, there's no email or anything like that.

---

### Post by newlinux on 2009-12-22
Your plan sounds okay and if you have a full backup of the DB it shouldn't be a problem to restore it and then have it automatically upgraded to the new schema (not speaking from personal experience with .22 - my backends are still on 8.04 and myth .21 - I'm not upgrading until the next LTS - 10.04. But this is how it worked when I went from .20 to .21...). Nothing is fullproof, but you can practice resoring your DB on your current install by restoring it to a different DB name. I did that the first time I did it just to make sure - then I compared the data in the tables and realized it worked just fine. I didn't use those scripts in the page you reference, I just used mysql to create a db and then import the data into it. Not sure if those scripts allow you the flexibility to import the backup to whatever database name you want...


It's hard to know what if you are missing anything without knowing what customizations you've made - but generally, as far a myth is concerned, the stuff you want are the DB, the media, maybe fstab if you are mounting network shares for video, LIRC configuration files, and external player configuration files.

Your backup scripts will probably work fine in your new installation - but there is no way to know for sure without seeing it, but if it using standard commands or something like rsync I don't imagine it would have any issues. i've been using the same backup scripts for years. 

Just my 2 cents. Good luck.

---

### Post by NautiusMaximus on 2009-12-22
Thanks, newlinux, the suggestion to try restoring the data to a new DB in my existing system sounds like a truly excellent one, which would certainly give me vastly increased confidence that things will work after the upgrade.

For a complete MySQL novice like me, could you be kind enough to suggest how to do the test (and indeed the real) restore, either with some the commands I need if that can be done easily or by pointing me to a suitable web page with instructions if that would be more appropriate?

Thanks for the reminder about fstab. That was actually quite a bit of fun to get working, so I'll certainly make sure that's backed up. I definitely won't be backing up my LIRC files, as I've never got the remote to work anyway. I shall try that anew with the new installation, and hope that it works better than in 8.10.

Thanks
NM

---

### Post by VastOne on 2009-12-22
Do you have /home on its own partition?  If you do, life is so much easier.  If not, I would try to get that done before installing new as it keeps your config the same with the new install

---

### Post by larsolav on 2009-12-22
I did a clean install on upgraded equipment from 8.04 to 9.10.
I found Simon's post number [16 ]("http://ubuntuforums.org/showpost.php?p=8182896&postcount=16") in this [thread ]("http://ubuntuforums.org/showthread.php?t=1292030")very simple and helpful. It worked for Simon and me.

---

### Post by newlinux on 2009-12-22
> **NautiusMaximus said:**
> Thanks, newlinux, the suggestion to try restoring the data to a new DB in my existing system sounds like a truly excellent one, which would certainly give me vastly increased confidence that things will work after the upgrade.

For a complete MySQL novice like me, could you be kind enough to suggest how to do the test (and indeed the real) restore, either with some the commands I need if that can be done easily or by pointing me to a suitable web page with instructions if that would be more appropriate?

Thanks for the reminder about fstab. That was actually quite a bit of fun to get working, so I'll certainly make sure that's backed up. I definitely won't be backing up my LIRC files, as I've never got the remote to work anyway. I shall try that anew with the new installation, and hope that it works better than in 8.10.

Thanks
NM

I'm not an expert in mysql - but I think the following commands would work (I use phpmyadmin for most mysql administration).
To do the whole database, I just use mysqldump to backup
```

mysqldump -u <myth_user> -p<mythdb_password>  <myth_db_name> > mythdatabase.sql

```

Then to restore the DB I would create a backup database and import the backup.


```

mysql -u root -p <rootdb_password> create database mythbackup
mysql -u root -p <rootdb_password> mythbackup < mythdatabase.sql

```

I think that will work...

---

### Post by NautiusMaximus on 2009-12-23
Many thanks for that, newlinux. I'll give that a try. That looks so simple that even I should be able to use it!

---

### Post by NautiusMaximus on 2009-12-27
OK, I tried that, and once I'd realised that there was, by default, no password for the MySQL root user, it worked more or less OK.

The only snag was that my mythtv MySQL user had no permissions to the newly created database. I was able to fix this simply by issuing the following statement within mysql (while logged into mysql as root):

```
GRANT ALL ON mythbackup.* TO 'mythtv'@'localhost'
```

Is it that simple? I gather that what I'll need to do after the upgrade is to delete the existing mythconverg database, replace it with an empty new one, and restore from the backup .sql file. If I then issue the GRANT ALL command above, will that be mission accomplished?

Many thanks
NM

---

### Post by nickrout on 2009-12-27
Backing up and restoring the database is well documented on the wiki page you referred to and also here:

[http://www.gossamer-threads.com/lists/mythtv/users/405443](http://www.gossamer-threads.com/lists/mythtv/users/405443)

---

### Post by ubnewbie2 on 2009-12-27
> **nickrout said:**
> Backing up and restoring the database is well documented on the wiki page you referred to and also here:

[http://www.gossamer-threads.com/lists/mythtv/users/405443](http://www.gossamer-threads.com/lists/mythtv/users/405443)

Yes, and I found the easiest way was to install the mysql-admin GUI. It's handy if you run into any troubles and need to drop and recreate the database, or the mythtv user, and backup and restore with it is a breeze.

---

### Post by nickrout on 2009-12-27
> **ubnewbie2 said:**
> Yes, and I found the easiest way was to install the mysql-admin GUI. It's handy if you run into any troubles and need to drop and recreate the database, or the mythtv user, and backup and restore with it is a breeze.

but without the checks and balances that the official script provides.  You have been warned!

---

### Post by newlinux on 2009-12-28
> **NautiusMaximus said:**
> OK, I tried that, and once I'd realised that there was, by default, no password for the MySQL root user, it worked more or less OK.

The only snag was that my mythtv MySQL user had no permissions to the newly created database. I was able to fix this simply by issuing the following statement within mysql (while logged into mysql as root):

```
GRANT ALL ON mythbackup.* TO 'mythtv'@'localhost'
```

Is it that simple? I gather that what I'll need to do after the upgrade is to delete the existing mythconverg database, replace it with an empty new one, and restore from the backup .sql file. If I then issue the GRANT ALL command above, will that be mission accomplished?

Many thanks
NM

Yeah i should have mentioned the default password for root. Didn't think about the permissions, but I probably was accessing the backup as the root user when I was just testing it out. When you go to really do this, I'd just create a backup, and then use the official scripts. This was more of a quick test that wouldn't overwrite any existing DBs.

---

### Post by ubnewbie2 on 2009-12-28
> **nickrout said:**
> but without the checks and balances that the official script provides.  You have been warned!

Yes I have been :-)  I should have stressed that it is most useful for getting you out of trouble.  I agree the script should be the first resource tried. If that fails, then the GUI is a great resource for sorting it out.

---

