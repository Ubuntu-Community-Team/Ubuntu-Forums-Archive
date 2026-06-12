---
title: "MythTV mythfilldatabase broken after clock change"
date: 2009-04-11
forum: Multimedia Software
---

### Post by AndrewWalker on 2009-04-11
For some reason I no longer get any tv guide data after the clocks changed from GMT to BST (or around that time). 
I saw a similar post relating to this but it was very old and didn't make any difference
[http://ubuntuforums.org/showthread.php?t=959211&highlight=mythfilldatabase+broken](http://ubuntuforums.org/showthread.php?t=959211&highlight=mythfilldatabase+broken)
mythfilldatabase doesn't actually give any errors though, here's the result.

mythtvuser@mythtvbox:~$ mythfilldatabase
2009-04-11 22:39:58.497 Using runtime prefix = /usr
2009-04-11 22:39:58.498 Empty LocalHostName.
2009-04-11 22:39:58.498 Using localhost value of mythtvbox
2009-04-11 22:39:58.512 New DB connection, total: 1
2009-04-11 22:39:58.519 Connected to database 'mythconverg' at host: localhost
2009-04-11 22:39:58.521 Closing DB connection named 'DBManager0'
2009-04-11 22:39:58.522 Connected to database 'mythconverg' at host: localhost
2009-04-11 22:39:58.526 New DB connection, total: 2
2009-04-11 22:39:58.527 Connected to database 'mythconverg' at host: localhost
2009-04-11 22:39:58.632 Source 1 configured to use only the broadcasted guide data. Skipping.
2009-04-11 22:39:58.636 Data fetching complete.
2009-04-11 22:39:58.636 Adjusting program database end times.
2009-04-11 22:39:58.818     0 replacements made
2009-04-11 22:39:58.818 Marking generic episodes.
2009-04-11 22:39:58.907     Found 0
2009-04-11 22:39:58.907 Marking repeats.
2009-04-11 22:39:58.985     Found 0
2009-04-11 22:39:58.985 Unmarking new episode rebroadcast repeats.
2009-04-11 22:39:58.987     Found 0
2009-04-11 22:39:59.189 Marking episode first showings.
2009-04-11 22:40:01.225     Found 4315
2009-04-11 22:40:01.225 Marking episode last showings.
2009-04-11 22:40:02.700     Found 4315
2009-04-11 22:40:02.701
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2009-04-11 22:40:02.704 Connecting to backend server: 192.168.0.7:6543 (try 1 of 5)
2009-04-11 22:40:02.704 Using protocol version 40
2009-04-11 22:40:02.711 Received a remote 'Clear Cache' request
2009-04-11 22:40:02.729 mythfilldatabase run complete.
2009-04-11 22:40:02.729 DataDirect: Deleting temporary files
mythtvuser@mythtvbox:~$

I'm only using the on-screen guide and I'm running the 64bit version of 8.10
Any suggestions?

---

