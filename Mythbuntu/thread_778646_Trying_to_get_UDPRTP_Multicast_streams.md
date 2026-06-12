---
title: "Trying to get UDP/RTP Multicast streams"
date: 2008-05-02
forum: Mythbuntu
---

### Post by TheCook on 2008-05-02
Hello all,

I've just installed Mythbuntu for the first time and have managed to get most of it working.  BUT I am trying to view some UDP/RTP Multicast streams.

I have created an m3u file with a single channel on it...
#EXTM3U
#EXTINF:0,202 - ABC1
udp://123.456.789.987:1234  (Numbers changed)

I also have a Haupague PVR-350 and can view TV via the antenna connection on it.  However, when I select channel 202 the current program stops for a short while and then continues without changing to 202.

If I back out of Mythbuntu I can run VLC and watch the stream without any troubles.  I just can't watch the stream from within Mythbuntu.

Have I missed something?

---

### Post by TheCook on 2008-05-02
Hello again.

I'll try and give a bit more detail.

I installed 8.04 last weekend.  I had a few troubles setting up routing tables to use the two ethernet cards the right way to access the streams and the internet... eventually sorted it out when I swapped the two cables over :lolflag:.
When I configured the backend I configured the PVR-350 and it scanned the channels OK.  I also configured a 'Network Recorder' and pointed it to file:///home/mythtv/iptv.m3u. I also set the 'tunning timeout' to about 15 seconds (just to be safe) The content of the m3u file is shown above.

I then created a listings source with 'no grabber' and associated the network recorder with the new source and scanned for channels.  The channels (i added a few more) are found and displayed.  When I back out and run mythfilldatabase I get:

2008-05-03 08:58:16.666 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-03 08:58:16.667 Empty LocalHostName.
2008-05-03 08:58:16.667 Using localhost value of MythTV
2008-05-03 08:58:16.687 New DB connection, total: 1
2008-05-03 08:58:16.713 Connected to database 'mythconverg' at host: localhost
2008-05-03 08:58:16.715 Closing DB connection named 'DBManager0'
2008-05-03 08:58:16.715 Connected to database 'mythconverg' at host: localhost
2008-05-03 08:58:16.719 New DB connection, total: 2
2008-05-03 08:58:16.719 Connected to database 'mythconverg' at host: localhost
2008-05-03 08:58:16.721 Source 1 configured with no grabber. Nothing to do.
2008-05-03 08:58:16.723 Data fetching complete.
2008-05-03 08:58:16.723 Adjusting program database end times.
2008-05-03 08:58:16.725     0 replacements made
2008-05-03 08:58:16.726 Marking generic episodes.
2008-05-03 08:58:16.726     Found 0
2008-05-03 08:58:16.726 Marking repeats.
2008-05-03 08:58:16.728     Found 0
2008-05-03 08:58:16.728 Unmarking new episode rebroadcast repeats.
2008-05-03 08:58:16.729     Found 0
2008-05-03 08:58:16.729 Marking episode first showings.
2008-05-03 08:58:16.729     Found 0
2008-05-03 08:58:16.730 Marking episode last showings.
2008-05-03 08:58:16.730     Found 0
2008-05-03 08:58:16.731 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-05-03 08:58:16.738 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-03 08:58:16.739 Using protocol version 40
2008-05-03 08:58:16.773 Received a remote 'Clear Cache' request
2008-05-03 08:58:16.828 mythfilldatabase run complete.
2008-05-03 08:58:16.851 DataDirect: Deleting temporary files


This was a procedure given on the [MythTV site]("http://www.mythtv.org/pipermail/mythtv-users/2007-September/192518.html").

Looking forward to any feedback.  Even a hint about this being a front end vs back end issue.  Or a pointer to anyone else that has tried this on 8.04

---

