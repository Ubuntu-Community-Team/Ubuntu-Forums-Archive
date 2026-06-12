---
title: "Odd jobqueue behaviour"
date: 2015-10-17
forum: Mythbuntu
---

### Post by Steve666 on 2015-10-17
I am using mythtv 0.27 on the latest mythbuntu version.
The system is set-up that it automatically shuts down when idle.

Now I noticed that the system is not shutting down anymore.
Mythwelcome is telling me that jobs in the queue still needs to be processed which is a good reason for not shutting down.
Looking into the job queue shows me that jobs for commercial detection and meta data gathering are waiting.
Two things are odd:
a) In mythbackend I configured that no jobs for commerical detection or for metadata gathering should be started
b) The listed jobs are never started or finished.

I deleted the jobs already and the system is then shutting down.
But within the next uptime of the system new jobs are created in the queue and the same behaviour starts again. :o

Any idea how to solve the issue?

---

### Post by Steve666 on 2015-10-18
Maybe I have understood the problem but I need some further testing.
I switched off commercial flagging and metadata gathering jobs in mythbackup.
However, the standard recording template entered the jobs into the recording tasks automatically.
It seems that this was causing a conflict.
Since I deleted the option out of the standard recording profile, it seems to work properly now.
I will still observe it but maybe it was the solution.

---

### Post by Steve666 on 2015-10-22
I can confirm now that the change of the parameters in the recording tasks solved the issue.

---

