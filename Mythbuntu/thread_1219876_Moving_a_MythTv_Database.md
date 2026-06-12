---
title: "Moving a MythTv Database"
date: 2009-07-22
forum: Mythbuntu
---

### Post by dotnick on 2009-07-22
I think I've found most everything I need to do this, but I need some clarification.

I have two older EIDE disks in my box, so I decided to get a new 1 TB SATA-II disk.  I'm now trying to move everything over to the new disk.  I have everything installed and I've been slowly moving all of my customized settings over for the system, but I'm still fuzzy on moving the database.

I found ..   [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

Do I need to run the backup script from my old install and then run the restore script from my new install to update the database?

my old database is /mnt/a/var/lib/mysql/mythconverge while my new is /var/lib/mysql/mythconverge

any clarification is welcome

---

### Post by ianhaycox on 2009-07-22
Is this a new system (fresh install), or have you just added the new disk to an existing system ?

If it's a new system then see [http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7) and if the hostname has changed [http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.15](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.15)

If you have added new disk should be a matter of taking the mysqldump from the working system with the old disk and then restoring it to the new database. I'm assuming the datafiles have not moved so the storage locations are the same as is the host name.

Hope that helps ?

---

### Post by dotnick on 2009-07-22
This is the same system, but I did a fresh install on the new hard disk.  I'm just moving things around.  So instead of booting off sda, now I'm booting off of sdb.  Since sdb is much faster, my boot up times have already dramatically decreased.  I'm hoping that my transcode and commercial flagging jobs will also be reduced in time now the the hard drive is faster.

I'll try this tonight, but this is my plan.

Boot into my "old" Mythbuntu 9.04 64 Bit
     Do the mysqldump steps as outlined on the mythtv website.

Reboot into "new" Mythbuntu 9.04 64 Bit
     Do the import steps as outlined on the mythtv website.

The commands only seem to get the recordings and information.  Is it also possible to import all of my previous settings for my tuners, schedulesdirect membership, acpi wakeup commands, etc.  I was really hoping to just copy my database over to the same location and it would "magically" open.  I kept the same hostname. Unfortunately that was not the case.

---

### Post by dotnick on 2009-07-22
I think I've done it, but it was certainly a round-about way to get there.

My mysql setup was iffy, couldn't log in as root.  So I did some searching, reinstalled mysql, re-created a root password, deleted the old mythconverg (from the new install), created mythconverg, and finally I was able to import the .sql file from my first (old) database.

Now I'm down to fixing the fine settings (ACPI wakeup, NVIDIA stuff) etc.  Almost there.

Thank you for the tip about mysqldump.  That was the ticket in the end.

---

