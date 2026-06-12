---
title: "Any Tips for Moving my Mythbox to a Different Machine?"
date: 2008-05-22
forum: Mythbuntu
---

### Post by SeanOB on 2008-05-22
Hello,

I'm changing my setup from a frontend/backend combined set-top box to having a frontend set-top with a backend on another machine.

My current frontend/backend box "MythBox" has 2 HDDs - one booting mythbuntu 8.04 and one with all of the recording data etc - the /mnt/myth drive (has all of the stuff typically in /lib/var/myth).

My current "other" machine "Other" - soon to be the backend - is currently running ubuntu 8.04.  This "Other" machine will sit in the back room and will be used for recording (backend), as a server (audio files), an occasional desktop, and very occasionally as a frontend.

My plan:
[LIST=1]
[*]Backup "MythBox" myth database (how do I do this?)
[*]Move all of the tuner cards from "MythBox" to "Other"
[*]Move the recordings drive from "MythBox" to "Other"
[*]Install Mythbuntu (via apt-get) onto "Other" and configure for  frontend/backend
[*]Overwrite(?) Merge(?) newly created mythtv database on "Other" with the one that I backed up "MythBox" database (how do I do this?)
[*]Test backend / frontend "Other" box - is database correct?  Does it record?  Can I watch all recordings that I recorded previously?
[*]Once "Other" Box is working correctly - the reconfigure "MythBox" as frontend only box
[/LIST]

Is there anything I'm missing?
How do I do the backup from one box and a restore on another?

I really don't want to lose my database - it knows what shows we've already seen - and that's a handy feature for the re-run loving wife.  (A previous upgrade gone wrong forced a reinstall which lost the database.  This generated a LOT of complaints from my user group - my one person user group.) :)

Thanks!

Sean

---

### Post by .nedberg on 2008-05-22
> **SeanOB said:**
> Hello,

I'm changing my setup from a frontend/backend combined set-top box to having a frontend set-top with a backend on another machine.

My current frontend/backend box "MythBox" has 2 HDDs - one booting mythbuntu 8.04 and one with all of the recording data etc - the /mnt/myth drive (has all of the stuff typically in /lib/var/myth).

My current "other" machine "Other" - soon to be the backend - is currently running ubuntu 8.04.  This "Other" machine will sit in the back room and will be used for recording (backend), as a server (audio files), an occasional desktop, and very occasionally as a frontend.

My plan:
[LIST=1]
[*]Backup "MythBox" myth database (how do I do this?)
[*]Move all of the tuner cards from "MythBox" to "Other"
[*]Move the recordings drive from "MythBox" to "Other"
[*]Install Mythbuntu (via apt-get) onto "Other" and configure for  frontend/backend
[*]Overwrite(?) Merge(?) newly created mythtv database on "Other" with the one that I backed up "MythBox" database (how do I do this?)
[*]Test backend / frontend "Other" box - is database correct?  Does it record?  Can I watch all recordings that I recorded previously?
[*]Once "Other" Box is working correctly - the reconfigure "MythBox" as frontend only box
[/LIST]

Is there anything I'm missing?
How do I do the backup from one box and a restore on another?

I really don't want to lose my database - it knows what shows we've already seen - and that's a handy feature for the re-run loving wife.  (A previous upgrade gone wrong forced a reinstall which lost the database.  This generated a LOT of complaints from my user group - my one person user group.) :)

Thanks!

Sean


Have a look here: [http://ubuntuforums.org/showthread.php?t=609564](http://ubuntuforums.org/showthread.php?t=609564)

Instead of ```
mysqldump -u mythtv -p mythconverg recorded > recorded.sql
```use```
mysqldump -u mythtv -p mythconverg > mythconverg.sql
``` and import that db to "Other"

Your plan looks fine. I did a similar thing when I went from KnoppMyth to Mythbuntu! And I have an equal user group! :)

---

### Post by SeanOB on 2008-05-29
Thanks!
So far so good -- I have the backend up and running (haven't plugged in an antenna yet - so haven't confirmed that the recording is working; but the tuners are being found so it should be okay).  The frontend found the backend once a fixed a few things.

Down to two annoyances:
1) The backend seems to think that the tuners are still present (but unconnected) on the original MythBox.  So now it lists 8 tuners - 4 on the new backend ("OTHER") and 4 on the old frontend/backend ("MythBox").  How do I delete the 4 old ones?  It's just an annoyance - since it knows that the 4 old ones are disconnected.

2) MythWeb doesn't have images for any of the shows that were recorded prior to the move.  How do I regenerate the cached images?

-Sean

---

### Post by .nedberg on 2008-05-29
> **SeanOB said:**
> Thanks!
So far so good -- I have the backend up and running (haven't plugged in an antenna yet - so haven't confirmed that the recording is working; but the tuners are being found so it should be okay).  The frontend found the backend once a fixed a few things.

Down to two annoyances:
1) The backend seems to think that the tuners are still present (but unconnected) on the original MythBox.  So now it lists 8 tuners - 4 on the new backend ("OTHER") and 4 on the old frontend/backend ("MythBox").  How do I delete the 4 old ones?  It's just an annoyance - since it knows that the 4 old ones are disconnected.

You can do it with mythtv-setup, just remove the tuners, or you could remove the entire backend from that system.

> **SeanOB said:**
> 
2) MythWeb doesn't have images for any of the shows that were recorded prior to the move.  How do I regenerate the cached images?

-Sean

Sorry, I have no idea. Doesn't it show when you select the recording?

---

### Post by SeanOB on 2008-05-29
> **.nedberg said:**
> You can do it with mythtv-setup, just remove the tuners, or you could remove the entire backend from that system.

The backend *is* removed from the system - so mythtv-setup is gone.  I think I'll have to tell it that it's a secondary backend; then run setup and delete the tuners and then tell it that it's not a backend anymore.

> **.nedberg said:**
> 
Sorry, I have no idea. Doesn't it show when you select the recording?
Nope.  The mythweb image cache folder has a bunch of 0kb files.  I deleted them all and they were regenerated as another set of empty files.

Neither of these are that big of a deal.  Just minor annoyances.

-Sean

---

