---
title: "Need help fixing MythTV MySQL"
date: 2008-06-22
forum: Mythbuntu
---

### Post by johnrt on 2008-06-22
I am running Ubuntu 8.04 with MythTV installed by installing Mythbuntu Control Centre and setting up as a Ubuntu desktop with both a backend and frontend. Configuration went fine with a Hauppauge 150 and a Hauppauge 500. Recording and playback was working fine until we had a power failure.

After rebooting the Recorded programs show blank and I cannot view live TV. I suspect that this is a MySQL issue as the recordings are still present, but if the database is not running or corrupted, the system does  not know about them or know about the channel information.

Is there any way to recover – fix- the database without losing the existing shows, recording schedule and channel information or is there some other - fixable - problem?

Thank you all: jrt

---

### Post by danbodoh on 2008-06-22
Check the various /var/log files for clues - is mythbackend dead? Is mysql dead?  Look at /var/log/mysql.*, /var/log/myth*.log, etc.

Dan Bodoh

---

### Post by tagra123 on 2008-06-22
Go to your recording directory --  I think its in var by default - dont remember because I made a separate folder from root just for mythtv recordings.

Anyway find the nuv files and try from the terminal

mythtv SomeRecordedFilename.nuv

If it plays then at least you know part of the system is working. I don't think mysql is used for this part of playback -- in anycase you should get some console messages.

If that works try typing mythfrontend -- a lot of output is usually in the terminal and can be useful in fixing your problem. 

If you backup your myth database try a restore. If you don't backup the database then  add a script to backup automatically.

---

### Post by tgm4883 on 2008-06-22
You database needs fixed.  Run the script here
```
/usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl
```

tagra123:  He has a PVR-150 and a PVR-500, there are no .nuv files.

:EDIT: 

Almost forgot.  Run that script, you might have to do a mythfilldatabase afterword.  Your shows and other data should be fine though.  Lastly, invest in a battery backup/surge protector.  Linux does not like to be turned off without shutting down properly, ever.

---

### Post by johnrt on 2008-06-23
> **danbodoh said:**
> Check the various /var/log files for clues - is mythbackend dead? Is mysql dead?  Look at /var/log/mysql.*, /var/log/myth*.log, etc.

Dan Bodoh

Dan:

My Myth logs seem to be at /var/log/mythtv/mythbackend.log and give the following error after the reboot: 

2008-06-22 18:38:02.585 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.inserttime, j.chanid, j.id;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was: Table './mythconverg/recorded' is marked as crashed and should be repaired

and many variations on this message, but is not completely dead.If I log into MythWed from a remote computer I still see no recorded programs nor a list of upcoming programs, but the program listing is full (the logs show a fill mythfilldatabase run after the reboot) and previously recorded shows are marked with a dotted line, So some parts of the database are intact.

The logs are verbose and I do not know what I am seeing.The interesting bit seems to be:

"Table './mythconverg/recorded' is marked as crashed and should be repaired"

That would be nice.


tgm4883

Is this command the one that might fix the database as mentioned above?

/usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

I have that file, but it is not executable. It shows as;

  -rw-r--r-- 1 root root  893 2007-08-04 05:25 optimize_mythdb.pl

I can change its permissions and run it, but I am reluctant to make the change without knowing if it is the right animal.

Point well made on the UPS. . .


tagra123

I still have playable recordings in the record directory.

If I get this fixed, I will be wanting to explore the automated database backup scripts.


Thank you all for the speedy replies.   jrt

---

### Post by tgm4883 on 2008-06-23
That script may also exist in /etc/cron.daily/, you can execute it from there or make the other one executable.  You should be able to activate daily running of the script via mcc, but last I checked there was a small bug in doing that since the script got moved. (so it probably won't be in cron.daily)

Lastly, you can go into mythweb settings and run a repair from there.

---

### Post by johnrt on 2008-06-23
> **tgm4883 said:**
> 
Lastly, you can go into mythweb settings and run a repair from there.

Well, that fixed it. Thank you very much! Oddly, I had been looking forward to watching some of the stuff that had been recorded.

Took a bit to find it, so for those that might follow:

mythweb  Settings > Database and click on the 'Repair Tables' button and wait a few minutes. I got back the recordings list, but not the upcoming recordings. That is OK. Easy to rebuild.

Thank you again.   jrt

---

