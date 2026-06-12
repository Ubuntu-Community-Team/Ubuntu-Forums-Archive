---
title: "Frontend lockups with livetv exit or recording end."
date: 2016-05-01
forum: Mythbuntu
---

### Post by JamesNorris on 2016-05-01
Since upgrading from 0.27 to 0.28, my frontend seems to lock up frequently (though not every time) when I ESC from liveTV or a recording/video comes to an end. 

I'd appreciate an easy answer, but failing this, I'd like to know how to troubleshoot it and figure out what the problem is.

---

### Post by JamesNorris on 2016-05-15
I've had a look in the frontend and backend logs, but nothing seems to indicate a problem. 

Frontend log, at the time of the problem showed only this:
```
May 15 19:01:58 LCARS-HD mythfrontend.real: mythfrontend[5951]: I CoreContext mythdbcon.cpp:422 (PurgeIdleConnections) New DB connection, total: 2
```

and the backend had these standard entries:
```
May 15 19:02:24 LCARS-HD mythbackend: mythbackend[1068]: I Scheduler scheduler.cpp:2267 (HandleReschedule) Reschedule requested for MATCH 0 2 0 2016-05-16T04:30:00Z E$
May 15 19:02:24 LCARS-HD mythbackend: mythbackend[1068]: I Scheduler scheduler.cpp:2380 (HandleReschedule) Scheduled 28 items in 0.0 = 0.02 match + 0.01 check + 0.02 $
May 15 19:02:24 LCARS-HD mythbackend: mythbackend[1068]: I TVRecEvent tv_rec.cpp:3685 (TuningFrequency) TVRec[34]: TuningFrequency
```

Where else do I start when trying to figure out the cause of this?

---

