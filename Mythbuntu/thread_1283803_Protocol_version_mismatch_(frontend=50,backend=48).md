---
title: "Protocol version mismatch (frontend=50,backend=48)"
date: 2009-10-05
forum: Mythbuntu
---

### Post by tacman2k on 2009-10-05
Hi everyone,

I'm running Mythbuntu 9.10 Beta with the lastest updates.

The last update broke my mythbox.

My mythfrontend.log revealed the following:

2009-10-05 21:42:33.989 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2009-10-05 21:42:34.061 Protocol version mismatch (frontend=50,backend=48)


Is there anything I can do to get this back up and running?



--
Edit:

Running version checks lead to the following:

mythbackend --version
MythTV Version   : 22242
MythTV Branch    : trunk
Network Protocol : 50
Library API      : 0.22.20091004-1
QT Version       : 4.5.2


mythfrontend --version
MythTV Version   : 22242
MythTV Branch    : trunk
Network Protocol : 50
Library API      : 0.22.20091004-1
QT Version       : 4.5.2


Still have the problem though. Any solutions?

---

### Post by ian dobson on 2009-10-05
Hi,

Wait a day or so then do another update. It looks as if the update "updated" your frontend but not the backend so they're nolonger running the same version.

It's still beta and things can go wrong sometimes.

Regards
Ian Dobson

---

### Post by Mitch_nl on 2009-10-06
do a 'dpkg-reconfigure mythtv-database' to update the database scheme on the backend.

---

