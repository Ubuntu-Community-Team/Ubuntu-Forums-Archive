---
title: "Back up recordings &amp; database"
date: 2011-01-29
forum: Mythbuntu
---

### Post by canoemoose on 2011-01-29
Hi all,
I'm faced with the interesting problem of my machine no longer playing video through the MythTV interface after upgrading to  MythTV 0.23.
Recorded videos still play through VLC or any other media player.  The MythTV interface crashes whenever navigating beyond a menu, so I can't even get into any settings to change them.

I therefore want to back up my recordings and reinstall Mythbuntu.

How do I back up the recordings and the database, so that when I restore the backup to the new installation MythTV finds the old recordings again?

Cheers :)

---

### Post by BicyclerBoy on 2011-01-29
Can we clarify ..

Recordings are missing from database listings ?
Videos are missing from videos listings ?

Videos will not play ?
Recordings will not play ? (Internal player)


Did you backup the database before upgrading ?
Did you run mythtv-setup after upgrade BEFORE anything else ?

---

### Post by canoemoose on 2011-01-29
No, everything appears in the listings, just the internal player doesn't play anything.

---

### Post by BicyclerBoy on 2011-01-29
I'm sure there was more than 1 question...

If you have a database backup before the upgrade you will be fine.
But if no user backup then go looking for the automatic backups (once a week).

Did you run mythtv-setup ?

If the new install tried to update the database schema then you should dump it before re-installing MythTV 0.22. Look in the logs.

Run mythtv-setup.
Look in the backend & frontend logs.
Run both from separate terminals with -v all options.
Uninstall all the mythtv extras.

---

### Post by nickrout on 2011-01-30
> **canoemoose said:**
> No, everything appears in the listings, just the internal player doesn't play anything.

there is one and one only way to properly backup and restore your database:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

Your recordings will be taking up a lot of space and will take a while to back up, best way is probably to an external drive.

by default they are in /var/lib/mythtv/recordings, but if you have added storage groups or moved the default location, that's up to you to keep track of and back up.

---

### Post by canoemoose on 2011-02-05
Sorry for my lack of replies - I've had exams over this past week.

The problem I'm having is that MythTV is crashing when I do anything that involves navigating beyond a menu.  If I try to do so (play a video/recording, access the settings, use the weather app), MythTV hangs and will only respond to the escape key, at which point it crashes. When run from a terminal, no errors are reported until the crash, at which point I just get a segfault.

I'm unable to run mythtv-setup - I get the exact same behaviour as the frontend.

This is a combined frontend and backend machine.

The recordings are stored on a separate drive, mounted at /mythtv, so to back up the recordings I'll simply unplug the drive.

Unless anyone can see a reason for me to do otherwise, I'll back the database up using the scripts linked to on the MythTV wiki, remove the recording drive, reinstall everything, then add the recordings drive and restore the database.

---

### Post by nickrout on 2011-02-05
and while you are about it, upgrade to 0.24

---

