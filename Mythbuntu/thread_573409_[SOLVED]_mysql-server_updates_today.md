---
title: "[SOLVED] mysql-server updates today?"
date: 2007-10-11
forum: Mythbuntu
---

### Post by dannyboy79 on 2007-10-11
I am curious if it's safe to do the upgrades that I am seeing Fesity Fawn running mythtv from the feisty-updates repo? They all look to be related to mysql. Another question, is it crucial that if I do do the updates (HA, I just accidentally wrote, "If I do do". HA HA) should I make sure that no recordings are scheduled to record that instance or that they are NO recordings currently recording?

Any comments from anyone?

---

### Post by davemorris on 2007-10-23
I've not given it a thought as to weather it was safe or not I've just upgrade it.  

The data in the database won't be affected with mysql upgrades, however as it swaps the versions over, the mythbackend won't be able to access the database for a few seconds.  This has not caused me any problems whilst recording, although it might do near the start/end of a recording or when people are using the frontends.

---

### Post by dannyboy79 on 2007-10-25
i did the upgrade and everything has been fine.

---

