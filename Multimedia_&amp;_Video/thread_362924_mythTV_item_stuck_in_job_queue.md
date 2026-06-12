---
title: "mythTV item stuck in job queue"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by fallscrape on 2007-02-16
Since setting up my box since last friday (7 days ago) I've recorded a number of programmes and movies.  The first movie I recorded didn't seem to work - it was just a black screen.  I recorded several others without restarting the backend which worked fine.  I put it down to one of those things.

Then last night I had a similar problem.  On analysis from work (where I have mythweb installed) the job is stuck in the job queue @ 51% complete (started some 10hrs ago)

The box runs dapper drake, has the latest patches installed via synaptic and has recorded other programmes since just fine.  The encoder is a Nova-T running on a 3500 semipron with 1gb ram, 150gb HD (78gb remaining).  The chip is still working as the load is 1.14 (up from a usual 0.68)

Any ideas how to unstick this job or shall I just delete it like I did the last one and hope the queue resolves itself?  It'd be a shame to loose the movie!

---

### Post by majoridiot on 2007-02-17
don't just delete the file, or you could cause more problems.  you should **always** delete 
files through myth.

it's definitely hung up for some reason.  i would stop the job and delete the recording via the
myth interface of choice.

what job was it performing?  flagging, transcoding or both?

---

### Post by fallscrape on 2007-02-18
Not sure how I stop the job - it is flagging I think.

I've checked the job queue and tried stopping/pausing the job but to no luck - there are several other jobs queued.  The film itself is still viewable unlike the previous one which died completely.

Is there any other way of cancelling jobs?

---

### Post by majoridiot on 2007-02-18
if you select system status, scroll down to the job queue, right arrow over and select the job, it
doesn't give you an option to cancel it, etc?

---

### Post by fallscrape on 2007-03-02
There is an option to skip, but it doesn't work when it gets stuck.  A swift reboot can help - I can get it to skip but I can't cancel a job.  Quite a bit of a problem really.

I suppose if I ps next time it happens I might get a job number and kill it from there.  but heyho.

---

