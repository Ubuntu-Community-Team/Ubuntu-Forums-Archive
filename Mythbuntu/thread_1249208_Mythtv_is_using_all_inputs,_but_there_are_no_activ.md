---
title: "Mythtv is using all inputs, but there are no active recordings"
date: 2009-08-25
forum: Mythbuntu
---

### Post by iitywygms on 2009-08-25
I just moved to trunk .22
I have finally got my backend running.  I upgraded frontend to .22 also.
When I start mythtv on the frontend, I get an error message.
Mythtv is using all inputs, but there are no active recordings
Here is a post from the error log.

2009-08-25 00:20:29.585 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on 'myth-backend' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-08-25 00:20:29.635 No error type from QSqlError?  Strange...
2009-08-25 00:20:29.685 Database not open while trying to load setting: Theme
2009-08-25 00:20:29.686 Unable to connect to database!
2009-08-25 00:20:29.686 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on 'myth-backend' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-08-25 00:20:29.736 No error type from QSqlError?  Strange...
2009-08-25 00:20:29.786 Database not open while trying to load setting: Theme
2009-08-25 00:20:29.787 Unable to connect to database!
2009-08-25 00:20:29.787 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on 'myth-backend' (111)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-08-25 00:20:29.837 No error type from QSqlError?  Strange...
2009-08-25 00:20:29.888 Database not open while trying to load setting: Theme
2009-08-25 00:20:34.349 Deleting UPnP client...



Here is the errors if I start from  a command line.

kevin@mythtv:/var/log/mythtv$ mythtv
2009-08-25 00:45:42.397 Using runtime prefix = /usr
2009-08-25 00:45:42.397 Empty LocalHostName.
2009-08-25 00:45:42.398 Using localhost value of mythtv
2009-08-25 00:45:42.398 Testing network connectivity to 'myth-backend'
2009-08-25 00:45:42.416 New DB connection, total: 1
2009-08-25 00:45:42.418 Connected to database 'mythconverg' at host: myth-backend
2009-08-25 00:45:42.418 Closing DB connection named 'DBManager0'
2009-08-25 00:45:42.489 ScreenSaverX11Private: Gnome screen saver support enabled
2009-08-25 00:45:42.574 DPMS is active.
2009-08-25 00:45:42.577 Primary screen: 0.
2009-08-25 00:45:42.578 Connected to database 'mythconverg' at host: myth-backend
2009-08-25 00:45:42.580 Using screen 0, 1280x720 at 0,0
2009-08-25 00:45:42.601 MythUI Image Cache size set to 20971520 bytes
2009-08-25 00:45:42.606 Current Schema Version: 1242
2009-08-25 00:45:42.724 Primary screen: 0.
2009-08-25 00:45:42.725 Using screen 0, 1280x720 at 0,0
2009-08-25 00:45:42.727 Using theme base resolution of 800x600
2009-08-25 00:45:42.780 LIRC: Successfully initialized '/dev/lircd' using '/home/kevin/.mythtv/lircrc' config
2009-08-25 00:45:42.801 JoystickMenuThread Error: Joystick disabled - Failed to read /home/kevin/.mythtv/joystickmenurc
2009-08-25 00:45:43.008 Using the Qt painter
2009-08-25 00:45:43.257 Loading base theme from /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-08-25 00:45:43.755 Loading base theme from /usr/share/mythtv/themes/default/base.xml
2009-08-25 00:45:43.960 TV: ctor
2009-08-25 00:45:44.055 New DB connection, total: 2
2009-08-25 00:45:44.056 Connected to database 'mythconverg' at host: myth-backend
2009-08-25 00:45:44.353 TV: StartTV() -- begin
2009-08-25 00:45:44.353 TV: ctor
2009-08-25 00:45:44.515 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-25 00:45:44.515 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-25 00:45:44.626 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-25 00:45:44.627 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2009-08-25 00:45:44.627 TV Error: Failed to get recording show list
2009-08-25 00:45:46.412 TV: StartTV -- process events 2 begin
2009-08-25 00:45:46.429 TV: StartTV -- process events 2 end
2009-08-25 00:45:46.430 TV::~TV() -- begin
2009-08-25 00:45:46.430 TV::~TV() -- lock
2009-08-25 00:45:46.431 TV::~TV() -- end
2009-08-25 00:45:46.431 TV: StartTV -- end

Which would leave me to believe that I cant connect to the database.
But if I do a  mysql -h myth-backend -u mythtv -p mythconverg
it will bring me to the mysql prompt.

Any ideas?
I use a hdhomerun

---

### Post by KillerKiwi on 2009-08-25
You got a setting wrong some where
```
127.0.0.1:6543 (try 1 of 5)
```

Id try the IP address in the backend general settings... it needs to be your external IP not the loop back (default is loopback)

---

### Post by iitywygms on 2009-08-26
That solved it.  
Thank you.

---

### Post by rusty0101 on 2009-11-04
I found another variation of this as well. I have a primary host that provides my mythbackend, and also provides on of my front ends. The 9.10 install set up the loopback interface correctly, including a /etc/hosts entry for it. However it also set up a hosts entry for the host name that I had provided during setup, also pointing at 127.0.0.1, so everywhere that the field had been filled in with the host name was resolving to the loopback interface ip, which is no good either.

I'm not sure how you would fix this with a dhcp interface setup, I've set mine with a static address, so dhcp really hasn't come up as an issue.

---

### Post by t3chn0b0y on 2009-11-27
I have the same error message.. But it happens after I go in and try to create a custom recording setting.. If I type the text in the box the hard drive goes bonkers and the screen freezes and eventually crashes to the desktop... I restart the system, and all my scheduled recordings are not showing, or my upcoming recordings.. But when doing a check the settings
are still setup correctly... but upon entering Live TV I get the message "error mythtv is using all input devices but there are no active recordings" I have noticed rebooting doesn't  help the situation, nor does optimizing and attempts to repair database, which report no errors.. But a cold boot.. completely shutdown of the system for a number of minutes and everything reappears.:confused: I can repeat this every time by going in to create a custom recording.. and instead of using the drop down box of built in settings I type them in.. and boom..

---

### Post by mythbuntu101 on 2010-01-19
how do you fix the "mythtv is using all inputs, but there are no active recordings" error?

---

### Post by iitywygms on 2010-01-20
I fixed it by doing what was said in post 2

---

### Post by benlyboy on 2010-01-21
hi

After moving over to .23 my system did this a couple of times. I found that if I shut down the backend then restarted it, it would work ok.
 
Hasn't done it as of late may have been fix in an update.

---

### Post by dmurphy787 on 2010-09-30
I have this error as well, but my router ip address is different to the ones listed in previous posts.  They list 127.0.0.1 but my understanding is that this is the ip address of the local host of that computer.  My HD Homerun is running through my router 192.168.2.10 but I have tried both of those ip addresss and neither seem to get rid of the error.  Can anyone please help me solve this problem.

---

### Post by LowSky on 2010-09-30
uodating to .23.1 should solve the problem of the tuners being in use.

dmurphy787 you can't rely on what other people use for their ip addresses.

For instance my localhost address is 192.186.0.244, and things work fine.

What you need to do is go through your mythtv settings and makes sure you specified the correct addresses on the backend and frontend be sure they all match.

---

