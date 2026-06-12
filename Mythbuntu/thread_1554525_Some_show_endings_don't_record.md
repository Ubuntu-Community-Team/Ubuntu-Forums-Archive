---
title: "Some show endings don't record"
date: 2010-08-16
forum: Mythbuntu
---

### Post by linuxhippy on 2010-08-16
This may have been addressed by others but I'm not sure how to look this one up.  Here's the problem-some shows start late because a baseball game runs into overtime and then I don't get the ending to the show I'm recording.  This has happened several times...is there anyway around this so that when mythtv encounters a baseball game in OT it delays recording of subsequent shows so that the entire show gets recorded?

---

### Post by LowSky on 2010-08-17
Sorry not really... The problem is that the TV data isn't constanly updating when this occurs. And even if mythfilldatabase wase running constantly some channels don't update their guide listing becase the game runs a bit long.

---

### Post by linuxhippy on 2010-08-17
I was wondering about updating Schedules Direct more often.  I guess the only solution is to record things an hour longer than usual if it is after a baseball game and hope the game didn't run into double OT!

---

### Post by linuxhippy on 2010-08-17
ok-this is what I did.  I will try running mythfilldatabase after a baseball game.  In schedule recording you can search for phrases to find out the times of a show.  I searched for MLB and found that most games during the week are at night (I record at night so day games are out).  I also found they're usually done by 10 PM on Sat. nights and played Sun. afternoon.  I then added this to my crontab using crontab -e:

25 23 * * 1-5 mythfilldatabase >~/mythfilldatable.log 2>&1
55 19 * * 6 mythfilldatabase >~/mythfilldatable.log 2>&1
55 16 * * 0 mythfilldatabase >~/mythfilldatable.log 2>&1

This will produce a log file in my home directory that I can check to make sure things are running.

---

### Post by winewood on 2010-08-19
You can manually adjust in the recording profile for your show to record and extra "X" minutes after the ending of the show.  For baseball games and football, it may be best to set  these for 1 hour after the shows scheduled ending.  I do this using MythWeb.  Schedule the recording via name for dynamic times, then go into advanced tab (if i recall correctly)
 
My system USED to not let me as it would conflict with the next show being taped.  Get another tuner to avoid these conflicts.

---

### Post by tgm4883 on 2010-08-19
> **linuxhippy said:**
> ok-this is what I did.  I will try running mythfilldatabase after a baseball game.  In schedule recording you can search for phrases to find out the times of a show.  I searched for MLB and found that most games during the week are at night (I record at night so day games are out).  I also found they're usually done by 10 PM on Sat. nights and played Sun. afternoon.  I then added this to my crontab using crontab -e:

25 23 * * 1-5 mythfilldatabase >~/mythfilldatable.log 2>&1
55 19 * * 6 mythfilldatabase >~/mythfilldatable.log 2>&1
55 16 * * 0 mythfilldatabase >~/mythfilldatable.log 2>&1

This will produce a log file in my home directory that I can check to make sure things are running.


If you are talking about SD or TMS:
I seriously doubt that will help, as it would require Schedules Direct (or TMS) to monitor and update the data for all of the games that may go into overtime and all shows that follow. In my experience, I haven't seen a listings provider do that.

In any case, it would be MUCH easier to just email schedules direct at  [https://www.schedulesdirect.org/contact](https://www.schedulesdirect.org/contact)


If you are using EIT:
It may work. I don't use EIT so I am unsure how often they update that data.

---

### Post by tgm4883 on 2010-08-19
Also, it may be benificial is a service is created that can handle all the data that overtime games would produce. Maybe this can be revived.

[http://www.mythtv.org/wiki/myth_recording_extender](http://www.mythtv.org/wiki/myth_recording_extender)

---

### Post by azmyth on 2010-08-19
I did some work on MRE to make it work. It will only extend sporting events based on the ESPN scoreboard so it won't adjust shows after the events. The TV listings aren't updated in realtime so your best bet is to just manually add more time to any shows after a sporting event.

---

