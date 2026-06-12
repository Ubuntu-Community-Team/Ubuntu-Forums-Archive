---
title: "Something wrong with Launchpad bug heat?!"
date: 2010-12-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by NHclimber on 2010-12-09
What's up with the bug heat on Launchpad?

Right now on the bugs page of Launchpad | Ubuntu, 1/2 of the "hot" bugs  are new, undecided bugs with bug heat of 3495!? 

No disrespect to  reporters of bug #683981, "Missing .info file error" for drush package  (which affects 2 people and happens to be a duplicate report), but that  hardly ranks with #642421, "Maverick could not load  /lib/modules/2.6.35-22-generic/modules.dep" which affect 206 people.   What gives?

I looked over the bug heat code and can only guess that the bug heat must be coming from an uninitialized record that a new bug is given (because the bug heat starts with the value from the database). Either that or devs are plugging in bug heat values directly into the database.  That sounds a bit too sinister though...

---

### Post by cariboo on 2010-12-09
You file bugs against launchpad here:

[https://bugs.launchpad.net/launchpad](https://bugs.launchpad.net/launchpad)

---

### Post by NHclimber on 2010-12-09
Thanks for link. Bug# 688364 successfully reported.  Hopefully, it gets read though - it only got a heat of 6.  (I admit - I was kind of hoping for a 4000+ although I would have been happy with a mid-2000...)

---

