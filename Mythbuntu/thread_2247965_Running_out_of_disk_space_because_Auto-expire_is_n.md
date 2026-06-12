---
title: "Running out of disk space because Auto-expire is not working"
date: 2014-10-11
forum: Mythbuntu
---

### Post by km782 on 2014-10-11
I am running Mythtv 0.26 on 12.04 LTS.  My system has been functioning well for a few years now.  A few weeks ago I ran out of disk space (many of my recording are marked so that they won't expire).  Mysql crashed and I had to go in and manually delete a few recordings so that there was enough free space that Mysql could start and I could use Mythtv again.  

After that, I went through my recordings and marked about 75gb worth of shows to be auto-expirable.  However, Mythtv will not expire these recordings and runs out of disk space again.  If I log into Mythweb it shows 75gb of expirable space that could be used for future recordings.  But, if I go to the information center on the front end, the list of expirable recordings is blank.  Any ideas on how to fix this?  Thanks in advance

---

### Post by Adam_Jacobs on 2014-10-11
Nothing immediately springs to mind, but have you had a good look through the mythbackend log? I've had problems with autoexpire in the past, and got good clues to the nature of the problem from that log.

---

### Post by khPWXxF on 2014-10-14
What are permissions and owner for fresh recordings?  I'm not able to check my setup now but expect 666 mythtv.
Are the older recordings which you expect to auto expire the same, or a different user?

Reason for asking is that if your older recordings were made with a previous installation of Ubuntu then the user corresponding to the user number stored in the directory (don't know proper term for this) will generally be different.

Phil

---

### Post by km782 on 2014-10-19
I'm not really sure how to tell what the permissions are.  I don't think I've messed with any settings that would have changed that though.

I've now upgraded to 0.27 and installed all of the updates (still on 12.04).  That hasn't fixed the problem.

So, I went ahead and deleted the 75gb of recordings via Mythweb.  Going to the status page they are then listed as deleted recordings but the space never actually became free.  In order to fix it I had to run flush_deleted_recgroup.pl and then the space showed up as free.  I looked through the backend log and didn't see any error message or anything to indicate what the problem was.  It just seems like Mythtv isn't acknowledging that there are auto-expirable or deleted recordings out there to use for disk space.

On the plus side, it looks like new recordings are properly auto-expiring.  Also, if I watch live tv, those recorded files are deleted properly.  I'll try setting more of the older recordings to auto-expire and see what happens.

---

### Post by tgm4883 on 2014-10-20
> **km782 said:**
> I'm not really sure how to tell what the permissions are.  I don't think I've messed with any settings that would have changed that though.

I've now upgraded to 0.27 and installed all of the updates (still on 12.04).  That hasn't fixed the problem.

So, I went ahead and deleted the 75gb of recordings via Mythweb.  Going to the status page they are then listed as deleted recordings but the space never actually became free.  In order to fix it I had to run flush_deleted_recgroup.pl and then the space showed up as free.  I looked through the backend log and didn't see any error message or anything to indicate what the problem was.  It just seems like Mythtv isn't acknowledging that there are auto-expirable or deleted recordings out there to use for disk space.

On the plus side, it looks like new recordings are properly auto-expiring.  Also, if I watch live tv, those recorded files are deleted properly.  I'll try setting more of the older recordings to auto-expire and see what happens.

If you posted your logs, we could have looked through them for you. You can see the permissions of a directory by doing 'ls -l'

---

### Post by khPWXxF on 2014-10-20
tgm4883 is quite right but let's walk you through it.

The suspicion is that user mythtv is not able to delete the files.  Let’s eliminate the permissons first  before looking for more complicated stuff.
 
First start a terminal session and change to the recordings directory.  On my standard mythbuntu system that’s
 
```
cd /var/lib/mythtv/recordings
```
 
Now check the files:
 
```
ls –l
```
 
On my system I get lines like this:
 
> -rw-r--r--  mythtv mythtv <size> <date> <filename.mpg>
 
The first column is the permissions read/write/execute for owner/group/all.  Here, mythtv can read and write, others can read.  Check that they are least this.
Following columns are Owner, Group, Size, Date written and Filename
 
If any of yours are different (eg different owner) then these commands will change group, owner and permissions respectively:
 
```
sudo chgrp mythtv *
sudo chown mythtv *
sudo chmod 644 *
```
 
 
If that doesn’t fix your problem then you need to start looking at the backend log for clues around the time when autoexpiry is taking place.
 
```
less /var/log/mythtv/mythfrontend.log
```
 
Best wishes
Phil

---

### Post by km782 on 2014-10-26
Thanks again for the help.  I looked at the permissions for my recordings directory and there were one or two that were listed as "root" instead of "mythtv"  I went ahead and changed them.  I'm not sure if it is a permissions problem though because Mythtv will delete recordings but only if I run flush_deleted_recgroup.pl

As an example I tried deleting a recording in the mythbackend log below.  The recording was removed according to mythweb but the file wasn't actually deleted.  So, I flushed the deleted recordings and then Mythtv deleted it.  I have a lot of free space now so it will take a little while because I can try out the autoexpire again but I'm hoping if this issue is fixed it will also solve the autoexpire problem.

```
Oct 26 17:49:29 HTPC mythbackend: mythbackend[2007]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Oct 26 18:04:29 HTPC mythbackend: mythbackend[2007]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Oct 26 18:19:29 HTPC mythbackend: mythbackend[2007]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Oct 26 18:34:29 HTPC mythbackend: mythbackend[2007]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Oct 26 18:43:18 HTPC mythbackend: mythbackend[2007]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 10
Oct 26 18:48:39 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:39 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 1)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:48:40 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 1)
Oct 26 18:48:59 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I Scheduler mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 14
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for CHECK 0 68 0 DoHandleDelete1 | Martha Stewart's Cooking School | Steakhouse | Baked stuffed clams; searing a porterhouse steak; creamed spinach; baked potatoes with various garnishes. | EP015596050042
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 2)
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 88 items in 0.1 = 0.00 match + 0.00 check + 0.05 place
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for CHECK -3 68 0 ForgetHistory | Martha Stewart's Cooking School | Steakhouse | Baked stuffed clams; searing a porterhouse steak; creamed spinach; baked potatoes with various garnishes. | EP015596050042
Oct 26 18:49:00 HTPC mythbackend: mythbackend[2007]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 88 items in 0.0 = 0.00 match + 0.00 check + 0.04 place
Oct 26 18:49:29 HTPC mythbackend: mythbackend[2007]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min
Oct 26 18:50:57 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:50:57 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:51:00 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:51:00 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 18:57:52 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Oct 26 18:57:52 HTPC mythbackend: mythbackend[2007]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: HTPC as a client (events: 0)
Oct 26 19:04:29 HTPC mythbackend: mythbackend[2007]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 15 min

```

---

### Post by tgm4883 on 2014-10-27
> **km782 said:**
>  <snip>So, I flushed the deleted recordings and then Mythtv deleted it.  I have a lot of free space now so it will take a little while because I can try out the autoexpire again but I'm hoping if this issue is fixed it will also solve the autoexpire problem.
</snip>

That sounds like it was moved to the "deleted" group, which is basically a trash can and working as designed. The logs don't show anything special because as you said, you don't have anything to autoexpire. 

We were actually hoping you would post your full logs, we can look back in time.

---

### Post by km782 on 2014-10-28
> **tgm4883 said:**
> That sounds like it was moved to the "deleted" group, which is basically a trash can and working as designed. The logs don't show anything special because as you said, you don't have anything to autoexpire. 

We were actually hoping you would post your full logs, we can look back in time.

I understand the recordings are moved to a "deleted" group and the space isn't freed up right away.  However, the problem I am having is those recordings are never actually deleted, even a week later and when the space is needed.  I had 75gb worth of "deleted" recordings and Mythtv never actually deleted them, so my system ran out of space and crashed.  That's why I'm thinking if I fix that problem it may solve the autoexpire problem.

I would post the full log but the mythbackend log file is around 6mb of text.  Unless you can think of something better, I probably should just wait until the autoexpire problem happens again and I can post all of the entries in the log file for that entire week.

Thanks as always for the help

---

### Post by tgm4883 on 2014-10-29
> **km782 said:**
> I understand the recordings are moved to a "deleted" group and the space isn't freed up right away.  However, the problem I am having is those recordings are never actually deleted, even a week later and when the space is needed.  I had 75gb worth of "deleted" recordings and Mythtv never actually deleted them, so my system ran out of space and crashed.  That's why I'm thinking if I fix that problem it may solve the autoexpire problem.

I would post the full log but the mythbackend log file is around 6mb of text.  Unless you can think of something better, I probably should just wait until the autoexpire problem happens again and I can post all of the entries in the log file for that entire week.

Thanks as always for the help

So compress it and attach it as a file. Bam, no longer 6MB.

---

