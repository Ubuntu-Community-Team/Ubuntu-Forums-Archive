---
title: "[SOLVED] Mythbuntu frontend has new MySQL problem"
date: 2008-08-05
forum: Multimedia Software
---

### Post by jk-menifee on 2008-08-05
Hello,

I've been successfully using mythtv for about eight months now, and I've been very pleased. Today is the first problem that stumped me and that there was not already help available for. So this is also my first post.

All of a sudden my frontend won't connect to my backend anymore. The frontend is mythbuntu 8.04 and the backend is ubuntu 8.04. (I successfully got past the database schema update a couple months back. :)) The frontend program runs fine on the backend.

When I try to run mythfrontend from the command line on the frontend, this is what I get. (I inserted "*****long pause*****" where the output pauses for a long time; at least two-three minutes.)

```
2008-08-05 18:45:46.015 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-05 18:45:46.538 XScreenSaver support enabled
2008-08-05 18:45:46.538 DPMS is active.
2008-08-05 18:45:46.538 Empty LocalHostName.
2008-08-05 18:45:46.538 Using localhost value of mythtv-familyrm
2008-08-05 18:45:46.539 Testing network connectivity to 192.168.1.150
2008-08-05 18:45:46.552 New DB connection, total: 1

**************long pause*************

2008-08-05 18:48:55.551 Unable to connect to database!
2008-08-05 18:48:55.551 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.150' (110)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-08-05 18:52:04.602 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2008-08-05 18:52:06.889 UPnPautoconf() - No UPnP backends found
2008-08-05 18:52:06.889 No UPnP backends found
2008-08-05 18:52:06.892 Primary screen 0.
2008-08-05 18:52:06.892 Using screen 0, 1366x768 at 0,0
2008-08-05 18:52:06.894 Switching to square mode (blue)
2008-08-05 18:52:06.910 Using the Qt painter
mythtv: unknown token "Navigation" in /home/mythtv-fam/.mythtv/lircrc:1221 ignored
mythtv: unknown token "Stream" in /home/mythtv-fam/.mythtv/lircrc:1236 ignored
mythtv: unknown token "Position" in /home/mythtv-fam/.mythtv/lircrc:1301 ignored
mythtv: unknown token "'######" in /home/mythtv-fam/.mythtv/lircrc:1302 ignored
mythtv: unknown token "Speed" in /home/mythtv-fam/.mythtv/lircrc:1383 ignored
mythtv: unknown token "Volume" in /home/mythtv-fam/.mythtv/lircrc:1415 ignored
mythtv: unknown token "Subtitle" in /home/mythtv-fam/.mythtv/lircrc:1449 ignored
mythtv: unexpected token in line /home/mythtv-fam/.mythtv/lircrc:1464
mythtv: unexpected token in line /home/mythtv-fam/.mythtv/lircrc:1604
mythtv: unknown token "Miscelaneous" in /home/mythtv-fam/.mythtv/lircrc:1732 ignored
mythtv: unknown token "Number" in /home/mythtv-fam/.mythtv/lircrc:1804 ignored
mythtv: unknown token "Syncing" in /home/mythtv-fam/.mythtv/lircrc:1899 ignored
2008-08-05 18:52:06.912 lirc init success using configuration file: /home/mythtv-fam/.mythtv/lircrc
2008-08-05 18:52:06.912 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythtv-fam/.mythtv/joystickmenurc
ICE default IO error handler doing an exit(), pid = 6025, errno = 32
```


I bet the next step will be for me to send some logs from the mysql server, but logging is not enabled and I haven't quite figured out how to enable it yet. I'll try again after this post.

John K.

---

### Post by jk-menifee on 2008-08-05
Just in case it matters, there was a re-start of the backend between the time it was working and now. Since the problem started I did try to re-start the backend one more time.

Also I just realized the timestamps in the output above tell us the pause was almost exactly 3 minutes. Duh! Good thing my internal clock matches the system one.

Thanks,

John K.

---

### Post by jk-menifee on 2008-08-07
bump... still need a hand please

---

### Post by jk-menifee on 2008-08-08
ok I figured it out. The restart implemented firewall settings on the server that I had configured a week ago. (My server's now accessible to me over the Internet via ssh which is kinda neat, but I didn't want the machine to be wide open. But I think I'm going to cancel the firewall settings because now I understand how my router is able to block all external traffic except that which I allow through port forwarding.) What clued me in was enabling mysql logging and seeing that the frontend login attempt wasn't even reaching the mysql server.

---

