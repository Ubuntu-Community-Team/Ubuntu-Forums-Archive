---
title: "Active EIT scan brings system to its knees after 10.04/0.23 upgrade"
date: 2010-05-05
forum: Mythbuntu
---

### Post by srenner on 2010-05-05
Hi all,

I have my master backend running in VMWare Player inside of my XP file server, with a HDHomerun dual tuner, running 24/7.  Everything was fine on 9.10, but since upgrading to 10.04, the EIT scan seems to constantly run and hammers the processor.  The load average is constantly swinging back and forth from 1.5 - 2.5+, whereas before the upgrade it would frequently be at 0.0, even with EIT scanning enabled and working properly.

The 0.23 release notes don't mention changes with EIT, and I didn't change any settings.  I've also gone back several times to try different settings.

Any ideas?  What can I do to make the EIT scan stop once it has enough info?

---

### Post by ian dobson on 2010-05-05
Hi,

I don't think you can get mythtv to stop scanning the EIT/EPG when it has enough. The only thing you can try is increasing the timeout before it moves on to the next channel.

I imagine you can change the value through mythtv-setup but I can't say where it is, but the settings are called "EITTransportTimeout" in the settings table in the database. I have mine set to 6 (minutes) and this reduced the mysql database thrashing quite abit.

Regards
Ian Dobson

---

### Post by colinnwn on 2010-05-05
Have you tried disabling EIT scan to see if that resolves the high load average? After upgrade, my Mythbox frontend and mythweb are very sluggish, and the disk is always churning even when I am not doing anything with it. 

TOP shows somewhat elevated looking CPU usage for a few processes, but not so high that i'd expect the computer to behave as it does. I'll have to see if disabling EIT fixes it.

---

### Post by srenner on 2010-05-06
Ian - Thanks for the suggestion, but that did not work.  I'm assuming that setting only comes into play when a tuner gets stuck on a particular channel while fetching EIT data, and that isn't what's happening.

colinnwn - Disabling EIT made the machine settle back down to a 0 load average.  That helps me verify that my problem is related to EIT somehow, but I do need the scanning enabled, because I have no other source for listings.

I've also noticed that the backend uses a lot of CPU for simple things like streaming to a single client, where it used to not even be noticeable.

Time is not on my side here, so I had to nuke the whole thing and go back to 9.10.  I now have EIT scanning enabled and a 0 load average.  I need to redo all my client machines, but I assume the high CPU while streaming is going to get fixed as well.

So long Mythbuntu 10.04 / MythTV 0.23...perhaps we'll meet again in a few months.

---

### Post by ian dobson on 2010-05-06
Hi,

No this option just sets how long the EIT scanner stays on one multiplex before moving on to the next one.

Maybe try cleaning out your eit_cache table.

Regards
Ian Dobson

---

### Post by srenner on 2010-05-06
I neglected to mention in my last post that a fresh install of 10.04 had the same bad results.  There is either a bug with the default 10.04 install, or perhaps a default setting on 10.04 is different than 9.10, and I simply didn't find the correct setting.  I tried pretty much everything I could think of in the backend setup UI, though.

Thanks anyway. :)

---

### Post by colinnwn on 2010-05-10
I finally disabled EIT scan on my Myth box. It did improve things, but it is still a very sluggish machine doing anything (even stuff unrelated to Myth, like Firefox). I'd say it improved the situation by half, compared to my pre-upgrade 9.10 experience. 

I gotta find the time, suck it up, blow the disk away, and start over soon.

---

### Post by ian dobson on 2010-05-11
Hi,

I have a feeling that your VMWare Player is not playing nice with the linux kernel. Not sure where to start looking though.

On my box (Quad Core/8Gb ram,6x2Tb WD drives in RAID) 10.04 is actually abit quicker than 9.10 or atleast a multithreaded data processing job that took 12Hours on 9.10 now only takes 11:30 on 10.04 (about 5% quicker).

I'd have a look in that direction, not sure where to look but VMWare Player is the only reason I can think that the box slows to a crawl.

Regards
Ian Dobson

---

### Post by colinnwn on 2010-05-11
Last night I did another update, hoping that would fix things, and it mostly did. It is about 80% better in responsiveness across the board in Myth and other apps. Load average is still a lot higher than it used to be. MythFrontEnd still occasionally stutters, but much less than it was.

Trying to squeeze the last bit out of it and figuring I had little to lose, I decided to re-enable 0.23 auto-builds. That didn't fix anything, but it did work this time, as opposed to in 9.10 when it borked MythTV. 

It is usable enough. Guess I'll stick with this upgraded 10.04 install hoping it continues to improve. Maybe someday I'll get in the mood and have the time to start from a fresh 10.04 install and see if it is 100%.

---

### Post by stormb on 2010-05-13
Just thought I'd add that I'm also experiencing this problem with EIT and 10.04.

Spec -
Acer Aspire Revo
1GB RAM (128MB of that for VDPAU gfx)
Freecom USB DVB-T tuner
UK Freeview
Mythbuntu 10.04 with 0.23+fixes auto builds (last updated today)

I was previously using 9.10 with the 0.22+fixes auto builds. CPU usage was zero most of the time and load averages were usually 0.00 or 0.01 when not recording or watching.

Since the upgrade I've seen mythbackend constantly use 2-3% CPU and mythfrontend use 1-2% CPU when doing nothing. Load average is 0.50 or 0.60, and the HD seems to be fairly busy.

I've temporarily disabled EIT scan and it appears to sort the mythbackend usage, although mythfrontend usage is still the same. By disabling EIT I can get load averages down to about 0.19-0.20.

I tried running mythbackend with "-v all", but there seems to be too much stuff to wade through for me to make sense of it. I spotted the following though (which happens pretty much all the time) -

2010-05-13 12:56:49.271 MSqlQuery::next(DBManager1) Result: "eventid = 35694, tableid = 81, version = 14, endtime = 1274104800"
2010-05-13 12:56:49.282 MSqlQuery::next(DBManager1) Result: "eventid = 35695, tableid = 81, version = 14, endtime = 1274108400"
2010-05-13 12:56:49.293 MSqlQuery::next(DBManager1) Result: "eventid = 35696, tableid = 81, version = 14, endtime = 1274112000"
2010-05-13 12:56:49.304 MSqlQuery::next(DBManager1) Result: "eventid = 35697, tableid = 81, version = 14, endtime = 1274115600"
2010-05-13 12:56:49.316 MSqlQuery::next(DBManager1) Result: "eventid = 35699, tableid = 81, version = 14, endtime = 1274122800"
2010-05-13 12:56:49.327 MSqlQuery::next(DBManager1) Result: "eventid = 35700, tableid = 81, version = 14, endtime = 1274126400"
2010-05-13 12:56:49.338 MSqlQuery::next(DBManager1) Result: "eventid = 35701, tableid = 81, version = 14, endtime = 1274130000"
2010-05-13 12:56:49.349 MSqlQuery::next(DBManager1) Result: "eventid = 35702, tableid = 81, version = 14, endtime = 1274133600"

If anyone has any ideas at all it would be much appreciated! Is there a way of running EIT data collection only at a certain time (like 30 minutes overnight or similar) ?

Will

---

### Post by krizze on 2010-06-30
I also have a similar problem on 10.04 with MythTV 0.23. When having active EIT enabled, the computer actually freeze completely after a short while, and I have to reboot it manually with the reset button. 

Disabling active EIT seems to fix the problem, although I experience some random freezes from time to time. Nothing in the logs, ofcourse.

---

