---
title: "MythTV: Can access remote from Windows but not Ubuntu"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by palmnut on 2007-10-18
I've been banging my head on this one for days now.

I have set up a backend on an old laptop running Gutsy and am trying to access it from another laptop (either running Edgy or Gutsy) over my wireless net. Every time I try to run the frontend I get the following:

   2007-10-18 19:56:18.664 Using runtime prefix = /usr
   2007-10-18 19:56:18.672 Gnome-Screensaver support enabled
   2007-10-18 19:56:18.673 DPMS is disabled.
   2007-10-18 19:56:18.697 New DB connection, total: 1
   2007-10-18 19:56:38.707 Unable to connect to database!
   2007-10-18 19:56:38.707 Driver error was [1/2013]:
   QMYSQL3: Unable to connect
   Database error was:
   Lost connection to MySQL server during query

   QSqlQuery::exec: database not open

Indeed, if I try to test the MySQL link by typing something like:

   mysqladmin -h 192.168.2.55 -u mythtv -p version

I get the following:

   mysqladmin: connect to server at '192.168.2.55' failed
   error: 'Lost connection to MySQL server during query'

Where should I look next?

The real pi55er here is that I can access the backend perfectly using the wife's laptop running Windoze and Mythtv Player.

---

### Post by palmnut on 2007-10-21
Ok, I'll reply to my own post with tonight's findings.

It was my wireless PCMCIA LAN card.

With either or my two Atheros based cards I get the no connection symptoms. Very infrequent and always flaky MySQL link and no connection to the backend sockets.

When I switch to the Ralink based card that normally lives in my wife's laptop I get connection, but the data rate doesn't seem to be good enough - the video is very choppy.

When I connect direct to my router with a bit of wire, everything works smoothly.

Curiosly the ZD1211 based USB wireless dongle on the backend can apparently transmit the data fast enough, despite only ever reporting a maximum data rate of 24Mbps.

---

