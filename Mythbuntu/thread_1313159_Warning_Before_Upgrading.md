---
title: "Warning Before Upgrading"
date: 2009-11-03
forum: Mythbuntu
---

### Post by nickrout on 2009-11-03
I am reposting (with permission of the author) a warning that appeared on the mythtv-users mailing list. The post is by Michael Dean, the guru of mythtv database issues. The thread is archived here [http://www.gossamer-threads.com/lists/mythtv/users/405443](http://www.gossamer-threads.com/lists/mythtv/users/405443) - there has been some discussion.

Here goes:

Just a quick heads up to anyone who is upgrading to some version of 0.22-fixes or trunk.

Please make sure you:

 a) Back up your database before upgrading ([http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) )

 b) If you need to restore your database, DROP the old database before restoring ([http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore))

 c) I highly recommend using the restore script to do any DB restores--it does a bunch of sanity checks alerts you when something is wrong ( [http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Database_Restore) )

 d) Do not do a partial/"new hardware" restore--even if you're using new hardware

 e) If at all possible, do not change MythTV system host names (to keep the upgrade as simple as possible)

Mike




Details for those who want them:

If you're not doing an "in-place" upgrade (so you need to restore your DB backup), it is critical that you DROP any existing database /before/ restoring your database backup.  There have been several cases of users getting failed DB upgrades because they restored their 0.21-fixes backup on top of a 0.22 "blank" database provided by a distro/packages--meaning that MySQL incorrectly stuffs 0.21-fixes data into a 0.22+ schema version (thereby corrupting data).  Furthermore, after doing so, the DB schema changes will fail--in this case, the DB upgrade fails with the error, "Duplicate column name 'default_authority'."

Note that a full restore is recommended.  There's no real reason to do a partial/"new hardware" restore.  Definitely do not do "23.7 Moving your data to new hardware" at [http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7) .  Doing so will corrupt your data.  Even if you use the restore script to do a partial restore (so the data is not corrupted), a partial restore requires a very much more complex approach to upgrading and requires that you completely reconfigure your system after upgrade.  In short, don't do a partial restore.

If you change hostnames on a MythTV system, it is critical that you update all the data in the database to change the old hostname to the new hostname so recordings, settings, keybindings, jumppoints, and /much/ more are properly found for the host.  Doing so is not straightforward--do /not/ do so manually through SQL.  Instead, use the restore script to change the hostname ( [http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend) ).  However, it is critical that you change the hostname after restoring the database but /before/ running any mythtv applications (mythfrontend/mythbackend/mythtv-setup) on the host with the new hostname.  If you forget to do so, changing the hostname becomes /much/ more difficult--to the point that restoring your pre-upgrade backup and doing the upgrade properly, and using the script to change the hostname, is the easiest solution.

---

