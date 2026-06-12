---
title: "Job Queue execution order/timing"
date: 2010-01-22
forum: Mythbuntu
---

### Post by bbruenfl on 2010-01-22
I was wondering if there is a facility in mythjobqueue to control the execution order of User Jobs based on file.  That is, on completing the recording job execute user job 1 on server x then, on completion of job 1, execute user job 2 on server y.  To clarify, both user jobs would be attached to the same chanid/starttime combination and selected at the time the recording job is created.

I've considered manually adding an entry to jobqueue via mysql at the end of the first script to queue the next job but that seems unnecessarily complex.

Any suggestions would be appreciated.

---

