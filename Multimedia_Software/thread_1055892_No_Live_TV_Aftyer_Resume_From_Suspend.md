---
title: "No Live TV Aftyer Resume From Suspend"
date: 2009-01-31
forum: Multimedia Software
---

### Post by jeffhills on 2009-01-31
After many hours I have managed to get one of my remote Mythbuntu frontends to suspend to RAM and wake up using the power button on a MCE remote.
My problems now are
1/ If I suspend while watching live TV, that card continues to be used inthe backend untill manually stopped.
2/ upon resume, the remote frontend allows access to recorded programes, guide data etc, but not live TV .The message 'should have got channel lock by now' comes up. If I try to change inputs, Mythtv frontend shutsdown, if I go back in all is OK.
Has anybody had the same problem, can anybody help please?
Jeff

---

### Post by defensorfedei on 2011-04-06
I can confirm that I am experiencing a similar problem.  I am using a frontend/backend combination machine with pvr-150.  I am experiencing two 'bugs' at the moment.

1- When I shut down the computer and restart it, then try to watch livetv, I get: "Error: mythtv is using all inputs, but there are no active recordings?"  I have a workout around script that use to restart the backend, which fixes the issue.

2-When I use suspend, all goes down fine, and it resumes fine, except when I select 'watch tv'  it never seems to get a lock on the cable.  I have not yet got the error message that the initial poster has reported however.

---

