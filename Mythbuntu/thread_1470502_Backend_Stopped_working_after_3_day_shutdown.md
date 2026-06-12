---
title: "Backend Stopped working after 3 day shutdown"
date: 2010-05-02
forum: Mythbuntu
---

### Post by saxd40 on 2010-05-02
I had the DVR portion of Mythbuntu working fine for a month or so.  I shut down the PC on 4/29 so I could put it in my new AV cabinet.  Today (5/2) I started Mythbuntu back up and got this message on the screen:

[FONT=Arial][SIZE=2][COLOR=#000000]Could not connect to the master  backend server -- is it running? Is the IP address set for it in the setup  program correct?

So I checked the backend log and saw this error which is causing the backend to restart over and over:


[/COLOR][/SIZE][/FONT]
2010-05-02 17:38:34.616 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org]("http://www.mythtv.org")
2010-05-02 17:38:35.237 Using runtime prefix = /usr
2010-05-02 17:38:35.327 Using configuration directory = /home/mythtv/.mythtv
2010-05-02 17:38:35.525 Empty LocalHostName.
2010-05-02 17:38:35.630 Using localhost value of myth01
2010-05-02 17:38:35.989 New DB connection, total: 1
2010-05-02 17:38:36.199 Connected to database 'mythconverg' at host: localhost
2010-05-02 17:38:36.255 Closing DB connection named 'DBManager0'
2010-05-02 17:38:36.333 Connected to database 'mythconverg' at host: localhost
2010-05-02 17:38:37.709 Current MythTV Schema Version (DBSchemaVer): 1244
2010-05-02 17:38:38.468 MythBackend: Running as a slave backend.
2010-05-02 17:38:39.110 New DB connection, total: 2
2010-05-02 17:38:39.403 Connected to database 'mythconverg' at host: localhost
[COLOR=Red]2010-05-02 17:38:40.764 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2010-05-02 17:38:40.945 ChannelBase(1) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?[/COLOR]
2010-05-02 17:38:41.257 New DB connection, total: 3
2010-05-02 17:38:41.468 Connected to database 'mythconverg' at host: localhost

<at this point the backend restarts and loops through the same messages again>

I made ***NO CHANGES*** to the system.  I just shut it down for 3 days.  When I restarted it I was met with this disaster.

help?

---

### Post by saxd40 on 2010-05-04
finally googed the right message from the log file and found the solution:

[http://spyder.wordpress.com/2008/06/11/a-crash-course-in-mythtv-backend-setup/](http://spyder.wordpress.com/2008/06/11/a-crash-course-in-mythtv-backend-setup/)

I caused the problem exactly the same way this guy did. The confusing issue is that the problem doesn't appear until you reboot. I didn't reboot for a couple of weeks, so I didn't realize the change I had made caused a problem right away.
 
The key is setting BOTH of the IP addresses in the first screen of general setup to the same IP. If you set one to the REAL ip and the other to the loopback ip (127.0.0.1) this puts your backend in slave mode automatically even though you have it set as a master backend.

---

