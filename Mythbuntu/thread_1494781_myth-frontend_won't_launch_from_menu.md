---
title: "myth-frontend won't launch from menu"
date: 2010-05-27
forum: Mythbuntu
---

### Post by bance on 2010-05-27
Not sure if it is a mythbuntu problem or something else !

I launched myth-frontend get the database configuration screen...... input info hit next/finish. the machine goes back to desk-top. 

try to re-launch and nothing....

sytem monitor shows everything sleeping......

I did a fresh install from cd of lucid. ran update manager, then installed mythbuntu for 10.04 on top.

anybody else have this problem?

anybody got any ideas?

---

### Post by petatkinson on 2010-05-27
Just been through the MythTV adventure and am currently watching TV on it.The safest way to install is the following

1)Fresh install
2)Update fron update manager
3)Add the non free repos
4)Log on the the Mythbuntu and download Mythbuntu Control Centre
5)Run Mythbuntu control centre and follow the instructions

This worked for me using a Hauppauge HVR4000 card

---

### Post by David Grigor on 2010-05-27
Have you looked in /var/log/mythtv/mythfrontend.log  for any additional information on what the problem/error may be ?

---

### Post by bance on 2010-05-28
OK, frontend now launching but still won't connect to database:- returns an error of either 'no upnp' or 'cannot connect to port 6543'


output from frontend log:-

Starting mythfrontend.real..
2010-05-28 12:09:08.342 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-05-28 12:09:08.343 Using runtime prefix = /usr
2010-05-28 12:09:08.343 Using configuration directory = /home/stephen/.mythtv
2010-05-28 12:09:08.983 Empty LocalHostName.
2010-05-28 12:09:08.984 Using localhost value of stephen-desktop

2010-05-28 12:09:09.140 UPnPautoconf() - Found one UPnP backend
2010-05-28 12:09:09.315 HttpComms::done() - NetworkOperation Error on Finish: Connection refused (or timed out) (1): url: 'http://stephen-desktop:0/Myth'
2010-05-28 12:09:09.331 MythXMLClient::GetConnectionInfo Failed - (1) unexpected end of file
2010-05-28 12:09:09.332 Cannot connect to port 6543 on database host stephen-desktop
2010-05-28 12:09:09.338 Primary screen: 0.
2010-05-28 12:09:09.338 Using screen 0, 1680x1050 at 0,0
2010-05-28 12:09:09.339 Could not find theme:  - Switching to Terra
2010-05-28 12:09:09.340 Using theme base resolution of 1280x720
2010-05-28 12:09:09.364 Desktop video mode: 1680x1050 59.9556 Hz
2010-05-28 12:09:09.578 get_ip: No address associated with hostname
2010-05-28 12:09:09.578 LIRC, Error: Failed to parse IP address ''
2010-05-28 12:09:09.578 JoystickMenuThread Error: Joystick disabled - Failed to read /home/stephen/.mythtv/joystickmenurc
2010-05-28 12:09:09.593 New DB connection, total: 1
2010-05-28 12:09:09.610 Using Frameless Window
2010-05-28 12:09:09.611 Using Full Screen Window
2010-05-28 12:09:09.648 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-05-28 12:09:22.832 Writing settings file /home/stephen/.mythtv/mysql.txt
2010-05-28 12:09:22.833 Closing DB connection named 'DBManager0'
2010-05-28 12:09:22.852 Cannot connect to port 6543 on database host stephen-desktop
2010-05-28 12:09:22.852 Cannot connect to port 6543 on database host stephen-desktop
2010-05-28 12:09:22.912 Primary screen: 0.
2010-05-28 12:09:22.912 Using screen 0, 1680x1050 at 0,0
2010-05-28 12:09:22.914 Using theme base resolution of 1280x720
2010-05-28 12:09:22.916 get_ip: No address associated with hostname
2010-05-28 12:09:22.916 LIRC, Error: Failed to parse IP address ''
2010-05-28 12:09:22.916 JoystickMenuThread Error: Joystick disabled - Failed to read /home/stephen/.mythtv/joystickmenurc
2010-05-28 12:09:22.933 Using Frameless Window
2010-05-28 12:09:22.933 Using Full Screen Window
2010-05-28 12:09:22.953 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-05-28 12:09:26.759 Writing settings file /home/stephen/.mythtv/mysql.txt
2010-05-28 12:09:26.759 Closing DB connection named 'DBManager0'
2010-05-28 12:09:26.769 Cannot connect to port 6543 on database host stephen-desktop
2010-05-28 12:09:26.769 Cannot connect to port 6543 on database host stephen-desktop
2010-05-28 12:09:26.833 Primary screen: 0.
2010-05-28 12:09:26.833 Using screen 0, 1680x1050 at 0,0
2010-05-28 12:09:26.834 Using theme base resolution of 1280x720
2010-05-28 12:09:26.836 get_ip: No address associated with hostname
2010-05-28 12:09:26.837 LIRC, Error: Failed to parse IP address ''
2010-05-28 12:09:26.837 JoystickMenuThread Error: Joystick disabled - Failed to read /home/stephen/.mythtv/joystickmenurc
2010-05-28 12:09:26.854 Using Frameless Window
2010-05-28 12:09:26.854 Using Full Screen Window
2010-05-28 12:09:26.865 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-05-28 12:09:30.486 User cancelled database configuration
2010-05-28 12:09:30.502 Failed to init MythContext, exiting.
2010-05-28 12:09:30.502 Deleting UPnP client...
Starting mythfrontend.real..
2010-05-28 12:49:06.639 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-05-28 12:49:06.640 Using runtime prefix = /usr
2010-05-28 12:49:06.640 Using configuration directory = /home/stephen/.mythtv
2010-05-28 12:49:07.128 Empty LocalHostName.
2010-05-28 12:49:07.129 Using localhost value of stephen-desktop
2010-05-28 12:49:07.130 Testing network connectivity to '192.168.10.2'
................................................................................
2010-05-28 12:49:09.368 UPnPautoconf() - No UPnP backends found
2010-05-28 12:49:09.368 No UPnP backends found
2010-05-28 12:49:09.378 Primary screen: 0.
2010-05-28 12:49:09.378 Using screen 0, 1680x1050 at 0,0
2010-05-28 12:49:09.379 Could not find theme:  - Switching to Terra
2010-05-28 12:49:09.381 Using theme base resolution of 1280x720
2010-05-28 12:49:09.455 Desktop video mode: 1680x1050 59.9556 Hz
2010-05-28 12:49:09.704 get_ip: No address associated with hostname
2010-05-28 12:49:09.705 LIRC, Error: Failed to parse IP address ''
2010-05-28 12:49:09.705 JoystickMenuThread Error: Joystick disabled - Failed to read /home/stephen/.mythtv/joystickmenurc
2010-05-28 12:49:09.741 New DB connection, total: 1
2010-05-28 12:49:09.764 Using Frameless Window
2010-05-28 12:49:09.764 Using Full Screen Window
2010-05-28 12:49:09.840 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-05-28 12:49:23.723 Writing settings file /home/stephen/.mythtv/mysql.txt
2010-05-28 12:49:23.724 Closing DB connection named 'DBManager0'
2010-05-28 12:49:23.742 Testing network connectivity to '192.168.10.2'
2010-05-28 12:49:23.768 Cannot connect to port 6543 on database host 192.168.10.2
2010-05-28 12:49:23.768 Cannot connect to port 6543 on database host 192.168.10.2
2010-05-28 12:49:23.821 Primary screen: 0.
2010-05-28 12:49:23.822 Using screen 0, 1680x1050 at 0,0
2010-05-28 12:49:23.823 Using theme base resolution of 1280x720
2010-05-28 12:49:23.825 get_ip: No address associated with hostname
2010-05-28 12:49:23.825 LIRC, Error: Failed to parse IP address ''
2010-05-28 12:49:23.825 JoystickMenuThread Error: Joystick disabled - Failed to read /home/stephen/.mythtv/joystickmenurc
2010-05-28 12:49:23.843 Using Frameless Window
2010-05-28 12:49:23.843 Using Full Screen Window
2010-05-28 12:49:23.861 Using the Qt painter
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
QFont::setPointSize: Point size <= 0 (0), must be greater than 0
2010-05-28 12:49:30.942 User cancelled database configuration
2010-05-28 12:49:30.949 Failed to init MythContext, exiting.
2010-05-28 12:49:30.949 Deleting UPnP client...


OK, if  I run mythbackend from terminal I get this :-

stephen@stephen-desktop:~$ mythbackend
2010-05-28 15:33:43.930 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-05-28 15:33:43.932 Using runtime prefix = /usr
2010-05-28 15:33:43.932 Using configuration directory = /home/stephen/.mythtv
2010-05-28 15:33:43.933 Empty LocalHostName.
2010-05-28 15:33:43.934 Using localhost value of stephen-desktop
2010-05-28 15:33:43.935 Testing network connectivity to '192.168.10.2'
2010-05-28 15:33:43.981 New DB connection, total: 1
2010-05-28 15:33:44.000 Connected to database 'mythconverg' at host: 192.168.10.2
2010-05-28 15:33:44.000 Closing DB connection named 'DBManager0'
2010-05-28 15:33:44.008 Connected to database 'mythconverg' at host: 192.168.10.2


To me that looks like it's connected.......... !!!!!!!!!!!

---

