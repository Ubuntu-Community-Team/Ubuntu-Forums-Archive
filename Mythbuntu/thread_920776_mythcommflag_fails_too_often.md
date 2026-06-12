---
title: "mythcommflag fails too often"
date: 2008-09-15
forum: Mythbuntu
---

### Post by newlinux on 2008-09-15
Since upgrading to hardy and .21 I've had two nagging issues. The first one aroun delayed keystroke response I've detailed in another thread. The second is that mythcommflag is much less reliable. I have two separate mythtv systems (1 a distributed multi-frontend/multi-backend system) and one self contained combined frontend/backend. On both systems it seems mythcommflag only completes 75% of the time.

On the distributed system, it was more like 50%, and I'd end up rerunning the job a couple of times and eventually it would complete. It seemed to happen no matter what backend processed the jobs, but I ended up restricting jobs to the recording host (which I really didn't want to do because I have a couple of backends which don't have tuners that were intended just for job processing) and that increased the reliability quite a bit.

On my other system I seem to have most of my mythcommflag problems with HD Mpeg-2 recordings. SD recordings off my framegrabber seem to always successfully complete mythcommflag processing.

I'm pretty much using the same tuners and recording the same things I did before I upgraded and back then mythcommflag rarely failed. 

Looking at the logs, I'll often see that mythcommflag completed 5 minutes after it started (even before the recording finished!) and found no breaks, or it will have found some crazy number of breaks, like 139 for an hour long recording.

I tried running mythcommflag commandline a few times and it seems to segfault a fair amount. 

Any ideas on how to even troubleshoot or improve this would be appreciated.

---

### Post by august495 on 2008-09-29
Have you found a solution for this? I recently did a reinstall and I am having similar issues.

---

### Post by newlinux on 2008-09-29
Nope. But restricting it to the recording host has helped quite a bit. For my standalone system I added another backend to do the commflagging and it has become more reliable. Ironically, this is a backend that used too very often fail commflagging remote recordings on my other system. So I still have no idea what the problem is. 

At least I got my keystroke delay issue fixed...

---

