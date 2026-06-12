---
title: "Error: GetCurrentChannelNum"
date: 2008-07-23
forum: Mythbuntu
---

### Post by bontux on 2008-07-23
Hi,

I running mythbuntu 8.04 on a hauppauge pvr150 card, but seem to be unable to change channels or record. My guide appears to be populated properly and I believe have set up the input connections, etc. properly. However I am getting an GetCurrentChannelNum error when I start up the backend.

Anyone know the cause/solution to this problem? Thanks.

mythbackend output:
```
2008-07-22 23:40:30.317 Using runtime prefix = /usr, libdir = /usr/lib
2008-07-22 23:40:30.318 Empty LocalHostName.
2008-07-22 23:40:30.318 Using localhost value of wormwood
2008-07-22 23:40:30.334 New DB connection, total: 1
2008-07-22 23:40:30.381 Connected to database 'mythconverg' at host: 192.168.1.102
2008-07-22 23:40:30.382 Closing DB connection named 'DBManager0'
2008-07-22 23:40:30.425 Connected to database 'mythconverg' at host: 192.168.1.102
2008-07-22 23:40:30.426 New DB connection, total: 2
2008-07-22 23:40:30.468 Connected to database 'mythconverg' at host: 192.168.1.102
2008-07-22 23:40:30.470 Current Schema Version: 1214
Starting up as the master server.
2008-07-22 23:40:30.494 New DB connection, total: 3
2008-07-22 23:40:30.528 Connected to database 'mythconverg' at host: 192.168.1.102
2008-07-22 23:40:30.654 Channel(/dev/video0) Error: GetCurrentChannelNum(226): Failed to find Channel
2008-07-22 23:40:30.654 Channel(/dev/video0)::TuneTo(226): Error, failed to find channel.
2008-07-22 23:40:30.762 New DB scheduler connection
2008-07-22 23:40:30.800 Connected to database 'mythconverg' at host: 192.168.1.102
2008-07-22 23:40:32.082 Main::Registering HttpStatus Extension
2008-07-22 23:40:32.082 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-07-22 23:40:32.082 Enabled verbose msgs:  important general
2008-07-22 23:40:32.083 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-07-22 23:40:33.802 Reschedule requested for id -1.
2008-07-22 23:40:33.826 Scheduled 1 items in 0.0 = 0.00 match + 0.02 place
2008-07-22 23:40:33.829 Seem to be woken up by USER
2008-07-22 23:40:40.864 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-07-22 23:40:40.865 UPnpMedia: BuildMediaMap Done. Found 0 objects

```

---

### Post by bontux on 2008-07-24
I figured out what I did wrong. In video sources I had 226 in the "Preset tuner to channel:" field. Leaving the field blank fixed my problem.

---

### Post by Pegel03 on 2009-04-04
Should be in 'input connections'.

---

