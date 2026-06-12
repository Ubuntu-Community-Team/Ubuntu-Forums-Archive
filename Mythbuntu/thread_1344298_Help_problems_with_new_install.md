---
title: "Help problems with new install"
date: 2009-12-02
forum: Mythbuntu
---

### Post by mega30000 on 2009-12-02
Any help would be appreciated.


I just did a fresh install of Mythbuntu 9.10.  I am having problems getting the frontend started.

Looks like some type of database problem.

I have attached my front and backend logs.

Thanks so much

Backend
2009-12-02 17:38:10.843 UPnPautoconf() - No UPnP backends found
2009-12-02 17:38:10.846 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2009-12-02 17:38:10.858 Deleting UPnP client...
2009-12-02 17:38:11.364 Failed to init MythContext, exiting.
2009-12-02 17:38:11.470 mythbackend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-12-02 17:38:11.471 Using runtime prefix = /usr
2009-12-02 17:38:11.472 Using configuration directory = /home/mythtv/.mythtv
2009-12-02 17:38:11.473 Empty LocalHostName.
2009-12-02 17:38:11.473 Using localhost value of hobgoblin
2009-12-02 17:38:11.479 New DB connection, total: 1
2009-12-02 17:38:11.492 Unable to connect to database!
2009-12-02 17:38:11.493 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)




FRONTEND
Starting mythfrontend.real..
2009-12-02 17:27:23.351 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-12-02 17:27:23.351 Using runtime prefix = /usr
2009-12-02 17:27:23.351 Using configuration directory = /home/daddy/.mythtv
2009-12-02 17:27:24.205 Empty LocalHostName.
2009-12-02 17:27:24.205 Using localhost value of hobgoblin
2009-12-02 17:27:24.215 New DB connection, total: 1
2009-12-02 17:27:24.221 Unable to connect to database!
2009-12-02 17:27:24.221 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2009-12-02 17:27:26.247 UPnPautoconf() - No UPnP backends found
2009-12-02 17:27:26.247 No UPnP backends found
2009-12-02 17:27:26.249 Primary screen: 0.
2009-12-02 17:27:26.250 Using screen 0, 1280x1024 at 0,0
2009-12-02 17:27:26.251 Using theme base resolution of 1280x720
2009-12-02 17:27:26.261 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2009-12-02 17:27:26.261 JoystickMenuThread Error: Joystick disabled - Failed to read /home/daddy/.mythtv/joystickmenurc
2009-12-02 17:27:26.266 Using the Qt painter
2009-12-02 17:27:37.110 User cancelled database configuration
2009-12-02 17:27:37.111 Failed to init MythContext, exiting.
2009-12-02 17:27:37.111 Deleting UPnP client...

---

### Post by nickrout on 2009-12-02
you haven't configured database access properly.

---

### Post by SiHa on 2009-12-03
Did you run mythtv-setup?

---

### Post by mega30000 on 2009-12-04
I gave up and just did an ubuntu 9.10 fresh install and then installed mythtv.  Had the same problem.

Found instructions at [https://help.ubuntu.com/community/MythTv/Install/Troubleshooting](https://help.ubuntu.com/community/MythTv/Install/Troubleshooting)


sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common

then when back into the backend setup and it worked

Thanks
T

---

