---
title: "myth TV backend - Failed to bind port 6543."
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by swimmer618 on 2007-05-07
I'm running Ubuntu Edgy with MythTV and a Hauppauge PVR-150MCE. I've tested the mysql connection, and everything appears to be ok (I can connect with: mysql -u root). 

I've tried running mythbackend as my user, root, and as mythtv. Thanks for any help.

2007-05-07 21:31:58.544 Using runtime prefix = /usr
2007-05-07 21:31:58.572 DBPassword is not set in mysql.txt
2007-05-07 21:31:58.619 New DB connection, total: 1
2007-05-07 21:31:58.631 Connected to database 'mythconverg' at host: localhost
2007-05-07 21:31:58.634 Current Schema Version: 1160
Starting up as the master server.
2007-05-07 21:31:58.670 New DB connection, total: 2
2007-05-07 21:31:58.670 Connected to database 'mythconverg' at host: localhost
2007-05-07 21:31:58.672 EITHelper: localtime offset -4:00:00 
2007-05-07 21:31:58.675 New DB connection, total: 3
2007-05-07 21:31:58.676 Connected to database 'mythconverg' at host: localhost
2007-05-07 21:31:58.728 New DB scheduler connection
2007-05-07 21:31:58.729 Connected to database 'mythconverg' at host: localhost
2007-05-07 21:31:58.730 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2007-05-07 21:31:58.733 Main::HttpServer Create Error
2007-05-07 21:31:58.733 Main::Registering HttpStatus Extension
2007-05-07 21:31:58.764 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-05-07 21:31:58.764 Enabled verbose msgs:  important general
2007-05-07 21:31:58.779 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-05-07 21:31:58.781 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2007-05-07 21:31:58.782 Failed to bind port 6543. Exiting.

---

