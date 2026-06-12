---
title: "Mythfilldatabase trouble"
date: 2008-05-19
forum: Mythbuntu
---

### Post by axelsvag on 2008-05-19
Since a few days I do not seems to be able to use the mythfilldatabase either from the onboard mythfilldatabase, a cron or from the terminal. When I try the command from terminal I first get this ```
2008-05-19 16:23:32.891 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-19 16:23:32.892 Empty LocalHostName.
2008-05-19 16:23:32.892 Using localhost value of aco-desktop
2008-05-19 16:23:32.900 New DB connection, total: 1
2008-05-19 16:23:32.903 Connected to database 'mythconverg' at host: localhost
2008-05-19 16:23:32.905 Closing DB connection named 'DBManager0'
2008-05-19 16:23:32.906 Connected to database 'mythconverg' at host: localhost
2008-05-19 16:23:32.910 New DB connection, total: 2
2008-05-19 16:23:32.911 Connected to database 'mythconverg' at host: localhost
2008-05-19 16:23:32.911 mythfilldatabase: Listings Download Started
2008-05-19 16:23:32.945 Updating source #1 (HFAB Kabeltv) with grabber tv_grab_combiner
2008-05-19 16:23:32.945 Found 20 channels for source 1 which use grabber
2008-05-19 16:23:32.952 Grabber has capabilities: baseline manualconfig 
2008-05-19 16:23:32.952 
2008-05-19 16:23:32.952 Checking day @ offset 0, date: m&#65533;n maj 19 2008
2008-05-19 16:23:32.976 Data is already present for m&#65533;n maj 19 2008, skipping
2008-05-19 16:23:32.977 
2008-05-19 16:23:32.977 Checking day @ offset 1, date: tis maj 20 2008
2008-05-19 16:23:32.977 Data Refresh always needed for tomorrow
2008-05-19 16:23:32.977 Refreshing data for tis maj 20 2008
2008-05-19 16:23:32.978 New DB connection, total: 3
2008-05-19 16:23:32.978 Connected to database 'mythconverg' at host: localhost


``` and it hangs there for about 4 minutes. After that it continues but does not update anything and give this ```
2008-05-19 16:27:27.885 New DB connection, total: 4
2008-05-19 16:27:27.886 Connected to database 'mythconverg' at host: localhost
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
Ignoring empty timestamp.
2008-05-19 16:27:27.964 New DB connection, total: 5
2008-05-19 16:27:27.964 Connected to database 'mythconverg' at host: localhost
2008-05-19 16:27:27.974 Updating icons for sourceid: 1
2008-05-19 16:27:28.859 Updated programs: 0 Unchanged programs: 564
2008-05-19 16:27:28.861 
2008-05-19 16:27:28.861 Checking day @ offset 2, date: ons maj 21 2008
2008-05-19 16:27:28.879 Data is already present for ons maj 21 2008, skipping
2008-05-19 16:27:28.879 
2008-05-19 16:27:28.879 Checking day @ offset 3, date: tor maj 22 2008
2008-05-19 16:27:28.897 Data is already present for tor maj 22 2008, skipping
2008-05-19 16:27:28.897 
2008-05-19 16:27:28.897 Checking day @ offset 4, date: fre maj 23 2008
2008-05-19 16:27:28.910 Data is already present for fre maj 23 2008, skipping
2008-05-19 16:27:28.910 
2008-05-19 16:27:28.911 Checking day @ offset 5, date: l&#65533;r maj 24 2008
2008-05-19 16:27:28.924 Data is already present for l&#65533;r maj 24 2008, skipping
2008-05-19 16:27:28.924 
2008-05-19 16:27:28.931 Checking day @ offset 6, date: s&#65533;n maj 25 2008
2008-05-19 16:27:28.942 Data refresh needed because only 13 out of 20 channels have at least one program listed for day @ offset 6 from 8PM - midnight.  Previous day had 18 channels with data in that time period.
2008-05-19 16:27:28.943 Refreshing data for s&#65533;n maj 25 2008
2008-05-19 16:36:41.832 Updating icons for sourceid: 1
2008-05-19 16:36:41.832 No programs found in data.
2008-05-19 16:36:41.832 Grabber is no longer returning program data, finishing
2008-05-19 16:36:41.833 Data fetching complete.
2008-05-19 16:36:41.833 Adjusting program database end times.
2008-05-19 16:36:41.929     0 replacements made
2008-05-19 16:36:41.931 mythfilldatabase: Listings Download Finished
2008-05-19 16:36:41.931 Marking generic episodes.
2008-05-19 16:36:41.957     Found 0
2008-05-19 16:36:41.957 Marking repeats.
2008-05-19 16:36:41.983     Found 0
2008-05-19 16:36:41.983 Unmarking new episode rebroadcast repeats.
2008-05-19 16:36:41.984     Found 0
2008-05-19 16:36:42.057 Marking episode first showings.
2008-05-19 16:36:44.165     Found 4830
2008-05-19 16:36:44.166 Marking episode last showings.
2008-05-19 16:36:46.287     Found 4830
2008-05-19 16:36:46.288 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-05-19 16:36:46.290 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-19 16:36:46.291 Using protocol version 40
2008-05-19 16:36:46.346 mythfilldatabase run complete.
2008-05-19 16:36:46.346 DataDirect: Deleting temporary files
ICE default IO error handler doing an exit(), pid = 7471, errno = 32

``` and it seems that it got stuck for every day it tries to update

Is it the grabber or my database that cause this problem?

---

### Post by axelsvag on 2008-05-22
After a fresh install everything seems to be working again. I have no idea what was causing the trouble so I can not say that it is solved.

---

