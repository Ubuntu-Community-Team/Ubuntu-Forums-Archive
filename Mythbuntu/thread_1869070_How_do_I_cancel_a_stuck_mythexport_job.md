---
title: "How do I cancel a stuck mythexport job?"
date: 2011-10-25
forum: Mythbuntu
---

### Post by sqeelurgle on 2011-10-25
I set a recording to export with mythexport.  I may have not properly set up mythexport, but anyway I now want to cancel the job.  It has been running without completing for over a week.  I think part of the problem is that every time the machine boots, it adds the job into the mythexport queue again.  I don't need the recording exported anymore, and want to cancel the job.  I have deleted all the jobs from the mythexport queue.  I have gone into system status and tried to stop the job in there, but it won't stop.  I call up the menu, and select "stop" but it keeps running.  I have tried to delete the original recording from the "watch recordings" screen, but it won't delete (I assume because it has a job running).  I could probably delete the file from the terminal, but I am worried that this won't actually stop the errant job.  I have killed the mythexport daemon from the terminal, but this doesn't allow me to stop the job, or delete the recording either.  In the meantime I have a myth box that won't do commercial detection because another job is running, and won't shut down when idle, because it's never idle.

Help please.

---

### Post by DaveQB on 2011-11-15
Try the "Job Queue" link on the mythexport web frontend.

I'd like a way to do it on mass through the CLI.

Anyone know??

---

