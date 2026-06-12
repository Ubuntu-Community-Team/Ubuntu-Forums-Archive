---
title: "mythdatabasefill is running but nothing in the EPG?"
date: 2008-05-20
forum: Mythbuntu
---

### Post by callagga on 2008-05-20
Hi,

Need some help debugging why when I run the following, whilst there are no error message, in the EPG after I don't see any guide info.

```
mythfilldatabase --file 1 output.xmltv
```

So what I run was here. You can see the tail end of "shepherd" which collects the Australian TV guide data.


```
2008-05-19 22:31:22.054 Unmarking new episode rebroadcast repeats.
2008-05-19 22:31:22.088     Found 0
2008-05-19 22:31:22.192 Marking episode first showings.
2008-05-19 22:31:23.337     Found 1228
2008-05-19 22:31:23.337 Marking episode last showings.
2008-05-19 22:31:24.468     Found 1228
2008-05-19 22:31:24.470
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-05-19 22:31:24.475 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-19 22:31:24.476 Using protocol version 40
2008-05-19 22:31:24.525 mythfilldatabase run complete.
2008-05-19 22:31:24.525 DataDirect: Deleting temporary files
[email]greg@mythtv:~/.shep[/email]herd$
```

Note there was/is a large xmltv.output file there. It seems to have current EPG data in it so looks ok.

Questions:

[1] How do I tell whether the "1" in my mydatabasefill line is correct? How can I verify this.

[2] Is there any log file available to look to to try to get a handle on what is going wrong?

[3] Which tables in the DB store the EPG data. Should I look here to check whether any got in? (although if it isn't showing up in the mythfrontend when looking at the guide that's a pretty solid indication I assume that something went wrong)

[4] Any other debugging tips?

[5] Oh, I did run mythdatabasefill with wrong options at one point and it asked me to choose which channels etc. I exited out of this without finishing. If I wanted to redefine what channels I want to see in my EPG what is the correct process to do this?

Thanks

PS. If this helps here is the log extract for the backend log at the time I ran shepherd and then mythbackend. Doesn't seem to point to the issue???

```

2008-05-19 21:07:18.924 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 21:22:18.953 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 21:31:56.488 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-19 21:31:56.496 Empty LocalHostName.
2008-05-19 21:31:56.498 Using localhost value of mythtv
2008-05-19 21:31:56.515 New DB connection, total: 1
2008-05-19 21:31:56.523 Connected to database 'mythconverg' at host: localhost
2008-05-19 21:31:56.525 Closing DB connection named 'DBManager0'
2008-05-19 21:31:56.527 Connected to database 'mythconverg' at host: localhost
2008-05-19 21:31:56.530 New DB connection, total: 2
2008-05-19 21:31:56.531 Connected to database 'mythconverg' at host: localhost
2008-05-19 21:31:56.535 Current Schema Version: 1214
Starting up as the master server.
2008-05-19 21:31:56.561 New DB connection, total: 3
2008-05-19 21:31:56.562 Connected to database 'mythconverg' at host: localhost
2008-05-19 21:31:56.577 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-05-19 21:31:56.901 New DB scheduler connection
2008-05-19 21:31:56.902 Connected to database 'mythconverg' at host: localhost
 is defined, but isn't attached to a cardinput.
2008-05-19 21:31:56.952 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-19 21:31:56.953 Main::Registering HtpStatus Extension
2008-05-19 21:31:56.954 mythbackend version: 0.21.20080304-1 URL:[www.mythtv.org](www.mythtv.org)
2008-05-19 21:31:56.955 Enabled verbose msgs:  important general
2008-05-19 21:31:56.957 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 21:31:59.908 Reschedule requested for id -1.
2008-05-19 21:31:59.977 Scheduled 0 items in 0.1 = 0.03 match + 0.03 place
2008-05-19 21:31:59.986 Seem to be woken up by USER
2008-05-19 21:33:16.911 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 21:48:16.954 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 21:57:52.370 MainServer::HandleAnnounce Monitor
2008-05-19 21:57:52.391 adding: mythtv as a client (events: 0)
2008-05-19 21:57:52.394 MainServer::HandleAnnounce Monitor
2008-05-19 21:57:52.395 adding: mythtv as a client (events: 1)
2008-05-19 21:57:52.403 Reschedule requested for id -1.
2008-05-19 21:57:52.453 Scheduled 0 items in 0.0 = 0.01 match + 0.04 place
2008-05-19 22:03:16.987 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 22:18:17.024 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 22:31:24.476 MainServer::HandleAnnounce Monitor
2008-05-19 22:31:24.517 adding: mythtv as a client (events: 0)
2008-05-19 22:18:17.024 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 22:31:24.476 MainServer::HandleAnnounce Monitor
2008-05-19 22:31:24.517 adding: mythtv as a client (events: 0)
2008-05-19 22:31:24.520 MainServer::HandleAnnounce Monitor
2008-05-19 22:31:24.521 adding: mythtv as a client (events: 1)
2008-05-19 22:31:24.524 Reschedule requested for id -1.
2008-05-19 22:31:24.590 Scheduled 0 items in 0.1 = 0.04 match + 0.03 place
2008-05-19 22:33:17.126 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 22:48:17.164 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 23:03:17.193 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 23:18:17.220 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 23:33:17.249 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 23:48:17.276 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 00:03:17.306 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 00:18:17.337 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 00:33:17.370 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 00:48:17.400 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 01:03:17.433 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 01:18:17.464 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 01:33:17.494 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 01:48:17.521 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 02:03:17.553 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 02:18:17.580 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 02:33:17.613 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 02:48:17.641 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 03:03:17.673 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 03:18:17.700 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 03:33:17.730 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 03:48:17.757 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 04:03:17.786 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 04:18:17.813 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 04:33:17.842 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 04:48:17.869 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 05:03:17.905 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 05:18:17.932 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 05:33:17.961 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 05:48:17.988 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 06:03:18.018 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-20 06:18:18.045 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

---

### Post by GoDamN on 2008-05-20
the --file option in mythfilldatabase takes two arguments, first being the Video Source the guide data is for and the second is the xmltv file containing the guide data.

change the "1" to whatever your Video Source is in mythtv-setup.

You are currently directing the guide data to source "1" which most likely does not exist.

---

### Post by callagga on 2008-05-20
oh..looking at the videosource table I see there are 2 entries, the first one looking a bit weird.  

I've gone through the backend installation process again for channels and it seems to have fixed it. Just going through grabbing phase now.

Question - If I go through the setup process again for channels etc, do I need to manually delete data out of the database (e.g. channel table / program table) or does the setup process clear whatever data it needs to?

---

