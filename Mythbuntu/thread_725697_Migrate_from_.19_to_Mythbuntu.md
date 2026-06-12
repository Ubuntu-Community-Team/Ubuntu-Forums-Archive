---
title: "Migrate from .19 to Mythbuntu?"
date: 2008-03-15
forum: Mythbuntu
---

### Post by fortytwo on 2008-03-15
I've got a backend I've been using for quite a while and have a new machine I'd like to make the backend.  I'd also like to put MythBuntu on the new machine (I installed Myth by hand on the current one).

Obviously I've got a good amount of recorded tv on the current backend, and a large amount of movies in MythVideo whose meta data I would rather not lose.

What is the best way to migrate to the new backend?  At what point should I move the drives with the recorded shows? (Which are spread across multiple drives brought together using lvm, by the way.  I can move the shows to another drive and move them back if necessary).  What's the process to migrate the database over?

Thanks.

---

### Post by foxbuntu on 2008-03-18
I would suggest installing phpmyadmin, exporting the db, copy out the shows and any other pertuiant data, make note of the location of the recording and such if you are not using mythtv defaults, then rebuild with Mythbuntu 8.04A4 and reinstall phpmyadmin on the new build, import the DB copy back the videos to the proper location and that should do it. You will have to of course setup any serial IR/Lirc, but this is easy with mythbuntu control centre.

---

