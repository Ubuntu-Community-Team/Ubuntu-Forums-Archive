---
title: "Skype Video Freeze;V4L2 failed to change capture frame rate"
date: 2009-09-07
forum: Multimedia Software
---

### Post by f00fyf00f3r on 2009-09-07
Skype: V4L2 failed to change capture frame rate

While on a video call on skype the video being received will freeze after about 30 seconds and sometimes a bit longer. Before this the video displays without issue. Sometimes, if you hold the call and then resume it will fix the issue until the next 30 secs are over and then the issue repeats. Perhaps unrelated but also if the video screen loses focus it will not refresh unless the call is held and resumed as well, and usually display whatever had overlapped it. Myself view is not affected by this. Full screen just conks out.

I ran skype through terminal and the message that we get exactly whet this occurs is: "Skype V4L2: Failed to change capture framerate (30)"

We get the same message in gdb

Machine: EEE 701 4g ssd running 9.04 NBR
Skype: Issue in both 2.0, 2.1
Skype on the other end: Latest XP release

Any ideas on what the issue could be here? I know the 701 is prob the issue but has anyone else had this issue?

---

### Post by f00fyf00f3r on 2009-09-12
bump

---

### Post by drakeoutlaw on 2009-09-28
Exactly the same problem on Sony Vaio FS630 running Ubuntu 8.04. The issue is related to V4L2. Someone please advise.

---

### Post by f00fyf00f3r on 2009-10-15
Hey, I noticed that the issue may be related to the version of Skype the other person is using.  If they are using the latest version this will occur (depending on their system).  In my case the other was on an eee 1005 with the latest Skype, and we downgraded her to 3.6.0.248 (windows).  After this the issue resolved.  This obviously is not an ideal solution, but I suppose that is more on Skype than anyone.  Are you able to provide similar information?

---

### Post by f00fyf00f3r on 2009-10-15
BTW, this was figured out by the time I installed the 9.10 NBR Beta, what are you running?

---

