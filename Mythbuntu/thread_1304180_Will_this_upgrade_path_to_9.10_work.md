---
title: "Will this upgrade path to 9.10 work?"
date: 2009-10-29
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-10-29
I am running 9.04, but I want to clean install 9.10 and go to a larger hard disk with ext4 on it, so...

Can I,

1. msqldump the existing mythconverg database, 
2. install my new disk, 
3. clean install mythbuntu 9.10 on the new disk with ext4
4. restore the mysql dump of the old database to the new one
5. copy the old recordings across to the new 9.10 install
6. start myth or reboot

and will it work?

---

### Post by tgm4883 on 2009-10-29
> **ubnewbie2 said:**
> I am running 9.04, but I want to clean install 9.10 and go to a larger hard disk with ext4 on it, so...

Can I,

1. msqldump the existing mythconverg database, 
2. install my new disk, 
3. clean install mythbuntu 9.10 on the new disk with ext4
4. restore the mysql dump of the old database to the new one
5. copy the old recordings across to the new 9.10 install
6. start myth or reboot

and will it work?

Yep, that should work

---

### Post by ubnewbie2 on 2009-10-29
> **tgm4883 said:**
> Yep, that should work

Great news then, thanks.  

So the differences in database schema between versions will be handled automatically?

And, more a general question for long term myth installations, but are there any database clean-ups recommended after it's been running for a few years?

---

### Post by funkydan2 on 2009-10-29
There some new scripts provided with 0.22 for backuping and restoring the database. The MythTV wiki seems to suggest that it might be safest and easiest in your situation to download the scripts and use them for your upgrade (they work for backing up pre 0.22 versions).

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by ubnewbie2 on 2009-10-29
> **funkydan2 said:**
> There some new scripts provided with 0.22 for backuping and restoring the database. The MythTV wiki seems to suggest that it might be safest and easiest in your situation to download the scripts and use them for your upgrade (they work for backing up pre 0.22 versions).

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

That info could prove most valuable.  Thanks for the link.  I probably will use those scripts.

A quick read of the page left me with a small question about hostnames. Because my home network is small, I just work with the ip address of the mythtv box. Does mythtv invent a 'hostname' for itself (or maybe it was a default in a question during the install that I've forgotten)?  Where can I check what the hostname is, so I can make the new one the same?

---

