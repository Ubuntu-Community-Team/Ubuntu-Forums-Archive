---
title: "Broken HDPVR"
date: 2010-04-08
forum: Mythbuntu
---

### Post by as08 on 2010-04-08
Hi!

I've been trying to get my HD-PVR mythtv setup working for over a month now. Im running Ubuntu Server 9.10 and myth .22-fixes. After the initial setup it seemed to work and i got a few successful recordings, but i am starting to believe I have some dead hardware.

The pvr will start to record after about a min the record lights shut off then will flash on and off over the period of a min, heres my backend log....

```
xloljkx@TheMyth:~$ mythbackend
2010-04-08 14:21:01.399 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-04-08 14:21:01.413 Using runtime prefix = /usr
2010-04-08 14:21:01.413 Using configuration directory = /home/xloljkx/.mythtv
2010-04-08 14:21:01.581 Empty LocalHostName.
2010-04-08 14:21:01.582 Using localhost value of TheMyth
2010-04-08 14:21:02.301 New DB connection, total: 1
2010-04-08 14:21:03.632 Connected to database 'mythconverg' at host: localhost
2010-04-08 14:21:03.633 Closing DB connection named 'DBManager0'
2010-04-08 14:21:03.794 Connected to database 'mythconverg' at host: localhost
2010-04-08 14:21:04.898 Current MythTV Schema Version (DBSchemaVer): 1244
2010-04-08 14:21:05.061 MythBackend: Starting up as the master server.
2010-04-08 14:21:05.628 New DB connection, total: 2
2010-04-08 14:21:05.649 Connected to database 'mythconverg' at host: localhost
2010-04-08 14:21:05.726 mythbackend: MythBackend started as master server
2010-04-08 14:21:06.416 New DB connection, total: 3
2010-04-08 14:21:06.442 Connected to database 'mythconverg' at host: localhost
2010-04-08 14:21:07.972 ret_pid(0) child(2366) status(0x0)
2010-04-08 14:21:08.511 ret_pid(2366) child(2366) status(0x0)
2010-04-08 14:21:08.512 External Tuning program exited with no error
2010-04-08 14:21:09.193 New DB scheduler connection
2010-04-08 14:21:09.232 Connected to database 'mythconverg' at host: localhost
2010-04-08 14:21:10.061 Enabling Upnpmedia rebuild thread.
2010-04-08 14:21:11.524 Main::Registering HttpStatus Extension
2010-04-08 14:21:11.525 Enabled verbose msgs:  important general
2010-04-08 14:21:11.609 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-04-08 14:21:12.556 Reschedule requested for id -1.
2010-04-08 14:21:19.454 mythbackend: Running housekeeping thread
2010-04-08 14:21:20.081 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-04-08 14:21:27.401 Scheduled 1346 items in 14.7 = 3.92 match + 10.78 place
2010-04-08 14:21:27.492 scheduler: Scheduled items: Scheduled 1346 items in 14.7 = 3.92 match + 10.78 place
2010-04-08 14:21:27.530 AUTO-Startup assumed
2010-04-08 14:21:27.697 TVRec(1): ASK_RECORDING 1 0 0 0
2010-04-08 14:21:29.039 TVRec(1): Changing from None to Watching RecordingOnly
2010-04-08 14:21:29.051 TVRec(1): HW Tuner: 1->1
2010-04-08 14:21:30.683 ret_pid(0) child(2394) status(0x0)
2010-04-08 14:21:31.687 ret_pid(0) child(2394) status(0x0)
2010-04-08 14:21:31.864 ret_pid(2394) child(2394) status(0x0)
2010-04-08 14:21:31.864 External Tuning program exited with no error
2010-04-08 14:21:34.013 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2010-04-08 14:21:34.020 Started recording: Everybody Loves Raymond "Misery Loves Company": channel 1139 on cardid 1, sourceid 1
2010-04-08 14:21:34.044 scheduler: Started recording: Everybody Loves Raymond "Misery Loves Company": channel 1139 on cardid 1, sourceid 1
2010-04-08 14:21:35.988 MainServer::ANN Monitor
2010-04-08 14:21:35.988 adding: ubook as a client (events: 0)
2010-04-08 14:21:36.005 MainServer::ANN Monitor
2010-04-08 14:21:36.005 adding: ubook as a client (events: 1)
2010-04-08 14:21:47.529 DevRdB(/dev/HDPVR) Error: Poll giving up
2010-04-08 14:21:47.533 MPEGRec(/dev/HDPVR) Error: Device error detected
2010-04-08 14:21:47.533 DevRdB(/dev/HDPVR): Stop(): Not running.
2010-04-08 14:22:06.208 DevRdB(/dev/HDPVR) Error: Poll giving up
2010-04-08 14:22:06.212 MPEGRec(/dev/HDPVR) Error: Device error detected
2010-04-08 14:22:06.212 DevRdB(/dev/HDPVR): Stop(): Not running.
2010-04-08 14:22:25.486 DevRdB(/dev/HDPVR) Error: Poll giving up
2010-04-08 14:22:25.494 MPEGRec(/dev/HDPVR) Error: Device error detected
2010-04-08 14:22:25.495 DevRdB(/dev/HDPVR): Stop(): Not running.
```When I issue 
```
cat /dev/HDPVR > test.ts
```it records but eventually turns off, sometimes it works for 10 min sometimes 10 sec... this is why I believe its hardware. 

I would like some of your opinions as to whether I should contact hauppague or persue some software troubleshooting unknown to me.

I forgot to add that I have a Dish STB outputting 720p and RCA audio, I have updated the firmware to 0x12, and I have udev rules giving mythtv rw perms.

Thanks!

---

### Post by as08 on 2010-04-08
Figured it out, apperently my system doesnt have usb 2.0....crap

[http://www.mythtv.org/pipermail/mythtv-users/2010-March/283154.html](http://www.mythtv.org/pipermail/mythtv-users/2010-March/283154.html)

---

