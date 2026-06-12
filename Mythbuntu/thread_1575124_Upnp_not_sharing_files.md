---
title: "Upnp not sharing files"
date: 2010-09-15
forum: Mythbuntu
---

### Post by cayqel on 2010-09-15
My Xbox can see my mythbuntu rig and connect to it but no files are shared.

After searching the forums I  came across
```
mythbackend --upnprebuild
```running it I got 
```
Table 'upnpmedia' is marked as crashed and should be repaired
```What do I need to do to repair upnpmedia?

edit: longer version of error I'm getting
```
2010-09-15 10:00:16.882 Connected to database 'mythconverg' at host: localhost
2010-09-15 10:00:16.888 DB Error (BuildMediaMap -- clearing table upnpmedia):
Query was:
DELETE FROM upnpmedia WHERE class = ?
Bindings were:
:ITEMCLASS=VIDEO
Driver error was [2/1194]:
QMYSQL3: Unable to execute statement
Database error was:
Table 'upnpmedia' is marked as crashed and should be repaired
```

---

### Post by joho500 on 2010-09-16
You can repair the tables in MCC (Mythbuntu Control Center) or in Mythweb.

Cheers,
Joost

---

