---
title: "Upgraded from 12.04 to 14.04 and my myth is waking every day at odd time"
date: 2016-08-13
forum: Mythbuntu
---

### Post by JasonEde on 2016-08-13
I've just upgraded from 12.04 to 14.04 by making a fresh install, copying recordings and moving database over. All has gone ok and it seems to be fine.

However, the system is starting up at 22:07 every day for no reason I can find. A grep of wakeup in the mythbackend.log shows this.

Aug 11 23:33:39 jason-pc mythbackend: mythbackend[8523]: N Scheduler scheduler.cpp:3132 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011mythshutdown --setwakeup 2016-08-12T22:07:13
Aug 12 03:05:02 jason-pc mythbackend: mythbackend[2128]: N Scheduler scheduler.cpp:3132 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011mythshutdown --setwakeup 2016-08-12T22:07:13
Aug 12 19:38:28 jason-pc mythbackend: mythbackend[2160]: N Scheduler scheduler.cpp:3132 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011mythshutdown --setwakeup 2016-08-12T22:07:13
Aug 12 22:22:45 jason-pc mythbackend: mythbackend[2158]: N Scheduler scheduler.cpp:3132 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011mythshutdown --setwakeup 2016-08-13T22:07:24
Aug 13 03:05:10 jason-pc mythbackend: mythbackend[2126]: N Scheduler scheduler.cpp:3132 (ShutdownServer) Running the command to set the next scheduled wakeup time :-#012#011#011#011#011mythshutdown --setwakeup 2016-08-13T22:07:24

I've just checked the settings and it's all set according to the acpi wakeup wiki article and was working fine before the upgrade. I've checked by pressing i on the mythwelcome screen and that's set correctly with a single maintenance slot at 2am and it's doing that.

Any idea how I can find out where this time has come from and why it thinks it needs to wake up? The next recording I have setup is 20:00 on 16th August.

Jason

---

### Post by JasonEde on 2016-08-13
I think I'm getting somewhere... I found an old recording schedule that was due to start at 22:20 with programs starting 3 minutes early which when combined with a 10 minute prior wakeup gave me 22:07. However, there was no episodes of that coming up so I don't know why myth was trying to wakeup then.

It's now wanting to wakeup at 07:42 every morning. I've pruned my recording schedules right down. Currently all of the items there last recorded on an evening and there is no instance of any of them coming up.

---

### Post by JasonEde on 2016-08-13
I've looked in my database... The record table looks correct, but in the recordmatch table I've a load of entries for channels I no longer have (I did a full re-tune and sort around after upgrade). Can I just remove the entries in there other than the 1 for my upcoming recording?

---

### Post by JasonEde on 2016-08-14
I cleaned out the recordings list and the system shutdown without setting a start time as I'd expect.

I then set a program to record at 8pm on Tuesday (16th) and then when it shut itself down it's set a wakeup for tomorrow morning at 07:42. I don't know and can't see why and am now at a loss.

---

### Post by JasonEde on 2016-08-25
I'm still getting this and it's not always waking up for recordings. (It's not woken up for the last 3) despite showing this on the mythwelcome screen that it's scheduled to. I've noticed on all the ones where it's not woken up I'd ticked this channel on the filters. I've unticked that to see if it makes any difference.

I still cannot find any reason why it's waking every morning at 07:42. I did wonder if it was EIT and updating the guide, but it's scheduled to be on during middle of the night for updating guides, doing backups etc.

---

### Post by JasonEde on 2016-09-03
Eventually tracked this down to the "Run guide data program at time suggested by the grabber." option being ticked. Unticked this and now it only wakes up when scheduled.

---

