---
title: "No partial upgrade due to exclusive lock"
date: 2010-03-10
forum: Mythbuntu
---

### Post by Familienvater on 2010-03-10
I have upgraded my backend (Debian Lenny) from mythtv 0.21 to 0.22 without any problems. It seems to work fine.

But upgrading my frontend from Mythbuntu 9.04 to 9.10 is drivin' me nuts!

During upgrade I am asked if I want a partial upgrade. If I say yes I get the message "unable to get exclusive lock - another package management is already running". But there is none! 

If I follow the upgrade process proposed by update-manager, i.e. no partial upgrade I get a total mixed up installation. During upgrade I get the message that the Mythbuntu-ControlCentre won't be upgraded. After installation Nvidia won't run, Network manager does run (why, I had deinstalled in in 9.04) but not funtion correctly, network freezes every 5-10 minutes.

I have repeated this procedure twice now from a clean, updated and working backup.

I have been with Mythbuntu since 8.04 and never had problems updgrading.

My first point to look at is this partial upgrade option not working. How do I get this partial upgrade on the way to 9.10?

---

### Post by Familienvater on 2010-03-10
You can see from the attached log of the beginning of the upgrade process  that Mythbuntu wants to keep all Mythtv related packages at the current version (at least that's how I understand it).

But as the partial upgrade fails du to the exclusive lock (would that be also logged somewhere? - I haven't found it) the upgrade process does upgrade all packages at the same time - and fails completely.

Is there are way to force Mythbuntu to do a partial upgrade only!

Please help me! My wife and children are starting to wonder why it takes now 2 days for me to get the TV working again!

Regards,

Familienvater

---

### Post by tgm4883 on 2010-03-10
What method are you using when trying to upgrade from 9.04 to 9.10?

---

### Post by Familienvater on 2010-03-22
Sorry, I did not answer earlier, but the last two weeks there were some other things to do...

I finally succeed. I deinstalled all Mythtv-stuff, upgraded to 9.10 and then reinstalled everything again. That did work!

Thanks everybody!

Familienvater

---

