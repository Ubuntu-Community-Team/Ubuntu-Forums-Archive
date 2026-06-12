---
title: "Mythbuntu suddenly stopped recording"
date: 2009-09-25
forum: Mythbuntu
---

### Post by zuixro on 2009-09-25
I've had an Mythbuntu 9.04 backend/frontend running for about 2 weeks. 2 nights ago I noticed that nothing new had been recorded that day. I logged into MythWeb and checked the backend status. Everything seemed normal. I looked under upcoming recordings and the list was empty. I looked under recording schedules and they were all fine. I searched for some of the shows and saw that there were new episodes coming up that should be recorded, but when it came time, they weren't. I know it's not the recording schedules because they worked fine for over 2 weeks. Basically it just suddenly stopped recording. Live TV works ok, and I can manually start a recording from there, but the scheduled recordings don't work.

The night that it stopped working, I had rebooted it (it was kindof a rough shutdown, it locked up, when I hit shutdown and I had to do a hard shutdown), and also tried using my Macbook Pro as a frontend (which worked, but I noticed that a few episodes of one show had been deleted (just the files, they were still in the database) I also noticed that nothing was coming up under the recordings). I think that I had also enabled "MySQL Tweaks", but I can't remember if that was that night when I enabled it. I disabled it though, and that hasn't helped.

I have a feeling that it is some problem in the database but I'm not sure. I've tried rebooting, fidling with database settings (always setting them back), running mythfilldatabase, nothing has worked, I've tried all the "Database Actions" under MythWeb, and all the tables checkout ok.  I'm sure it's something simple that I'm missing. Anyone else have a similar problem? Anything I could try would help.

---

### Post by klc5555 on 2009-09-25
> **zuixro said:**
> I've had an Mythbuntu 9.04 backend/frontend running for about 2 weeks. 2 nights ago I noticed that nothing new had been recorded that day. I logged into MythWeb and checked the backend status. Everything seemed normal. I looked under upcoming recordings and the list was empty. I looked under recording schedules and they were all fine. I searched for some of the shows and saw that there were new episodes coming up that should be recorded, but when it came time, they weren't. I know it's not the recording schedules because they worked fine for over 2 weeks. Basically it just suddenly stopped recording. Live TV works ok, and I can manually start a recording from there, but the scheduled recordings don't work.

The night that it stopped working, I had rebooted it (it was kindof a rough shutdown, it locked up, when I hit shutdown and I had to do a hard shutdown), and also tried using my Macbook Pro as a frontend (which worked, but I noticed that a few episodes of one show had been deleted (just the files, they were still in the database) I also noticed that nothing was coming up under the recordings). I think that I had also enabled "MySQL Tweaks", but I can't remember if that was that night when I enabled it. I disabled it though, and that hasn't helped.

I have a feeling that it is some problem in the database but I'm not sure. I've tried rebooting, fidling with database settings (always setting them back), running mythfilldatabase, nothing has worked, I've tried all the "Database Actions" under MythWeb, and all the tables checkout ok.  I'm sure it's something simple that I'm missing. Anyone else have a similar problem? Anything I could try would help.

1) Don't do dirty shutdowns. MySQL databases are kinda fragile and one time out of every 3 or 4 dirty shutdowns or resets you end up either damaging the mythconverg database or toasting it completely. 

2) Check your backend log in /var/logs/mythtv from the time a recording has failed to happen, to see what messages may have been left behind. Might not be database at all --sometimes the XFS  filesystem (of the partition holding /var/lib/) may need a bit of massaging after a dirty shutdown. (Though it's usually the database... <sigh>) 

3) If it really does seem to be the database, try doing a proper shutdown, let the machine set off for a few (>30) seconds, and then power it back up (a "cold boot"). Every once in a while this will fix things all by itself. If it doesn't, your next step will be to run the database optimize and repair scripts from the "advanced" page of the Myth Control Centre.

4) You can try (from a terminal):
 mysqlcheck --auto-repair -A -u mythtv -pmysqlpass

where you substitute your real mysql password (available in the first page of your frontend's "General" setup, or in the file "mysql.txt" in the "mythtv" user directory) for "mysqlpass" after "-p" (no space after -p)

5) You may end up having to restore your mythconverg database from a backup. Most recent one from before the dirty shutdown if you've been doing daily backups like the mythtv manual recommends ( [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance) )
or if you haven't, then the most recent weekly backup found in the directory /var/backups if you have accumulated any. Recordings made since the date of the backup that you restore from can be added back into the database later.

6) Don't do dirty shutdowns.

---

### Post by zuixro on 2009-09-26
> **klc5555 said:**
> 1) Don't do dirty shutdowns. MySQL databases are kinda fragile and one time out of every 3 or 4 dirty shutdowns or resets you end up either damaging the mythconverg database or toasting it completely.

I avoid it, this one was an accident.

> **klc5555 said:**
> 2) Check your backend log in /var/logs/mythtv from the time a recording has failed to happen, to see what messages may have been left behind. Might not be database at all --sometimes the XFS filesystem (of the partition holding /var/lib/) may need a bit of massaging after a dirty shutdown. (Though it's usually the database... <sigh>)

I looked in the log but couldn't find anything of interest...
How does one go about "massaging" an XFS file system?

> **klc5555 said:**
> 3) If it really does seem to be the database, try doing a proper shutdown, let the machine set off for a few (>30) seconds, and then power it back up (a "cold boot"). Every once in a while this will fix things all by itself. If it doesn't, your next step will be to run the database optimize and repair scripts from the "advanced" page of the Myth Control Centre.

Tried it, Then tried it again after ever solution I tried.

Tried the optimization button, but there was no Repair button (I did try the repair button from MythWeb, I think it's the same thing)

> **klc5555 said:**
> 4) You can try (from a terminal):
mysqlcheck --auto-repair -A -u mythtv -pmysqlpass

where you substitute your real mysql password (available in the first page of your frontend's "General" setup, or in the file "mysql.txt" in the "mythtv" user directory) for "mysqlpass" after "-p" (no space after -p)[/quote]

Tried it, nope.

> **klc5555 said:**
> 5) You may end up having to restore your mythconverg database from a backup. Most recent one from before the dirty shutdown if you've been doing daily backups like the mythtv manual recommends ( [http://www.mythtv.org/wiki/User_Manualeriodic_Maintenance](http://www.mythtv.org/wiki/User_Manualeriodic_Maintenance) )
or if you haven't, then the most recent weekly backup found in the directory /var/backups if you have accumulated any. Recordings made since the date of the backup that you restore from can be added back into the database later.

I didn't have any backups that I made (Though I will certainly start now) I restored one from the 20th (before it stopped recording) and that didn't work.

> **klc5555 said:**
> 6) Don't do dirty shutdowns.

See answer 1.


One other thing that I may have done, I had some NFS shared folders from my NAS added for a while, but IP addresses changed a few weeks ago and they were broken. I went into /etc/fstab and fixed them. I don't know why that would have broken it, but you never know.


An interesting note: When I set up a recording schedule, even though I select "Record all episodes on any channel," none of them are selected when I go back to the guide. Some that I have already recorded show up as such though.  This leads me to believe that it's a problem with whatever does the scheduling. Is there something like "mythscheduler" or something that sets it when to record? If it exists, that sounds like a likely cuprit.

I'm about to the point where I either:
A: Rebuild the entire database
or
B: Reinstall MythBuntu


Comments? Ideas?

---

### Post by klc5555 on 2009-09-26
> **zuixro said:**
> I avoid it, this one was an accident.



I looked in the log but couldn't find anything of interest...
How does one go about "massaging" an XFS file system?



xfs_check, xfs_db, xfs_repair would be a start. XFS is less forgiving of dirty shutdowns than ext3 is. 

At this point, I believe you'd be better off taking a couple of dbbackups, backing up whatever recordings you may have, wiping, reinstalling, and restoring  db and recordings from the backups. Not elegant, but on a two-week-old system with a minimal data history, it's more likely to be time-effective than several days spent in debugging and repair. Particularly when an inordinate amount of tinkering around and about the original incident may have obscured whatever the underlying failure was and render it more difficult to diagnose and fix.

---

### Post by nigels on 2009-11-14
> **klc5555 said:**
> 
4) You can try (from a terminal):
 mysqlcheck --auto-repair -A -u mythtv -pmysqlpass


Worked for me - thanks for the info!

- Nigel

---

### Post by jMon54 on 2009-11-17
> **klc5555 said:**
> 
4) You can try (from a terminal): mysqlcheck --auto-repair -A -u mythtv -pmysqlpass

Would there be any harm in setting this up as a cron job once a week?

---

### Post by klc5555 on 2009-11-17
> **jMon54 said:**
> Would there be any harm in setting this up as a cron job once a week?

AFAIK, it ought to be fine. I usually prefer to have database repair stuff like this going on while I'm sitting at a terminal watching it for errors, but that's my own paranoia.

I might also prefer to do some crontab editing, so that a script performing this particular weekly repair would execute at some point shortly after my daily mythconverg backup script has done its day's job, but again that's just me.

---

### Post by jMon54 on 2009-11-17
> **klc5555 said:**
> AFAIK, it ought to be fine. I usually prefer to have database repair stuff like this going on while I'm sitting at a terminal watching it for errors, but that's my own paranoia.

I might also prefer to do some crontab editing, so that a script performing this particular weekly repair would execute at some point shortly after my daily mythconverg backup script has done its day's job, but again that's just me.

That makes sense to me.  Thanks for taking the time to post.

---

