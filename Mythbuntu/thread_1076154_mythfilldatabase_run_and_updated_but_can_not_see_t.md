---
title: "mythfilldatabase run and updated but can not see the program guide"
date: 2009-02-21
forum: Mythbuntu
---

### Post by copycat on 2009-02-21
Hey,

I searched the forum for similar issues without result.  
Mythbuntu is running fine for 2 years now.  A month ago I fresh installed 8.10 on new hardware and connected my old hardware as frontend. (works fine).

I use mc2xml (cool tool) to download a good xmltv.mxl. Then I run a mythfilldatabase --file 1 & 2 for my pvr500.

It imports the file.  I can see that planned programs extend there date for the next 15 days update.

Since some day ago the program guide shows only programs for 1 German channel... the other channels don't provide any data.

I did a "mythfilldatabase  --do-channel-updates --refresh-all --file 1 /mc2xml/xmltv.xml" without results.

Any clue?

pcxpert@MythMan:/var/lib/mythtv/videos$ mythfilldatabase --file 1 /mc2xml/xmltv.xml
2009-02-21 09:07:03.737 Bypassing grabbers, reading directly from file
2009-02-21 09:07:03.741 Using runtime prefix = /usr
2009-02-21 09:07:03.775 Empty LocalHostName.
2009-02-21 09:07:03.775 Using localhost value of MythMan
2009-02-21 09:07:03.889 New DB connection, total: 1
2009-02-21 09:07:03.918 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:03.918 Closing DB connection named 'DBManager0'
2009-02-21 09:07:03.919 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:05.041 New DB connection, total: 2
2009-02-21 09:07:05.042 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:05.507 Updating icons for sourceid: 1
2009-02-21 09:07:05.532 New DB connection, total: 3
2009-02-21 09:07:05.532 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:09.612 New DB connection, total: 4
2009-02-21 09:07:09.612 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:13.917 Updated programs: 6 Unchanged programs: 5647
2009-02-21 09:07:14.060 Adjusting program database end times.
2009-02-21 09:07:14.273     0 replacements made
2009-02-21 09:07:14.273 Marking generic episodes.
2009-02-21 09:07:14.402     Found 0
2009-02-21 09:07:14.402 Marking repeats.
2009-02-21 09:07:14.534     Found 0
2009-02-21 09:07:14.534 Unmarking new episode rebroadcast repeats.
2009-02-21 09:07:14.535     Found 0
2009-02-21 09:07:14.793 Marking episode first showings.
2009-02-21 09:07:17.716     Found 5656
2009-02-21 09:07:17.717 Marking episode last showings.
2009-02-21 09:07:20.530     Found 5656
2009-02-21 09:07:20.541
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-02-21 09:07:20.544 Connecting to backend server: 192.168.111.4:6543 (try 1 of 5)
2009-02-21 09:07:20.545 Using protocol version 40
2009-02-21 09:07:20.577 Received a remote 'Clear Cache' request
Segmentation fault
pcxpert@MythMan:/var/lib/mythtv/videos$ mythfilldatabase --file 2 /mc2xml/xmltv.xml
2009-02-21 09:07:26.763 Bypassing grabbers, reading directly from file
2009-02-21 09:07:26.764 Using runtime prefix = /usr
2009-02-21 09:07:26.764 Empty LocalHostName.
2009-02-21 09:07:26.764 Using localhost value of MythMan
2009-02-21 09:07:26.779 New DB connection, total: 1
2009-02-21 09:07:26.783 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:26.783 Closing DB connection named 'DBManager0'
2009-02-21 09:07:26.784 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:27.377 New DB connection, total: 2
2009-02-21 09:07:27.378 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:27.835 Updating icons for sourceid: 2
2009-02-21 09:07:27.836 New DB connection, total: 3
2009-02-21 09:07:27.836 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:31.276 New DB connection, total: 4
2009-02-21 09:07:31.277 Connected to database 'mythconverg' at host: localhost
2009-02-21 09:07:35.536 Updated programs: 6 Unchanged programs: 5647
2009-02-21 09:07:35.677 Adjusting program database end times.
2009-02-21 09:07:35.847     0 replacements made
2009-02-21 09:07:35.847 Marking generic episodes.
2009-02-21 09:07:35.994     Found 0
2009-02-21 09:07:35.994 Marking repeats.
2009-02-21 09:07:36.147     Found 0
2009-02-21 09:07:36.147 Unmarking new episode rebroadcast repeats.
2009-02-21 09:07:36.147     Found 0
2009-02-21 09:07:36.430 Marking episode first showings.
2009-02-21 09:07:39.178     Found 5656
2009-02-21 09:07:39.178 Marking episode last showings.
2009-02-21 09:07:41.890     Found 5656
2009-02-21 09:07:41.891
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-02-21 09:07:41.893 Connecting to backend server: 192.168.111.4:6543 (try 1 of 5)
2009-02-21 09:07:41.894 Using protocol version 40
2009-02-21 09:07:41.911 Received a remote 'Clear Cache' request
2009-02-21 09:07:41.920 mythfilldatabase run complete.
2009-02-21 09:07:41.920 DataDirect: Deleting temporary files

---

### Post by parc on 2009-02-22
I have also problems with this tool. I'm running one Mythbuntu system with 8.04 (backend and frontend) and one with 8.10 (backend without GUI) and more or less after some times (some channels in) my EPG is getting empty (at least nothing is shown in the www interface).

Then I've to quit the GUI and configure the backend (dummy) and then it starts a new mythfilldatabase and mostly after that task I have a filled EPG again.

Thats rather boring .....

---

### Post by copycat on 2009-02-23
Parc,

thanks for the reply, at least I'm satisfied that it is a bug.

What machine do you quit the GUI on?  My backend is a 8.10 with gui?  My frontend is it too.

You restart setup for the backend then? I think if I put it on "frontend only" it looses the database and all current recordings. Can you tell some more details of the procedure you followed?

Shouldn't it be better to report a bug?
Maybe the ubuntu guys need some logs to detect what the issue is.

---

