---
title: "Planning migration from feisty/MythTV-0.20 to latest Mythbuntu - migrating DB content"
date: 2008-09-30
forum: Mythbuntu
---

### Post by sadams on 2008-09-30
Hi All,

Context:
========
I am a long-term Unix user & ex sys-admin and convert to ubuntu since warty 4 years ago. I live in the UK and utilise the UK's freeview digital TV service.

I have a MythTV V0.20 system based on feisty built in April 2007.
At that time I built it up from scratch on a pre-release feisty (couldn't get edgy to work with the NVidia card) which I have stuck with since then.

* I did once "roll forward" to a production release but it broke my USB Wifi adapter - apparently there were some firmware differences... nightmare! had to roll back again using backups and have never installed any updates ever since!

The box is "In service" in our house - combined front and back ends and works well - all is good. 
I am considering moving forward to the latest & greatest etc and need to plan my software migration to the new environment. 
NB - software changes only - not hardware.

I will need to negotiate a "service outage" with my "key users" to get a window to do my upgrade/migration - so I want my plan to work!!!  ;-)


Current Env:
============
S/W:
/etc/issue: Ubuntu feisty (development branch)
MythTV package: Version: 0.20-svn20070122-0.0ubuntu6
mysql-server - Version: 5.0.32-2

H/W: 
AMD Athlon(tm) 64 Processor 3200+
1 GB RAM
2 x Hauppauge Nova-T DVB-T
2 x 250GB Drives 

Specific Questions:
===================
I wish to retain my existing Database and recordings - and hopefully all my recording rules etc (if possible)
I wish to do a full and complete new installation of the OS and MythTV (Clean, simple... best method) and it looks as though using Mythbuntu is the best choice.
I will retain the current root partition as my roll-back option if the new install fails.

So:
1) Mysql DB - getting my old data into my new database...:
Can I just export my database via "mysqldump" and import them into the new "empty" DB which will be created via the Mythbuntu install?
Any hints/tips/options?
Any general advice/warnings?
Any showstopper issues?

2) My Content files.
I have these in a dedicated and discrete filesystem (via Vol Mgr) - i am assuming so long as I (the sys admin) ensure the filesystem is mounted correctly (on the same mountpoint) then MythTV will happily keep on using it... and that my exisitng content will be inherited into the new environment.
Can anyone here confirm this - and add any reassurance?


Many many thanks in advance for any help you can provide.

Regards,
 Steve.

---

### Post by kpatz on 2008-09-30
> **sadams said:**
> 
1) Mysql DB - getting my old data into my new database...:
Can I just export my database via "mysqldump" and import them into the new "empty" DB which will be created via the Mythbuntu install?
Any hints/tips/options?
Any general advice/warnings?
Any showstopper issues?This worked fine for me.  Just make sure to dump indexes etc. when you do the mysqldump (the defaults should suffice).  You could always shut down mysql and then backup the /var/lib/mysql/mythconverg directory, and restore it after you reinstall.  Do this before running mythsetup for the first time, then it will automagically upgrade the database to the current version.> 2) My Content files.
I have these in a dedicated and discrete filesystem (via Vol Mgr) - i am assuming so long as I (the sys admin) ensure the filesystem is mounted correctly (on the same mountpoint) then MythTV will happily keep on using it... and that my exisitng content will be inherited into the new environment.
Can anyone here confirm this - and add any reassurance?Yes - once you restore the database, as long as your content is in the same place as before (same path after mounting, etc.) it will just work.

---

### Post by novellahub on 2008-09-30
See this thread for details on migrating a old mythtv/Ubuntu install to a fresh one retaining the old recording database:

[http://ubuntuforums.org/showthread.php?t=800722](http://ubuntuforums.org/showthread.php?t=800722)

I have done this sucessfully on both Mythbuntu and Knoppmyth systems.

---

### Post by sadams on 2008-10-01
Hi - thanks to the two posters for their responses :-)

I will investigate further the info/links provided and make my plan...

Next question... hold on a while and wait for an Intrepid version of Mythbuntu... or go ahead on gutsy ?

Comments welcomed :-)

Steve.

---

