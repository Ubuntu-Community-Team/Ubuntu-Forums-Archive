---
title: "Mythtv records in LiveTV, not in Preset recording"
date: 2010-07-12
forum: Mythbuntu
---

### Post by Sonthun on 2010-07-12
Hi.  I have two Hauppauge tuner cards.  The HVR-1600 and the HVR-2250 (with two tuners on it).  I can get all three tuners to record at once if I go in to Watch TV and tell each one to record.  They all produce viable recordings that play back fine.  

But, if I preset a recording using either the Program Guide or Manual Record only the 1600 works.  The two tuners on the 2250 says they recorded, but nothing happens.  It even shows the file in the Watch Programs, but then the file doesn't actually exist.  Can somebody help me with this?  They both worked fine until I upgraded to 10.4.  I'd really appreciate any pointers.  Thanks.

---

### Post by LowSky on 2010-07-13
I would delete the tuners from the backend and re-add them. I would give priority to the 2250's Tuners. Also check your mythtv logs to see if any errors are occuring.

---

### Post by Sonthun on 2010-07-13
Thanks.  That actually helped.  I found the logs and was able to diagnose it from there.  Seems like somehow the permissions for the directory only worked for the 1600 and not the 2250.  I re-did the permissions and now it works.

---

