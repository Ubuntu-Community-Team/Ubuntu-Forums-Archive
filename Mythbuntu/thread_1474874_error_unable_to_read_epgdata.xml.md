---
title: "error: unable to read epgdata.xml"
date: 2010-05-06
forum: Mythbuntu
---

### Post by orduek on 2010-05-06
Hi,
I just installed Mythbuntu 10.04
I use MegaEpg as my mythtv EPG.
I use this script in order to pull it and then mythfilldatabse to the mythtv database:
```
#!/bin/sh
wine /home/ormetal/Megaepg/MegaEPG/megaepg.exe

mythfilldatabase --file 1 /home/ormetal/Megaepg/MegaEPG/xml/epgdata.xml
```

for some reason I get this output when run it in terminal:
```
HTPC:~$ mythfilldatabase --file 1 /home/ormetal/Megaepg/MegaEPG/xml/epgdata.xml
2010-05-06 20:20:36.026 Bypassing grabbers, reading directly from file
2010-05-06 20:20:36.026 Using runtime prefix = /usr
2010-05-06 20:20:36.026 Using configuration directory = /home/ormetal/.mythtv
2010-05-06 20:20:36.027 Empty LocalHostName.
2010-05-06 20:20:36.027 Using localhost value of HTPC
2010-05-06 20:20:36.027 Testing network connectivity to '192.168.0.154'
2010-05-06 20:20:36.036 New DB connection, total: 1
2010-05-06 20:20:36.303 Connected to database 'mythconverg' at host: 192.168.0.154
2010-05-06 20:20:36.303 Closing DB connection named 'DBManager0'
2010-05-06 20:20:36.670 Connected to database 'mythconverg' at host: 192.168.0.154
2010-05-06 20:20:36.673 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-06 20:20:36.677 Error unable to open '/home/ormetal/Megaepg/MegaEPG/xml/epgdata.xml' for reading.
2010-05-06 20:20:36.677 DataDirect: Deleting temporary files
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.

```
In idea why I get unable to open for reading?

---

### Post by ian dobson on 2010-05-07
Hi,

can you do a ls -o /home/ormetal/Megaepg/MegaEPG/xml/epgdata.xml

and post the results here, and maybe attach the xml file to you post. Maybe the xmlfile isn't 100% xml conform.

Regards
Ian Dobson

---

### Post by orduek on 2010-05-07
OK,
This is embarrassing,
the real path was /home/ormetal/MegaEPG/MegaEPG/xml/
I used /home/ormetal/Megaepg/MegaEPG/xml

thank you for that command - it made me finally realize it.

---

