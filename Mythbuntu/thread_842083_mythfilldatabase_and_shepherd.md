---
title: "mythfilldatabase and shepherd"
date: 2008-06-27
forum: Mythbuntu
---

### Post by phillipcc on 2008-06-27
hi everyone after being forced to reinstall mythbuntu the mythfilldatabase worked a few times then i get the following if anyone can help me out please let me know post below
i am using mythbuntu 8.04 mythfilldatabase and shepherd

phil@phil-tv:~$ mythfilldatabase
2008-06-27 15:38:36.933 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-27 15:38:36.957 Empty LocalHostName.
2008-06-27 15:38:36.962 Using localhost value of phil-tv
2008-06-27 15:38:36.989 New DB connection, total: 1
2008-06-27 15:38:36.999 Connected to database 'mythconverg' at host: localhost
2008-06-27 15:38:37.002 Closing DB connection named 'DBManager0'
2008-06-27 15:38:37.005 Connected to database 'mythconverg' at host: localhost
2008-06-27 15:38:37.025 New DB connection, total: 2
2008-06-27 15:38:37.027 Connected to database 'mythconverg' at host: localhost
2008-06-27 15:38:37.044 Updating source #1 (tv0) with grabber tv_grab_au
2008-06-27 15:38:37.045 Found 7 channels for source 1 which use grabber
2008-06-27 15:38:38.414 Grabber has capabilities: baseline manualconfig preferredmethod 
2008-06-27 15:38:39.751 Grabber prefers method: allatonce
2008-06-27 15:38:39.753 New DB connection, total: 3
2008-06-27 15:38:39.755 Connected to database 'mythconverg' at host: localhost
shepherd v1.3.7 (linux)

Reading configuration file: /home/phil/.shepherd/shepherd.conf
Reading channels file: /home/phil/.shepherd/channels.conf
Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98, <FN> line 8.
2008-06-27 15:38:41.953 FAILED: xmltv returned error code 512.
2008-06-27 15:38:41.965 Error in 1:1: unexpected end of file
2008-06-27 15:38:41.966 Updating icons for sourceid: 1
2008-06-27 15:38:41.968 New DB connection, total: 4
2008-06-27 15:38:41.969 Connected to database 'mythconverg' at host: localhost
2008-06-27 15:38:41.971 No programs found in data.
2008-06-27 15:38:41.977 Failed to fetch some program info
2008-06-27 15:38:41.978 Adjusting program database end times.
2008-06-27 15:38:42.030     0 replacements made
2008-06-27 15:38:42.031 Marking generic episodes.
2008-06-27 15:38:42.075     Found 0
2008-06-27 15:38:42.075 Marking repeats.
2008-06-27 15:38:42.132     Found 0
2008-06-27 15:38:42.132 Unmarking new episode rebroadcast repeats.
2008-06-27 15:38:42.183     Found 0
2008-06-27 15:38:42.338 Marking episode first showings.
2008-06-27 15:38:44.582     Found 1028
2008-06-27 15:38:44.582 Marking episode last showings.
2008-06-27 15:38:46.742     Found 1028
2008-06-27 15:38:46.748 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-06-27 15:38:46.771 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-27 15:38:46.783 Using protocol version 40
2008-06-27 15:38:46.825 Received a remote 'Clear Cache' request
2008-06-27 15:38:46.833 mythfilldatabase run complete.
2008-06-27 15:38:46.833 DataDirect: Deleting temporary files


hope someone can point me in the right direction any help most appreciated
bye
phillip cole

---

### Post by ian dobson on 2008-06-27
Hi,

Looks as if you have an old version of a perl lib, I'm not sure exactly which one but have a look here:- [http://www.overclockers.com.au/wiki/MythTV-TV_GRAB_AU](http://www.overclockers.com.au/wiki/MythTV-TV_GRAB_AU) 

Extra have a look at the "apt-get install" command.

Regards
Ian Dobson

---

