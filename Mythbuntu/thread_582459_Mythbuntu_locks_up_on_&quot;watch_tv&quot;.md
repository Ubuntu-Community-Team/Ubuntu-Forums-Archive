---
title: "Mythbuntu locks up on &quot;watch tv&quot;"
date: 2007-10-19
forum: Mythbuntu
---

### Post by dougsnell on 2007-10-19
This is my first foray into Myth, so bear with me on anything which might seem like a dumb question.

The Myth backend locks up whenever I select "Watch TV" ... either from the frontend on the primary backend or from another laptop running a frontend.  Actually, Myth doesn't lock up, the entire machine does.  Mouse stops responding, keyboard caps/num/scroll lock stop working ... I have to power off and back on (no Ctrl-Alt-Backspace or Del).

 I've been through a multitude of complete re-installs (Guided - use entire disk), and have changed machines; same result each time.  The one thing I can't fully test is whether the Hauppage 500 is faulty itself.  The symptoms would generally suggest a hardware problem, but I know I'm in over my head in the world of Linux trying to second-guess hardware troubleshooting (I'm a Windows tech by day).

I did dig up the log ... included below from startup to crash:

2007-10-20 11:20:59.825 Using runtime prefix = /usr
2007-10-20 11:21:00.170 New DB connection, total: 1
2007-10-20 11:21:00.208 Connected to database 'mythconverg' at host: localhost
2007-10-20 11:21:00.305 Current Schema Version: 1160
Starting up as the master server.
2007-10-20 11:21:00.487 New DB connection, total: 2
2007-10-20 11:21:00.491 Connected to database 'mythconverg' at host: localhost
2007-10-20 11:21:00.506 EITHelper: localtime offset -4:00:00 
2007-10-20 11:21:00.734 New DB connection, total: 3
2007-10-20 11:21:00.760 Connected to database 'mythconverg' at host: localhost
2007-10-20 11:21:01.087 EITHelper: localtime offset -4:00:00 
2007-10-20 11:21:01.314 New DB scheduler connection
2007-10-20 11:21:01.349 Connected to database 'mythconverg' at host: localhost
2007-10-20 11:21:01.485 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-20 11:21:01.831 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-20 11:21:03.162 Main::Registering HttpStatus Extension
2007-10-20 11:21:03.171 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-10-20 11:21:03.183 Enabled verbose msgs:  important general
2007-10-20 11:21:03.186 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2007-10-20 11:21:03.199 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2007-10-20 11:21:03.212 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2007-10-20 11:21:03.487 Reschedule requested for id -1.
2007-10-20 11:21:03.505 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2007-10-20 11:21:03.521 Seem to be woken up by USER
2007-10-20 11:23:30.622 MainServer::HandleAnnounce Monitor
2007-10-20 11:23:30.628 adding: mythtv as a client (events: 0)
2007-10-20 11:23:30.629 MainServer::HandleAnnounce Monitor
2007-10-20 11:23:30.630 adding: mythtv as a client (events: 1)
2007-10-20 11:23:30.633 MainServer::HandleAnnounce Playback
2007-10-20 11:23:30.649 adding: mythtv as a client (events: 0)
2007-10-20 11:23:30.658 TVRec(1): Changing from None to WatchingLiveTV
2007-10-20 11:23:30.660 TVRec(1): HW Tuner: 1->1

(The next entry starts with "Using runtime prefix = /usr", and repeats for the next few lines from there.)

Any help is greatly appreciated,

---

### Post by apauna on 2007-10-21
One other way to test tv out is with mplayer

open a terminal and type in below:

```
mplayer -tv driver=v4l:width=640:height=480:outfmt=i420 -vc rawi420 -vo xv tv://
```

I am not sure exactly the command line as it has been a while, but I have used mplayer in the past to test tv tuner cards for problems.

may have to remove the -vo xv as this only works well on nvidia cards, that is unless you have an nvidia card.

---

### Post by superm1 on 2007-10-21
Go into mythtv-setup and make sure you choose the right kind of tuner.  This is a very similar result from if you chose V4L tuner rather than MPEG2 encoder.

---

### Post by dougsnell on 2007-10-22
I'm sure I have the right tuner ... it was something I was very happy to find at ([https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)). Just for giggles I even tried vario

But I greatly appreciate both your responses.  I'll give the mplayer a try a bit later ... I'm in the middle of fiddling around with another machine and seeing if there are any issues with it (to test the hardware problem theory).

---

