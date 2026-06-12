---
title: "Got myself in a mess with database."
date: 2009-04-08
forum: Mythbuntu
---

### Post by drifting on 2009-04-08
I am an idiot, lets just leave it at that for now.

I foolishly followed another thread on here as I was having major delays when I tried to search anything in Mythbuntu, I ran the database cleanup script, remove orphans etc, well it went one better and whiped all my recordings, about 18motnhs worth. Did not expect that, and little I could do about it.

Anyway, I removed the remainder of the recordings, and thought I would start again, clean sweep etc. However there is still data held in the database about previous recordings, and I would like that gone, however I would like to keep the upcoming recordings. Is that possible ?

I ran the same script last night again, and it promptly told me there were unlinked recordings again, which had only been recorded last night (they were in the recorded programs) so I am confused, and concerned my database is really messed up.

Do I just wipe the whole server and start again ? As I am running out of time as I am away for a month from Monday.

I must admit I have been discussing this in another thread, but felt that I had hijacked that from it's previous owner.

Regards Paul.

---

### Post by klc5555 on 2009-04-08
> **drifting said:**
> I am an idiot, lets just leave it at that for now.

I foolishly followed another thread on here as I was having major delays when I tried to search anything in Mythbuntu, I ran the database cleanup script, remove orphans etc, well it went one better and whiped all my recordings, about 18motnhs worth. Did not expect that, and little I could do about it.

Anyway, I removed the remainder of the recordings, and thought I would start again, clean sweep etc. However there is still data held in the database about previous recordings, and I would like that gone, however I would like to keep the upcoming recordings. Is that possible ?

I ran the same script last night again, and it promptly told me there were unlinked recordings again, which had only been recorded last night (they were in the recorded programs) so I am confused, and concerned my database is really messed up.

Do I just wipe the whole server and start again ? As I am running out of time as I am away for a month from Monday.

I must admit I have been discussing this in another thread, but felt that I had hijacked that from it's previous owner.

Regards Paul.

First thing is _don't_ _don't_ _don't_ run the myth.find_orphans.pl script with the --dodelete switch unless you're sure that's what you really want to do. --dodelete deletes orphan _recordings_. The --dodbdelete switch is the one that deletes leftover database entries when the recording itself is gone. Without one of these switches set, the script by default doesn't delete anything: it only informs. Before running any of these /.contrib scripts read the #comment lines and options sections at the start of the script so that you understand thoroughly what they do, because the wiki documentation for most of them is next to nonexistent.

Second thing is back up the database as dscribed in the periodic maintenance section of the manual ( [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance) ) before running a script which is likely to affect the database. Heck, cut and paste the little eight-line automagical daily backup script the manual supplies for you, supply your own mysql password, and set it up cron.daily as the manual recommends. It works. It's a life-saver.

Now if I understand your situation properly, you have only a handful of actual recordings left, but the database data for the older, deleted recordings survive and you wish to delete that leftover data. The Completely Safe way to do so is from the front-end, in the Watch Recordings menu. If you right-click on a particular recording's entry in the Recordings menu, the menu will protest that the recording can't be found but will allow you to delete its entry from this menu.

If you have new recordings that can't be found in your recordings menu, that's what myth.rebuilddatabase.pl is for.

If your database seems to be operating in a less-than-optimal fashion, the first thing to do is to go into Mythbuntu Control Center and in the advanced section of the menu, trigger the optimize mysql utilies.

Finally, as a last resort, if mythconverg seems totally hosed, one can, after First Backing It Up (just in case), drop mythconverg and create a new stubby blank one from the command-line, whereupon mythtv's backend setup will be run again as though this were a brand new Mythbuntu installation.

---

### Post by drifting on 2009-04-09
Thank you once again for an excellent post. I understand what you were saying, and to make matters worse (funny) I found out I had backed up the database with a cron job, just did it so long ago I had forgotten :-) No matter.

Nearly grasped what I was on about. If say I setup a program to catch each episode, it currently thinks it has them, marking it as previously recorded, it does not list them in recorded programs. I would like it to record those episodes it thinks it has again? ie the ones I deleted.

Does that make sense ?

Paul.

---

### Post by klc5555 on 2009-04-09
> **drifting said:**
> Thank you once again for an excellent post. I understand what you were saying, and to make matters worse (funny) I found out I had backed up the database with a cron job, just did it so long ago I had forgotten :-) No matter.

Nearly grasped what I was on about. If say I setup a program to catch each episode, it currently thinks it has them, marking it as previously recorded, it does not list them in recorded programs. I would like it to record those episodes it thinks it has again? ie the ones I deleted.

Does that make sense ?

Paul.

I'm not certain about this, because it's been a while since I deleted metadata without a recording from "Watch Recordings", and I don't have an example on hand to test. But in the delete sequence for normal recordings you get a dialogue allowing to choose whether simply to delete or to "delete but allow rerecord". If this dialogue appears when deleting recordingless metadata, then you're in business. 

Also, in "upcoming recordings" the grayed-out entries for upcoming previously or currently recorded episodes have an editable option for "forget previous", but I don't know whether this option has to be set for each individual upcoming previously-recorded episode, or whether the setting holds across an entire search profile. 

Cheers! :)

---

