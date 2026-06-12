---
title: "cannot find backend help"
date: 2008-12-31
forum: Mythbuntu
---

### Post by strokeboy on 2008-12-31
Hi I lost my backend.  What I was trying to do was change from the default 127.0.0.1 IP address to a real static one which I got from ipconfig.  This was so that I could access the backend from other computers in the house.  Obviously this went terribly wrong.  I have tried to revert to the old way and have reinstalled (through synaptic) mythtv, mythtv-database, backend, frontend.  All to no avail.  I have tried to put the real ip address in the frontend, but it keeps going back to localhost. I can ping the static ip from other pc's.  Furthermore, I was thinking that the database is too full. The properties says that there is only 3 GB left out of 500.  That is why I am so desirous of retrieving the data base and not starting over.  We have some 500 shows recorded on there.  I will post my mythtv log (most recent).  If there are any suggestions, please help.  Thanks.

2008-12-30 18:08:44.782 Using runtime prefix = /usr
2008-12-30 18:08:44.871 Empty LocalHostName.
2008-12-30 18:08:44.912 Using localhost value of Hoesha
2008-12-30 18:08:44.967 New DB connection, total: 1
2008-12-30 18:08:45.010 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:08:45.046 Closing DB connection named 'DBManager0'
2008-12-30 18:08:45.087 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:08:45.129 New DB connection, total: 2
2008-12-30 18:08:45.179 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:08:45.222 Current Schema Version: 1214
Starting up as the master server.
2008-12-30 18:08:45.315 New DB connection, total: 3
2008-12-30 18:08:45.352 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:08:45.445 New DB scheduler connection
2008-12-30 18:08:45.485 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:08:46.798 Main::Registering HttpStatus Extension
2008-12-30 18:08:46.845 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-30 18:08:46.878 Enabled verbose msgs:  important general
2008-12-30 18:08:46.922 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-12-30 18:08:47.011 Failed to bind port 3. Exiting.
2008-12-30 18:12:09.388 Using runtime prefix = /usr
2008-12-30 18:12:09.441 Empty LocalHostName.
2008-12-30 18:12:09.515 Using localhost value of Hoesha
2008-12-30 18:12:09.578 New DB connection, total: 1
2008-12-30 18:12:09.637 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:12:09.740 Closing DB connection named 'DBManager0'
2008-12-30 18:12:09.782 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:12:09.907 New DB connection, total: 2
2008-12-30 18:12:10.023 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:12:10.124 Current Schema Version: 1214
Starting up as the master server.
2008-12-30 18:12:10.232 New DB connection, total: 3
2008-12-30 18:12:10.281 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:12:10.470 New DB scheduler connection
2008-12-30 18:12:10.513 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:12:11.784 Main::Registering HttpStatus Extension
2008-12-30 18:12:11.833 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-30 18:12:11.949 Enabled verbose msgs:  important general
2008-12-30 18:12:11.993 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-12-30 18:12:12.209 Failed to bind port 3. Exiting.
2008-12-30 18:24:37.243 Using runtime prefix = /usr
2008-12-30 18:24:37.293 Empty LocalHostName.
2008-12-30 18:24:37.334 Using localhost value of Hoesha
2008-12-30 18:24:37.389 New DB connection, total: 1
2008-12-30 18:24:37.440 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:24:37.484 Closing DB connection named 'DBManager0'
2008-12-30 18:24:37.534 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:24:37.585 New DB connection, total: 2
2008-12-30 18:24:37.626 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:24:37.669 Current Schema Version: 1214
Starting up as the master server.
2008-12-30 18:24:37.786 New DB connection, total: 3
2008-12-30 18:24:37.824 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:24:37.917 New DB scheduler connection
2008-12-30 18:24:37.957 Connected to database 'mythconverg' at host: localhost
2008-12-30 18:24:39.244 Main::Registering HttpStatus Extension
2008-12-30 18:24:39.284 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-12-30 18:24:39.326 Enabled verbose msgs:  important general
2008-12-30 18:24:39.369 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QServerSocket: failed to bind or listen to the socket
2008-12-30 18:24:39.450 Failed to bind port 3. Exiting.

---

