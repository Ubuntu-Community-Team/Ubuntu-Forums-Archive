---
title: "Mythbuntu Schedules Direct Channel Fetch"
date: 2010-03-10
forum: Multimedia Software
---

### Post by myth1914 on 2010-03-10
[FONT=Arial]I am attempting to build a friends myth backend.  I'm not new to this process and have tried to locate anything on the symptom, but have yet to find a solution.

I can add the source from Schedules direct, and I am able to pull data as per [http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295](http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295) [/FONT]using tv_grab_na_dd

[FONT=Arial]I have purged the database package as well as dropped the database from mysql to start over, etc.

When I choose the "Fetch Channels From Listing Source", it pauses for less than a second and does nothing.  I can scan, but Comcast in the area pulls channels on all QAM types and creates unrealistic conflicts to resolve along with missing channels etc.

I am running a functional system with the same lineup (even tried using that account for testing) so I have pretty much eliminated SD.org as the issue.  Is there a way to fetch the channel xmltvid data without the backend setup and import it to the database so SD.org can fill in the channels with listing info?

I should note that I previously had channel data and listings, but the channels were off.  At the time it seemed logical to update the listings with SD and re-pull rather than manually editing them.  The tuner HAD recorded two channels simultaneously, and tuned without issue.  So I know it's not the tuner.

Mythbuntu 9.10
Samsung DVB tuner (per probe)
active SD.org account
[/FONT]

---

### Post by myth1914 on 2010-03-12
OK.  I've exported my functional channel list, cut the channel data and inserted it into the new database.  That seemed to work, but now it is only pulling on one of the two sources.

Any ideas?

---

