---
title: "CD Ripping only works once"
date: 2008-01-02
forum: Mythbuntu
---

### Post by John Lentz on 2008-01-02
I'm new to the mythtv, so this is probably a setup issue, but I can't find it.  What is happening is that I can rip one of my CDs just fine, however, when I put the next CD in, it won't recognize it (nothing happens when I press import CD).  When I esc out of the frontend, it gives the error about not being able to connect to the backend, check IP address ...  If I go into backend setup, everything is OK for the IP (I've tried 127.0.0.1 and also my lan address).  When I leave the setup, it must do something because I can then start the frontend and it will detect and rip one CD again, before it stops working and I get the connection error msg again when I leave the frontend.

Is there a setting I need to correct?  Since it works occasionally, it doesn't seem like a permissions thing - does it?

Thanks,

John

---

### Post by John Lentz on 2008-01-02
Update on issue.  I found that after I push Import CD and nothing happens, the tray comes open.  If I just leave the CD in the tray and don't close it or do anything else, eventually the tray will close itself.  Not sure how long that takes, since I wasn't looking at the PC, but I'm guessing 5-10 minutes(?).  After it closes the tray, I can then push Import CD and it works.    Any ideas on how to get it to work quicker?

Thanks,

John

---

### Post by volkswagner on 2008-01-02
Check you log files /var/log/mysql.log, /var/log/mythtv/mythfrontend.log and mythbackend.log

Sounds more like a connection problem or mysql.

---

### Post by John Lentz on 2008-01-03
I think I finally figured it out.  When I put a CD in, I need to wait about 10-15 secs for the pc to detect/sort out what I put in.  If I wait that amount of time, then import CD works.  Must be sensitive that way.

---

