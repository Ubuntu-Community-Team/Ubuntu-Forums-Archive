---
title: "Backend problems."
date: 2007-12-14
forum: Mythbuntu
---

### Post by Scrier on 2007-12-14
Hi 

I'm currently setting up my mythTV frontend and backend and I have some issues here. First I tell the specs:
Backend:
[I]ASUS M2A-VM HDMI motherboard
2.5 something dual core amd athlon 64 processor
4 gig ram
2 120 gig sata disk mirrored for OS.
Extra network card
Onboard VGA
FireWire Card and 3 (not yet installed) external harddrives on 1 TB each.[/I]
FrontEnd:[I]
ASUS P5B motherboard.
Intel dual Core 2.4 Ghz
2 gig ram
1 x 500 gb wd disk
2 nova t-500 tv cards.
8800 gt passive cooled graphic card.[/I]

Now the issue I have is that I can't connect to the database from the frontend and checking into the backend there is no ip defined on the active DB connections and it complains about no TV cards.

> 2007-12-15 02:10:08.473 Using runtime prefix = /usr
2007-12-15 02:10:08.481 New DB connection, total: 1
2007-12-15 02:10:08.485 Connected to database 'mythconverg' at host: localhost
2007-12-15 02:10:08.485 Current Schema Version: 1160
Starting up as the master server.
2007-12-15 02:10:08.489 New DB connection, total: 2
2007-12-15 02:10:08.489 Connected to database 'mythconverg' at host: localhost
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-12-15 02:10:08.489 New DB connection, total: 3
QServerSocket: failed to bind or listen to the socket
2007-12-15 02:10:08.489 Connected to database 'mythconverg' at host: localhost
2007-12-15 02:10:08.489 MediaServer::HttpServer Create Error
2007-12-15 02:10:08.489 Main::Registering HttpStatus Extension
2007-12-15 02:10:08.489 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-15 02:10:08.493 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.
Segmentation fault (core dumped)

---

### Post by volkswagner on 2007-12-15
you have your tv tuners listed under the frontend.  If this is true this machine needs to be a slave backend and frontend machine, this can be set up in control center under sytem roles.  May be best to have tuners on your master backend.

---

### Post by Scrier on 2007-12-15
Yeah I figured that so far so im going with the primary frontend / backend on the machine I have the tuner cards on and put the opther as a backend / ubunthu desktop for storing purpose only.

---

### Post by Scrier on 2007-12-16
Hmm I moved one of my Nova T-500 cards to the backend, started the installation but I fail at selecting the VideoSource. I followed [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Desktop) guide with Primary Backend, No Frontend and Uvuntu Desktop as selctions, but when I come to videosource I can't find any but the North America, Transmitted Guide Only and no grabber thus I cannot continue with scanning from channels here. Any ideas? 
Also the nova T-500 seems to be problematic at the least so if you suggest another card that is better and makes little issues with the install here feel free to inform me. I am not that famiiar with linux yet so I would like this to go smooth for once, and im ready to invest in proper hardware to do so.

---

