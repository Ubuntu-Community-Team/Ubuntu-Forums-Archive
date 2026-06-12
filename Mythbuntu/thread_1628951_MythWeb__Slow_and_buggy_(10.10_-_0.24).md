---
title: "MythWeb : Slow and buggy (10.10 - 0.24)"
date: 2010-11-23
forum: Mythbuntu
---

### Post by Xrcam on 2010-11-23
Got this when i click an item in the schedule:
 
 
 
**Warning** at /usr/share/mythtv/mythweb/modules/tv/detail.php, line 305:
!!NoTrans: Invalid argument supplied for foreach()!!
**Warning** at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
!!NoTrans: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:150)!!


 
Also experiencing 2 minutes delay before page complete.
 
Had not this problem with 10.10 0.23.1... ant clues ?

---

### Post by LowSky on 2010-11-23
hmmm... mythweb is actually working faster for me with the upgrade.

take a look at the files it is warning you about with Gedit you can find the line in quesiton very easily

also mythbuntu control center has an option to repair the database. try running that, it might fix the issue.

---

### Post by pu15e on 2010-11-23
When that kinda thing happens here (10.04, 0.24 autobuilds), it's always owing to the back end playing up.

Sorry I can be no more help than that presently, but I haven't yet ascertained why the backend regularly stops all incoming connections (from other frontends and sbe's, mythweb and, usually, even ssh), yet still functions locally (backend is till running / recording / commflagging)...

Cheers,
 Mattt.

---

### Post by Xrcam on 2010-11-23
Solved.
Database optimization did the trick.
 
Thanks.

---

