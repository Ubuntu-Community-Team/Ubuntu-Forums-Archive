---
title: "frontend only setup"
date: 2010-01-31
forum: Mythbuntu
---

### Post by lime4x4 on 2010-01-31
I have the latest version of mythbuntu running as a backend/frontend setup. I built another computer just for a frontend setup. I typed in the address of the backend server and it failes to connect. I triple checked user name and password. Is there something in the backend server that has to be setup?

---

### Post by Thelasko on 2010-01-31
There should be a separate MySQL password that you need.  It might be different from the system password.

---

### Post by nickrout on 2010-01-31
on the backend run ```
sudo dpkg-reconfigure mythtv-database
``` which will set it up for receiving database connections from the LAN.

---

### Post by lime4x4 on 2010-01-31
odd when i ssh into the mythtv box and run that command i get the following error. This is after i get the screen that asks if i want to modify the backend

john@john-mythtv:~$ sudo dpkg-reconfigure mythtv-database
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database

---

### Post by nickrout on 2010-01-31
weird!

---

### Post by klc5555 on 2010-01-31
> **lime4x4 said:**
> I have the latest version of mythbuntu running as a backend/frontend setup. I built another computer just for a frontend setup. I typed in the address of the backend server and it failes to connect. I triple checked user name and password. Is there something in the backend server that has to be setup?

Assuming the frontend/backend is still functioning correctly after the mysql reconfigure:

The backend needs to have the machine's actual ip address set in the backend setup (not 127.0.0.1).

The PIN in the backend setup needs to be set at 0000

The MySQL service needs to be set for external access in the "services" page of Mythbuntu Control Center.

In the remote frontend: the ip address of the backend needs to be entered. The username is 'mythtv'; the password is the MySQL password (not the user's password) from the backend --found in the mysql.txt file in the /home/mythtv/.mysql directory on the backend, among other places.

---

### Post by lime4x4 on 2010-01-31
Setting the pin allows me to connect to the data base. Now a new problem. If i try to start mythtv front-end i get the a quick flash on the screen then when i look in the error logs this is what i show



Starting mythfrontend.real..
2010-01-31 15:53:53.493 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-01-31 15:53:53.494 Using runtime prefix = /usr
2010-01-31 15:53:53.495 Using configuration directory = /home/john/.mythtv
2010-01-31 15:53:54.387 Empty LocalHostName.
2010-01-31 15:53:54.387 Using localhost value of john-mythtv1
2010-01-31 15:53:54.388 Testing network connectivity to '192.168.1.100'
2010-01-31 15:53:54.476 New DB connection, total: 1
2010-01-31 15:53:54.477 Unable to connect to database!
2010-01-31 15:53:54.477 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.100' (111)

---

### Post by lime4x4 on 2010-01-31
it seems mythtv can't connect to the xserver

john@john-mythtv1:~$ mythfrontend
xprop:  unable to open display ''
mythfrontend.real: cannot connect to X server

---

### Post by nickrout on 2010-01-31
> **lime4x4 said:**
> it seems mythtv can't connect to the xserver

john@john-mythtv1:~$ mythfrontend
xprop:  unable to open display ''
mythfrontend.real: cannot connect to X server

are you connected via ssh or something? If so DISPLAY needs to be set, like:

```
export DISPLAY=:0
mythfrontend
```

---

### Post by larsolav on 2010-02-01
> **lime4x4 said:**
> Setting the pin allows me to connect to the data base. Now a new problem. If i try to start mythtv front-end i get the a quick flash on the screen then when i look in the error logs this is what i show



Starting mythfrontend.real..
2010-01-31 15:53:53.493 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-01-31 15:53:53.494 Using runtime prefix = /usr
2010-01-31 15:53:53.495 Using configuration directory = /home/john/.mythtv
2010-01-31 15:53:54.387 Empty LocalHostName.
2010-01-31 15:53:54.387 Using localhost value of john-mythtv1
2010-01-31 15:53:54.388 Testing network connectivity to '192.168.1.100'
2010-01-31 15:53:54.476 New DB connection, total: 1
2010-01-31 15:53:54.477 Unable to connect to database!
2010-01-31 15:53:54.477 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.100' (111)

The flashing of the myth frontend main page sounds like when I first set up a second FE. What I noticed here is that the frontend also has to be listed as being in the same city location as the frontend on that world map that shows up when setting the Time Zone. I don't know why!I have my Backend set for Chicago in the central time zone, and then on the FE I set it for another mid-western town and I would get kicked out of myth frontend. Then when I set the FE to Chicago it worked OK. May be a coincidence, but worth a shot

---

### Post by peedeeramone on 2010-06-04
how do you change the timezone settings in the frontend if it wont load? i just set up a fresh mythbuntu 10.04 install, and i think the frontend might have worked initially, but it definitely doesnt anymore. it seems to load and then quits like you are saying. how would i go about changing the settings for the timezone if i cant load the program? thanks


for reference: when i run mythfrontend via ssh this is what shows



htpc@htpc:~$ mythfrontend
2010-06-04 15:52:38.302 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-06-04 15:52:38.303 Using runtime prefix = /usr
2010-06-04 15:52:38.303 Using configuration directory = /home/htpc/.mythtv
2010-06-04 15:52:38.999 Empty LocalHostName.
2010-06-04 15:52:38.999 Using localhost value of htpc
2010-06-04 15:52:39.021 New DB connection, total: 1
2010-06-04 15:52:39.028 Connected to database 'mythconverg' at host: localhost
2010-06-04 15:52:39.029 Closing DB connection named 'DBManager0'
2010-06-04 15:52:40.322 DPMS is active.
2010-06-04 15:52:40.354 Primary screen: 0.
2010-06-04 15:52:40.356 Connected to database 'mythconverg' at host: localhost
2010-06-04 15:52:40.361 Using screen 0, 1680x1050 at 0,0
2010-06-04 15:52:40.413 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
2010-06-04 15:52:40.415 Desktop video mode: 0x0 0 Hz
2010-06-04 15:52:41.714 MythUI Image Cache size set to 20971520 bytes
2010-06-04 15:52:41.748 Enabled verbose msgs:  important general
2010-06-04 15:52:41.788 Primary screen: 0.
2010-06-04 15:52:41.790 Using screen 0, 1680x1050 at 0,0
2010-06-04 15:52:41.792 Using theme base resolution of 1280x720
2010-06-04 15:52:41.807 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-06-04 15:52:41.808 JoystickMenuThread Error: Joystick disabled - Failed to read /home/htpc/.mythtv/joystickmenurc
2010-06-04 15:52:41.878 Using Frameless Window
2010-06-04 15:52:41.878 Using Full Screen Window
2010-06-04 15:52:45.168 Using the Qt painter
2010-06-04 15:52:45.172 Removing stale cache dir: /home/htpc/.mythtv/themecache/Mythbuntu.1152.864
2010-06-04 15:52:45.411 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-06-04 15:52:45.444 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-06-04 15:52:45.485 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-06-04 15:52:45.485 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-06-04 15:52:45.504 New DB connection, total: 2
2010-06-04 15:52:45.507 Connected to database 'mythconverg' at host: localhost
2010-06-04 15:52:45.515 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-04 15:52:47.335 Registering Internal as a media playback plugin.
2010-06-04 15:52:47.427 Cannot load language en_us for module mytharchive
2010-06-04 15:52:47.435 Cannot load language en_us for module mythbrowser
2010-06-04 15:52:47.449 Registering WebBrowser as a media playback plugin.
2010-06-04 15:52:47.449 Cannot load language en_us for module mythbrowser
2010-06-04 15:52:47.556 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.557 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.558 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.574 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.575 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.576 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.579 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.580 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.587 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-04 15:52:47.588 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-06-04 15:52:47.589 Cannot load language en_us for module mythgallery
2010-06-04 15:52:47.616 Cannot load language en_us for module mythgame
2010-06-04 15:52:47.628 Cannot load language en_us for module mythmovies
2010-06-04 15:52:47.702 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-06-04 15:52:47.867 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-06-04 15:52:47.894 Cannot load language en_us for module mythmusic
2010-06-04 15:52:47.920 Cannot load language en_us for module mythnetvision
2010-06-04 15:52:47.937 Cannot load language en_us for module mythnews
2010-06-04 15:52:47.969 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-06-04 15:52:48.085 Cannot load language en_us for module mythvideo
2010-06-04 15:52:48.111 Cannot load language en_us for module mythweather
2010-06-04 15:52:48.119 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-06-04 15:52:48.332 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-06-04 15:52:48.338 Found mainmenu.xml for theme 'Mythbuntu'
2010-06-04 15:53:12.119 MythContext: Connecting to backend server: 192.168.1.149:6543 (try 1 of 1)
2010-06-04 15:53:12.121 Using protocol version 56
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault
htpc@htpc:~$ 



sorry for reviving an old thread...

---

### Post by larsolav on 2010-06-04
i don't think you set the time zone and city location in Mythtv. I think you can do that from the desktop. I am not by the computer, but what happens when you are on the desktop and point your mouse over the clock in the upper tight corner (or right click it?)? Can you set the zone/location by doing that?

---

### Post by peedeeramone on 2010-06-04
its set to chicago/central. i have the backend set to auto i think because i dont know what the +/- number is. thats the only timezone setting on the backend i could find.

---

### Post by nickrout on 2010-06-04
What makes you think this is a timezone issue? I see nothing in the log to indicate that.

What about the log entry just before the crash about not being able to mount /dev/sdb?

---

### Post by peedeeramone on 2010-06-04
it was having the same symptoms as others so i thought about trying that.

theres only one drive so i dont even know where sdb is coming from.

---

