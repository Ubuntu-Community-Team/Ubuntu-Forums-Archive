---
title: "Updates break livetv"
date: 2008-10-12
forum: Mythbuntu
---

### Post by fenx7 on 2008-10-12
After installing mythbuntu 8.04.1 from the iso all is mostly well. I noticed that the update manager was showing a large number of updates to be installed. By default they were all ticked, so I installed the bunch of them and when my system restarted the performance of live tv significantly degraded and was noticably jerky.

What should've I have done to fix? I reinstalled from cd and have not updated as the system was in an unusable state.

I want to have the latest updates, but do not want to upgrade without being able to fix the problems.

---

### Post by jbman on 2008-10-13
do you have backports ticked?

I have a/v issues after the latest backports which gives myth 18... release of 0.21.

Check your playback setting make sure its the same it was before the updates.

---

### Post by madman_lxl on 2008-10-13
I had a similar issue a few weeks back updated and everything ran like a legless zombie. Seems for some reason that the delete slow box was un-ticked in my case. Slammed the hdd's I/O.

---

### Post by fenx7 on 2008-10-19
I have unchecked the backports for now and the updates went resonably well, although noe the hdd light flickers on and off very often (1 second on and 1 second off). I have installed iotop to monitor hdd activity, but it does not show any problems - excessive disk access.

Can the backports be installed without modifying the mythtv settings?

---

### Post by fenx7 on 2008-12-29
Upgraded to 8.10 and installed backports and system dropped frames.

I had to change to the slim profile to avoid dropping frames. Still have the hdd flickering quite often, even when not recording or playing tv.

---

