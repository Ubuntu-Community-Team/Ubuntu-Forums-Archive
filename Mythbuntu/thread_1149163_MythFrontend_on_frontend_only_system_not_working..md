---
title: "MythFrontend on frontend only system not working."
date: 2009-05-04
forum: Mythbuntu
---

### Post by iankellogg on 2009-05-04
I've gone up and down the forums for the past 2 hours and So far nothing seems to make any sense at all. I've double checked the backend and its configured correctly. But when I start up mythfrontend on the system I want to use, below is all that I get. I've let it sit for half an hour and it never does anything. It does respond to the backend going down but that's about it.


[email]ian@atom:~/.mythtv[/email]$ mythfrontend
2009-05-04 23:43:30.197 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2009-05-04 23:43:30.200 MediaRenderer::HttpServer Create Error
2009-05-04 23:43:30.221 XScreenSaver support enabled
2009-05-04 23:43:30.222 DPMS is active.
2009-05-04 23:43:30.223 Using localhost value of atom
2009-05-04 23:43:30.224 Testing network connectivity to 192.168.1.20
2009-05-04 23:43:30.261 New DB connection, total: 1
2009-05-04 23:43:30.534 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-04 23:43:30.538 Closing DB connection named 'DBManager0'
2009-05-04 23:43:30.541 Primary screen 0.
2009-05-04 23:43:30.543 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-04 23:43:30.548 Using screen 0, 1920x1200 at 0,0
2009-05-04 23:43:30.571 New DB connection, total: 2
2009-05-04 23:43:30.573 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-04 23:43:30.578 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-05-04 23:43:30.579 Enabled verbose msgs:  important general

---

### Post by iankellogg on 2009-05-05
more information, i tried mythwelcome this time.

[email]ian@atom:~/.mythtv[/email]$ mythwelcome 
2009-05-05 00:12:05.161 Using runtime prefix = /usr
2009-05-05 00:12:05.180 XScreenSaver support enabled
2009-05-05 00:12:05.184 DPMS is active.
2009-05-05 00:12:05.185 Using localhost value of atom
2009-05-05 00:12:05.187 Testing network connectivity to 192.168.1.20
2009-05-05 00:12:05.213 New DB connection, total: 1
2009-05-05 00:12:05.221 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-05 00:12:05.223 Closing DB connection named 'DBManager0'
2009-05-05 00:12:05.284 Primary screen 0.
2009-05-05 00:12:05.286 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-05 00:12:05.289 Using screen 0, 1920x1200 at 0,0
2009-05-05 00:12:05.469 Primary screen 0.
2009-05-05 00:12:05.471 Using screen 0, 1920x1200 at 0,0
2009-05-05 00:12:05.475 No theme dir: /home/ian/.mythtv/themes
2009-05-05 00:12:05.476 The theme () is missing a themeinfo.xml file
2009-05-05 00:12:05.476 Switching to square mode ()
get fences failed: -1
param: 6, val: 0
2009-05-05 00:12:05.571 Using the Qt painter
2009-05-05 00:12:05.584 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ian/.mythtv/joystickmenurc
2009-05-05 00:12:05.633 lirc init success using configuration file: /home/ian/.lircrc
2009-05-05 00:12:05.752 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2009-05-05 00:12:06.282 Connecting to backend server: 192.168.1.20:6543 (try 1 of 5)
2009-05-05 00:12:06.282 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-05-05 00:12:09.843 mythshutdown --startup returned: 1
Killed

---

### Post by iankellogg on 2009-05-05
I got a bit further along but still not luck, if anyone has an idea willing to try anything at this point


[email]ian@atom:~/.mythtv[/email]$ mythwelcome 
2009-05-05 00:29:38.988 Using runtime prefix = /usr
2009-05-05 00:29:39.006 XScreenSaver support enabled
2009-05-05 00:29:39.012 DPMS is active.
2009-05-05 00:29:39.013 Using localhost value of atom
2009-05-05 00:29:39.015 Testing network connectivity to 192.168.1.20
2009-05-05 00:29:39.042 New DB connection, total: 1
2009-05-05 00:29:39.316 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-05 00:29:39.318 Closing DB connection named 'DBManager0'
2009-05-05 00:29:39.321 Primary screen 0.
2009-05-05 00:29:39.323 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-05 00:29:39.330 Using screen 0, 1920x1200 at 0,0
2009-05-05 00:29:39.644 Primary screen 0.
2009-05-05 00:29:39.646 Using screen 0, 1920x1200 at 0,0
2009-05-05 00:29:39.651 No theme dir: /home/ian/.mythtv/themes
2009-05-05 00:29:39.651 The theme () is missing a themeinfo.xml file
2009-05-05 00:29:39.651 Switching to square mode ()
get fences failed: -1
param: 6, val: 0
2009-05-05 00:29:39.797 Using the Qt painter
2009-05-05 00:29:39.823 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ian/.mythtv/joystickmenurc
2009-05-05 00:29:39.844 New DB connection, total: 2
2009-05-05 00:29:39.847 Connected to database 'mythconverg' at host: 192.168.1.20
2009-05-05 00:29:39.850 lirc init success using configuration file: /home/ian/.lircrc
2009-05-05 00:29:40.013 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/welcome-ui.xml
2009-05-05 00:29:40.560 Connecting to backend server: 192.168.1.20:6543 (try 1 of 5)
2009-05-05 00:29:40.561 Using protocol version 40
2009-05-05 00:30:10.743 MythSocket(115e020:12): readStringList: Error, timeout.
2009-05-05 00:30:10.743 Connection to backend server lost
2009-05-05 00:30:10.744 Connecting to backend server: 192.168.1.20:6543 (try 1 of 5)
2009-05-05 00:30:22.746 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
ICE default IO error handler doing an exit(), pid = 8839, errno = 32




I didn't do anything to the backend while it said it lost the connection. in fact Im watching tv on it now.

---

### Post by klc5555 on 2009-05-05
> **iankellogg said:**
> I got a bit further along but still not luck, if anyone has an idea willing to try anything at this point




I didn't do anything to the backend while it said it lost the connection. in fact Im watching tv on it now.

Just a shot, but assuming you set your mysql service on the backend to accept remote connections (as a master backend), I've noticed that setting the PIN number to 0000 on the master now seems to be mandatory, rather than optional like before. Left with blank spaces as the PIN, the master backend in 9.04 refuses all remote MySQL connections.

---

### Post by iankellogg on 2009-05-05
The third post was me having the pin set to 0000

That's the furthest I have gotten with this whole thing. I have read every guide I can get my hands on and followed, double checked, or experimented with the settings listed in the guide. I have read all the documentation on the wiki and the pdf for mythbuntu. Mysql has no issues, I am able to use mysql and connect to the database from any machine in my house. What I don't understand is how the backend is refusing connections. I have both of the ip's in the backend set to 192.168.1.20 which is a static ip for the backend. 

The frontend that is installed with the backend only seems to work when its "master database" is set to localhost. If I set it to the ip 192.168.1.20 it refuses to connect even though its on the same machine.

---

### Post by klc5555 on 2009-05-05
> **iankellogg said:**
> The third post was me having the pin set to 0000

That's the furthest I have gotten with this whole thing. I have read every guide I can get my hands on and followed, double checked, or experimented with the settings listed in the guide. I have read all the documentation on the wiki and the pdf for mythbuntu. Mysql has no issues, I am able to use mysql and connect to the database from any machine in my house. What I don't understand is how the backend is refusing connections. I have both of the ip's in the backend set to 192.168.1.20 which is a static ip for the backend. 

The frontend that is installed with the backend only seems to work when its "master database" is set to localhost. If I set it to the ip 192.168.1.20 it refuses to connect even though its on the same machine.

Sorry, I'm stumped. The only time I've ever seen the local frontend fail to connect to its local backend when set to a non-loopback IP has been when I've forgotten to go to the "Services" tab in the Mythbuntu Control Center and enable the MySQL service on the ethernet interface. But I'm sure you've done this to have been able to connect to the database from other machines in the house. 

Maybe the master backend is unaware that 192.168.1.20 is in fact the local machine. Of course, pinging 'localhost' from the backend machine itself will work, but can the machine ping itself if 192.168.1.20 is used instead? If not, then a '192.168.1.20  localhost' line could be added to /etc/hosts

But otherwise I'm baffled. Perhaps other folks will have additional ideas.

---

### Post by iankellogg on 2009-05-05
Pinging works to itself via localhost and 192.168.1.20

---

### Post by iankellogg on 2009-05-06
I got tired of messing with it, reinstalled mythbuntu with the cd and selected frontend only. Made sure the internet connection was working before finishing the install. It works now. 

Not sure on why this happens but at least it works, Mythbuntu still installs the backend when you tell it to install the frontend only.

---

