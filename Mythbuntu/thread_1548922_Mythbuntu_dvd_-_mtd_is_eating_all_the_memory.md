---
title: "Mythbuntu dvd - mtd is eating all the memory"
date: 2010-08-09
forum: Mythbuntu
---

### Post by Huwle on 2010-08-09
I have recently found that my mythbuntu system (10.04 64 bit) has stopped being able to handle dvd playback and import. On inserting a dvd, the system quickly becomes unusable and I can hear the hard drive going berserk. This used to work, so I wonder if an update has caused this??

Using 'top' shows that the mtd (MythTV Transcoding Daemon) is hogging the processor and has eaten around 80% of the system memory. The swap usage has gone through the roof - hence the hard drive madness.

I ran tried again with mtd running from the command line and it printed out the following:

```

2010-08-09 08:25:47.333 Using runtime prefix = /usr
2010-08-09 08:25:47.333 Using configuration directory = /home/huw/.mythtv
2010-08-09 08:25:47.356 Empty LocalHostName.
2010-08-09 08:25:47.357 Using localhost value of huw-tv
2010-08-09 08:25:47.444 New DB connection, total: 1
2010-08-09 08:25:47.491 Connected to database 'mythconverg' at host: localhost
2010-08-09 08:25:47.491 Closing DB connection named 'DBManager0'
2010-08-09 08:25:47.492 Connected to database 'mythconverg' at host: localhost
2010-08-09 08:25:47.502 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-08-09 08:25:47.506 Cannot load language en_gb for module mythdvd
2010-08-09 08:25:47.511 mtd started at Mon Aug 9 08:25:47 2010
2010-08-09 08:25:47.511 mtd is running on a host called huw-tv
2010-08-09 08:25:47.512 08:25:47: Waiting for connections/jobs
2010-08-09 08:25:47.512 08:25:47: mtd is listening on port 2442
libdvdread: Using libdvdcss version 1.2.10 for DVD access

*** libdvdread: CHECK_VALUE failed in dvdread/ifo_read.c:1203 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgn != 0 ***


*** libdvdread: CHECK_VALUE failed in dvdread/ifo_read.c:1914 ***
*** for pgci_ut->nr_of_lus < 100 ***

```

I assume mtd has hit a tight loop inside libdvdread? Anyone had similar woes?

---

### Post by Huwle on 2010-08-09
Update - I've just found that this appears to be an issue with one particular DVD - Micmacs (a strange French film). If I kill the mtd process, I can play this DVD no problem, but clearly can't import without mtd.

I've tried a different DVD and mtd behaves itself just fine. So what could be different about micmacs that upsets mtd so badly?

---

### Post by LowSky on 2010-08-09
Its a new type of DVD encryption, they hid the main movie a few chapters deep and it throws off the rippper.
there is away around it, play the movie using VLC find out what chapter the movie starts from, then rip using an app like acidrip. As long as the program is pointed directly and isn't trying to find the right chapter it should work smoothly

---

### Post by Huwle on 2010-08-12
Yes, you're right. I believe it is Arccos protection.
I have disabled the mtd daemon from starting up by commenting out the mtd lines in /usr/share/mythbuntu/session.sh. Now at least I can insert the disc and watch it without causing a denial of service attack.
I know some closed source rippers have ways around arccos, but none as yet in the foss world (I think).

---

