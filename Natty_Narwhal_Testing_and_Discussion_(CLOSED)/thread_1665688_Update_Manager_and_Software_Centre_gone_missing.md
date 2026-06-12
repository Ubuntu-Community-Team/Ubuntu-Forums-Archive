---
title: "Update Manager and Software Centre gone missing"
date: 2011-01-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jennybrew on 2011-01-12
This evening after booting and going through the  usual mess of half drawn screens and delays I discovered Update Manager and Software Centre were not working.
Neither would open.
The fix turned out to be a quick visit to Synaptic and a "mass" mark for upgrade.
Once completed all is now well but I really cant understand what happened here ..and I do like to try and understand these things :)
Anyone have any ideas what happened here ?

---

### Post by ronacc on 2011-01-12
all kinds of changes in progress right now so its hard to say which caused it , next time something wont start try starting it from a terminal , that will usually give you some info about where things go wrong .

---

### Post by Yellow Pasque on 2011-01-13
The newer versions of the software that you tried to run were dependent on (upgraded versions of) packages not available when you did your last update. This can be caused by errors in dependencies or even some updates not propagating to the repo mirrors fast enough. This kind of breakage is very common in Ubuntu alpha testing and is usually corrected within 24 hours so that an upgrade remedies the issue.

---

