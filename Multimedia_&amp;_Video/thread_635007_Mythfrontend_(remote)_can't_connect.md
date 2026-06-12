---
title: "Mythfrontend (remote) can't connect"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by lingenfr on 2007-12-08
I have read previous posts concerning similar issues, but can't seem to get this going. I am trying to install a frontend on a Kubuntu Gutsy system following the community documentation. 

[https://help.ubuntu.com/community/MythTV_Gutsy_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Frontend_Desktop)

Everything appears to be correct and mythbuntu-control-centre passes the test on the mysql connect. However, whenever I try and access a function that requires a connection to the backend, it tells me it can't find it and to check my IP. The backend/frontend is on a feisty system that was also installed using the community documentation. 

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

I have edited the mysql.txt file on the backend and bind-address 127.0.0.1 was already commented out. I restarted mysql anyway. No joy. On my frontend, the IP address is correct and I have tried it with and without the unique-machine-identifier option. Here is the output from running mythfrontend from the the command line:

2007-12-08 11:12:45.621 Using runtime prefix = /usr
2007-12-08 11:12:45.628 DPMS is active.
2007-12-08 11:12:45.642 New DB connection, total: 1
2007-12-08 11:12:45.797 Connected to database 'mythconverg' at host: 192.168.1.114
2007-12-08 11:12:45.799 Total desktop dim: 1280x1024, with 1 screen[s].
2007-12-08 11:12:45.805 Using screen 0, 1280x1024 at 0,0
2007-12-08 11:12:45.854 Current Schema Version: 1160
2007-12-08 11:12:45.859 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-12-08 11:12:45.859 Enabled verbose msgs:  important general
2007-12-08 11:12:47.128 Total desktop dim: 1280x1024, with 1 screen[s].
2007-12-08 11:12:47.133 Using screen 0, 1280x1024 at 0,0
2007-12-08 11:12:47.135 Switching to square mode (G.A.N.T.)
2007-12-08 11:12:47.262 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-12-08 11:12:47.547 Joystick disabled.
2007-12-08 11:12:48.031 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-12-08 11:12:48.120 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-12-08 11:12:48.405 Registering Internal as a media playback plugin.
2007-12-08 11:12:53.859 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T./ui.xml
2007-12-08 11:12:54.046 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-12-08 11:12:54.046 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.
2007-12-08 11:12:58.231 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-12-08 11:12:58.231 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.

I don't know where to change the backend server address in the frontend configuration other than where I already have. Help.

---

### Post by lingenfr on 2007-12-09
Yet again it is cathartic to come here and talk to myself. I uprgraded my master backend box and now I can connect just fine.

---

### Post by volksman on 2008-02-16
The REAL fix is in the mythtv-setup app under general.  Change anything that says 127.0.0.1 or localhost to the actual IP of the backend...

---

### Post by lingenfr on 2008-02-29
Thanks for playing, but no. The solution is to have the correct authentican method which the myth develpers routinely change. There were other fixes such as enable old style passwords, but the best was to get both boxes on the same myth version.

---

