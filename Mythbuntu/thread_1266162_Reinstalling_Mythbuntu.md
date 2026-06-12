---
title: "Reinstalling Mythbuntu"
date: 2009-09-14
forum: Mythbuntu
---

### Post by chrisblue on 2009-09-14
I seem to have a very borked myth install. 9.04 was installed and doing an upgrade via the upgrade manager. I think a kernel upgrade quit halfway though and now I am unable to start Myth.

The splash screen loads then I get a dialog box on a teminal type screen saying 

Server  Authorisation dir (daemon /ServAuthDir) is set to /var/lib/gdm but this does not exist. please correct gdm config and restart gdm.

Then drops me to text login.

Have booted into a live disk and the gdm directory does exist but cannot be accessed.

Also have found that I cannot esc into the grub menu as the machine is booting to see if any earlier kernel will be any different. It seem as though at the stage in the boot sequence my keyboard is not recognised (tried both a USB and PS2 type).

Anyway it seems so borked that I think the best approach is to reinstall however of course i don't have a separate /home partition. Is there anyway I can backup my database and recording files so that I can re load them with a new install? If so where are they located on a default mythbuntu install? And how to I reinstall them?

Cheers

Chris

---

### Post by Boppy3125 on 2009-09-14
You mentioned booting into a live CD, can you do that and grab database and recordings?  I think it you put everything back into the same locations, you might be safe.  At the very least, you will have the recordings files to load up manually.  I believe I saw a thread at one time on a script to load up recordings.

---

### Post by klc5555 on 2009-09-14
> **chrisblue said:**
> I seem to have a very borked myth install. 9.04 was installed and doing an upgrade via the upgrade manager. I think a kernel upgrade quit halfway though and now I am unable to start Myth.

The splash screen loads then I get a dialog box on a teminal type screen saying 

Server  Authorisation dir (daemon /ServAuthDir) is set to /var/lib/gdm but this does not exist. please correct gdm config and restart gdm.

Then drops me to text login.

Have booted into a live disk and the gdm directory does exist but cannot be accessed.

Also have found that I cannot esc into the grub menu as the machine is booting to see if any earlier kernel will be any different. It seem as though at the stage in the boot sequence my keyboard is not recognised (tried both a USB and PS2 type).

Anyway it seems so borked that I think the best approach is to reinstall however of course i don't have a separate /home partition. Is there anyway I can backup my database and recording files so that I can re load them with a new install? If so where are they located on a default mythbuntu install? And how to I reinstall them?

Cheers

Chris

If you have a default Mythbuntu 9.04 install, your recordings are in /var/lib/mythtv/recordings If the system was originally installed as Mythbuntu 9.04 (or 8.10, or 8.04) /var/lib will be in its own (big) XFS partition. Your root partition (including /home) will be very small --8 to 12 Gigs. The actual database file (if I'm remembering correctly) should be at /var/lib/mysql/mythconverg  So your recordings and mythconverg should be on this separate non-root partition, in theory safe from a root partition meltdown. (I wonder if your root partition hit 100 percent full while updating...)

You may also have one or more automatic weekly database backups under /var/backups If you can in fact log in to your old installation and can run mysqldump from a prompt, you can try to also make an up-to-date mythconverg backup as described here: [http://mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://mythtv.org/wiki/User_Manual:Periodic_Maintenance)

mysqldump -u mythtv -pmythtv mythconverg -c > mythtv_backup.sql

where you substitute your actual mysql password after -p[no space]

After you have backed up the recordings by whatever means you have to access the drive, and have backed up one or more copies of whatever mythconverg backups you may have, have performed a clean mythbuntu install (if necessary), have set up the backend on this reconstituted system (so that it generates a new mythconverg database to restore to) and have restored your recordings to /var/lib/mythtv/recordings on your reconstituted system, you can restore your backed up mythconverg as described here: [http://mythtv.org/wiki/Backup_your_database](http://mythtv.org/wiki/Backup_your_database)

whose restore command looks a bit different in Ubuntu, and comes out as:

mysql -u mythtv -p[your-new-mysql-password] mythconverg < myth_bakup.sql

(substitute whatever your backup file of mythconverg is actually named for "myth_bakup.sql". No space after "-p") 

The backing up of the files prior to reinstallation I'll have to leave to you, depending on what means you have available and feel comfortable with; and what the root partition on the drive still has left in it. Possible methods include dropping in a second drive with an OS; booting from a rescue CD and mounting the XFS partition to copy things off; taking the drive out and mounting it in a second machine; installing a minimal Linux plus networking into your former root partition, then mounting the XFS partition to copy stuff off ... etc., etc.  

If through some freakish misfortune, you can't salvage any backup of mythconverg, but can still restore your recordings to a new Mythbuntu installation, you can use the script myth.rebuilddatabase.pl to add these old recordings (or any old recordings missing from your mythconverg backup) to your new database. Time-consuming and not perfect, but adequate.

Good luck.

---

### Post by chrisblue on 2009-09-14
Thanks klc. I will work though your suggestions and report back on my level of success which might be useful for someone else in the same predicament.

Good thought about maxing out the root partition. I will investigate further. I did run gparted from the live CD but none of the partitions showed their mount points so apart from one storage directory on drive b and the boot partition I wasn't sure how it was partitioned up on the original installation.

Cheers

Chris.

---

### Post by chrisblue on 2009-09-15
Hi klc,

Ok what I have found is that I have pretty much as you described with a 10gb root partition, a 2 gb swap and the balance, I assume for var/lib formatted as xfs.

I also have a 2nd drive that is dedicated for recordings and is part of a storage group in myth so I suspect that some of the storage is on the var/lib drive.

I have tried to check the partition using xfs_check and repair but it quits saying that it cant' find a matching superblock when I try the repair. I cannot mount the device, although that could be because I am doing it wrong.

Given that I cannot mount the device I can't get any data off it. I am thinking at this stage that I might reformat that drive and start again, rebuilding my recordings if possible and if not.....well it is just TV not life or death.

Cheers
Chris.

---

### Post by chrisblue on 2009-09-15
Ok tried one last thing before reformatting. In the partition editor there is a repair option. This didn't repair the drive, pretty much the same superblock message that I mentioned before but it did repeat something I read on the man pages for xfs_repair about the -L option that blows away the log file and recreates it.

It said that this was a risky operation but since I figured the next step was a format, how much worse could it get. So I tried and it repaired whatever the problem was!

Myth boots fine again...........still have some issues with the half installed upgrade but at least I can salvage both the database and recordings before reinstalling.

Thanks for the help......I will use your advice to do a decent back up tomorrow.

Chris.

---

### Post by klc5555 on 2009-09-15
The user manual page I cited also has a very useful little script to run from cron.daily that does a daily backup of the database. I added a line to mine to put extra copies of the daily mythconverg backups to each of the drives I use for recordings storage, because if the recordings survive you might as well have a database for them. It's made life a lot easier on several occasions.

Also I stopped keeping any recordings anywhere on the drive I use for the OS. Separate recordings drives only. This has allowed me to blow away everything on the OS drive and reinstall (or as when I upgraded directly from 7.10 to 9.04), then reconnect the recordings drives, restore the database, and be back operating as though nothing had happened in about an hour.  

Glad you were able to recover your recordings! 

All the best! :)

---

