---
title: "schedules direct with mythbuntu 16.04"
date: 2016-07-03
forum: Mythbuntu
---

### Post by jonathan.k3 on 2016-07-03
Did a fresh install of mythbuntu 16.04. Filled out the video sources part of the setup with my schedules direct info.

When mythfilldatabase runs after closing the backend setup, it runs. But no guide data is in the frontend. Is anyone else having this issue?

---

### Post by jonathan.k3 on 2016-07-05
Ended up going back to mythbuntu 14.04.4 with mythtv 0.27. SchedulesDirect works as expected with guide data working after initial setup. Perhaps I need to upgrade from 0.27 to 0.28 instead of doing a fresh install of mythbuntu 16.04 for this issue to resolve; haven't done this yet, just putting it out there for anyone else who might have had the same issue above.

---

### Post by jfaberna on 2016-08-01
> **jonathan.k3 said:**
> Did a fresh install of mythbuntu 16.04. Filled out the video sources part of the setup with my schedules direct info.

When mythfilldatabase runs after closing the backend setup, it runs. But no guide data is in the frontend. Is anyone else having this issue?

Yes I'm having the same problem. New install of Mythbuntu 16.04.1 from CDROM. I need to dig into the mythfilldatabase output on the console or log, but it looks normal at glance. I'm also having to setup storage directories before I can watch any TV.

---

### Post by singogli on 2016-09-22
I have this problem.  For me doing: sudo su - mythtv     and then: mythfilldatabase --dd-grab-all   fills in the Program Guide for a temporary fix. I have changed the backend Setup-General-Program Schedule Downloading Options-Run guide data program at time suggested by the grabber to unchecked and Guide data program execution start and Guide data Program execution end to 3 and 5 so it runs when there is likely to be less traffic.
I won't know if that fixes it for a few weeks when the last manual update expires. You might want to give that a try if the manual mythfilldatabase works.

---

### Post by diyhouse on 2016-09-22
I have a 16.04 fresh install with SD,. (on top as you might say),.. and sorry it works fine,..... Not much help I appreciate,. but I would say have you remembered to open the privs up on the caching file ( look in the VideSource.xmltv file for the refs in the .xmltv folder ... did you do a "mfdb --configure"  if you don't mythtv user will not be able to populate the dbase, or will not know where how to login... and make sure you have pulled the latest xmltv download file and installed it.... Just follow the README's  they work fine,.. or should do.... and don't forget to reset the grabber stuff in myth-backend setup to SD JSON output....

Like I said,.. that's all I have done... and SD works for me with a clean 16.04 install,.. so be assured it does work.... just stick with it... hope that helps a little

---

