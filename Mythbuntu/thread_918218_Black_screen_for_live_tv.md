---
title: "Black screen for live tv"
date: 2008-09-12
forum: Mythbuntu
---

### Post by polka on 2008-09-12
I am running Kubuntu 8.04 have installed the mythbuntu packages. I am using Hauppauge wintv pvr 150R Model 1062. Lspci recognized the card as does mythtv. When I run Mythbuntu Live CD Frontend -Mythtv Viewer and try to watch tv all I get is a black screen for about 30 sec and then return to the menu.

Here is what I get when I run mythbackend from a terminal:

2008-09-12 14:39:13.313 Using runtime prefix = /usr
2008-09-12 14:39:13.318 Empty LocalHostName.
2008-09-12 14:39:13.318 Using localhost value of ubuntu
2008-09-12 14:39:13.386 New DB connection, total: 1
2008-09-12 14:39:13.415 Connected to database 'mythconverg' at host: localhost
2008-09-12 14:39:13.417 Closing DB connection named 'DBManager0'
2008-09-12 14:39:13.420 Connected to database 'mythconverg' at host: localhost
2008-09-12 14:39:13.427 New DB connection, total: 2
2008-09-12 14:39:13.428 Connected to database 'mythconverg' at host: localhost
2008-09-12 14:39:13.439 Current Schema Version: 1214
Running as a slave backend.
2008-09-12 14:39:13.501 New DB connection, total: 3
2008-09-12 14:39:13.502 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2008-09-12 14:39:14.043 MediaServer::HttpServer Create Error
2008-09-12 14:39:14.043 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-09-12 14:39:14.043 Enabled verbose msgs:  important general
QServerSocket: failed to bind or listen to the socket
2008-09-12 14:39:14.072 Failed to bind port 6543. Exiting.

When I start the frontend I get the Mythbuntu Live Session Configuration. After I enter my password and test the connection it says successful. Does this not mean that the frontend can connect to the backend?

If I run : ivtv-tune --channel=2 -d/dev/video0; cat /dev/video0 | mplayer -
Mplayer opens channel 2 without sound, so I know the card works.

 I did chown the dir that holds the downloads mythtv:mythtv, and chmod 775.

I have tried three channel frequency table choices (us-cable, us-cable-hrc, and us-cable-irc) no luck with any.

Please any help on how to be able to watch tv.

Thanks

Jerry

---

