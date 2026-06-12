---
title: "Recovering recorded programmes"
date: 2010-02-23
forum: Mythbuntu
---

### Post by byronmyth on 2010-02-23
Ok, after struggling to sort out a Nvidia driver 90-95 issue I ended up with my system in such a state that I did a fresh install. 
 
My system is a dual drive system, with all the recorded TV programmes on the second untouched drive. Is it possible to get those imported to the fresh install?

---

### Post by klc5555 on 2010-02-23
> **byronmyth said:**
> Ok, after struggling to sort out a Nvidia driver 90-95 issue I ended up with my system in such a state that I did a fresh install. 
 
My system is a dual drive system, with all the recorded TV programmes on the second untouched drive. Is it possible to get those imported to the fresh install?

If you made backup/backups of your old mythconverg database prior to all of this, then you can restore the best such backup and the job will be done. Refer to any of a number of pages like the mythtv wiki doc [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

If you made no backups, but mythbuntu was running for some time (weeks) there may have been one or more automated weekly backups dumped into /var/backups Restore one of these and the job will be mostly done.

If you have no backups at all to restore, or need to import the additional programs that may have accumulated since your last backup, you need to use the script myth.rebuilddatabase.pl  [http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)

The script is a lifesaver, but a bit slow and has some quirks that are not well-documented. First, it will search the previous 10 days of listings, but if it doesn't find anything, and you don't type in a title, the mythtv filename (e.g. 1785_20091212090000.mpg) becomes the title of the show. This of course may easily be corrected afterward (show-by-show) in the frontend.

Second, the script will always use the mythtv 4-digit code for the channel that it finds in the file rather than what the channel's more conventional number is. _Don't_ change this, because the script will rename the file to correspond to the channel info you type in, and while the program will play, other utilities like mythtranscode will no longer be able to access the new filename.

Third, the script will offer to commflag (and frame index with a seektable) each recording as it adds it. This is necessary, but mythcommflag may or may not properly build the seektable on a DVB recording --if later you find you can't skip forward or backward in such a DVB recording, you may have to rebuild the seektable for the recording individually yourself from a prompt, by using something along the lines of "mythtranscode --mpeg2 --buildindex -c -s" 


Adding an entire drive full of recordings by this script can get a bit ... tedious, so for the future I'd strongly recommend implementing a little daily database backup script cron job of the sort described in [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)    
I'd also recommend adding a directory to your recordings-storage drive along the lines of "/backups" and add a line to your script that would copy each daily mythconverg backup to this "/backups" directory, so that when the next meltdown happens (and there's always a next meltdown), as long as your recordings have survived on their drive your recordings metadata will have survived also. Then restoring everything will become a mere five-minute task from the command prompt.

Good luck!

---

