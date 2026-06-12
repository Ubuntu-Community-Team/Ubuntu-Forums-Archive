---
title: "Strange mythbuntu_backup.pl error"
date: 2010-10-16
forum: Mythbuntu
---

### Post by ahood on 2010-10-16
Hello,

I am interested in upgrading my mythbuntu 8.04 to 10.04 and the first step is to backup the database. I am following the steps described Mythtv [Database Backup and Restore]("http://www.mythtv.org/wiki/Database_Backup_and_Restore#Script-based_Database_Backup_and_Restore") Wiki.

I saved the 'mythconverg_backup.pl' file to /usr/share/mythtv and made it executable for owner and group. I also changed the group to 'mythtv'. 

I do the recommended command...
> echo "DBBackupDirectory=/home/username" > ~/.mythtv/backuprc

*Note: I replaced 'username' with the username used to log into the system and administer commands.*

I execute the backup script using the command...
> perl /usr/share/mythtv/mythconverg_backup.pl 

I then get the following error message...
> syntax error at /usr/share/mythtv/mythconverg_backup.pl line 8, near "<"
Unrecognized character \xE2 at /usr/share/mythtv/mythconverg_backup.pl line 10.

I have googled this error but cannot find information on it.

Any suggestion on resolving the error will be appreciated.

Perhaps there is an alternative way to backup the database?

With kind regards,

DrH

Note: The error above was caused by downloading the mythconverg_backup.pl file incorrectly using the command line tool wget. After using the correct command I was able to successfully execute a backup of the mysql database.

---

