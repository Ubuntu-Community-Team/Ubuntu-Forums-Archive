---
title: "mythtv worked in older ubuntus, not karmic"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Afkpuz on 2009-11-17
I've been running ubuntu 8.04 with mythtv for a while.  I thought I would try out the new ubuntu with myttv.  For some reason, the back end will not start anymore.  Even after I do a sudo killall mythbackend.  Here is the full error message.


```
2009-11-17 17:44:37.753 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-17 17:44:37.753 Using runtime prefix = /usr
2009-11-17 17:44:37.753 Using configuration directory = /home/alex/.mythtv
2009-11-17 17:44:37.754 Empty LocalHostName.
2009-11-17 17:44:37.754 Using localhost value of mythtv-center
2009-11-17 17:44:37.761 New DB connection, total: 1
2009-11-17 17:44:37.765 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:37.765 Closing DB connection named 'DBManager0'
2009-11-17 17:44:37.766 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:37.769 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-17 17:44:37.770 MythBackend: Starting up as the master server.
2009-11-17 17:44:37.775 New DB connection, total: 2
2009-11-17 17:44:37.775 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:37.779 New DB connection, total: 3
2009-11-17 17:44:37.780 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:37.863 New DB scheduler connection
2009-11-17 17:44:37.863 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:37.870 MediaServer::HttpServer Create Error
2009-11-17 17:44:37.871 Enabled verbose msgs:  important general
2009-11-17 17:44:37.872 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-17 17:44:37.873 Failed to bind port 6543. Exiting.
2009-11-17 17:44:37.873 Backend exiting, MainServer initialization error.
alex@mythtv-center:~$ sudo killall mythbackend
alex@mythtv-center:~$ mythbackend
2009-11-17 17:44:43.356 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-17 17:44:43.356 Using runtime prefix = /usr
2009-11-17 17:44:43.356 Using configuration directory = /home/alex/.mythtv
2009-11-17 17:44:43.357 Empty LocalHostName.
2009-11-17 17:44:43.357 Using localhost value of mythtv-center
2009-11-17 17:44:43.364 New DB connection, total: 1
2009-11-17 17:44:43.368 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:43.368 Closing DB connection named 'DBManager0'
2009-11-17 17:44:43.368 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:43.371 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-17 17:44:43.373 MythBackend: Starting up as the master server.
2009-11-17 17:44:43.377 New DB connection, total: 2
2009-11-17 17:44:43.379 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:43.382 New DB connection, total: 3
2009-11-17 17:44:43.383 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:43.463 New DB scheduler connection
2009-11-17 17:44:43.463 Connected to database 'mythconverg' at host: localhost
2009-11-17 17:44:43.470 MediaServer::HttpServer Create Error
2009-11-17 17:44:43.471 Enabled verbose msgs:  important general
2009-11-17 17:44:43.472 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-17 17:44:43.473 Failed to bind port 6543. Exiting.
2009-11-17 17:44:43.473 Backend exiting, MainServer initialization error.
```

I used synaptic to install the mythtv package and did everything the same way I always do.  Can anyone help me or should I just revert back to 8.04?

---

### Post by sdowney717 on 2009-11-17
what do you use myth to do?
could xbmc work instead?

---

### Post by HappyFeet on 2009-11-17
I also had trouble with mythtv in karmic, and went back to jaunty, where it works perfect. Sorry I can't be of more help.

---

### Post by Afkpuz on 2009-11-18
I use mythtv to record analog and digital tv.  The problem is that something changed in karmic that is keeping the backend from starting

---

### Post by lgiordano on 2009-11-18
looks like port 6543 is in use.

Can you post the output of ```
netstat | grep 6543
```

---

### Post by Afkpuz on 2009-11-18
nothing is output when I try your command.  However, I have discovered something even weirder.  If i do a killall command and then quickly start the backend, it will start!  I still get an error about the dvb card, but it starts and analog tv works, no digital.  The dvb message is
```
eno: Device or resource busy (16)
2009-11-18 22:43:58.612 DVBChan(5:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.

```

However, if I killall and wait 10 seconds, the backend will not start.  This is so strange

---

### Post by sdowney717 on 2009-11-19
for recording tv for me i run mencoder like so

> mencoder /dev/video0 -o $(date +%A-%m-%d-%Y+%T).avi -endpos 02:10:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame

(for some reason this web site is putting a 'space' after vqmin=2 that should not be there, should say vqmax=31)
mencoder /dev/video0 -o $(date +%A-%m-%d-%Y+%T).avi -endpos 02:10:00 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac mp3lame


this creates am mpeg4 mp3 audio file with the name of dayofweek, date, time.
the parameter -endpos tells mencoder how long to record
my dev/video0 is a pci capture card adaptec videooh
I have dish network and can record anything off the dish or atsc that feeds into the tv inputs using the capture card.
I can only change channels by using the dish remote.
I can schedule recordings by using alarm-clock which lets you run a terminal command

the mencoder command only works if mplayer is compiled with liblame support otherwise you could just say -oac pcm or -oac copy.
and alarm-clock i think has to be left running

$(date +%A-%m-%d-%Y+%T+%p) shows this as name Thursday-11-19-2009+09:17:00+AM:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?date](http://unixhelp.ed.ac.uk/CGI/man-cgi?date)

$(date +%A-%p-%m-%d-%Y+%T) Thursday-AM-11-19-2009+09:18:24

---

### Post by Afkpuz on 2009-11-19
Well, I would really like to use mythtv if I could.  Does anyone know what is going on here?  Especially, why isn't my pvr 1250 working?  I can live with quick restart of mythbackend

---

### Post by lgiordano on 2009-11-19
mythbackend uses port 6543, and this error message from your terminal output basically says mythbackend is exiting because the required port was in use...

```
2009-11-17 17:44:37.873 Failed to bind port 6543. Exiting.
```

I've seen other people with this error and it was usually due to incorrect settings in their backend. Try removing the HVR-1250 card and setting it up again, go through the backend settings and make sure everything is in order.

When I get home I'll compare my terminal output of "mythbackend" after a "sudo killall mythbackend" and see if that provides any clues.

---

### Post by Afkpuz on 2009-11-19
Ok, I'm abandoning this endeavor and rolling back.  I just don't think karmic+mythtv is stable on my system.  I went back and removed the dvb card and then redid it.  Even though I used the exact same settings, I was able to start the backend normally.  I proceeded to watch about 60 mins of tv and the backend mysteriously quit mid recording.  So, I don't want to mess with it.

---

### Post by lgiordano on 2009-11-19
Sorry to hear that. Before rolling back, why not run mythbackend one last time and post the output when it crashes? Might be something that takes less time to fix than rolling back.

---

