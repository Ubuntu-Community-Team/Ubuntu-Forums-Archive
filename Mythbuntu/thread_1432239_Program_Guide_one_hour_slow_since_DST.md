---
title: "Program Guide one hour slow since DST"
date: 2010-03-17
forum: Mythbuntu
---

### Post by Barry_IA on 2010-03-17
[FONT=Palatino Linotype]Hi Folks![/FONT]

Having problems with the Program Guide and recording being one hour off since we started Daylight Savings Time last Sunday (March 14).  The system time is correct, but the Program Guide says the Noon News is from 11 a.m. until Noon -- should be Noon to 1.

The system (Backend) properly switched time; I downloaded the latest updates this morning and rebooted (soft, vs. power); no change.

I am currently obtaining the programming guide information off the air (not via SchedulesDirect yet).  I also noted last night when channel-surfing (via antenna -- not via Mythbuntu) one of the local TV stations and its sub-channels were showing the wrong time: was 9 p.m. and the TV displayed 8 p.m.  Next station the time changed back to the correct/current time.  No idea if that has any bearing on my problem -- my station guide starts with Ch 4.1 (RF 4) and the station with the problem is Ch 8.1/8.2/8.3 (RF 38 ).

So how do I correct this problem?

TIA!

---

### Post by azmyth on 2010-03-18
Don't know if this will fix your problem but I'd also set the timezone in the php.ini file.

I'd also make sure you have the proper timezone set in the system you can find out by entering

date

at a shell prompt

---

### Post by Barry_IA on 2010-03-19
Hi Azmyth!

Went to check your suggestions and the Program Guide was displaying correctly!  Fixed itself some time after the recordings of the 16th and before those of the 17th.  Maybe you scared it into behaving?! <gg>

The only odd thing was the system was asleep when I went to check -- first time I remember it doing that.  Will have to keep an eye on it to see if it does it again; else got a hint on where that setting is?

Thanks!

---

