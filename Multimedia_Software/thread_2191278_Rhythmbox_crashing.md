---
title: "Rhythmbox crashing"
date: 2013-12-01
forum: Multimedia Software
---

### Post by jsavga on 2013-12-01
For some time I've been having issues with Rhythmbox crashing on me. It usually happens when changing tracks, but not always. 

Today I launched it from a terminal and this is the output when it crashed:

[IMG]http://home.comcast.net/~jsavga//temp/Rhythmbox.png[/IMG]

---

### Post by jsavga on 2013-12-02
BTW, this is in Ubuntu 13.10 but the problem has been around at least since 13.04.

---

### Post by tgalati4 on 2013-12-02
It looks like your rhthmbox database is corrupt in a way that is not fixable.  Perhaps deleting it and do a fresh import.  How many tracks were in your database?

---

### Post by jsavga on 2013-12-03
I can't find how to delete the database, there is no hidden file associated with rhythmbox under Home. Rhythmbox itself doesn't seem to have a menu icon (I seem to remember a while back it having a menu). Shouldn't it have an menu icon top right?


**EDIT:** Found them under */home/.local/share/rhythmbox* named as *rhythmdb.xml* and *playlists.xml*. Renamed them adding .old to the end and launched Rhythmbox to let it build a new database. Imported the same libraries (1388 songs) and so far it seems to be doing alright.

---

### Post by tgalati4 on 2013-12-03
Check the SMART status of your hard drive to make sure it is not having problems.  Database errors can be expected if you have a large database (over 10K tracks) and you move things around a lot.  Otherwise, your database is small, so such an error is something to investigate.

---

### Post by jsavga on 2013-12-03
I spoke to soon, the problem is back. At first when it happens, Rhythmbox just stops playing in between songs. I remember this is how the problem started off before. Eventually it leads to Rhythmbox crashing.

---

