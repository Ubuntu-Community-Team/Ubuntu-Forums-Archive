---
title: "Mythbuntu doesn't respond to system clock changes."
date: 2008-12-12
forum: Mythbuntu
---

### Post by michwill on 2008-12-12
Hi All,

I'm having a bit of a scheduling problem with Mythbuntu.  Basically, my system clock was about 2 minutes fast, so my shows were recording too early and cutting off the end of each show.  I then decided to simply set my system clock back by 2 minutes.  However, this didn't solve the issue.  The recordings still start 2 mins early and cut off the end.

Is the MythTV clock of previously scheduled repeat items somehow not tied to the system clock?


Best.

---

### Post by majoridiot on 2008-12-12
> **michwill said:**
> Hi All,

I'm having a bit of a scheduling problem with Mythbuntu.  Basically, my system clock was about 2 minutes fast, so my shows were recording too early and cutting off the end of each show.  I then decided to simply set my system clock back by 2 minutes.  However, this didn't solve the issue.  The recordings still start 2 mins early and cut off the end.

Is the MythTV clock of previously scheduled repeat items somehow not tied to the system clock?


Best.

mythtv should start to record based on the scheduled time of recording, the current system time and 
any +/- recording offsets you may have set up.

what i would check:

from the desktop, under system-->time and date, make sure it is set to "synchronize with internet servers"
and that you have it set to synch from the closest available time server.  you may need to use the "unlock"
button to change the settings.

check/replace your mobo battery- low voltage can make your clock flaky.

check to make sure there are no recording offsets set up for any of your tuner or shows.  you can
do this via frontend setup.

test-record a few shows you would not normally record on channels you would not normally watch to see if
there are any issues there.

lastly, verify that the shows are *actually* being shown on time.  some stations are rather cavalier with their
observation of time and "schedules".  running a few minutes fast or late is no surprise on a lot of them.

---

