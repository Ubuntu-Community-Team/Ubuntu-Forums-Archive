---
title: "Tuner discrepency in Frontend and Backend - Haupauge 1250"
date: 2012-02-09
forum: Mythbuntu
---

### Post by the_pod on 2012-02-09
Hi.  Have had a mythbox running for several years now.  After the superbowl I decided to upgrade the system.  Moved via the Update Manager from 10.4 LTS to the current 11.10 mythbuntu.  

Side question - did this upgrade my mythtv version from .22 to .24?  I believe so, but I'm not sure.

Anyway, I have 2 tuners.  The first is an HDHomeRun (so technically 2 tuners here).  This works quite well.  

The 2nd tuner is an Hauppauge 1250.  Am using the digital side obviously.

The problem I'm running into is that there is a discrepency between the # of tuners in the front-end and the backend.  In the backend, it shows 3 tuners - 2 HDHRs and 1 DVB (LGDT3305 aka the 1250).  This is what I want.

In the frontend, however, it shows 4 tuners.  The 1250 is being double-counted.  This is quite frustrating since this means that, on occasion, some shows will not be recorded if they are assigned to the 4th (and non-existent) tuner.

I have deleted the DVB from the backend a half dozen times, restarted front end (now down to the 2 HDHR tuners), gone back to the backend, added the 1250, and then back to the frontend to check - every time with the 1250 being duplicated and the system showing 4 tuners.

Fwiw, this would happen on occasion with the 10.04 (.22) system I had, however deleting from the backend and re-adding would take care of the problem.

Has anyone encountered this and/or have a work-around?  I find it frustrating and would like to have all 3 tuners working appropriately without having a non-existent wild-card tuner potentially screwing up the recording schedules.

Thanks for any help.

-Scott

---

### Post by nickrout on 2012-02-09
Do you have multirec set up for the dvb card? (in card setup |recording options).

It is a great feature, and I have mine set to 4 each, same as for my hdhrs.

---

### Post by the_pod on 2012-02-14
Thanks. Finally had some time to tinker and this was indeed the issue.   I was never aware of this feature and thought I was going crazy.  All better.

---

