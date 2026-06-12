---
title: "Shakey about 8.02 to 10.4 upgrade, and Mythbuntu"
date: 2010-09-15
forum: Mythbuntu
---

### Post by drifting on 2010-09-15
Hi all.


Just a little advice before I finally get myself in gear and do the major upgrade. Have to say that my current Myth has been running like a dream for most things.

I believe from reading the how to post that the following will be of some help? :-

mythtv-common:
  Installed: 0.21.0+fixes21768-0ubuntu0+mythbuntu1
  Candidate: 0.21.0+fixes21768-0ubuntu0+mythbuntu1
  Version table:
 *** 0.21.0+fixes21768-0ubuntu0+mythbuntu1 0

I have taken a snapshot of the root drive with Acronis, and also have backed up the database to numerous places. 

All data drives are formatted to XFS, with the OS drive on ext3

Is there anything I should be aware of?

Regards Paul

---

### Post by LowSky on 2010-09-15
If its running like a dream, then I would say dont upgrade.

Also I do not know if Mythtv will upgrade correctly. your going from .21 to .23, hopefully it doesn't break anything.

---

### Post by drifting on 2010-09-15
Yes valid point, but I am also concious of falling behind on versions, and the longer I leave it the more the DB seems to change, and I really do not fancy losing 3 years of information. It might have been 4 years, but dumbo here did not backup the database, a very sharp lesson learned.

Regards Paul

---

### Post by alien878 on 2010-09-16
You have your backups, so I would say just go for it.  If you run into problems, just restore and try 9.08, etc.  Note that you may have to re-install grub to fix up the MBR after a restore.

FYI:  You will see a lot of changes.  Many good, some bad.  It depends on your system.  Ex. I'm stuck on 9.08 because of some serious regressions in the mantis drivers need for my system.

---

### Post by elliott6 on 2010-09-16
I upgraded, and haven't really been unhappy at all.  Was on 8.10 and wanted to get to the latest LTS.

There were a few minor hiccups, but nothing that couldn't be solved with a quick search and some config changes.

Good luck and just go for it!

---

### Post by egandy on 2010-09-18
My system has been from 8.04 to 10.04.   I ran 7.10 on it before that but didn't upgrade from it.  For the most part it all went well for me.  There were a couple times I had to manually delete some things to make an upgrade complete.  The upgrades only cause me two problems that really stand out in my memory.  First was the login bug that sometimes caused me to have to attempt to login several times before it actually logs in.  The other problem is my sound sometimes is muted on login now.  Neither one is a real big deal for me because I rarely reboot.  I've never tried very hard to fix either one.  The upgrades have actually fixed more problems for me than they have caused.  I think 9.10 was very stable compared to prior versions and 10.04 seems to be the best version to date.  The frontend is faster and more stable than ever and the backend seems to be rock solid as always.

---

### Post by drifting on 2010-09-25
Oh I so wished mine went ok, but sadly no! I shall open another post about the nightmares of my tuner cards. All I can say is thank heaven for backups and Acronis :-) Now back on a fully working 8.04 LTS, just knew I should have left it alone :-)

The saga will continue when i have a few days off, and find out more about all tuners being unavialable.

---

