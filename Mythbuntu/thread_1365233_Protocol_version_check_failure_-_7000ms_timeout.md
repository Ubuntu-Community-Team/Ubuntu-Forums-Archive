---
title: "Protocol version check failure - 7000ms timeout"
date: 2009-12-27
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-12-27
I am seeing this error all over the place, the log except below is from the front-end trying to display the recorded programs page - just as an example.  Very occasionally this doesn't happen and I can see the recorded shows, but most often it fails and just shows blanks.

```
2009-12-27 15:13:39.944 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-12-27 15:13:40.542 Loading window theme from /usr/share/mythtv/themes/Terra/recordings-ui.xml
2009-12-27 15:13:40.723 MythContext: Connecting to backend server: 192.168.1.103:6543 (try 1 of 1)
2009-12-27 15:13:47.726 MythSocket(a80e2b0:22): readStringList: Error, timed out after 7000 ms.
2009-12-27 15:13:47.726 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2009-12-27 15:13:47.727 SortedList is Empty
```

I get the same error when I run mythfilldatabase

```
2009-12-27 15:17:56.237 MythContext: Connecting to backend server: 192.168.1.103:6543 (try 1 of 1)
2009-12-27 15:18:03.240 MythSocket(89afb28:13): readStringList: Error, timed out after 7000 ms.
2009-12-27 15:18:03.240 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.
2009-12-27 15:18:03.241 Error rescheduling id -1 in ScheduledRecording::signalChange
2009-12-27 15:18:03.241 MythContext: Connecting to backend server: 192.168.1.103:6543 (try 1 of 1)
2009-12-27 15:18:10.245 MythSocket(8996ec0:13): readStringList: Error, timed out after 7000 ms.
2009-12-27 15:18:10.245 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.

```

I even see it just after starting mythfrontend

```

2009-12-27 15:20:31.122 Loading window theme from /usr/share/mythtv/themes/Terra/menu-ui.xml
2009-12-27 15:20:31.212 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-12-27 15:20:31.214 Found mainmenu.xml for theme 'Terra'
2009-12-27 15:20:31.227 MythContext: Connecting to backend server: 192.168.1.103:6543 (try 1 of 1)
2009-12-27 15:20:38.232 MythSocket(87735c8:22): readStringList: Error, timed out after 7000 ms.
2009-12-27 15:20:38.232 Protocol version check failure. The response to MYTH_PROTO_VERSION was empty.

```

---

### Post by ubnewbie2 on 2009-12-27
Found that the default settings for the backend ip address were the problem.  There's two of them, the local backend ip, and the master backend ip.  The master was set to a real ip address, but the local was set to 127.0.0.1 - which should work, but DOESN'T.  Setting it to the actual ip fixed the problem.

btw: another symptom of this was really slow mythweb performance with occasional errors.  That too, is fixed now.

---

### Post by mbobak on 2010-10-04
Ok....same problem here.

*Where* are each of the local backend ip and master backend ip set???

Help!

AdvThanksance,

-Mark

---

### Post by ktbos on 2010-10-28
Mark, the settings are in mythtv-setup on the first page of the General settings.

---

