---
title: "why does my hdhomerun break mythtv?!"
date: 2010-05-15
forum: Mythbuntu
---

### Post by Afkpuz on 2010-05-15
This is a bug that I've had since 9.10.  No one ever has an answer, so I hope this time will be different.

Mythtv works fine when using analog tuners.  However, when I add an hdhomerun, I get the following error when starting mythbackend

```

2010-05-15 15:36:28.145 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-05-15 15:36:28.145 Using runtime prefix = /usr
2010-05-15 15:36:28.146 Using configuration directory = /home/alex/.mythtv
2010-05-15 15:36:28.146 Empty LocalHostName.
2010-05-15 15:36:28.146 Using localhost value of mythtv-box
2010-05-15 15:36:28.154 New DB connection, total: 1
2010-05-15 15:36:28.160 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.160 Closing DB connection named 'DBManager0'
2010-05-15 15:36:28.161 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.165 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-15 15:36:28.166 MythBackend: Starting up as the master server.
2010-05-15 15:36:28.169 New DB connection, total: 2
2010-05-15 15:36:28.170 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.176 New DB connection, total: 3
2010-05-15 15:36:28.177 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.291 New DB scheduler connection
2010-05-15 15:36:28.292 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.299 MediaServer::HttpServer Create Error
2010-05-15 15:36:28.299 Enabled verbose msgs:  important general
2010-05-15 15:36:28.301 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-05-15 15:36:28.302 Failed to bind port 6543. Exiting.
2010-05-15 15:36:28.302 Backend exiting, MainServer initialization error.


```

It is clearly caused by my digtal tuner, and THERE ARE NO OTHER BACKEND PROCESSES RUNNING.  I issue a 
```
sudo killall mythbackend
```
Then a 
```
mythbackend
```

And get the same results.  If I do that sequence quick enough, the backend starts.  However, it is stupid and freezes immediately after beginning live tv.  Please help, I don't want to have to roll back to 8.10 (which is the only reliable ubuntu+mythtv combo I've found on my system).  If I sound angry, it's cause I'm mad that this bug has persisted for more than a year!

---

### Post by superm1 on 2010-05-15
> **Afkpuz said:**
> This is a bug that I've had since 9.10.  No one ever has an answer, so I hope this time will be different.

Mythtv works fine when using analog tuners.  However, when I add an hdhomerun, I get the following error when starting mythbackend

```

2010-05-15 15:36:28.145 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-05-15 15:36:28.145 Using runtime prefix = /usr
2010-05-15 15:36:28.146 Using configuration directory = /home/alex/.mythtv
2010-05-15 15:36:28.146 Empty LocalHostName.
2010-05-15 15:36:28.146 Using localhost value of mythtv-box
2010-05-15 15:36:28.154 New DB connection, total: 1
2010-05-15 15:36:28.160 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.160 Closing DB connection named 'DBManager0'
2010-05-15 15:36:28.161 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.165 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-15 15:36:28.166 MythBackend: Starting up as the master server.
2010-05-15 15:36:28.169 New DB connection, total: 2
2010-05-15 15:36:28.170 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.176 New DB connection, total: 3
2010-05-15 15:36:28.177 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.291 New DB scheduler connection
2010-05-15 15:36:28.292 Connected to database 'mythconverg' at host: localhost
2010-05-15 15:36:28.299 MediaServer::HttpServer Create Error
2010-05-15 15:36:28.299 Enabled verbose msgs:  important general
2010-05-15 15:36:28.301 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-05-15 15:36:28.302 Failed to bind port 6543. Exiting.
2010-05-15 15:36:28.302 Backend exiting, MainServer initialization error.


```

It is clearly caused by my digtal tuner, and THERE ARE NO OTHER BACKEND PROCESSES RUNNING.  I issue a 
```
sudo killall mythbackend
```
Then a 
```
mythbackend
```

And get the same results.  If I do that sequence quick enough, the backend starts.  However, it is stupid and freezes immediately after beginning live tv.  Please help, I don't want to have to roll back to 8.10 (which is the only reliable ubuntu+mythtv combo I've found on my system).  If I sound angry, it's cause I'm mad that this bug has persisted for more than a year!

I suspect this happens because you are fighting with upstart.  You shouldn't be manually killing and starting the backend, but rather using the 'start' and 'stop' commands to start it's upstart script.

Eg:

sudo stop mythtv-backend

sudo start mythtv-backend

---

### Post by brian_hammerhead on 2010-05-16
I don't know why you are having the problem.  I use the HD Homerun with no problems at all.  Here are my configuration steps if it helps.

I am using over the air ATSC on both tuners with a feed from an antenna on my roof.

Sorry about the format.  I have a outline view in MS Word where I document my install steps and it doesn't paste well.  I think you will get the idea of the outline (a, i, 1).

From MythTV Backend Setup:

       a)       3 – Video Sources
  i)        (New Video Source)
  (1)     Video Source Name = Schedules Direct
  (2)    Listing Grabber: North America (Schedules Direct.org)
  (3)    User: {put username here}
  (4)    Pass: {put password here}
  (5)    [Retrieve Lineups]
  (6)    Channel Frequency Table: us-bcast
  (7)    Finish
  ii)      (New Video Source)
  (1)     Video source name = VCR
  (2)    Listings Grabber: No grabber
  (3)    Channel frequency table: default
  (4)    FINISH
  iii)    ESC
  b)      4 – Input Connections
  i)        [HDHomeRun: ID 10141872 port 0]
  (1)     Display Name: HDHomerun-0
  (2)    Video Source: Schedules Direct
  (3)    [Scan for Channels]
  (a)    Scan Configuration
  (i)     Desired Services: TV+Radio
  (ii)   Only Free: Checked
  (iii) Test Decryptability: Unchecked
  (iv)  Scan Type: Full Scan
  (v)    Frequency Table: Broadcast
  (vi)  Modulation: Terrestrial (8-VSB)
  (vii)Scanning Range: ATSC 2 – ATSC 83  (Ch 9 – Ch 50 works also)
  (b)    [Scanning….]
  (i)     "Found 35 new non-confliciting ATSC channel(s)."
  (ii)   Insert All
  (iii) "Found 2 new non-conflicting MPEG channel(s)."
  (iv)  Insert All
  (v)    FINISH
  (vi)  Check starting channel is populated
  (vii)NEXT
  (c)    Interaction between inputs
  (i)     FINISH
  ii)      [HDHomeRun: ID 10141872 port 1]
  (1)     Display Name: HDHomerun-1
  (2)    Video Source: Schedules Direct
  (3)    [Scan for Channels]
  (a)    Scan Configuration
  (i)     Desired Services: TV+Radio
  (ii)   Only Free: Checked
  (iii) Test Decryptability: Unchecked
  (iv)  Scan Type: Full Scan
  (v)    Frequency Table: Broadcast
  (vi)  Modulation: Terrestrial (8-VSB)
  (vii)Scanning Range: ATSC 2 – ATSC 83  (Ch 9 – Ch 50 works also)
  (b)    [Scanning….]
  (i)     "Found 3 Off Air channels"
  (ii)   Delete All
  (iii) "Found 33 old ATSC channels"
  (iv)  Update All
  (v)    "Found 2 new non-conflicting MPEG channels"
  (vi)  Insert All
  (vii)"Found 1 new conflicting MPEG channel(s)
  (viii)                      TRIED INSERT ALL > Cancel, DON'T DO THIS NEXT TIME.
  (ix)  "Found 1 unused transport(s)."
  (x)    Delete all
  (xi)  FINISH
  (xii)Check starting channel is populated
  (xiii)                      NEXT
  (c)    Interaction between inputs
  (i)     FINISH

---

### Post by Afkpuz on 2010-05-21
Superm1, I tried your commands with no results.  It looked like the backend was stopped, then started, but the frontend proved that nothing was working correctly.  Couldn't watch tv or see recordings.  Now, the backend is not starting regardless of tuners chosen.  

This problem is present on a fresh install and has persisted since ubuntu 9.10.  Any advice would be appreciated.

---

### Post by matt06 on 2010-05-21
```
2010-05-15 15:36:28.299 MediaServer::HttpServer Create Error
2010-05-15 15:36:28.302 Failed to bind port 6543. Exiting.
```

These look like networking errors to me?

---

### Post by superm1 on 2010-05-21
> **Afkpuz said:**
> Superm1, I tried your commands with no results.  It looked like the backend was stopped, then started, but the frontend proved that nothing was working correctly.  Couldn't watch tv or see recordings.  Now, the backend is not starting regardless of tuners chosen.  

This problem is present on a fresh install and has persisted since ubuntu 9.10.  Any advice would be appreciated.

So when you try to start the backend (using sudo start mythtv-backend) take a look at /var/log/mythtv/mythbackend.log

Hopefully it should help to explain why the backend is refusing to start.

---

### Post by Afkpuz on 2010-05-27
This is such a weird problem.  I checked the log when I was only using my analog tuner card.  Found out that my video folder didn't have permissions correct.  Fixed that and things worked great.  Then, I added my hdhomerun back into the mix.  This time, backend started and I could watch analog, but when I press "y" to change tuners, all control froze up.  couldn't play/pause, rewind, or esc from analog tv.  It never switched over to digital either.  I had to restart the computer.  Here is the log info from that session.

```
2010-05-27 00:00:00.559 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:00.575 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:00.584 Finished recording MythBusters "Demolition Derby Special": channel 1036
2010-05-27 00:00:00.652 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2010-05-27 00:00:00.660 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:00.668 ProgramInfo(): Updated pathname '':'' -> '1036_20100527000000.mpg'
2010-05-27 00:00:00.716 TVRec(1): RingBufferChanged()
2010-05-27 00:00:00.725 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:00.736 Finished recording MythBusters "Demolition Derby Special": channel 1036
2010-05-27 00:00:00.766 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:00.783 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-05-27 00:00:00.790 Using runtime prefix = /usr
2010-05-27 00:00:00.798 Using configuration directory = /home/mythtv/.mythtv
2010-05-27 00:00:00.807 Empty LocalHostName.
2010-05-27 00:00:00.818 Using localhost value of mythtv-box
2010-05-27 00:00:00.835 New DB connection, total: 1
2010-05-27 00:00:00.843 Connected to database 'mythconverg' at host: localhost
2010-05-27 00:00:00.848 Closing DB connection named 'DBManager0'
2010-05-27 00:00:00.857 Connected to database 'mythconverg' at host: localhost
2010-05-27 00:00:00.869 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-27 00:00:00.875 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:01.126 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:00:01.133 ProgramInfo(): Updated pathname '':'' -> '1036_20100527000000.mpg'
2010-05-27 00:00:01.258 [mp2 @ 0x3b2960]Header missing
2010-05-27 00:00:01.269 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.273 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.283 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.290 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.298 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.306 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.316 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.323 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.397 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.415 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.423 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.433 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.440 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.450 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:01.457 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.244 AFD: Opened codec 0x9a75a00, id(MPEG2VIDEO) type(Video)
2010-05-27 00:00:06.255 AFD: codec MP2 has 2 channels
2010-05-27 00:00:06.263 AFD: Opened codec 0x9a75da0, id(MP2) type(Audio)
2010-05-27 00:00:06.305 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.313 AFD Error: Unknown decoding error
2010-05-27 00:00:06.321 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.330 AFD Error: Unknown decoding error
2010-05-27 00:00:06.338 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.346 AFD Error: Unknown decoding error
2010-05-27 00:00:06.355 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.363 AFD Error: Unknown decoding error
2010-05-27 00:00:06.372 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.380 AFD Error: Unknown decoding error
2010-05-27 00:00:06.388 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.396 AFD Error: Unknown decoding error
2010-05-27 00:00:06.488 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.496 AFD Error: Unknown decoding error
2010-05-27 00:00:06.505 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.513 AFD Error: Unknown decoding error
2010-05-27 00:00:06.521 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.530 AFD Error: Unknown decoding error
2010-05-27 00:00:06.539 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.546 AFD Error: Unknown decoding error
2010-05-27 00:00:06.555 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.563 AFD Error: Unknown decoding error
2010-05-27 00:00:06.571 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.580 AFD Error: Unknown decoding error
2010-05-27 00:00:06.588 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.596 AFD Error: Unknown decoding error
2010-05-27 00:00:06.605 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.613 AFD Error: Unknown decoding error
2010-05-27 00:00:06.621 [mpeg2video @ 0x3b2960]mpeg_decode_postinit() failure
2010-05-27 00:00:06.630 AFD Error: Unknown decoding error
2010-05-27 00:00:06.641 [mpeg2video @ 0x3b2960]warning: first frame is no keyframe
2010-05-27 00:00:06.654 [mpeg2video @ 0x3b2960]warning: first frame is no keyframe
2010-05-27 00:00:06.667 [mpeg2video @ 0x3b2960]warning: first frame is no keyframe
2010-05-27 00:00:06.716 Preview: Grabbed preview '/home/alex/bertha/tv/1036_20100526235848.mpg' 480x480@64s
2010-05-27 00:00:06.825 ~MythContext waiting for threads to exit.
2010-05-27 00:02:04.407 Expiring 44 MBytes for 1036 @ Wed May 26 23:00:00 2010 => MythBusters "Demolition Derby Special"
2010-05-27 00:02:04.417 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:02:04.477 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
2010-05-27 00:02:07.427 ProgramInfo(): Updated pathname '':'' -> '1036_20100526235848.mpg'
```

So once again, digital tuners are screwing up my mythtv!

---

### Post by rulet on 2010-06-12
I have this log after I do:
```
r@NGF:~$ sudo start mythtv-backend
mythtv-backend start/running, process 2120

```
 And then last strings after I do **cat /var/log/mythtv/mythbackend.log**
 :
```
2010-06-12 23:50:51.917 New DB connection, total: 3
2010-06-12 23:50:51.928 Connected to database 'mythconverg' at host: localhost
2010-06-12 23:50:51.935 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-06-12 23:50:51.951 Main::Registering HttpStatus Extension
2010-06-12 23:50:51.963 Enabled verbose msgs:  important general
2010-06-12 23:50:51.977 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-12 23:50:51.990 SG(r) Error: Group 'r' wants to use directory '/home/r//', but this directory is not writeable.
r@NGF:~$ 

```
 
 What that should mean?

---

### Post by superm1 on 2010-06-12
> **rulet said:**
> I have this log after I do:
```
r@NGF:~$ sudo start mythtv-backend
mythtv-backend start/running, process 2120

```
 And then last strings after I do **cat /var/log/mythtv/mythbackend.log**
 :
```
2010-06-12 23:50:51.917 New DB connection, total: 3
2010-06-12 23:50:51.928 Connected to database 'mythconverg' at host: localhost
2010-06-12 23:50:51.935 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-06-12 23:50:51.951 Main::Registering HttpStatus Extension
2010-06-12 23:50:51.963 Enabled verbose msgs:  important general
2010-06-12 23:50:51.977 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-12 23:50:51.990 SG(r) Error: Group 'r' wants to use directory '/home/r//', but this directory is not writeable.
r@NGF:~$ 

```
 
 What that should mean?

This means you are trying to tell it to save recordings to the directory /home/r/, but the user 'mythtv' nor group 'mythtv' can write to that directory.  You need to adjust permissions, or adjust the location to somewhere really writable by user mythtv or group mythtv.

---

### Post by rulet on 2010-06-13
Finally, I can talk to developer.
And how to adjust permissions for mythtv to /home/r?

---

### Post by rulet on 2010-06-13
And when I made settings for tv-card and inputs in backend I've got this:
```
r@NGF:~$ mythbackend
2010-06-13 11:12:17.463 mythbackend version: branches/release-0-23-fixes [25073] www.mythtv.org
2010-06-13 11:12:17.463 Using runtime prefix = /usr
2010-06-13 11:12:17.463 Using configuration directory = /home/r/.mythtv
2010-06-13 11:12:17.464 Empty LocalHostName.
2010-06-13 11:12:17.464 Using localhost value of NGF
2010-06-13 11:12:17.473 New DB connection, total: 1
2010-06-13 11:12:17.478 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:17.478 Closing DB connection named 'DBManager0'
2010-06-13 11:12:17.479 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:17.483 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-13 11:12:17.485 MythBackend: Starting up as the master server.
2010-06-13 11:12:17.487 New DB connection, total: 2
2010-06-13 11:12:17.488 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:18.824 New DB connection, total: 3
2010-06-13 11:12:18.825 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:25.915 New DB scheduler connection
2010-06-13 11:12:25.915 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:25.923 MediaServer::HttpServer Create Error
2010-06-13 11:12:25.923 Enabled verbose msgs:  important general
2010-06-13 11:12:25.925 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-13 11:12:25.930 Failed to bind port 6543. Exiting.
2010-06-13 11:12:25.930 Backend exiting, MainServer initialization error.
r@NGF:~$ 

```

 How to fix that errors?

---

### Post by Afkpuz on 2010-06-15
Thank for highjacking my thread.  

does anyone have an answer for why I am unable to switch to my digital tuners.  I posted the log info earlier in this thread.

---

### Post by superm1 on 2010-06-15
> **rulet said:**
> And when I made settings for tv-card and inputs in backend I've got this:
```
r@NGF:~$ mythbackend
2010-06-13 11:12:17.463 mythbackend version: branches/release-0-23-fixes [25073] www.mythtv.org
2010-06-13 11:12:17.463 Using runtime prefix = /usr
2010-06-13 11:12:17.463 Using configuration directory = /home/r/.mythtv
2010-06-13 11:12:17.464 Empty LocalHostName.
2010-06-13 11:12:17.464 Using localhost value of NGF
2010-06-13 11:12:17.473 New DB connection, total: 1
2010-06-13 11:12:17.478 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:17.478 Closing DB connection named 'DBManager0'
2010-06-13 11:12:17.479 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:17.483 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-13 11:12:17.485 MythBackend: Starting up as the master server.
2010-06-13 11:12:17.487 New DB connection, total: 2
2010-06-13 11:12:17.488 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:18.824 New DB connection, total: 3
2010-06-13 11:12:18.825 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:25.915 New DB scheduler connection
2010-06-13 11:12:25.915 Connected to database 'mythconverg' at host: localhost
2010-06-13 11:12:25.923 MediaServer::HttpServer Create Error
2010-06-13 11:12:25.923 Enabled verbose msgs:  important general
2010-06-13 11:12:25.925 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-06-13 11:12:25.930 Failed to bind port 6543. Exiting.
2010-06-13 11:12:25.930 Backend exiting, MainServer initialization error.
r@NGF:~$ 

```

 How to fix that errors?
Don't start the backend like that.

You need to start and stop it using upstart.

```
sudo stop mythtv-backend
```

```
sudo start mythtv-backend

```

---

### Post by superm1 on 2010-06-15
> **rulet said:**
> Finally, I can talk to developer.
And how to adjust permissions for mythtv to /home/r?

You should use the chown tool.  It's a little bit out of the scope of this forum to explain how to use it, so i'd recommend you just google a little bit or look at it's man page (man chown)

---

### Post by superm1 on 2010-06-15
> **Afkpuz said:**
> Thank for highjacking my thread.  

does anyone have an answer for why I am unable to switch to my digital tuners.  I posted the log info earlier in this thread.

No guarantees, but I would recommend you start out by upgrading to the current -fixes build.  24158 was a little before 0.23 launched, you can get the latest -fixes build from [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

---

### Post by Afkpuz on 2010-06-15
Thanks for all the help superm1.  I'll check into it

---

