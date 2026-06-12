---
title: "upgraded to 11, now video card is gone"
date: 2011-06-27
forum: Mythbuntu
---

### Post by Gr8RedShark on 2011-06-27
Just upgraded Mythbuntu to Natty, and the video capture card no longer works. When I try to watch TV, it just hangs. When I try to configure the video card through the Mythbuntu Backend setup, it hangs. I tried deleting the Video Source (in the Backend setup) and then creating a new one - when I try to create a new one, it hangs. This capture card worked fine out of the box with Mythbuntu 10.10. Any ideas how to get it working? It's a Leadtek Winfast PVR 2000.

---

### Post by tgm4883 on 2011-06-29
> **Gr8RedShark said:**
> Just upgraded Mythbuntu to Natty, and the video capture card no longer works. When I try to watch TV, it just hangs. When I try to configure the video card through the Mythbuntu Backend setup, it hangs. I tried deleting the Video Source (in the Backend setup) and then creating a new one - when I try to create a new one, it hangs. This capture card worked fine out of the box with Mythbuntu 10.10. Any ideas how to get it working? It's a Leadtek Winfast PVR 2000.

What is the full version of mythtv you are using? Are you keeping up to date with mythbuntu-repos?

---

### Post by Gr8RedShark on 2011-07-06
MythTV version is 0.24-243-g9ba3ece
MythTV Branch is fixes/0.24
Network protocol is 63
Library API version is 0.24.20101129-1
QT version is 4.7.2

---

### Post by tgm4883 on 2011-07-06
> **Gr8RedShark said:**
> MythTV version is 0.24-243-g9ba3ece
MythTV Branch is fixes/0.24
Network protocol is 63
Library API version is 0.24.20101129-1
QT version is 4.7.2

Use Mythbuntu repos to update your MythTV version. After that if it still doesn't work lets see some backend logs

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by Gr8RedShark on 2011-07-13
Just ran the update manager, found about 44 updates. Problem remains. Which MythTV logs are a good place to start?

---

### Post by tgm4883 on 2011-07-13
> **Gr8RedShark said:**
> Just ran the update manager, found about 44 updates. Problem remains. Which MythTV logs are a good place to start?

/var/log/mythtv/mythbackend.log

---

### Post by Gr8RedShark on 2011-07-13
The relevant message says "no valid capture cards are defined in database. Perhaps you should re-read the installation instructions?" 
There are many other messages about connecting to the database, loading a config file, nothing *else* that strikes me as unusual...

Strange, when I installed Mythbuntu 10.10, it found my capture card right away.

---

### Post by tgm4883 on 2011-07-13
> **Gr8RedShark said:**
> The relevant message says "no valid capture cards are defined in database. Perhaps you should re-read the installation instructions?" 
There are many other messages about connecting to the database, loading a config file, nothing *else* that strikes me as unusual...

Strange, when I installed Mythbuntu 10.10, it found my capture card right away.

Well that's not entirely true, since you have to add it in mythtv-setup. Are you able to add it in mythtv-setup after you upgraded the packages?

---

### Post by Gr8RedShark on 2011-07-13
No, that's the problem that persists. I run mythtv-setup, go to "Capture cards" try to add a new capture card (I deleted them all when this first came up, thinking that re-creating it would fix it), and then the screen goes empty (all that's visible is the desktop background image). That's it. The only error in the MythTV Setup console window has to do with not being able to connect to lircd (that's a problem I'm willing to deal with later).

The first time I installed Mythbuntu, attempting to add a capture card went very smoothly.

---

### Post by tgm4883 on 2011-07-14
> **Gr8RedShark said:**
> No, that's the problem that persists. I run mythtv-setup, go to "Capture cards" try to add a new capture card (I deleted them all when this first came up, thinking that re-creating it would fix it), and then the screen goes empty (all that's visible is the desktop background image). That's it. The only error in the MythTV Setup console window has to do with not being able to connect to lircd (that's a problem I'm willing to deal with later).

The first time I installed Mythbuntu, attempting to add a capture card went very smoothly.

Reproduce the issue then post the backend logs here.

---

### Post by Gr8RedShark on 2011-07-18
I had some time, here's the backend log dump of me trying to add a video source (and yes, I ran all updates right before I reproduced the problem):

```

[FONT=Courier New]2011-07-18 22:22:02.781 mythbackend version: fixes/0.24 [v0.24.1-46-g63b8603] [www.mythtv.org]("http://www.mythtv.org/")
2011-07-18 22:22:02.829 Using runtime prefix = /usr
2011-07-18 22:22:02.979 Using configuration directory = /home/mythtv/.mythtv
2011-07-18 22:22:03.098 Empty LocalHostName.
2011-07-18 22:22:03.155 Using localhost value of mythmachine
2011-07-18 22:22:03.227 New DB connection, total: 1
2011-07-18 22:22:03.275 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:03.389 Closing DB connection named 'DBManager0'
2011-07-18 22:22:03.479 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:03.522 Current locale EN_CA
2011-07-18 22:22:03.618 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-07-18 22:22:03.722 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-18 22:22:03.800 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-18 22:22:03.895 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-18 22:22:03.964 MythBackend: Starting up as the master server.
2011-07-18 22:22:04.032 New DB connection, total: 2
2011-07-18 22:22:04.093 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:04.169 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-18 22:22:04.205 New DB scheduler connection
2011-07-18 22:22:04.300 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:04.401 Scheduler, Error: No capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2011-07-18 22:22:04.490 New DB connection, total: 3
2011-07-18 22:22:04.491 Main::Registering HttpStatus Extension
2011-07-18 22:22:04.693 Enabled verbose msgs:  important general
2011-07-18 22:22:04.594 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:04.758 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-18 22:22:07.596 Reschedule requested for id -1.
2011-07-18 22:22:07.757 Scheduled 0 items in 0.2 = 0.08 match + 0.08 place
2011-07-18 22:22:07.821 Seem to be woken up by USER
2011-07-18 22:23:24.494 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-18 22:33:08.945 mythbackend version: fixes/0.24 [v0.24.1-46-g63b8603] [www.mythtv.org]("http://www.mythtv.org/")
2011-07-18 22:33:09.092 Using runtime prefix = /usr
2011-07-18 22:33:09.152 Using configuration directory = /home/mythtv/.mythtv
2011-07-18 22:33:09.290 Empty LocalHostName.
2011-07-18 22:33:09.335 Using localhost value of mythmachine
2011-07-18 22:33:09.447 New DB connection, total: 1
2011-07-18 22:33:09.550 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:09.592 Closing DB connection named 'DBManager0'
2011-07-18 22:33:09.637 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:09.982 Current locale EN_CA
2011-07-18 22:33:10.110 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-07-18 22:33:10.349 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-18 22:33:10.590 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-18 22:33:10.704 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-18 22:33:10.762 MythBackend: Starting up as the master server.
2011-07-18 22:33:10.877 New DB connection, total: 2
2011-07-18 22:33:10.917 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:10.969 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-18 22:33:11.009 New DB scheduler connection
2011-07-18 22:33:11.153 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:11.218 Scheduler, Error: No capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2011-07-18 22:33:11.324 Main::Registering HttpStatus Extension
2011-07-18 22:33:11.392 Enabled verbose msgs:  important general
2011-07-18 22:33:11.624 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-18 22:33:14.316 Reschedule requested for id -1.
2011-07-18 22:33:14.792 Scheduled 0 items in 0.5 = 0.17 match + 0.31 place
2011-07-18 22:33:14.913 Seem to be woken up by USER
2011-07-18 22:33:23.098 MainServer::ANN Monitor
2011-07-18 22:33:23.169 adding: mythmachine as a client (events: 0)
2011-07-18 22:33:23.237 MainServer::ANN Monitor
2011-07-18 22:33:23.320 adding: mythmachine as a client (events: 1)[/FONT]

```

---

### Post by tgm4883 on 2011-07-19
> **Gr8RedShark said:**
> I had some time, here's the backend log dump of me trying to add a video source (and yes, I ran all updates right before I reproduced the problem):

```

[FONT=Courier New]2011-07-18 22:22:02.781 mythbackend version: fixes/0.24 [v0.24.1-46-g63b8603] [www.mythtv.org]("http://www.mythtv.org/")
2011-07-18 22:22:02.829 Using runtime prefix = /usr
2011-07-18 22:22:02.979 Using configuration directory = /home/mythtv/.mythtv
2011-07-18 22:22:03.098 Empty LocalHostName.
2011-07-18 22:22:03.155 Using localhost value of mythmachine
2011-07-18 22:22:03.227 New DB connection, total: 1
2011-07-18 22:22:03.275 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:03.389 Closing DB connection named 'DBManager0'
2011-07-18 22:22:03.479 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:03.522 Current locale EN_CA
2011-07-18 22:22:03.618 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-07-18 22:22:03.722 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-18 22:22:03.800 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-18 22:22:03.895 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-18 22:22:03.964 MythBackend: Starting up as the master server.
2011-07-18 22:22:04.032 New DB connection, total: 2
2011-07-18 22:22:04.093 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:04.169 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-18 22:22:04.205 New DB scheduler connection
2011-07-18 22:22:04.300 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:04.401 Scheduler, Error: No capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2011-07-18 22:22:04.490 New DB connection, total: 3
2011-07-18 22:22:04.491 Main::Registering HttpStatus Extension
2011-07-18 22:22:04.693 Enabled verbose msgs:  important general
2011-07-18 22:22:04.594 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:22:04.758 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-18 22:22:07.596 Reschedule requested for id -1.
2011-07-18 22:22:07.757 Scheduled 0 items in 0.2 = 0.08 match + 0.08 place
2011-07-18 22:22:07.821 Seem to be woken up by USER
2011-07-18 22:23:24.494 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-18 22:33:08.945 mythbackend version: fixes/0.24 [v0.24.1-46-g63b8603] [www.mythtv.org]("http://www.mythtv.org/")
2011-07-18 22:33:09.092 Using runtime prefix = /usr
2011-07-18 22:33:09.152 Using configuration directory = /home/mythtv/.mythtv
2011-07-18 22:33:09.290 Empty LocalHostName.
2011-07-18 22:33:09.335 Using localhost value of mythmachine
2011-07-18 22:33:09.447 New DB connection, total: 1
2011-07-18 22:33:09.550 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:09.592 Closing DB connection named 'DBManager0'
2011-07-18 22:33:09.637 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:09.982 Current locale EN_CA
2011-07-18 22:33:10.110 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-07-18 22:33:10.349 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-18 22:33:10.590 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-18 22:33:10.704 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-18 22:33:10.762 MythBackend: Starting up as the master server.
2011-07-18 22:33:10.877 New DB connection, total: 2
2011-07-18 22:33:10.917 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:10.969 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-18 22:33:11.009 New DB scheduler connection
2011-07-18 22:33:11.153 Connected to database 'mythconverg' at host: localhost
2011-07-18 22:33:11.218 Scheduler, Error: No capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2011-07-18 22:33:11.324 Main::Registering HttpStatus Extension
2011-07-18 22:33:11.392 Enabled verbose msgs:  important general
2011-07-18 22:33:11.624 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-18 22:33:14.316 Reschedule requested for id -1.
2011-07-18 22:33:14.792 Scheduled 0 items in 0.5 = 0.17 match + 0.31 place
2011-07-18 22:33:14.913 Seem to be woken up by USER
2011-07-18 22:33:23.098 MainServer::ANN Monitor
2011-07-18 22:33:23.169 adding: mythmachine as a client (events: 0)
2011-07-18 22:33:23.237 MainServer::ANN Monitor
2011-07-18 22:33:23.320 adding: mythmachine as a client (events: 1)[/FONT]

```

Hmm, was the mythtv-backend service stopped when you were adding the cards?

---

### Post by Gr8RedShark on 2011-07-20
Y'know, I'm not sure if the mythbackend process was running when I tried running setup, so I tried running it manually (after running ps -A | grep myth and verifying that there was no existing process), here's the result:
```

mythman@mythmachine:~$ mythbackend 
2011-07-20 22:40:04.160 mythbackend version: fixes/0.24 [v0.24.1-46-g63b8603] www.mythtv.org
2011-07-20 22:40:04.161 Using runtime prefix = /usr
2011-07-20 22:40:04.161 Using configuration directory = /home/mythman/.mythtv
2011-07-20 22:40:04.162 Empty LocalHostName.
2011-07-20 22:40:04.162 Using localhost value of mythmachine
2011-07-20 22:40:04.179 New DB connection, total: 1
2011-07-20 22:40:04.201 Connected to database 'mythconverg' at host: localhost
2011-07-20 22:40:04.208 Closing DB connection named 'DBManager0'
2011-07-20 22:40:04.213 Connected to database 'mythconverg' at host: localhost
2011-07-20 22:40:04.216 Current locale EN_CA
2011-07-20 22:40:04.216 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-07-20 22:40:04.239 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-20 22:40:04.248 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-20 22:40:04.251 MediaServer::HttpServer Create Error
2011-07-20 22:40:04.254 MythBackend: Starting up as the master server.
2011-07-20 22:40:04.260 New DB connection, total: 2
2011-07-20 22:40:04.261 Connected to database 'mythconverg' at host: localhost
2011-07-20 22:40:04.265 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-20 22:40:04.266 New DB scheduler connection
2011-07-20 22:40:04.267 Connected to database 'mythconverg' at host: localhost
2011-07-20 22:40:04.268 Scheduler, Error: No capture cards are defined in the database.
            Perhaps you should re-read the installation instructions?
2011-07-20 22:40:04.274 New DB connection, total: 3
2011-07-20 22:40:04.275 Enabled verbose msgs:  important general
2011-07-20 22:40:04.276 Connected to database 'mythconverg' at host: localhost
2011-07-20 22:40:04.287 Failed to bind port 6543. Exiting.
2011-07-20 22:40:04.287 Backend exiting, MainServer initialization error.
Error in my_thread_global_end(): 1 threads didn't exit

```

---

