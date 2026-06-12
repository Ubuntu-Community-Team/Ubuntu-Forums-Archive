---
title: "Adding programming information on new channels"
date: 2009-07-20
forum: Mythbuntu
---

### Post by Caps18 on 2009-07-20
I installed a new high powered antenna last weekend to pick up the Cincinnati TV stations 50 miles away, and it worked.  Now I rescanned the TV stations in the backend and they show up in the program guide in MythTV, however there is no schedule information for those new channels.

I did login to my Schedules Direct account and added those new channels to my lineup.  But, they didn't send me the TV listings when I updated 2 minutes later.  Did I not wait long enough maybe?  Is there something else that I forgot to do?

---

### Post by klc5555 on 2009-07-20
> **Caps18 said:**
> I installed a new high powered antenna last weekend to pick up the Cincinnati TV stations 50 miles away, and it worked.  Now I rescanned the TV stations in the backend and they show up in the program guide in MythTV, however there is no schedule information for those new channels.

I did login to my Schedules Direct account and added those new channels to my lineup.  But, they didn't send me the TV listings when I updated 2 minutes later.  Did I not wait long enough maybe?  Is there something else that I forgot to do?

If you updated your account at SchedulesDirect with the new channels, and if you added the xmltvid numbers for those new channels to your database (either through Channel Editor in the backend, or after typing "e" while watching each channel in LiveTV from the frontend), and if you have run mythfilldatabase with the defaults to update your guide information, then you should see the schedule information begin to be populated with "tomorrow's" listings : i.e., move forward in the schedule and see if you have information filling in for after midnight tonight. A default mythfilldatabase fills in tomorrow, and then 13 days from tomorrow.

If yiu ran mythfilldatabase --refresh-all, that will give you everything starting with tomorrow and running through 14 days.  If you want today's listings changed, run mythfilldatabase --refresh-today

---

### Post by Caps18 on 2009-07-20
That was part of what was going on.  It did take an hour or so for the changes I made on-line to take effect.  But after I waited, it still only updated from tomorrow's listings on.  The --refresh-today command did the trick to get today.

Thanks

---

