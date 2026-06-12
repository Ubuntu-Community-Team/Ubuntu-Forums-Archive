---
title: "System shuffling tuner cards on Edgy"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by aaltieri on 2007-10-31
Greetings;

I'm running into a problem with my Edgy/MythTV system.  On Random boots, the system re-orders my Tuner cards.  I have three cards:  An Aver a180, a PVR150 and a PVR500 (2 tuners).  Most boots they stay in order.  But once in a while it will load the aver BETWEEN the two PVR500 tuners.

Is there a way to force them to load in a certain order or tie the specific card to the specific device?  My last Ubuntu build did not have this problem.  It's just since rebuilding the box that I'm having issues.

Thanks.

Peace.

Anthony.

---

### Post by afljafa on 2007-11-04
I have precisely the same problem in Gusty. PVR keeps switching device numbers with a HVR on reboots - pain.

---

### Post by afljafa on 2007-11-04
Blacklisting ivtv and modprobing it after everything else has finished seems to resolve the issue.

---

