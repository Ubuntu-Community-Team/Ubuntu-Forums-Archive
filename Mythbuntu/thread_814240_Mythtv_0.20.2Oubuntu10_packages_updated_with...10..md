---
title: "Mythtv 0.20.2Oubuntu10 packages updated with...10.1--now can't edit recordings"
date: 2008-05-31
forum: Mythbuntu
---

### Post by klc5555 on 2008-05-31
Greetings:

I needed to upgrade my NVidea graphics driver on a machine running Mythbuntu 7.10 I was still using the one from the iso install of Mythbuntu 7.10, and, in general I had kept this particular installation very close to the .iso Mythbuntu 7.10 level.

Doing this through Update manager, I noticed that all of the Mythtv 0.20.2Oubuntu10 packages for Gutsy had been revised to 0.20.2Oubuntu10.1 I did the "security" and the "recomended" Gutsy updates, including all the Mythtv revisions from 0.20.2...10 to 0.20.2...10.1 

The updates work, with the exception of editing recordings. If I now bring up the "edit recordings" box and its bottom-of-the-screen slider while in a recording, the operation fails with the error message  "No seek table"

Which package is the one likely to be at fault? And can I backlevel just the one package back to 0.20.2...10 or am I likely to have to backlevel everything?

---

### Post by klc5555 on 2008-05-31
Never mind.

The problem was the seek tables for all my existing recordings evidently got nuked when I upgraded the  mythtv packages from 0.20.2...10 to 0.20.2...10.1. "mythcommflag --rebuild", etc., couldn't fix them.

But since the seek tables are part of mythconverg, a quick restore from my daily mythconverg backup fixed everything.

Hooray for daily mythconverg backups! And hooray for the scripts found in the mythtv wiki user manual at

 [http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/index.php/User_Manual:Periodic_Maintenance) 

which have already saved my butt more than once.

Cheers.

---

