---
title: "Is upgrading to 0.27 also a good time to update distribution?"
date: 2013-10-03
forum: Mythbuntu
---

### Post by NikosF on 2013-10-03
My backend and four frontends are all currently running on 12.04 LTS and 0.26.  All is working well with the exception of one front-end which keeps locking up and I can't get LIRC working correctly.

I'm thinking of re-installing the OS on that one and am thinking about going to 13.04 (or potentially waiting for 13.10).  At the same time I would update all the machines to 0.27.  I do quite like having all my myth units running the same software, so am tempted to upgrade all OSs if I'm going to do it for one.

Any thoughts?
Thanks
Nick

PS: Been running effectively the same myth system since 2005 when I was running Fedora Core 5 or so.  Kept with Fedora until F15 or so then jumped off onto Ubuntu.

---

### Post by novellahub on 2013-10-03
I would stick with 12.04 LTS.  Then update to Mythtv 0.27 using the Mythbuntu Repos.   Also doing a backup of the database before the upgrade of Mythtv.   As far as the machine locking up, try to see if it is hardware related (Upgrade BIOS if necessary, check airflow, clean out any dust).  I have found that there is temperature settings in some BIOS setups that halt a machine if it gets to a certain temperature.  I have found them to be too low at times and had to increase the value.   Then the machine locking up behaved again after that.

---

