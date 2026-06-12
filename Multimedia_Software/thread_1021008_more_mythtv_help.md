---
title: "more mythtv help"
date: 2008-12-24
forum: Multimedia Software
---

### Post by newtolinuxhardy on 2008-12-24
i need even more help with mythtv.  when i run the backend setup it tells me

2008-12-24 20:42:40.286 Using runtime prefix = /usr
2008-12-24 20:42:40.297 XScreenSaver support enabled
2008-12-24 20:42:40.298 DPMS is active.
2008-12-24 20:42:40.299 Empty LocalHostName.
2008-12-24 20:42:40.299 Using localhost value of Jeremy
2008-12-24 20:42:40.312 New DB connection, total: 1
2008-12-24 20:42:40.322 Unable to connect to database!
2008-12-24 20:42:40.323 Driver error was [1/2003]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to MySQL server on 'jeremy' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2008-12-24 20:42:40.375 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
QServerSocket: failed to bind or listen to the socket
2008-12-24 20:42:40.426 MCP::InitUPnP() - HttpServer Create Error
2008-12-24 20:42:40.427 Deleting UPnP client...
2008-12-24 20:42:40.427 No UPnP backends found
2008-12-24 20:42:40.541 max_width: 1360 max_height: 768
2008-12-24 20:42:40.543 Primary screen 0.
2008-12-24 20:42:40.543 Using screen 0, 1024x768 at 0,0
2008-12-24 20:42:40.544 No theme dir: /home/jeremy/.mythtv/themes/blue
2008-12-24 20:42:40.545 Switching to square mode (blue)
2008-12-24 20:42:40.626 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-24 20:42:40.628 lirc_init failed for mythtv, see preceding messages
2008-12-24 20:42:40.628 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jeremy/.mythtv/joystickmenurc
2008-12-24 20:42:43.368 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-12-24 20:42:43.374 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-12-24 20:42:43.375 DB Error (Clear setting):
Query was:

No error type from QSqlError?  Strange...
2008-12-24 20:42:43.375 DB Error (SaveSettingOnHost query failure: ):
Query was:

No error type from QSqlError?  Strange...
2008-12-24 20:42:47.714 User cancelled database configuration
2008-12-24 20:42:47.725 Failed to init MythContext, exiting.


it then proceeds to run the mythtv frontend setup.  it asks me for my language.   i select English(US) and press enter.  i then get the following error

no UPnP backends found

i click ok and proceed with setup.  i input the correct information and it tells me

cannot log in to database?

i don't remember if i set a password or not.  how would i check to see if i did?  if i did how would i delete it?

EDIT: some info i found on the internet said not to set a password for the mysql database.  i believe that i might have but don't remember.

---

### Post by newtolinuxhardy on 2008-12-24
i ran

sudo dpkg-reconfigure mythtv-database

and input the name of my computer as the localhost and the name of my administrator account and its password and i got the following error

jeremy@Jeremy:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for jeremy: 
Failed to connect to database: Can't connect to MySQL server on 'Jeremy' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

help me!:confused:

EDIT: the frontend setup still tells me 

no UPnP backends found

please help

---

### Post by newtolinuxhardy on 2008-12-24
i found some info online and reconfigured the MySQL database.  but when i run the frontend setup i get the same error: no UPnP backends found

i input localhost as the host server, root as the user and the password the database generated for me as the password on the frontend setup(because these are the same things i set the database up for, except for the password which i left blank)  i then ran the same items through the frontend setup except i use no password on the password section.  i still get the following error: cannot log in to database? (yes the question mark it included on the error screen)

---

### Post by wolfen69 on 2008-12-24
when i was running ubuntu and wanted mythtv, i could never get it to work right. that's why i installed [Mythbuntu]("http://www.mythbuntu.org/") and called it a day. everything is preinstalled and seemed to run alot smoother. if you don't like the xfce desktop, just run ```
sudo apt-get install ubuntu-desktop
``` to have good old gnome.  sorry i can't be of more help.

---

### Post by newtolinuxhardy on 2008-12-24
thats what i'm going to have to do.  thanks for the help anyway.  i'll leave this thread open and unsolved if anyone has any more suggestions.

P.S. i would like to reformat the drive before i install mythbuntu.  how would i do that?

---

