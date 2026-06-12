---
title: "MythTV frontend crashes when time shifting"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-08-26
I've had a working MythTV setup for a while now, consisting of a frontend/backend machine, as well as two other remote frontend-only machines.  It has been working great for more than 6 months, and I haven't done ANYTHING to it in that time, other than using the MythTV frontend.  Suddenly, now, the frontend freezes when I try to jump ahead while watching certain recordings.  I've found that if I wait several minutes, it eventually just bails out of playing the show and returns to the list of recorded shows.

I tried running mythfrontend in a terminal to see if any errors were displayed.  When it froze, I used ALT+Tab to switch over to the terminal, and all it said was something like:

ac-tex damaged at 8-18

I'm not sure if that is related, since the recording I was watching was made on 8/21.  So far, I've found at least two recordings that this error occurs on, and at least one more recent recording that works fine.  In all cases, playback seems unaffected, except while jumping ahead, or when the commercial auto-skip is engaged (I tried shutting off the auto-skip feature, and the error still occurs).

Does anyone have any ideas?  I was thinking that it might be a hardware problem, like a bad hard drive, but I would think that would crash the whole system, not just the frontend.  In my case, the backend process does not seem to be affected.

---

### Post by dmfrey on 2007-09-11
I started to experience this issue as well, but only after I upgraded to myth 0.20.2 to get the Schedules Direct update.  All playback was working fine prior to this upgrade.  

My setup consists of a server in another room that does all the recordings over firewire from DCT-6200 and a frontend in my entertainment center.

I also ran the frontend from a terminal window and found the same messages that you found.  There were no errors.

I saw one page in the MythTV Wiki about disabling Real Time Priority Threads, but the problem still existed after this setting was changed.

Have you been able to solve the issue?

---

### Post by josesanders on 2007-09-14
It seemed to have occured only on a few recordings.  I deleted them, and I haven't had any problems since then, but I haven't been using the system very much lately.  I have not yet done the update for the schedules.

The only thing that I can think of is that we had a lot of thunderstorms right around the time the bad recordings were made, and power quality in my apartment is pretty bad to begin with, so I think that maybe there was some data corruption as a result of that.

---

