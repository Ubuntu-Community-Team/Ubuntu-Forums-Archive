---
title: "Backend constantly accessing hard drive"
date: 2008-09-16
forum: Mythbuntu
---

### Post by mjezell on 2008-09-16
Hi all,

This may be a problem unique to my setup which is :

ASUS M2N-E AMD  MB
Athlon 64 X2 5800+ Processor
4 GIG Single Channel Memory
3+ Tera GIG of SATA Storage in a LVM setup
750 Watts PS
Samsung DVD Burner

I built this box to consolidate my servers into one unit with the myth-server having the highest priority.  When I went to load Mythbuntu 8.04.01 64 version on the system I got a strange reaction from the SATA hd where the system was loaded.  The drive constantly was being access without any breaks or downtime.  I decided to load up just the server version of Ubuntu and everything went well.  Drive acted as it should.  Did a manual install of MythTV and after I setup the backend the drive started going crazy again.  I'm not referring to the drive spinning up and the drive light blinking every few seconds, I'm talking about the drive running constantly with the light staying on solid.  I've been using MythTV since version 1.9 but never ran into this problem.  Searching the forum and googling the problem hasn't shown a hd problem of this extent.  

Any ideas or suggestions would be appreciated.

Solved:
Seems that the database was not installed properly and the backend could not access it.  Must continue to try until it can because as soon as I corrected the database problem the drive started running as normal.  Thanks to all who took the time to look at this post.

---

### Post by Ocelaris on 2008-11-09
Sorry, I'm having the same problem, what exactly did you change with the database to correct this problem?

---

### Post by foxbuntu on 2008-11-11
This usually happens because of a bad password or other backend setting and the drive access comes from endless writing to the logs about the failure. I would suggest looking in the backend log (/var/log/mythtv/mythbackend.log) to discover the problem.

---

### Post by Ocelaris on 2008-11-12
Yes, this was definetly the case. I reran dkpg-reconfigure mythtv-common on something like that, and it fixed it lickety split. The backend logs were like 100 pages though...

---

