---
title: "MythTV Backend not working"
date: 2012-02-08
forum: Multimedia Software
---

### Post by Ben1005 on 2012-02-08
Using 64-bit computer(still not sure whether that has to do with an installation or the actual computer), and Ubuntu 11.10. MythTV Backend absolutely refuses to boot, and does so with this message:

2012-02-08 19:44:30.726 mythbackend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org]("http://www.mythtv.org")
2012-02-08 19:44:30.726 Using runtime prefix = /usr
2012-02-08 19:44:30.726 Using configuration directory = /home/bryce/.mythtv
2012-02-08 19:44:30.727 Empty LocalHostName.
2012-02-08 19:44:30.727 Using localhost value of bryces-laptop
2012-02-08 19:44:30.746 New DB connection, total: 1
2012-02-08 19:44:30.749 Connected to database 'mythconverg' at host: localhost
2012-02-08 19:44:30.752 Closing DB connection named 'DBManager0'
2012-02-08 19:44:30.752 Connected to database 'mythconverg' at host: localhost
2012-02-08 19:44:30.754 Current locale EN_US
2012-02-08 19:44:30.754 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-02-08 19:44:30.759 Current MythTV Schema Version (DBSchemaVer): 1264
2012-02-08 19:44:30.764 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2012-02-08 19:44:30.772 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2012-02-08 19:44:30.777 MythBackend: Starting up as the master server.
2012-02-08 19:44:30.784 New DB connection, total: 2
2012-02-08 19:44:30.785 Connected to database 'mythconverg' at host: localhost
2012-02-08 19:44:30.789 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2012-02-08 19:44:30.790 Channel(/dev/video1)::Open(): Can't open video device, error "No such file or directory"
2012-02-08 19:44:30.790 MythBackend, Warning: No valid capture cards are defined in the database.
2012-02-08 19:44:30.791 New DB scheduler connection
2012-02-08 19:44:30.792 Connected to database 'mythconverg' at host: localhost
2012-02-08 19:44:30.793 Scheduler, Warning: Listings source 'HDPVR' is defined, but is not attached to a card input.
2012-02-08 19:44:30.793 Scheduler, Error: No channel sources defined in the database

Tried everything I can think of, with trying to define channels and redefining sources, but I'm just lout of ideas. Any help on this would be appreciated.

Probably very important to also mention that I'm using a Hauppaugue(I think that's how you spell it) HDPVR with an input from my Xbox 360 going through an audio mixer to gather commentary and I'm also using a different USB cable from what was provided because the original wasn't long enough.

---

### Post by vidtek on 2012-03-04
Ben-

Does your installation work with any other programme such as Kaffeine?

Mythtv is difficult to set up from scratch, try using Kaffeine to see if you can get a picture on that first.  You may need to revert to your original USB cable.

Get Kaffeine working with good sound and picture once you know all your hardware is working you can go on from there with Mythtv.

Tony

---

