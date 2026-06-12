---
title: "Scanning channels on Backen is ok, but no TV on frontend."
date: 2009-03-08
forum: Mythbuntu
---

### Post by sperwer on 2009-03-08
I'm a totally newbie in Linux and MythTV it is a big challenge for me to get it to work.

I have installed the MythBuntu package and was finally able to scan som channels on the back-end. i have set it up to start on a FTA channel.

When i start front-end theres is no response when trying to look live TV.
I have been browsing / searching in  this and severel other forums just to getting more confused.

Any suggestion to where start troubleshooting is appreciated.

Sperwer

Update:
just noticed the errorslogs.log

2009-03-08 17:17:55.476 DVBChan(1:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)
2009-03-08 17:17:55.547 DVBChan(2:0) Error: Opening DVB frontend device failed.
			eno: No such file or directory (2)

I have created a live TV directory for the home of MythTV user, maybe the directory should be placed somewhere else.

Hardware
Dell Latitude D610 (laptop)
Skystar 2 USB

---

### Post by nickrout on 2009-03-08
your frontend makes logs at /ver/log/mythtv/mythfrontend.log

Take a look and see what is in that log straight after you try and watch tv.

Also, can you record a programme? And play it back? ie is your problem limited to live tv or all of myth's tv related functions?

---

