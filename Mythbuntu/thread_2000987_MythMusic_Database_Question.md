---
title: "MythMusic Database Question"
date: 2012-06-10
forum: Mythbuntu
---

### Post by johnlatz on 2012-06-10
I have an audio file that changes on a somewhat regular basis.  Under previous versions of MythMusic, simply having that audio file have the same name was enough to insure the database tracked it.  However, under MythMusic 0.25, the database apparently tracks dates as well as file names (date_entered & date_modified), and when those dates differ from what is currently in the database, an entirely new database entry is created.  In so doing, I wind up with several database references to the same file.

Is there a means to change the behavior of the database such that as long as the filename remains the same, no new entry in the database is created?

---

