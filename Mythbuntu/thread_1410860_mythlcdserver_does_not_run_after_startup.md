---
title: "mythlcdserver does not run after startup"
date: 2010-02-19
forum: Mythbuntu
---

### Post by x-wolf on 2010-02-19
Hi,
 
I'm having trouble with mythlcdserver after booting up my mythbuntu computer. Mythlcdserver does not start and this is in my log file of mythfrontend:
 
 
 
2010-02-19 14:27:47.888 Starting mythlcdserver
QWidget: Cannot create a QWidget when no GUI is being used
2010-02-19 14:27:48.506 Connecting to lcd server: localhost:6545 (try 1 of 10)
2010-02-19 14:27:49.102 Connecting to lcd server: localhost:6545 (try 2 of 10)
2010-02-19 14:27:49.603 Connecting to lcd server: localhost:6545 (try 3 of 10)
2010-02-19 14:27:50.104 Connecting to lcd server: localhost:6545 (try 4 of 10)
2010-02-19 14:27:50.605 Connecting to lcd server: localhost:6545 (try 5 of 10)
2010-02-19 14:27:51.106 Connecting to lcd server: localhost:6545 (try 6 of 10)
2010-02-19 14:27:51.606 Connecting to lcd server: localhost:6545 (try 7 of 10)
2010-02-19 14:27:52.108 Connecting to lcd server: localhost:6545 (try 8 of 10)
2010-02-19 14:27:52.609 Connecting to lcd server: localhost:6545 (try 9 of 10)
2010-02-19 14:27:53.110 Connecting to lcd server: localhost:6545 (try 10 of 10)
 
I am using Mythbuntu 9.10 with MythTV version 0.22 on an Antec Veris Fusion (with LCDProc and the imon driver). I have the LCD and not the VFD screen.
 
My computer automatically starts up with mythtv. If I close down mythfrontend and I start it up again, mythlcdserver is started and the information shows up at my lcd screen. I have already found many howto's and changed already the settings for LCDServerHost (data and hostname) in the settings table, but this does not fix the problem. 
Does anyone know where to fix this problem?
Thanks

---

### Post by ian dobson on 2010-02-19
Hi,
 
Sounds like another race condition in mythtv. I've seen several since they've gone over to using upstart.

Findout which server drives the LCD display and make sure it starts before X (look in /etc/rc for SxxLCDd) and change the xx to a lower number.

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-19
+1 for this problem. My LCDd starts and waits for the client and automatically defaults to clock on first boot. I then have to restart myth frontend to see anything useable on the lcd.

 I too have the 1-10 tries to start LCDd.

 So Ian are we udpdating the rc.d defaults to a lower number than 5. I think that what it was set to when I compiled and installed LcdProc. 
 
 Now if we could only figure out why it is taking 40+ seconds to load the frontend from a useable desktop.

 Dave.

---

### Post by ian dobson on 2010-02-19
Hi,

Yep. When linux starts it looks in the /etc/rcX.d level for all scripts starting with S. It starts the scripts one after another using the number after the S to know what order to start them in.

so /etc/rc3.d/S06Test will start before /etc/rc3.d/S99Test when the system switchs to run level 5.

Hope this helps abit.

A really nice solution would be to get all services into upstart and get upstart to run the scripts based on the dependances. I've already done this for afew services for my backed (When network is started, start Apache/FTP server/Email server/MySQL when Apache/MySQL is running start Mythtvbackend). It took several hours to setup/test but my Big Iron backend boots in less then 30 seconds.

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-20
Ian,

 ofcourse there is no rcS directory there are rc0.d through rcX.d each one of those directories has either K20LCDd or S20LCDd, I am a little concerned about changing them to like 19 as Lirc is loaded up at K19 and S19. 

 and again do each of the files in each rcX.d directory need to be changed manually from 20 to XX and then run sudo update-rc.d LCDd defaults. 
 
 for if I run sudo update-rc.d LCdd defaults remove and then update-rc.d LCDd defaults it just sets them the S20, K20 files.

 Dave

---

### Post by ian dobson on 2010-02-20
Hi,

Just change the S20LCDd files to S10LCDd or so. This will start the LCDd daemon earlier on the boot process. That should solve it.

The K20LCDd is for Kill service at step 20. We want to Start the script earlier.

If you start LCDd too soon in the boot process, nothing "bad" will happen, it's not a really important process, the system will boot without it, allowing you to solve any problems.


Regards
Ian Dobson

---

### Post by rodercot on 2010-02-20
Changed them all the S10 and still the same issue. Maybe we are not having the same issues. 

 My problem is I boot Myth for the first time it loads the front end lcd finds the client and immediately switches to the clock and that is all the action I see from the LCD I must restart the front end to have the LCD display anything other than the clock.

 Dave

---

### Post by x-wolf on 2010-02-21
I've changed LCDd to S20LCDd, and LCDd starts earlier then before but it does not solve my problem. LCDProc is already showing it's information before Mythfrontend starts up. So I don't think that's the problem (and that was also the case when LCDd was started up as S60LCDd). 
Mythlcdserver is not running after boot. Only when I stop mythfrontend and restart it again, mythlcdserver runs.....
 
Does anyone have another suggestion for me?

---

### Post by ian dobson on 2010-02-21
Hi,

Maybe this could be something to do with your problem:-
[http://www.gossamer-threads.com/lists/mythtv/commits/406372](http://www.gossamer-threads.com/lists/mythtv/commits/406372)

Could it be that your network (lo) is starting too late, are you using network-manager?

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-22
> **ian dobson said:**
> Hi,

Maybe this could be something to do with your problem:-
[http://www.gossamer-threads.com/lists/mythtv/commits/406372](http://www.gossamer-threads.com/lists/mythtv/commits/406372)

Could it be that your network (lo) is starting too late, are you using network-manager?

Regards
Ian Dobson

 Ian that looks promising, I have Ipv6 disable via grub2 default command line. 

 Where is this "TABLE" that is referred to in the link you pasted. 
 I have tried multiple times to change my host name in Mythbuntu and no matter where I change the name in the log it always says it cannot find hostmame using 127.0.0.1 for hostname.

 Regards,

 Dave

---

### Post by ian dobson on 2010-02-22
Hi,

The table is an mysql database table where mythtv stores all it's configuration options.

OK Try this:-

1) Go to the terminal and enter:-
mysql -uUUUUUU -pXXXXX

change UUUU to your user name (mythtv?) and change XXXX to the password.
Then enter and the mysql> prompt:-
SELECT * FROM `mythconverg`.`settings` WHERE `value` LIKE 'LCDServerHost';

This will just show you the current setting for the parameter "LCDServerHost"

If you see localhost as the value then we can do the next step and actually change the value, but I've not got a mythtv box here to play with :)

ps. You might be able to change the host name used by mythlcd through the Frontend setup.

Regards
Ian Dobson

---

### Post by utar on 2010-02-23
I had this problem too.  The easier way then editing the database directly is to tweak your hosts file:

[http://ubuntuforums.org/showthread.php?p=8333534](http://ubuntuforums.org/showthread.php?p=8333534)


Utar

---

### Post by rodercot on 2010-02-23
that fix was a no go for me and if I try to edit mysql on the frontend that is having the issue I see this.

 ```
xbmc@xbmclvgrm:~$ mysql -u mythtv -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

 Regards,

 Dave

---

### Post by ian dobson on 2010-02-23
Hi,

can you run the sql command on your backend, where the mysql server is installed. 

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-24
IAN,

 Yes I was questioning that in my head. Why would I have mysql on a frontend, OK here is the output of what you asked for. 

 ```
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2403
Server version: 5.0.67-0ubuntu6.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SELECT * FROM `mythconverg`.`settings` WHERE `value` LIKE 'LCDServerHost';
Empty set (0.00 sec)

mysql>

```

 I am also wondering - should the mysql password be the same as the database password. I am pretty sure when I setup the backend that I just hit enter. but now it has a password AND it is not the same as the password the frontends connect with.

 If I change this on the backend what host name would I put in to the LCDServerHost line, I have two frontends with LCD's.

 My Backend is based on 8.10 and my Frontends are 9.10 all with .22 via Avenards Repos.

 Thanks for the help here. 

 Regards,

 Dave

---

### Post by ian dobson on 2010-02-24
Hi,

OK it looks as if the LCDServerHost value is not set, mybe we just need to add it to the settings, I'll have a look on my box if I can find abit more information about the LCD server...

edit: OK try this:-

1) Go to the terminal and enter:-
mysql -uUUUUUU -pXXXXX

change UUUU to your user name (mythtv?) and change XXXX to the password.
Then enter and the mysql> prompt:-
 
mysql> insert into mythconverg.settings (value,data,hostname) values ('LCDServerHost','127.0.0.1','YourHostName'); 
mysql> quit

Change YourHostName to the name of your frontend(s).

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-24
Hi Ian,
 
 OK I changed that sorry for the late reply, I had not noticed that you edited your post. 

 I added the line to the table and rebooted and saw NO change in the process and I still have the ten connection tried in the log only now instead of listing localhost:6545 it says 
127.0.0.1:6545

 The data I entered was like so. 
 
 ('LCDServerHost','127.0.0.1',null);
 
 I am not sure if null needed 'null' or null. is this ok.

 I am not sure how to enter multiple frontends in the command

 would it be 'hostname','hostname','hostname'); etc... 

 I am really confused but I am sure this is why it taking so long for myth to load a frontend after boot-up. 

 In my general setup on the front end for the actual database I have the master b/e ip address and I have ping checked off but I have no port listed. Should there be.

 I just had a quick look in the LCDd.conf file and in the server section of that file it has bind=127.0.0.1 and the port set to 13666, I am not sure if this would have any bearing but I am grasping at straws now. exact same affect on two separate systems.

 Regards,

 Dave

---

### Post by ian dobson on 2010-02-24
Hi,

No null ist not correct.

Just enter the command as I wrote it with the name of your first backend as the last parameter, then repeat the command but using the name of the second backend.

insert into mythconverg.settings (value,data,hostname) values ('LCDServerHost','127.0.0.1','Frontend1_Name'); 
insert into mythconverg.settings (value,data,hostname) values ('LCDServerHost','127.0.0.1','Frontend2_Name'); 

This will intert 2 rows into your settings database.

Regards
Ian Dobson

---

### Post by Neon Dusk on 2010-02-25
@rodercot using null is fine - just means it applies to all your frontends

However the LCDServerHost setting isn't your problem (and wasn't the problem of the OP). If mythtv can use the LCD after restarting mythfrontend then the connection is working fine.

There's a launchpad bug about your (and the OPs) issue [here](https://bugs.launchpad.net/mythbuntu/+bug/509065). There doesn't seem to be a solution. One thing I would try is to add a small delay to the auto login procedure from 'Mythbuntu Control Centre -> Startup Behavior'

---

### Post by rodercot on 2010-02-25
I went mythweb and deleted the null enter actually deleted the entry for all hosts and and then recreated it for my two frontends with LCD devices and yep still no change.

 One thing I noticed in mythweb is that I have a bunch of hosts names in there that are no longer on my system how would I go about removing those host entries from the backend. There are about 10 hostnames and currently I only have three frontends and one backend.

 have the 1-10 tries in the log. 

 Yes if I restart mythfrontend after it connects right away. 

 So I will look into the delay.

 Thanks,

 Dave

---

### Post by rodercot on 2010-02-25
> **Neon Dusk said:**
> @rodercot using null is fine - just means it applies to all your frontends

However the LCDServerHost setting isn't your problem (and wasn't the problem of the OP). If mythtv can use the LCD after restarting mythfrontend then the connection is working fine.

There's a launchpad bug about your (and the OPs) issue [here](https://bugs.launchpad.net/mythbuntu/+bug/509065). There doesn't seem to be a solution. One thing I would try is to add a small delay to the auto login procedure from 'Mythbuntu Control Centre -> Startup Behavior'

 Thanks,

 I posted my comments on that bug as well. I will look into the delay idea this evening. any idea on how to achieve that. 

 would it be the same as stopping myth from autostarting and then autostart xbmc and come back to myth via my LiveTV switch or will that remain that it is the first time the f/e is launched. 

 rgds,

 Dave

---

### Post by Neon Dusk on 2010-02-25
Are you systems set-up to auto login and then autostart mythfrontend?

If they are then my suggestion was to use the option avaiable via 'Mythbuntu Control Center -> Startup Behavior - login' to delay the auto login by 5 secs to see if it makes any difference

(I'm away from the PC at the moment so can't check the actual wording in the control center)

---

### Post by rodercot on 2010-02-25
> **Neon Dusk said:**
> Are you systems set-up to auto login and then autostart mythfrontend?

If they are then my suggestion was to use the option avaiable via 'Mythbuntu Control Center -> Startup Behavior - login' to delay the auto login by 5 secs to see if it makes any difference

(I'm away from the PC at the moment so can't check the actual wording in the control center)

 
 It is already set to 10 Seconds, If you set it any higher it actually boots up and pauses with a login window in the center of the screen with a countdown clock wating for the 15 seconds to expire then logs in.

 You had the right place by the way. you can also get it from the menu - system -> Login Window.

 Regards,

 Dave

---

### Post by Neon Dusk on 2010-02-25
mythlcdserver is started from either mythfrontend or mythwelcome. I doubt it will make a difference but you could try enabling mythwelcome (uncomment the mythwelcome line in /etc/mythtv/session-settings) to see if it makes a difference.

---

### Post by rodercot on 2010-02-25
> **Neon Dusk said:**
> mythlcdserver is started from either mythfrontend or mythwelcome. I doubt it will make a difference but you could try enabling mythwelcome (uncomment the mythwelcome line in /etc/mythtv/session-settings) to see if it makes a difference.

 Thanks for the suggestion, that amde no change either. 
 
 Dave

---

### Post by rodercot on 2010-02-25
one thing I noticed and not sure if it makes any difference at all but in the frontend log and with the 10 mythlcd errors

 connecting to lcd server 127.0.0.1:6545 

 but in looking at my backend->setup->general the backends port is 6543 

 again I am grasping at straws here. 

 Dave

---

### Post by Neon Dusk on 2010-02-26
No that's normal mythlcdserver should listen on 6545

When the frontend starts and the LCD isn't working  could you ssh into the machine and kill the mythlcdserver process?
```

killall mythlcdserver

```
You can see if it's running using
```

ps aux | grep mythlcdserver

```

The frontend should then restart mythlcdserver after 10s. If this works you could put together a hack that kills mythlcdserver after the frontend is started.

---

### Post by rodercot on 2010-02-26
> **Neon Dusk said:**
> No that's normal mythlcdserver should listen on 6545

When the frontend starts and the LCD isn't working  could you ssh into the machine and kill the mythlcdserver process?
```

killall mythlcdserver

```
You can see if it's running using
```

ps aux | grep mythlcdserver

```

The frontend should then restart mythlcdserver after 10s. If this works you could put together a hack that kills mythlcdserver after the frontend is started.

 No luck with that. I looked to see if it was running. killed the process. It did not restart.

 went to setup-appearance and to the enable lcd screen then clicked finish, I did not change anything I just clicked finish and it restarted the lcdserver and here is the last of the log.

 ```
xbmc@zotac-ion:~$ ps aux | grep mythlcdserver
xbmc      1708  0.0  0.0   3040   804 pts/0    S+   04:46   0:00 grep --color=au                                        to mythlcdserver
xbmc@zotac-ion:~$ killall mythlcdserver
xbmc@zotac-ion:~$ tail -f /var/log/mythtv/mythfrontend.log
2010-02-26 04:50:22.392 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2010-02-26 04:50:22.892 Connecting to lcd server: 127.0.0.1:6545 (try 2 of 10)
2010-02-26 04:50:23.393 Connecting to lcd server: 127.0.0.1:6545 (try 3 of 10)
2010-02-26 04:50:23.893 Connecting to lcd server: 127.0.0.1:6545 (try 4 of 10)
2010-02-26 04:50:24.394 Connecting to lcd server: 127.0.0.1:6545 (try 5 of 10)
2010-02-26 04:50:24.895 Connecting to lcd server: 127.0.0.1:6545 (try 6 of 10)
2010-02-26 04:50:25.395 Connecting to lcd server: 127.0.0.1:6545 (try 7 of 10)
2010-02-26 04:50:25.896 Connecting to lcd server: 127.0.0.1:6545 (try 8 of 10)
2010-02-26 04:50:26.396 Connecting to lcd server: 127.0.0.1:6545 (try 9 of 10)
2010-02-26 04:50:26.897 Connecting to lcd server: 127.0.0.1:6545 (try 10 of 10)

```

 Regards,
 
 Dave

---

### Post by Neon Dusk on 2010-02-26
Some other things you could try :-

Change the frontend logging options in /etc/mythtv/session-setting to 'MYTHFRONTEND_OPTS="--verbose network,socket" to see if returns anything useful.

Disable the automatic frontend start to see if you still have the same issue when the frontend is maually started . If you do you could manually start mythlcdserver before starting the frontend (this will also allow you to use the mythlcdserver --verbose option to get detailed output)

---

### Post by rodercot on 2010-02-26
> **Neon Dusk said:**
> Some other things you could try :-

Change the frontend logging options in /etc/mythtv/session-setting to 'MYTHFRONTEND_OPTS="--verbose network,socket" to see if returns anything useful.

Disable the automatic frontend start to see if you still have the same issue when the frontend is maually started . If you do you could manually start mythlcdserver before starting the frontend (this will also allow you to use the mythlcdserver --verbose option to get detailed output)

 I will try and report back, I did a complete fresh install this morning and only did the first set of updates, never updated my repos or myth repos for myth updates and tried the options listed and none of them work. 

 rgds,

 Dave

---

### Post by rodercot on 2010-02-26
The extra logging options do not provide any further info. but if I open two terminals and start mythlcdserver in one I get this.

 ```
xbmc@feantecion:~$ mythlcdserver
2010-02-26 12:51:12.165 Using runtime prefix = /usr
2010-02-26 12:51:12.165 Using configuration directory = /home/xbmc/.mythtv
2010-02-26 12:51:12.166 Empty LocalHostName.
2010-02-26 12:51:12.187 New DB connection, total: 1
2010-02-26 12:51:17.239 Closing DB connection named 'DBManager0'
2010-02-26 12:51:22.304 Using protocol version 50

```

 And then in the other terminal I start mythfrontend i get this and it connects and works.

 ```
xbmc@feantecion:~$ mythfrontend
2010-02-26 12:52:08.075 mythfrontend version: branches/release-0-22-fixes [23604] www.mythtv.org
2010-02-26 12:52:08.113 Using runtime prefix = /usr
2010-02-26 12:52:08.113 Using configuration directory = /home/xbmc/.mythtv
2010-02-26 12:52:08.813 Empty LocalHostName.
2010-02-26 12:52:08.813 Using localhost value of feantecion
2010-02-26 12:52:08.814 Testing network connectivity to '192.168.1.199'
2010-02-26 12:52:08.835 New DB connection, total: 1
2010-02-26 12:52:13.892 Connected to database 'mythconverg' at host: 192.168.1.199
2010-02-26 12:52:13.893 Closing DB connection named 'DBManager0'
2010-02-26 12:52:13.950 ScreenSaverX11Private: Gnome screen saver support enabled
2010-02-26 12:52:13.952 DPMS is active.
2010-02-26 12:52:13.974 Primary screen: 0.
2010-02-26 12:52:19.024 Connected to database 'mythconverg' at host: 192.168.1.199
2010-02-26 12:52:19.026 Using screen 0, 1920x1080 at 0,0
2010-02-26 12:52:19.080 MythUI Image Cache size set to 20971520 bytes
2010-02-26 12:52:19.081 Enabled verbose msgs:  important general
2010-02-26 12:52:19.116 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2010-02-26 12:52:19.120 New DB connection, total: 2
2010-02-26 12:52:19.130 Primary screen: 0.
2010-02-26 12:52:19.131 Using screen 0, 1920x1080 at 0,0
2010-02-26 12:52:19.168 Using theme base resolution of 1280x720
2010-02-26 12:52:19.200 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/xbmc/.mythtv/lircrc' config
2010-02-26 12:52:19.200 JoystickMenuThread Error: Joystick disabled - Failed to read /home/xbmc/.mythtv/joystickmenurc
2010-02-26 12:52:19.877 Using the OpenGL painter
2010-02-26 12:52:20.375 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-02-26 12:52:20.417 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-02-26 12:52:20.477 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-02-26 12:52:20.478 Unable to load window 'backgroundwindow' from base
2010-02-26 12:52:20.483 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-26 12:52:21.430 Desktop video mode: 1920x1080 59.9413 Hz
2010-02-26 12:52:21.696 Registering Internal as a media playback plugin.
2010-02-26 12:52:21.758 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-02-26 12:52:21.837 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-02-26 12:52:21.845 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-02-26 12:52:21.852 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-02-26 12:52:21.866 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-02-26 12:52:21.992 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-02-26 12:52:21.996 Found mainmenu.xml for theme 'Mythbuntu'
2010-02-26 12:52:23.219 Using NV NPOT texture extension
2010-02-26 12:52:23.631 MythContext: Connecting to backend server: 192.168.1.199:6543 (try 1 of 1)
2010-02-26 12:52:23.631 Using protocol version 50
2010-02-26 12:52:24.173 Connected to database 'mythconverg' at host: 192.168.1.199

```

 so it looks like mythlcdserver is not starting at all when the frontend starts automatically on a cold bootup but starts the 2nd time around with the system already up.

 Regards,

 Dave

---

### Post by rodercot on 2010-02-26
AH! I got some -verbose messages here. Is this a permissions issue... here are few lines it goes on 10 times.. ofcourse.

 ```
2010-02-26 13:15:49.677 Starting mythlcdserver
2010-02-26 13:15:50.184 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2010-02-26 13:15:50.184 MythSocket(a040a88:21): new socket
2010-02-26 13:15:50.184 MythSocketThread: readyread thread start
2010-02-26 13:15:50.185 MythSocket(a040a88:21): UpRef: 1
2010-02-26 13:15:50.185 MythSocket(a040a88:21): attempting connect() to (127.0.0.1:6545)
2010-02-26 13:15:50.185 MythSocket(a040a88:21): connect() failed (ConnectionRefused)
2010-02-26 13:15:50.685 Connecting to lcd server: 127.0.0.1:6545 (try 2 of 10)
2010-02-26 13:15:50.686 MythSocket(a040a88:21): DownRef: 0
2010-02-26 13:15:50.686 MythSocket(ffffffffb020fdd8:26): new socket
2010-02-26 13:15:50.686 MythSocket(ffffffffb020fdd8:26): UpRef: 1
2010-02-26 13:15:50.686 MythSocket(ffffffffb020fdd8:26): attempting connect() to (127.0.0.1:6545)
2010-02-26 13:15:50.686 MythSocket(ffffffffb020fdd8:26): connect() failed (ConnectionRefused)

```

 Dave

---

### Post by ian dobson on 2010-02-26
Hi,

No, it looks as if LCDd takes a long time to start and mythlcd is trying to contact it before it's up and running.

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-26
> **ian dobson said:**
> Hi,

No, it looks as if LCDd takes a long time to start and mythlcd is trying to contact it before it's up and running.

Regards
Ian Dobson

 Well that makes no sense Ian, as I have tried the rc.d defaults as low as 10 and the lcd just sits On the server screen with no clients waiting until myth starts and why would it work if I start mythlcdserver session prior to starting mythfrontend. 

 Dave

---

### Post by ian dobson on 2010-02-27
Hi rodercot,

My replay was for your post #32. A connection refused error means that no server is listening on the port, or it's already in use if the server only supports one connection.

Could you enable verbose logging for mythfrontend and post the full log here. This sounds alot like a race condition.

Edit: If there's a way to add dubug/verbose messaging to LCDd then please add it and add the output here.

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-27
Well here it is that is a lot of information to view, I have X out the DB ip address and password. I will have a look in the syslog and see if there is anything in there for the LCD process. I set it to report there from the LCDd.conf file. One setting in the LCDd.conf file has me confused there is a User=nobody which is uncommented and it says to set a user if you want LCdd to run other than root, why would it be uncommented by default.

One other thing that has me a bit stumped is my /etc/hosts file has this 

127.0.0.1   Localhost
127.0.1.1   frontendname

 should my frontends name not be the localhost as well.

 If you see a way from this to speed up mythfrontend startup please advise other than the obvious LCDd issues.

 ```
Starting mythfrontend.real..
2010-02-27 07:49:43.418 mythfrontend version: branches/release-0-22-fixes [23604] www.mythtv.org
2010-02-27 07:49:43.419 (old)Settings::ReadSettings(settings.txt) - No such file
2010-02-27 07:49:43.420 Using runtime prefix = /usr
2010-02-27 07:49:43.420 Using configuration directory = /home/xbmc/.mythtv
2010-02-27 07:49:43.420 UPnp - Constructor
2010-02-27 07:49:43.420 MediaRenderer::Begin
2010-02-27 07:49:43.442 ThreadPool:AddWorkerThread - HTTP_WorkerThread
2010-02-27 07:49:43.443 HttpServer() - SharePath = /usr/share/mythtv/
2010-02-27 07:49:43.482 UPnp::Initialize - Begin
2010-02-27 07:49:43.482 UPnp::Initialize - Starting TaskQueue
2010-02-27 07:49:43.483 UPnp::Initialize - Creating SSDP Thread at port 6547
2010-02-27 07:49:43.485 MSocketDevice::setBlocking(false)
2010-02-27 07:49:43.485 MSocketDevice::setBlocking(false)
2010-02-27 07:49:43.485 MSocketDevice::setBlocking(false)
2010-02-27 07:49:43.485 UPnp::Initialize - End
2010-02-27 07:49:43.485 MediaRenderer::Creating UPnp Description
2010-02-27 07:49:43.486 MediaRenderer::Registering MythFEXML Service.
2010-02-27 07:49:43.486 MediaRenderer::Registering CMGR Service.
2010-02-27 07:49:43.486 UPnp::Start - Starting SSDP Thread (Multicast)
2010-02-27 07:49:43.487 UPnp::Start - Enabling Notifications
2010-02-27 07:49:43.487 SSDP::EnableNotifications() - creating new task
2010-02-27 07:49:43.487 SSDP::EnableNotifications() - sending NTS_byebye
2010-02-27 07:49:43.487 LookupUDN(urn:schemas-upnp-org:device:MediaRenderer:1) sName=UPnP/UDN/MediaRenderer, sUDN=5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
2010-02-27 07:49:43.488 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.489 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::upnp:rootdevice
Cache  =max-age=3600
2010-02-27 07:49:43.628 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.629 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::upnp:rootdevice
Cache  =max-age=3600
2010-02-27 07:49:43.629 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.629 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
Cache  =max-age=3600
2010-02-27 07:49:43.782 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.782 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
Cache  =max-age=3600
2010-02-27 07:49:43.783 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.783 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-02-27 07:49:43.993 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.994 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-02-27 07:49:43.994 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:43.994 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-02-27 07:49:44.012 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.013 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-02-27 07:49:44.013 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.013 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-02-27 07:49:44.190 MSocketDevice::close: Closed socket 19
2010-02-27 07:49:44.191 SSDP::EnableNotifications() - sending NTS_alive
2010-02-27 07:49:44.191 SSDP::EnableNotifications() - Task added to UPnP queue
2010-02-27 07:49:44.191 UPnp::Start - Returning
2010-02-27 07:49:44.191 MediaRenderer::End
2010-02-27 07:49:44.191 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.192 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-02-27 07:49:44.215 (old)Settings::ReadSettings(settings.txt) - No such file
2010-02-27 07:49:44.216 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBHostName' = 'xxx.xxx.x.xxx'.
2010-02-27 07:49:44.217 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-02-27 07:49:44.217 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-02-27 07:49:44.217 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-02-27 07:49:44.217 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt) - 'DBPassword' = 'xxxxxxxx'.
2010-02-27 07:49:44.217 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) - No such file
2010-02-27 07:49:44.217 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt) - 'DBHostName' = 'xxx.xxx.x.xxx'.
2010-02-27 07:49:44.218 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt) - 'DBUserName' = 'mythtv'.
2010-02-27 07:49:44.218 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt) - 'DBName' = 'mythconverg'.
2010-02-27 07:49:44.218 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt) - 'DBType' = 'QMYSQL3'.
2010-02-27 07:49:44.218 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt) - 'DBPassword' = 'xxxxxxxx'.
2010-02-27 07:49:44.218 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-02-27 07:49:44.218 Empty LocalHostName.
2010-02-27 07:49:44.219 Using localhost value of feantecion
2010-02-27 07:49:44.219 MCP::DefaultUPnP() - No default UPnP backend
2010-02-27 07:49:44.219 Testing network connectivity to '192.168.1.199'
2010-02-27 07:49:44.242 New DB connection, total: 1
2010-02-27 07:49:44.284 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.284 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::upnp:rootdevice
Cache  =max-age=3600
2010-02-27 07:49:44.512 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.512 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =upnp:rootdevice
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::upnp:rootdevice
Cache  =max-age=3600
2010-02-27 07:49:44.513 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.513 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
Cache  =max-age=3600
2010-02-27 07:49:44.688 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.689 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
Cache  =max-age=3600
2010-02-27 07:49:44.689 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.689 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-02-27 07:49:44.816 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.816 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-02-27 07:49:44.817 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:44.817 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-02-27 07:49:45.051 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:45.051 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-02-27 07:49:45.051 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:45.051 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-02-27 07:49:45.096 MSocketDevice::close: Closed socket 20
2010-02-27 07:49:45.096 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:49:45.096 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:alive
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-02-27 07:49:53.107 Connected to database 'mythconverg' at host: 192.168.1.199
2010-02-27 07:49:53.108 Closing DB connection named 'DBManager0'
2010-02-27 07:49:53.138 ScreenSaverX11Private: Gnome screen saver support enabled
2010-02-27 07:49:53.140 DPMS is active.
2010-02-27 07:49:53.162 Primary screen: 0.
2010-02-27 07:49:58.211 Connected to database 'mythconverg' at host: 192.168.1.199
2010-02-27 07:49:58.213 Using screen 0, 1920x1080 at 0,0
2010-02-27 07:49:58.260 MythUI Image Cache size set to 20971520 bytes
2010-02-27 07:49:58.260 user: 1000 effective user: 1000 before privileged thread
2010-02-27 07:49:58.260 user: 1000 effective user: 1000 after privileged thread
2010-02-27 07:49:58.260 user: 1000 effective user: 1000 run_priv_thread
2010-02-27 07:49:58.261 Enabled verbose msgs: all nodatabase
2010-02-27 07:49:58.264 lcddevice: An LCD object now exists (LCD() was called)
2010-02-27 07:49:58.264 lcddevice: connecting to host: 127.0.0.1 - port: 6545
2010-02-27 07:49:58.291 Starting mythlcdserver
2010-02-27 07:49:58.909 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2010-02-27 07:49:58.909 MythSocket(9db2dc8:21): new socket
2010-02-27 07:49:58.910 MythSocketThread: readyread thread start
2010-02-27 07:49:58.910 ProcessAddRemoveQueues
2010-02-27 07:49:58.910 Construct FD_SET
2010-02-27 07:49:58.910 Empty FD_SET, sleeping
2010-02-27 07:49:58.910 MythSocket(9db2dc8:21): UpRef: 1
2010-02-27 07:49:58.910 Empty FD_SET, woken up
2010-02-27 07:49:58.910 ProcessAddRemoveQueues
2010-02-27 07:49:58.910 MythSocket(9db2dc8:21): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:49:58.911 Construct FD_SET
2010-02-27 07:49:58.911 Empty FD_SET, sleeping
2010-02-27 07:49:58.911 MythSocket(9db2dc8:21): connect() failed (ConnectionRefused)
2010-02-27 07:49:59.411 Connecting to lcd server: 127.0.0.1:6545 (try 2 of 10)
2010-02-27 07:49:59.411 MythSocket(9db2dc8:21): DownRef: 0
2010-02-27 07:49:59.411 Empty FD_SET, woken up
2010-02-27 07:49:59.411 MythSocket(ffffffffafa015f0:26): new socket
2010-02-27 07:49:59.411 ProcessAddRemoveQueues
2010-02-27 07:49:59.412 Construct FD_SET
2010-02-27 07:49:59.412 Empty FD_SET, sleeping
2010-02-27 07:49:59.412 MythSocket(ffffffffafa015f0:26): UpRef: 1
2010-02-27 07:49:59.412 Empty FD_SET, woken up
2010-02-27 07:49:59.412 MythSocket(ffffffffafa015f0:26): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:49:59.412 ProcessAddRemoveQueues
2010-02-27 07:49:59.412 Construct FD_SET
2010-02-27 07:49:59.412 Empty FD_SET, sleeping
2010-02-27 07:49:59.412 MythSocket(ffffffffafa015f0:26): connect() failed (ConnectionRefused)
2010-02-27 07:49:59.912 Connecting to lcd server: 127.0.0.1:6545 (try 3 of 10)
2010-02-27 07:49:59.912 MythSocket(ffffffffafa015f0:26): DownRef: 0
2010-02-27 07:49:59.912 Empty FD_SET, woken up
2010-02-27 07:49:59.913 MythSocket(ffffffffafa019a0:27): new socket
2010-02-27 07:49:59.913 ProcessAddRemoveQueues
2010-02-27 07:49:59.913 Construct FD_SET
2010-02-27 07:49:59.913 Empty FD_SET, sleeping
2010-02-27 07:49:59.913 MythSocket(ffffffffafa019a0:27): UpRef: 1
2010-02-27 07:49:59.913 Empty FD_SET, woken up
2010-02-27 07:49:59.913 MythSocket(ffffffffafa019a0:27): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:49:59.913 ProcessAddRemoveQueues
2010-02-27 07:49:59.913 Construct FD_SET
2010-02-27 07:49:59.913 MythSocket(ffffffffafa019a0:27): connect() failed (ConnectionRefused)
2010-02-27 07:49:59.913 Empty FD_SET, sleeping
2010-02-27 07:50:00.413 Connecting to lcd server: 127.0.0.1:6545 (try 4 of 10)
2010-02-27 07:50:00.414 MythSocket(ffffffffafa019a0:27): DownRef: 0
2010-02-27 07:50:00.414 Empty FD_SET, woken up
2010-02-27 07:50:00.414 MythSocket(ffffffffafa01b50:28): new socket
2010-02-27 07:50:00.414 ProcessAddRemoveQueues
2010-02-27 07:50:00.414 Construct FD_SET
2010-02-27 07:50:00.414 Empty FD_SET, sleeping
2010-02-27 07:50:00.414 MythSocket(ffffffffafa01b50:28): UpRef: 1
2010-02-27 07:50:00.414 Empty FD_SET, woken up
2010-02-27 07:50:00.414 MythSocket(ffffffffafa01b50:28): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:00.414 ProcessAddRemoveQueues
2010-02-27 07:50:00.414 Construct FD_SET
2010-02-27 07:50:00.414 MythSocket(ffffffffafa01b50:28): connect() failed (ConnectionRefused)
2010-02-27 07:50:00.414 Empty FD_SET, sleeping
2010-02-27 07:50:00.915 Connecting to lcd server: 127.0.0.1:6545 (try 5 of 10)
2010-02-27 07:50:00.915 MythSocket(ffffffffafa01b50:28): DownRef: 0
2010-02-27 07:50:00.915 Empty FD_SET, woken up
2010-02-27 07:50:00.915 MythSocket(ffffffffafa01c50:29): new socket
2010-02-27 07:50:00.915 ProcessAddRemoveQueues
2010-02-27 07:50:00.915 Construct FD_SET
2010-02-27 07:50:00.915 Empty FD_SET, sleeping
2010-02-27 07:50:00.915 MythSocket(ffffffffafa01c50:29): UpRef: 1
2010-02-27 07:50:00.915 Empty FD_SET, woken up
2010-02-27 07:50:00.915 MythSocket(ffffffffafa01c50:29): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:00.916 ProcessAddRemoveQueues
2010-02-27 07:50:00.916 Construct FD_SET
2010-02-27 07:50:00.916 MythSocket(ffffffffafa01c50:29): connect() failed (ConnectionRefused)
2010-02-27 07:50:00.916 Empty FD_SET, sleeping
2010-02-27 07:50:01.416 Connecting to lcd server: 127.0.0.1:6545 (try 6 of 10)
2010-02-27 07:50:01.416 MythSocket(ffffffffafa01c50:29): DownRef: 0
2010-02-27 07:50:01.416 Empty FD_SET, woken up
2010-02-27 07:50:01.416 MythSocket(ffffffffafa01f68:30): new socket
2010-02-27 07:50:01.416 ProcessAddRemoveQueues
2010-02-27 07:50:01.416 Construct FD_SET
2010-02-27 07:50:01.417 Empty FD_SET, sleeping
2010-02-27 07:50:01.417 MythSocket(ffffffffafa01f68:30): UpRef: 1
2010-02-27 07:50:01.417 Empty FD_SET, woken up
2010-02-27 07:50:01.417 MythSocket(ffffffffafa01f68:30): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:01.417 ProcessAddRemoveQueues
2010-02-27 07:50:01.417 Construct FD_SET
2010-02-27 07:50:01.417 MythSocket(ffffffffafa01f68:30): connect() failed (ConnectionRefused)
2010-02-27 07:50:01.417 Empty FD_SET, sleeping
2010-02-27 07:50:01.917 Connecting to lcd server: 127.0.0.1:6545 (try 7 of 10)
2010-02-27 07:50:01.917 MythSocket(ffffffffafa01f68:30): DownRef: 0
2010-02-27 07:50:01.917 Empty FD_SET, woken up
2010-02-27 07:50:01.917 MythSocket(ffffffffafa02130:31): new socket
2010-02-27 07:50:01.917 ProcessAddRemoveQueues
2010-02-27 07:50:01.918 Construct FD_SET
2010-02-27 07:50:01.918 Empty FD_SET, sleeping
2010-02-27 07:50:01.918 MythSocket(ffffffffafa02130:31): UpRef: 1
2010-02-27 07:50:01.918 Empty FD_SET, woken up
2010-02-27 07:50:01.918 MythSocket(ffffffffafa02130:31): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:01.918 ProcessAddRemoveQueues
2010-02-27 07:50:01.918 Construct FD_SET
2010-02-27 07:50:01.918 MythSocket(ffffffffafa02130:31): connect() failed (ConnectionRefused)
2010-02-27 07:50:01.918 Empty FD_SET, sleeping
2010-02-27 07:50:02.418 Connecting to lcd server: 127.0.0.1:6545 (try 8 of 10)
2010-02-27 07:50:02.419 MythSocket(ffffffffafa02130:31): DownRef: 0
2010-02-27 07:50:02.419 Empty FD_SET, woken up
2010-02-27 07:50:02.419 MythSocket(ffffffffafa02310:32): new socket
2010-02-27 07:50:02.419 ProcessAddRemoveQueues
2010-02-27 07:50:02.419 Construct FD_SET
2010-02-27 07:50:02.419 Empty FD_SET, sleeping
2010-02-27 07:50:02.419 MythSocket(ffffffffafa02310:32): UpRef: 1
2010-02-27 07:50:02.419 Empty FD_SET, woken up
2010-02-27 07:50:02.419 MythSocket(ffffffffafa02310:32): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:02.419 ProcessAddRemoveQueues
2010-02-27 07:50:02.419 Construct FD_SET
2010-02-27 07:50:02.419 MythSocket(ffffffffafa02310:32): connect() failed (ConnectionRefused)
2010-02-27 07:50:02.419 Empty FD_SET, sleeping
2010-02-27 07:50:02.920 Connecting to lcd server: 127.0.0.1:6545 (try 9 of 10)
2010-02-27 07:50:02.920 MythSocket(ffffffffafa02310:32): DownRef: 0
2010-02-27 07:50:02.920 Empty FD_SET, woken up
2010-02-27 07:50:02.920 MythSocket(9db60e0:33): new socket
2010-02-27 07:50:02.920 ProcessAddRemoveQueues
2010-02-27 07:50:02.920 Construct FD_SET
2010-02-27 07:50:02.920 Empty FD_SET, sleeping
2010-02-27 07:50:02.920 MythSocket(9db60e0:33): UpRef: 1
2010-02-27 07:50:02.920 Empty FD_SET, woken up
2010-02-27 07:50:02.920 MythSocket(9db60e0:33): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:02.920 ProcessAddRemoveQueues
2010-02-27 07:50:02.921 Construct FD_SET
2010-02-27 07:50:02.921 MythSocket(9db60e0:33): connect() failed (ConnectionRefused)
2010-02-27 07:50:02.921 Empty FD_SET, sleeping
2010-02-27 07:50:03.421 Connecting to lcd server: 127.0.0.1:6545 (try 10 of 10)
2010-02-27 07:50:03.421 MythSocket(9db60e0:33): DownRef: 0
2010-02-27 07:50:03.421 Empty FD_SET, woken up
2010-02-27 07:50:03.421 MythSocket(9d23450:34): new socket
2010-02-27 07:50:03.421 ProcessAddRemoveQueues
2010-02-27 07:50:03.421 Construct FD_SET
2010-02-27 07:50:03.421 Empty FD_SET, sleeping
2010-02-27 07:50:03.421 MythSocket(9d23450:34): UpRef: 1
2010-02-27 07:50:03.422 Empty FD_SET, woken up
2010-02-27 07:50:03.422 MythSocket(9d23450:34): attempting connect() to (127.0.0.1:6545)
2010-02-27 07:50:03.422 ProcessAddRemoveQueues
2010-02-27 07:50:03.422 Construct FD_SET
2010-02-27 07:50:03.422 MythSocket(9d23450:34): connect() failed (ConnectionRefused)
2010-02-27 07:50:03.422 Empty FD_SET, sleeping
2010-02-27 07:50:03.922 lcddevice: An LCD device is being snuffed out of existence (~LCD() was called)
2010-02-27 07:50:03.922 MythSocket(9d23450:34): DownRef: 0
2010-02-27 07:50:03.922 Empty FD_SET, woken up
2010-02-27 07:50:03.922 ProcessAddRemoveQueues
2010-02-27 07:50:03.922 lcddevice: An LCD object now exists (LCD() was called)
2010-02-27 07:50:03.922 Construct FD_SET
2010-02-27 07:50:03.923 Empty FD_SET, sleeping
2010-02-27 07:50:03.947 No theme dir: /home/xbmc/.mythtv/themes/Mythbuntu
2010-02-27 07:50:03.950 Primary screen: 0.
2010-02-27 07:50:03.951 Using screen 0, 1920x1080 at 0,0
2010-02-27 07:50:03.951 (old)Settings::ReadSettings(settings.txt) - No such file
2010-02-27 07:50:03.952 No theme dir: /home/xbmc/.mythtv/themes/Mythbuntu
2010-02-27 07:50:03.984 Using theme base resolution of 1280x720
2010-02-27 07:50:03.990 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'BackgroundColor' = '#404040'.
2010-02-27 07:50:03.990 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ForegroundColor' = 'white'.
2010-02-27 07:50:03.990 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'BackgroundPixmap' = 'background.png'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Comedy' = 'DarkOrchid'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Animals' = 'ForestGreen'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Nature' = 'SprintGreen'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_SciFi' = 'DarkBlue'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Horror' = 'firebrick3'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Action' = 'maroon'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Game' = 'orchid'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Children's' = 'MediumSlateBlue'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Edu' = 'CornflowerBlue'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Adult' = 'thistle3'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Musical' = 'turquoise3'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_News' = 'DarkOrange3'.
2010-02-27 07:50:03.991 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Reality' = 'sienna'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Cooking' = 'tan3'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Doc' = 'goldenrod'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Sports' = 'DarkCyan'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Mystery' = 'SlateGrey'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Drama' = 'rosybrown3'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Classic' = 'grey62'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Crime' = 'MediumVioletRed'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'Cat_Talk' = 'MediumTurquoise'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveForeground' = '#FFFFFF'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveButton' = '#404040'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveLight' = '#606060'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveMidlight' = '#505050'.
2010-02-27 07:50:03.992 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveDark' = '#202020'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveMid' = '#303030'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveText' = '#FFFFFF'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveBrightText' = '#FFFFFF'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveButtonText' = '#FFFFFF'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveBase' = '#202020'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveBackground' = '#404040'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveShadow' = '#000000'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveHighlight' = '#808080'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'ActiveHighlightedText' = '#FFFFFF'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveForeground' = '#FFFFFF'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveButton' = '#254A55'.
2010-02-27 07:50:03.993 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveLight' = '#435B70'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveMidlight' = '#324C57'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveDark' = '#204150'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveMid' = '#214351'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveText' = '#FFFFFF'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveBrightText' = '#FFFFFF'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveButtonText' = '#ffffff'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveBase' = '#254E56'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveBackground' = '#264F57'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveShadow' = '#000000'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveHighlight' = '#2D733F'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'InactiveHighlightedText' = '#000000'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledForeground' = '#FFFFFF'.
2010-02-27 07:50:03.994 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledButton' = '#404040'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledLight' = '#24385C'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledMidlight' = '#192944'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledDark' = '#1A2E53'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledMid' = '#1B2D53'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledText' = '#4F535B'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledBrightText' = '#71757E'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledButtonText' = '#4F535B'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledBase' = '#1E3356'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledBackground' = '#1E3356'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledShadow' = '#000000'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledHighlight' = '#274E57'.
2010-02-27 07:50:03.995 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'DisabledHighlightedText' = '#ffffff'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'curTimeChan_bgColor' = '#8f2813'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'curTimeChan_fgColor' = '#ffffff'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'date_bgColor' = '#0f2e8f'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'date_dsColor' = '#000000'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'date_fgColor' = '#ffffff'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'chan_bgColor' = '#0f2f5a'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'chan_dsColor' = '#000000'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'chan_fgColor' = '#ffffff'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'time_bgColor' = '#0f2e8f'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'time_dsColor' = '#000000'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'time_fgColor' = '#ffffff'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'prog_bgColor' = '#2d587b'.
2010-02-27 07:50:03.996 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'prog_fgColor' = '#ffffff'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'progLine_Color' = '#104064'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'progArrow_Color' = '#ffffff'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'progArrow_Type' = '0'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'curProg_bgColor' = '#85a5bc'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'curRecProg_bgColor' = '#bc4c32'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'curProg_dsColor' = '#000000'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'curProg_fgColor' = '#eefb92'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'misChanIcon_bgColor' = '#000000'.
2010-02-27 07:50:03.997 (old)Settings::ReadSettings(/usr/share/mythtv/themes/Mythbuntu/qtlook.txt) - 'misChanIcon_fgColor' = '#ffffff'.
2010-02-27 07:50:04.018 LIRC: Successfully initialized '/var/run/lirc/lircd' using '/home/xbmc/.mythtv/lircrc' config
2010-02-27 07:50:04.019 JoystickMenuThread Error: Joystick disabled - Failed to read /home/xbmc/.mythtv/joystickmenurc
2010-02-27 07:50:04.651 Using the OpenGL painter
2010-02-27 07:50:04.797 Keeping cache dir: /home/xbmc/.mythtv/themecache/Terra.1920.1080
2010-02-27 07:50:04.864 MythUIImage(165715232): Load(), spawning thread to load 'shared/lb-check-empty.png'
2010-02-27 07:50:04.864 MythUIImage::LoadImage(165715232, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:04.864 MythUIImage(-1348065896): Load(), spawning thread to load 'shared/lb-check-half.png'
2010-02-27 07:50:04.865 MythUIImage::LoadImage(-1348065896, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:04.865 MythUIImage(-1383920416): Load(), spawning thread to load 'shared/lb-check-full.png'
2010-02-27 07:50:04.866 MythUIImage(-1383919488): Load(), spawning thread to load 'shared/lb-arrow.png'
2010-02-27 07:50:04.866 MythUIImage::LoadImage(-1383919488, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:04.867 MythUIImage::LoadImage(-1383920416, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:04.868 MythUIImage(166363064): Load(), spawning thread to load 'shared/lb-check-empty.png'
2010-02-27 07:50:04.868 MythUIImage(166364800): Load(), spawning thread to load 'shared/lb-check-half.png'
2010-02-27 07:50:04.868 MythUIImage(166367040): Load(), spawning thread to load 'shared/lb-check-full.png'
2010-02-27 07:50:04.869 MythUIImage(166368632): Load(), spawning thread to load 'shared/lb-arrow.png'
2010-02-27 07:50:04.870 MythUIImage(-1383909000): Load(), spawning thread to load 'shared/lb-check-empty.png'
2010-02-27 07:50:04.870 MythUIImage(-1383833864): Load(), spawning thread to load 'shared/lb-check-half.png'
2010-02-27 07:50:04.870 MythUIImage(166370280): Load(), spawning thread to load 'shared/lb-check-full.png'
2010-02-27 07:50:04.871 MythUIImage(166371928): Load(), spawning thread to load 'shared/lb-arrow.png'
2010-02-27 07:50:04.871 MythUIImage(-1383829792): Load(), spawning thread to load 'shared/uparrow.png'
2010-02-27 07:50:04.872 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-check-empty.png---1x-1.png: :3600:
2010-02-27 07:50:04.873 MythUIHelper::CacheImage : Cache Count = :1: size :3600:
2010-02-27 07:50:04.873 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.873 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-check-full.png---1x-1.png: :3600:
2010-02-27 07:50:04.873 MythUIImage(-1419770000): Load(), spawning thread to load 'shared/downarrow.png'
2010-02-27 07:50:04.873 MythUIImage::LoadImage(166363064, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:04.873 MythUIHelper::CacheImage : Cache Count = :2: size :3600:
2010-02-27 07:50:04.873 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.873 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-check-half.png---1x-1.png: :3600:
2010-02-27 07:50:04.874 MythUIHelper::CacheImage : Cache Count = :3: size :3600:
2010-02-27 07:50:04.874 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.874 MythUIImage::LoadImage(166367040, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:04.874 MythUIImage::LoadImage(166364800, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:04.874 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.874 MythUIImage(166378168): Load(), spawning thread to load 'shared/schedule_disabled.png'
2010-02-27 07:50:04.874 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.875 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-arrow.png---1x-1.png: :2304:
2010-02-27 07:50:04.875 MythUIImage::LoadImage(-1383909000, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:04.875 MythUIHelper::CacheImage : Cache Count = :4: size :2304:
2010-02-27 07:50:04.875 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.875 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.875 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.875 MythUIImage::LoadImage(166368632, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:04.875 MythUIImage::LoadImage(166370280, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:04.875 MythUIImage(-1419768440): Load(), spawning thread to load 'shared/schedule_conflict.png'
2010-02-27 07:50:04.875 MythUIImage::LoadImage(-1383833864, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:04.876 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.876 MythUIImage::LoadImage(-1383829792, shared/uparrow.png) Object upoff
2010-02-27 07:50:04.876 MythUIImage(-1419764848): Load(), spawning thread to load 'shared/schedule_other.png'
2010-02-27 07:50:04.876 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.876 MythUIImage::LoadImage(-1419770000, shared/downarrow.png) Object dnoff
2010-02-27 07:50:04.876 MythUIImage::LoadImage(166371928, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:04.877 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.877 MythUIImage(166380488): Load(), spawning thread to load 'shared/schedule_record.png'
2010-02-27 07:50:04.877 MythUIImage::LoadImage(166378168, shared/schedule_disabled.png) Object statusimage
2010-02-27 07:50:04.878 NOT IN RAM CACHE, Adding, and adding to size :shared-uparrow.png---1x-1.png: :8100:
2010-02-27 07:50:04.878 MythUIHelper::CacheImage : Cache Count = :5: size :8100:
2010-02-27 07:50:04.878 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.878 MythUIImage(-1419730512): Load(), spawning thread to load 'shared/schedule_recording.png'
2010-02-27 07:50:04.878 MythUIImage::LoadImage(-1419768440, shared/schedule_conflict.png) Object statusimage
2010-02-27 07:50:04.878 NOT IN RAM CACHE, Adding, and adding to size :shared-downarrow.png---1x-1.png: :8100:
2010-02-27 07:50:04.879 MythUIHelper::CacheImage : Cache Count = :6: size :8100:
2010-02-27 07:50:04.879 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.879 MythUIImage::LoadImage(-1419764848, shared/schedule_other.png) Object statusimage
2010-02-27 07:50:04.877 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.879 NOT IN RAM CACHE, Adding, and adding to size :shared-schedule_disabled.png---1x-1.png: :5476:
2010-02-27 07:50:04.880 MythUIHelper::CacheImage : Cache Count = :7: size :5476:
2010-02-27 07:50:04.880 MythUIImage::LoadImage(166380488, shared/schedule_record.png) Object statusimage
2010-02-27 07:50:04.880 MythUIImage::LoadImage found in cache :shared-schedule_disabled.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.880 MythUIImage(166413056): Load(), loading 'shared/schedule_disabled.png' in foreground
2010-02-27 07:50:04.880 MythUIImage::LoadImage(-1419730512, shared/schedule_recording.png) Object statusimage
2010-02-27 07:50:04.880 MythUIImage::LoadImage(166413056, shared/schedule_disabled.png) Object statusimage
2010-02-27 07:50:04.880 NOT IN RAM CACHE, Adding, and adding to size :shared-schedule_conflict.png---1x-1.png: :5476:
2010-02-27 07:50:04.880 MythUIHelper::CacheImage : Cache Count = :8: size :5476:
2010-02-27 07:50:04.881 MythUIImage::LoadImage found in cache :shared-schedule_conflict.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.881 MythUIImage::LoadImage found in cache :shared-schedule_disabled.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.881 MythUIImage(-1383807096): Load(), loading 'shared/schedule_conflict.png' in foreground
2010-02-27 07:50:04.882 MythUIImage::LoadImage(-1383807096, shared/schedule_conflict.png) Object statusimage
2010-02-27 07:50:04.882 MythUIImage::LoadImage found in cache :shared-schedule_conflict.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.882 MythUIImage(-1383774392): Load(), spawning thread to load 'shared/schedule_other.png'
2010-02-27 07:50:04.883 MythUIImage(166414728): Load(), spawning thread to load 'shared/schedule_record.png'
2010-02-27 07:50:04.883 MythUIImage(166273920): Load(), spawning thread to load 'shared/schedule_recording.png'
2010-02-27 07:50:04.884 MythUIImage(166279880): Load(), loading 'shared/schedule_disabled.png' in foreground
2010-02-27 07:50:04.884 MythUIImage::LoadImage(166279880, shared/schedule_disabled.png) Object statusimage
2010-02-27 07:50:04.884 MythUIImage::LoadImage found in cache :shared-schedule_disabled.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.885 MythUIImage(166280912): Load(), loading 'shared/schedule_conflict.png' in foreground
2010-02-27 07:50:04.885 MythUIImage::LoadImage(166280912, shared/schedule_conflict.png) Object statusimage
2010-02-27 07:50:04.885 MythUIImage::LoadImage found in cache :shared-schedule_conflict.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.885 MythUIImage(166383128): Load(), spawning thread to load 'shared/schedule_other.png'
2010-02-27 07:50:04.886 MythUIImage(166384912): Load(), spawning thread to load 'shared/schedule_record.png'
2010-02-27 07:50:04.886 MythUIImage(166387872): Load(), spawning thread to load 'shared/schedule_recording.png'
2010-02-27 07:50:04.887 MythUIImage(166391808): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:50:04.887 MythUIImage::LoadImage(166391808, shared/uparrow.png) Object upoff
2010-02-27 07:50:04.887 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.888 MythUIImage(166175536): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:50:04.888 MythUIImage::LoadImage(166175536, shared/downarrow.png) Object dnoff
2010-02-27 07:50:04.888 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.891 MythUIImage(166201016): Load(), spawning thread to load 'shared/checkbox_background_off.png'
2010-02-27 07:50:04.892 MythUIImage(166202592): Load(), spawning thread to load 'shared/checkbox_background_selected.png'
2010-02-27 07:50:04.892 MythUIImage(166206360): Load(), spawning thread to load 'shared/checkbox_halfcheck.png'
2010-02-27 07:50:04.893 MythUIImage(166329304): Load(), spawning thread to load 'shared/checkbox_fullcheck.png'
2010-02-27 07:50:04.894 MythUIImage(166339240): Load(), spawning thread to load 'shared/lb-rtarrow-reg.png'
2010-02-27 07:50:04.894 MythUIImage(166341248): Load(), spawning thread to load 'shared/lb-rtarrow-sel.png'
2010-02-27 07:50:04.895 MythUIImage(166342888): Load(), spawning thread to load 'shared/lb-ltarrow-reg.png'
2010-02-27 07:50:04.896 MythUIImage(166345464): Load(), spawning thread to load 'shared/lb-ltarrow-sel.png'
2010-02-27 07:50:04.896 NOT IN RAM CACHE, Adding, and adding to size :shared-schedule_recording.png---1x-1.png: :5476:
2010-02-27 07:50:04.896 MythUIHelper::CacheImage : Cache Count = :9: size :5476:
2010-02-27 07:50:04.896 MythUIImage::LoadImage found in cache :shared-schedule_recording.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.896 NOT IN RAM CACHE, Adding, and adding to size :shared-schedule_record.png---1x-1.png: :5476:
2010-02-27 07:50:04.897 MythUIHelper::CacheImage : Cache Count = :10: size :5476:
2010-02-27 07:50:04.897 MythUIImage::LoadImage found in cache :shared-schedule_record.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.897 MythUIImage::LoadImage(166273920, shared/schedule_recording.png) Object statusimage
2010-02-27 07:50:04.897 MythUIImage::LoadImage(166414728, shared/schedule_record.png) Object statusimage
2010-02-27 07:50:04.897 MythUIImage::LoadImage found in cache :shared-schedule_recording.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.897 MythUIImage::LoadImage found in cache :shared-schedule_record.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.898 MythUIImage::LoadImage(166384912, shared/schedule_record.png) Object statusimage
2010-02-27 07:50:04.898 MythUIImage::LoadImage found in cache :shared-schedule_record.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.898 MythUIImage::LoadImage(166387872, shared/schedule_recording.png) Object statusimage
2010-02-27 07:50:04.898 NOT IN RAM CACHE, Adding, and adding to size :shared-schedule_other.png---1x-1.png: :5476:
2010-02-27 07:50:04.898 MythUIHelper::CacheImage : Cache Count = :11: size :5476:
2010-02-27 07:50:04.898 MythUIImage::LoadImage found in cache :shared-schedule_other.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.898 MythUIImage::LoadImage found in cache :shared-schedule_recording.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.899 MythUIImage::LoadImage(166201016, shared/checkbox_background_off.png) Object background
2010-02-27 07:50:04.899 MythUIImage::LoadImage(166202592, shared/checkbox_background_selected.png) Object background
2010-02-27 07:50:04.899 MythUIImage::LoadImage(-1383774392, shared/schedule_other.png) Object statusimage
2010-02-27 07:50:04.899 MythUIImage(-1419760120): Load(), spawning thread to load 'shared/lb-rtarrow-reg.png'
2010-02-27 07:50:04.899 MythUIImage::LoadImage found in cache :shared-schedule_other.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.900 MythUIImage(-1419756400): Load(), spawning thread to load 'shared/lb-rtarrow-sel.png'
2010-02-27 07:50:04.900 MythUIImage::LoadImage(166206360, shared/checkbox_halfcheck.png) Object background
2010-02-27 07:50:04.900 MythUIImage::LoadImage(166383128, shared/schedule_other.png) Object statusimage
2010-02-27 07:50:04.900 MythUIImage(-1383772320): Load(), spawning thread to load 'shared/lb-ltarrow-reg.png'
2010-02-27 07:50:04.901 NOT IN RAM CACHE, Adding, and adding to size :shared-checkbox_background_off.png---1x-1.png: :1936:
2010-02-27 07:50:04.901 MythUIHelper::CacheImage : Cache Count = :12: size :1936:
2010-02-27 07:50:04.901 MythUIImage::LoadImage found in cache :shared-checkbox_background_off.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.901 MythUIImage(-1383770872): Load(), spawning thread to load 'shared/lb-ltarrow-sel.png'
2010-02-27 07:50:04.901 MythUIImage::LoadImage(166329304, shared/checkbox_fullcheck.png) Object mark
2010-02-27 07:50:04.904 MythUIImage::LoadImage found in cache :shared-schedule_other.png---1x-1.png: RefCount = 4
2010-02-27 07:50:04.904 NOT IN RAM CACHE, Adding, and adding to size :shared-checkbox_halfcheck.png---1x-1.png: :1764:
2010-02-27 07:50:04.904 MythUIHelper::CacheImage : Cache Count = :13: size :1764:
2010-02-27 07:50:04.904 MythUIImage::LoadImage found in cache :shared-checkbox_halfcheck.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.904 MythUIImage::LoadImage(166341248, shared/lb-rtarrow-sel.png) Object dnoff
2010-02-27 07:50:04.904 MythUIImage::LoadImage(166339240, shared/lb-rtarrow-reg.png) Object dnon
2010-02-27 07:50:04.905 NOT IN RAM CACHE, Adding, and adding to size :shared-checkbox_fullcheck.png---1x-1.png: :1764:
2010-02-27 07:50:04.905 MythUIHelper::CacheImage : Cache Count = :14: size :1764:
2010-02-27 07:50:04.905 MythUIImage::LoadImage found in cache :shared-checkbox_fullcheck.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.905 MythUIImage::LoadImage(166342888, shared/lb-ltarrow-reg.png) Object upon
2010-02-27 07:50:04.931 NOT IN RAM CACHE, Adding, and adding to size :shared-checkbox_background_selected.png---1x-1.png: :1936:
2010-02-27 07:50:04.931 MythUIHelper::CacheImage : Cache Count = :15: size :1936:
2010-02-27 07:50:04.931 MythUIImage::LoadImage found in cache :shared-checkbox_background_selected.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.931 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-rtarrow-reg.png---1x-1.png: :1944:
2010-02-27 07:50:04.931 MythUIImage::LoadImage(166345464, shared/lb-ltarrow-sel.png) Object upoff
2010-02-27 07:50:04.931 MythUIHelper::CacheImage : Cache Count = :16: size :1944:
2010-02-27 07:50:04.932 MythUIImage::LoadImage found in cache :shared-lb-rtarrow-reg.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.932 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-rtarrow-sel.png---1x-1.png: :1944:
2010-02-27 07:50:04.932 MythUIImage::LoadImage(-1419760120, shared/lb-rtarrow-reg.png) Object dnon
2010-02-27 07:50:04.932 MythUIHelper::CacheImage : Cache Count = :17: size :1944:
2010-02-27 07:50:04.932 MythUIImage::LoadImage found in cache :shared-lb-rtarrow-sel.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.932 MythUIImage::LoadImage(-1419756400, shared/lb-rtarrow-sel.png) Object dnoff
2010-02-27 07:50:04.932 MythUIImage::LoadImage found in cache :shared-lb-rtarrow-reg.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.932 MythUIImage::LoadImage found in cache :shared-lb-rtarrow-sel.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.933 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-ltarrow-reg.png---1x-1.png: :1944:
2010-02-27 07:50:04.933 MythUIHelper::CacheImage : Cache Count = :18: size :1944:
2010-02-27 07:50:04.933 MythUIImage::LoadImage found in cache :shared-lb-ltarrow-reg.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.933 MythUIImage::LoadImage(-1383772320, shared/lb-ltarrow-reg.png) Object upon
2010-02-27 07:50:04.933 MythUIImage::LoadImage found in cache :shared-lb-ltarrow-reg.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.943 NOT IN RAM CACHE, Adding, and adding to size :shared-lb-ltarrow-sel.png---1x-1.png: :1944:
2010-02-27 07:50:04.943 MythUIHelper::CacheImage : Cache Count = :19: size :1944:
2010-02-27 07:50:04.943 MythUIImage::LoadImage found in cache :shared-lb-ltarrow-sel.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.943 MythUIImage::LoadImage(-1383770872, shared/lb-ltarrow-sel.png) Object upoff
2010-02-27 07:50:04.943 MythUIImage::LoadImage found in cache :shared-lb-ltarrow-sel.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.950 MythUIImage(166397088): Load(), spawning thread to load 'lb-rtarrow-reg.png'
2010-02-27 07:50:04.950 MythUIImage::LoadImage(166397088, lb-rtarrow-reg.png) Object dnon
2010-02-27 07:50:04.960 MythUIImage(166398688): Load(), spawning thread to load 'lb-rtarrow-sel.png'
2010-02-27 07:50:04.960 MythUIImage::LoadImage(166398688, lb-rtarrow-sel.png) Object dnoff
2010-02-27 07:50:04.960 NOT IN RAM CACHE, Adding, and adding to size :lb-rtarrow-reg.png---1x-1.png: :1944:
2010-02-27 07:50:04.960 MythUIHelper::CacheImage : Cache Count = :20: size :1944:
2010-02-27 07:50:04.961 MythUIImage::LoadImage found in cache :lb-rtarrow-reg.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.961 MythUIImage(-1419751352): Load(), spawning thread to load 'lb-ltarrow-reg.png'
2010-02-27 07:50:04.961 MythUIImage::LoadImage(-1419751352, lb-ltarrow-reg.png) Object upon
2010-02-27 07:50:04.962 NOT IN RAM CACHE, Adding, and adding to size :lb-rtarrow-sel.png---1x-1.png: :1944:
2010-02-27 07:50:04.962 MythUIHelper::CacheImage : Cache Count = :21: size :1944:
2010-02-27 07:50:04.962 MythUIImage::LoadImage found in cache :lb-rtarrow-sel.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.962 MythUIImage(-1419752560): Load(), spawning thread to load 'lb-ltarrow-sel.png'
2010-02-27 07:50:04.963 MythUIImage::LoadImage(-1419752560, lb-ltarrow-sel.png) Object upoff
2010-02-27 07:50:04.964 MythUIImage(-1419683528): Load(), loading 'lb-rtarrow-reg.png' in foreground
2010-02-27 07:50:04.964 MythUIImage::LoadImage(-1419683528, lb-rtarrow-reg.png) Object dnon
2010-02-27 07:50:04.964 MythUIImage::LoadImage found in cache :lb-rtarrow-reg.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.965 MythUIImage(-1419681528): Load(), loading 'lb-rtarrow-sel.png' in foreground
2010-02-27 07:50:04.965 MythUIImage::LoadImage(-1419681528, lb-rtarrow-sel.png) Object dnoff
2010-02-27 07:50:04.965 MythUIImage::LoadImage found in cache :lb-rtarrow-sel.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.966 MythUIImage(-1419679112): Load(), spawning thread to load 'lb-ltarrow-reg.png'
2010-02-27 07:50:04.966 MythUIImage(-1419677328): Load(), spawning thread to load 'lb-ltarrow-sel.png'
2010-02-27 07:50:04.967 MythUIImage(-1419670240): Load(), spawning thread to load 'cursor.png'
2010-02-27 07:50:04.973 NOT IN RAM CACHE, Adding, and adding to size :lb-ltarrow-sel.png---1x-1.png: :1944:
2010-02-27 07:50:04.973 MythUIHelper::CacheImage : Cache Count = :22: size :1944:
2010-02-27 07:50:04.973 MythUIImage::LoadImage found in cache :lb-ltarrow-sel.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.973 MythUIImage::LoadImage(-1419670240, cursor.png) Object cursor
2010-02-27 07:50:04.974 MythUIImage::LoadImage(-1419677328, lb-ltarrow-sel.png) Object upoff
2010-02-27 07:50:04.974 NOT IN RAM CACHE, Adding, and adding to size :cursor.png---1x-1.png: :540:
2010-02-27 07:50:04.974 MythUIHelper::CacheImage : Cache Count = :23: size :540:
2010-02-27 07:50:04.974 MythUIImage::LoadImage found in cache :cursor.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.974 MythUIImage::LoadImage found in cache :lb-ltarrow-sel.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.982 MythUIImage(-1419670240): Load(), spawning thread to load 'cursor.png'
2010-02-27 07:50:04.982 MythUIImage::LoadImage(-1419670240, cursor.png) Object cursor
2010-02-27 07:50:04.983 MythUIImage(-1419651960): Load(), spawning thread to load 'progressbar_background.png'
2010-02-27 07:50:04.984 NOT IN RAM CACHE, Adding, and adding to size :cursor.png--1x38.png: :152:
2010-02-27 07:50:04.984 MythUIHelper::CacheImage : Cache Count = :24: size :152:
2010-02-27 07:50:04.984 MythUIImage::LoadImage found in cache :cursor.png--1x38.png: RefCount = 2
2010-02-27 07:50:04.984 MythUIImage::LoadImage(-1419651960, progressbar_background.png) Object background
2010-02-27 07:50:04.984 NOT IN RAM CACHE, Adding, and adding to size :lb-ltarrow-reg.png---1x-1.png: :1944:
2010-02-27 07:50:04.984 MythUIHelper::CacheImage : Cache Count = :25: size :1944:
2010-02-27 07:50:04.984 MythUIImage(-1419650640): Load(), spawning thread to load 'progressbar_fill.png'
2010-02-27 07:50:04.984 MythUIImage::LoadImage found in cache :lb-ltarrow-reg.png---1x-1.png: RefCount = 2
2010-02-27 07:50:04.985 MythUIImage::LoadImage(-1419650640, progressbar_fill.png) Object progressimage
2010-02-27 07:50:04.985 MythUIImage::LoadImage(-1419679112, lb-ltarrow-reg.png) Object upon
2010-02-27 07:50:04.986 MythUIImage::LoadImage found in cache :lb-ltarrow-reg.png---1x-1.png: RefCount = 3
2010-02-27 07:50:04.987 MythUIImage(166259976): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:04.987 MythUIImage::LoadImage(166259976, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:04.988 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 5
2010-02-27 07:50:04.988 NOT IN RAM CACHE, Adding, and adding to size :progressbar_background.png--804x57.png: :183312:
2010-02-27 07:50:04.989 MythUIHelper::CacheImage : Cache Count = :26: size :183312:
2010-02-27 07:50:04.989 MythUIImage::LoadImage found in cache :progressbar_background.png--804x57.png: RefCount = 2
2010-02-27 07:50:04.989 MythUIImage(166260952): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:04.989 MythUIImage::LoadImage(166260952, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:04.989 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 5
2010-02-27 07:50:04.990 MythUIImage(166261824): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:04.990 NOT IN RAM CACHE, Adding, and adding to size :progressbar_fill.png--804x57.png: :183312:
2010-02-27 07:50:04.990 MythUIImage::LoadImage(166261824, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:04.990 MythUIHelper::CacheImage : Cache Count = :27: size :183312:
2010-02-27 07:50:04.990 MythUIImage::LoadImage found in cache :progressbar_fill.png--804x57.png: RefCount = 2
2010-02-27 07:50:04.990 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 5
2010-02-27 07:50:04.991 MythUIImage(166263296): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:04.991 MythUIImage::LoadImage(166263296, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:04.991 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 5
2010-02-27 07:50:04.992 MythUIImage(166421632): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:04.992 MythUIImage::LoadImage(166421632, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:04.992 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 6
2010-02-27 07:50:04.993 MythUIImage(166422848): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:04.993 MythUIImage::LoadImage(166422848, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:04.993 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 6
2010-02-27 07:50:04.994 MythUIImage(166423936): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:04.994 MythUIImage::LoadImage(166423936, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:04.994 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 6
2010-02-27 07:50:04.994 MythUIImage(166426544): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:04.994 MythUIImage::LoadImage(166426544, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:04.995 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 6
2010-02-27 07:50:04.995 MythUIImage(166430056): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:04.996 MythUIImage::LoadImage(166430056, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:04.996 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 7
2010-02-27 07:50:04.996 MythUIImage(166431672): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:04.996 MythUIImage::LoadImage(166431672, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:04.997 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 7
2010-02-27 07:50:04.997 MythUIImage(166433248): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:04.997 MythUIImage::LoadImage(166433248, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:04.998 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 7
2010-02-27 07:50:04.998 MythUIImage(166435320): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:04.998 MythUIImage::LoadImage(166435320, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:04.998 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 7
2010-02-27 07:50:04.999 MythUIImage(166436744): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:50:04.999 MythUIImage::LoadImage(166436744, shared/uparrow.png) Object upoff
2010-02-27 07:50:04.999 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 4
2010-02-27 07:50:05.000 MythUIImage(166439440): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:50:05.000 MythUIImage::LoadImage(166439440, shared/downarrow.png) Object dnoff
2010-02-27 07:50:05.000 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 4
2010-02-27 07:50:05.002 MythUIImage(166452496): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:05.002 MythUIImage::LoadImage(166452496, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:05.003 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 8
2010-02-27 07:50:05.003 MythUIImage(166454272): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:05.003 MythUIImage::LoadImage(166454272, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:05.003 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 8
2010-02-27 07:50:05.004 MythUIImage(166456424): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:05.004 MythUIImage::LoadImage(166456424, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:05.004 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 8
2010-02-27 07:50:05.005 MythUIImage(166457992): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:05.005 MythUIImage::LoadImage(166457992, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:05.005 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 8
2010-02-27 07:50:05.006 MythUIImage(166462344): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:05.006 MythUIImage::LoadImage(166462344, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:05.006 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 9
2010-02-27 07:50:05.006 MythUIImage(166464752): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:05.006 MythUIImage::LoadImage(166464752, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:05.008 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 9
2010-02-27 07:50:05.008 MythUIImage(166466520): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:05.008 MythUIImage::LoadImage(166466520, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:05.008 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 9
2010-02-27 07:50:05.009 MythUIImage(166467112): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:05.009 MythUIImage::LoadImage(166467112, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:05.009 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 9
2010-02-27 07:50:05.010 MythUIImage(166471152): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:05.010 MythUIImage::LoadImage(166471152, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:05.010 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 10
2010-02-27 07:50:05.011 MythUIImage(166472128): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:05.011 MythUIImage::LoadImage(166472128, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:05.011 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 10
2010-02-27 07:50:05.011 MythUIImage(166473936): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:05.012 MythUIImage::LoadImage(166473936, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:05.012 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 10
2010-02-27 07:50:05.012 MythUIImage(166475688): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:05.012 MythUIImage::LoadImage(166475688, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:05.013 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 10
2010-02-27 07:50:05.013 MythUIImage(166478608): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:50:05.013 MythUIImage::LoadImage(166478608, shared/uparrow.png) Object upoff
2010-02-27 07:50:05.013 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 5
2010-02-27 07:50:05.014 MythUIImage(166480496): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:50:05.014 MythUIImage::LoadImage(166480496, shared/downarrow.png) Object dnoff
2010-02-27 07:50:05.014 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 5
2010-02-27 07:50:05.053 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/0.png'
2010-02-27 07:50:05.053 MythUIImage::LoadImage(166411608, busyimages/0.png) Object animation
2010-02-27 07:50:05.054 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/1.png'
2010-02-27 07:50:05.055 MythUIImage::LoadImage(166411608, busyimages/1.png) Object animation
2010-02-27 07:50:05.055 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/2.png'
2010-02-27 07:50:05.055 MythUIImage::LoadImage(166411608, busyimages/2.png) Object animation
2010-02-27 07:50:05.056 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/3.png'
2010-02-27 07:50:05.056 MythUIImage::LoadImage(166411608, busyimages/3.png) Object animation
2010-02-27 07:50:05.056 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/4.png'
2010-02-27 07:50:05.057 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/5.png'
2010-02-27 07:50:05.057 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/6.png'
2010-02-27 07:50:05.058 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/7.png'
2010-02-27 07:50:05.058 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/8.png'
2010-02-27 07:50:05.058 NOT IN RAM CACHE, Adding, and adding to size :busyimages-0.png---1x-1.png: :98596:
2010-02-27 07:50:05.058 MythUIHelper::CacheImage : Cache Count = :28: size :98596:
2010-02-27 07:50:05.058 MythUIImage::LoadImage found in cache :busyimages-0.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.059 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/9.png'
2010-02-27 07:50:05.059 NOT IN RAM CACHE, Adding, and adding to size :busyimages-1.png---1x-1.png: :98596:
2010-02-27 07:50:05.059 MythUIImage::LoadImage(166411608, busyimages/4.png) Object animation
2010-02-27 07:50:05.059 MythUIHelper::CacheImage : Cache Count = :29: size :98596:
2010-02-27 07:50:05.059 MythUIImage::LoadImage found in cache :busyimages-1.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.059 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/10.png'
2010-02-27 07:50:05.059 MythUIImage::LoadImage(166411608, busyimages/5.png) Object animation
2010-02-27 07:50:05.060 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/11.png'
2010-02-27 07:50:05.060 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/12.png'
2010-02-27 07:50:05.060 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/13.png'
2010-02-27 07:50:05.060 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/14.png'
2010-02-27 07:50:05.061 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/15.png'
2010-02-27 07:50:05.061 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/16.png'
2010-02-27 07:50:05.061 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/17.png'
2010-02-27 07:50:05.061 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/18.png'
2010-02-27 07:50:05.062 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/19.png'
2010-02-27 07:50:05.062 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/20.png'
2010-02-27 07:50:05.062 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/21.png'
2010-02-27 07:50:05.063 NOT IN RAM CACHE, Adding, and adding to size :busyimages-5.png---1x-1.png: :98596:
2010-02-27 07:50:05.063 MythUIHelper::CacheImage : Cache Count = :30: size :98596:
2010-02-27 07:50:05.063 MythUIImage::LoadImage found in cache :busyimages-5.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.063 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/22.png'
2010-02-27 07:50:05.063 MythUIImage::LoadImage(166411608, busyimages/6.png) Object animation
2010-02-27 07:50:05.063 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/23.png'
2010-02-27 07:50:05.064 MythUIImage(166411608): Load(), spawning thread to load 'busyimages/24.png'
2010-02-27 07:50:05.065 MythUIImage(-1419661424): Load(), loading 'progressbar_background.png' in foreground
2010-02-27 07:50:05.065 MythUIImage::LoadImage(-1419661424, progressbar_background.png) Object background
2010-02-27 07:50:05.065 MythUIImage::LoadImage found in cache :progressbar_background.png--804x57.png: RefCount = 3
2010-02-27 07:50:05.066 MythUIImage(-1419658624): Load(), loading 'progressbar_fill.png' in foreground
2010-02-27 07:50:05.066 MythUIImage::LoadImage(-1419658624, progressbar_fill.png) Object progressimage
2010-02-27 07:50:05.066 MythUIImage::LoadImage found in cache :progressbar_fill.png--804x57.png: RefCount = 3
2010-02-27 07:50:05.066 NOT IN RAM CACHE, Adding, and adding to size :busyimages-6.png---1x-1.png: :98596:
2010-02-27 07:50:05.066 MythUIHelper::CacheImage : Cache Count = :31: size :98596:
2010-02-27 07:50:05.066 MythUIImage::LoadImage found in cache :busyimages-6.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.067 MythUIImage::LoadImage(166411608, busyimages/7.png) Object animation
2010-02-27 07:50:05.106 NOT IN RAM CACHE, Adding, and adding to size :busyimages-7.png---1x-1.png: :98596:
2010-02-27 07:50:05.106 MythUIHelper::CacheImage : Cache Count = :32: size :98596:
2010-02-27 07:50:05.106 MythUIImage::LoadImage found in cache :busyimages-7.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.106 MythUIImage::LoadImage(166411608, busyimages/8.png) Object animation
2010-02-27 07:50:05.107 NOT IN RAM CACHE, Adding, and adding to size :busyimages-4.png---1x-1.png: :98596:
2010-02-27 07:50:05.107 MythUIHelper::CacheImage : Cache Count = :33: size :98596:
2010-02-27 07:50:05.107 MythUIImage::LoadImage found in cache :busyimages-4.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.107 MythUIImage::LoadImage(166411608, busyimages/9.png) Object animation
2010-02-27 07:50:05.121 NOT IN RAM CACHE, Adding, and adding to size :busyimages-2.png---1x-1.png: :98596:
2010-02-27 07:50:05.121 MythUIHelper::CacheImage : Cache Count = :34: size :98596:
2010-02-27 07:50:05.121 MythUIImage::LoadImage found in cache :busyimages-2.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.121 MythUIImage::LoadImage(166411608, busyimages/10.png) Object animation
2010-02-27 07:50:05.124 NOT IN RAM CACHE, Adding, and adding to size :busyimages-8.png---1x-1.png: :98596:
2010-02-27 07:50:05.124 MythUIHelper::CacheImage : Cache Count = :35: size :98596:
2010-02-27 07:50:05.124 MythUIImage::LoadImage found in cache :busyimages-8.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.124 MythUIImage::LoadImage(166411608, busyimages/11.png) Object animation
2010-02-27 07:50:05.125 NOT IN RAM CACHE, Adding, and adding to size :busyimages-9.png---1x-1.png: :98596:
2010-02-27 07:50:05.125 MythUIHelper::CacheImage : Cache Count = :36: size :98596:
2010-02-27 07:50:05.125 MythUIImage::LoadImage found in cache :busyimages-9.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.126 MythUIImage::LoadImage(166411608, busyimages/12.png) Object animation
2010-02-27 07:50:05.126 NOT IN RAM CACHE, Adding, and adding to size :busyimages-3.png---1x-1.png: :98596:
2010-02-27 07:50:05.127 MythUIHelper::CacheImage : Cache Count = :37: size :98596:
2010-02-27 07:50:05.127 MythUIImage::LoadImage found in cache :busyimages-3.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.127 NOT IN RAM CACHE, Adding, and adding to size :busyimages-10.png---1x-1.png: :98596:
2010-02-27 07:50:05.127 MythUIImage::LoadImage(166411608, busyimages/13.png) Object animation
2010-02-27 07:50:05.127 MythUIHelper::CacheImage : Cache Count = :38: size :98596:
2010-02-27 07:50:05.127 MythUIImage::LoadImage found in cache :busyimages-10.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.127 MythUIImage::LoadImage(166411608, busyimages/14.png) Object animation
2010-02-27 07:50:05.129 NOT IN RAM CACHE, Adding, and adding to size :busyimages-11.png---1x-1.png: :98596:
2010-02-27 07:50:05.129 MythUIHelper::CacheImage : Cache Count = :39: size :98596:
2010-02-27 07:50:05.132 MythUIImage::LoadImage found in cache :busyimages-11.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.133 MythUIImage(166565144): Load(), loading 'cursor.png' in foreground
2010-02-27 07:50:05.133 MythUIImage::LoadImage(166411608, busyimages/15.png) Object animation
2010-02-27 07:50:05.133 MythUIImage::LoadImage(166565144, cursor.png) Object cursor
2010-02-27 07:50:05.133 NOT IN RAM CACHE, Adding, and adding to size :busyimages-12.png---1x-1.png: :98596:
2010-02-27 07:50:05.135 MythUIHelper::CacheImage : Cache Count = :40: size :98596:
2010-02-27 07:50:05.135 MythUIImage::LoadImage found in cache :busyimages-12.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.135 NOT IN RAM CACHE, Adding, and adding to size :busyimages-14.png---1x-1.png: :98596:
2010-02-27 07:50:05.135 MythUIImage::LoadImage(166411608, busyimages/16.png) Object animation
2010-02-27 07:50:05.135 MythUIHelper::CacheImage : Cache Count = :41: size :98596:
2010-02-27 07:50:05.136 MythUIImage::LoadImage found in cache :busyimages-14.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.136 MythUIImage::LoadImage found in cache :cursor.png--1x38.png: RefCount = 3
2010-02-27 07:50:05.136 MythUIImage::LoadImage(166411608, busyimages/17.png) Object animation
2010-02-27 07:50:05.136 NOT IN RAM CACHE, Adding, and adding to size :busyimages-13.png---1x-1.png: :98596:
2010-02-27 07:50:05.136 MythUIHelper::CacheImage : Cache Count = :42: size :98596:
2010-02-27 07:50:05.136 MythUIImage::LoadImage found in cache :busyimages-13.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.136 MythUIImage::LoadImage(166411608, busyimages/18.png) Object animation
2010-02-27 07:50:05.139 NOT IN RAM CACHE, Adding, and adding to size :busyimages-15.png---1x-1.png: :98596:
2010-02-27 07:50:05.139 MythUIHelper::CacheImage : Cache Count = :43: size :98596:
2010-02-27 07:50:05.140 MythUIImage::LoadImage found in cache :busyimages-15.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.140 MythUIImage::LoadImage(166411608, busyimages/19.png) Object animation
2010-02-27 07:50:05.140 MythUIImage(166522080): Load(), loading 'cursor.png' in foreground
2010-02-27 07:50:05.140 MythUIImage::LoadImage(166522080, cursor.png) Object cursor
2010-02-27 07:50:05.141 MythUIImage::LoadImage found in cache :cursor.png--1x38.png: RefCount = 4
2010-02-27 07:50:05.142 NOT IN RAM CACHE, Adding, and adding to size :busyimages-17.png---1x-1.png: :98596:
2010-02-27 07:50:05.142 MythUIHelper::CacheImage : Cache Count = :44: size :98596:
2010-02-27 07:50:05.142 MythUIImage::LoadImage found in cache :busyimages-17.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.142 MythUIImage::LoadImage(166411608, busyimages/20.png) Object animation
2010-02-27 07:50:05.143 MythUIImage(166558792): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:05.143 MythUIImage::LoadImage(166558792, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:05.143 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 11
2010-02-27 07:50:05.145 NOT IN RAM CACHE, Adding, and adding to size :busyimages-18.png---1x-1.png: :98596:
2010-02-27 07:50:05.145 MythUIHelper::CacheImage : Cache Count = :45: size :98596:
2010-02-27 07:50:05.145 MythUIImage::LoadImage found in cache :busyimages-18.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.146 MythUIImage(-1419630112): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:05.146 MythUIImage::LoadImage(-1419630112, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:05.146 MythUIImage::LoadImage(166411608, busyimages/21.png) Object animation
2010-02-27 07:50:05.146 NOT IN RAM CACHE, Adding, and adding to size :busyimages-19.png---1x-1.png: :98596:
2010-02-27 07:50:05.146 MythUIHelper::CacheImage : Cache Count = :46: size :98596:
2010-02-27 07:50:05.146 MythUIImage::LoadImage found in cache :busyimages-19.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.146 NOT IN RAM CACHE, Adding, and adding to size :busyimages-16.png---1x-1.png: :98596:
2010-02-27 07:50:05.146 MythUIImage::LoadImage(166411608, busyimages/22.png) Object animation
2010-02-27 07:50:05.146 MythUIHelper::CacheImage : Cache Count = :47: size :98596:
2010-02-27 07:50:05.147 MythUIImage::LoadImage found in cache :busyimages-16.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.147 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 11
2010-02-27 07:50:05.147 MythUIImage::LoadImage(166411608, busyimages/23.png) Object animation
2010-02-27 07:50:05.147 NOT IN RAM CACHE, Adding, and adding to size :busyimages-20.png---1x-1.png: :98596:
2010-02-27 07:50:05.148 MythUIHelper::CacheImage : Cache Count = :48: size :98596:
2010-02-27 07:50:05.148 MythUIImage::LoadImage found in cache :busyimages-20.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.150 MythUIImage(-1383320056): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:05.151 NOT IN RAM CACHE, Adding, and adding to size :busyimages-22.png---1x-1.png: :98596:
2010-02-27 07:50:05.151 MythUIImage::LoadImage(166411608, busyimages/24.png) Object animation
2010-02-27 07:50:05.151 MythUIImage::LoadImage(-1383320056, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:05.151 MythUIHelper::CacheImage : Cache Count = :49: size :98596:
2010-02-27 07:50:05.151 MythUIImage::LoadImage found in cache :busyimages-22.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.151 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 11
2010-02-27 07:50:05.152 MythUIImage(-1419641160): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:05.152 MythUIImage::LoadImage(-1419641160, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:05.153 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 11
2010-02-27 07:50:05.154 MythUIImage(166985400): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:05.154 MythUIImage::LoadImage(166985400, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:05.154 NOT IN RAM CACHE, Adding, and adding to size :busyimages-24.png---1x-1.png: :98596:
2010-02-27 07:50:05.154 MythUIHelper::CacheImage : Cache Count = :50: size :98596:
2010-02-27 07:50:05.154 MythUIImage::LoadImage found in cache :busyimages-24.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.155 NOT IN RAM CACHE, Adding, and adding to size :busyimages-21.png---1x-1.png: :98596:
2010-02-27 07:50:05.155 MythUIHelper::CacheImage : Cache Count = :51: size :98596:
2010-02-27 07:50:05.155 MythUIImage::LoadImage found in cache :busyimages-21.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.155 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 12
2010-02-27 07:50:05.155 NOT IN RAM CACHE, Adding, and adding to size :busyimages-23.png---1x-1.png: :98596:
2010-02-27 07:50:05.155 MythUIHelper::CacheImage : Cache Count = :52: size :98596:
2010-02-27 07:50:05.155 MythUIImage::LoadImage found in cache :busyimages-23.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.156 MythUIImage(166499632): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:05.156 MythUIImage::LoadImage(166499632, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:05.156 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 12
2010-02-27 07:50:05.156 MythUIImage(166987480): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:05.156 MythUIImage::LoadImage(166987480, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:05.157 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 12
2010-02-27 07:50:05.157 MythUIImage(166988400): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:05.157 MythUIImage::LoadImage(166988400, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:05.157 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 12
2010-02-27 07:50:05.158 MythUIImage(166991840): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:50:05.158 MythUIImage::LoadImage(166991840, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:50:05.158 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 13
2010-02-27 07:50:05.159 MythUIImage(166492776): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:50:05.159 MythUIImage::LoadImage(166492776, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:50:05.159 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 13
2010-02-27 07:50:05.160 MythUIImage(166494264): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:50:05.160 MythUIImage::LoadImage(166494264, shared/lb-check-full.png) Object checkfull
2010-02-27 07:50:05.160 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 13
2010-02-27 07:50:05.160 MythUIImage(166495864): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:50:05.160 MythUIImage::LoadImage(166495864, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:50:05.161 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 13
2010-02-27 07:50:05.161 MythUIImage(166498664): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:50:05.161 MythUIImage::LoadImage(166498664, shared/uparrow.png) Object upoff
2010-02-27 07:50:05.161 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 6
2010-02-27 07:50:05.162 MythUIImage(166527312): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:50:05.162 MythUIImage::LoadImage(166527312, shared/downarrow.png) Object dnoff
2010-02-27 07:50:05.162 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 6
2010-02-27 07:50:05.167 MythUIImage(166547584): Load(), loading 'cursor.png' in foreground
2010-02-27 07:50:05.167 MythUIImage::LoadImage(166547584, cursor.png) Object cursor
2010-02-27 07:50:05.167 MythUIImage::LoadImage found in cache :cursor.png--1x38.png: RefCount = 5
2010-02-27 07:50:05.231 MythUIImage(166554080): Load(), spawning thread to load 'shared/directory.png'
2010-02-27 07:50:05.231 MythUIImage::LoadImage(166554080, shared/directory.png) Object icon
2010-02-27 07:50:05.232 MythUIImage(-1419632608): Load(), spawning thread to load 'shared/directory.png'
2010-02-27 07:50:05.232 MythUIImage(-1419632608): Load(), spawning thread to load 'shared/updirectory.png'
2010-02-27 07:50:05.232 MythUIImage::LoadImage(-1419632608, shared/updirectory.png) Object icon
2010-02-27 07:50:05.233 MythUIImage(166571056): Load(), spawning thread to load 'shared/directory.png'
2010-02-27 07:50:05.233 MythUIImage(166571056): Load(), spawning thread to load 'shared/executable.png'
2010-02-27 07:50:05.234 NOT IN RAM CACHE, Adding, and adding to size :shared-directory.png--225x111.png: :67488:
2010-02-27 07:50:05.234 MythUIHelper::CacheImage : Cache Count = :53: size :67488:
2010-02-27 07:50:05.234 MythUIImage::LoadImage found in cache :shared-directory.png--225x111.png: RefCount = 2
2010-02-27 07:50:05.234 MythUIImage::LoadImage(166571056, shared/executable.png) Object icon
2010-02-27 07:50:05.234 MythUIImage::LoadImage(-1419632608, shared/directory.png) Object icon
2010-02-27 07:50:05.234 MythUIImage(166574168): Load(), loading 'shared/directory.png' in foreground
2010-02-27 07:50:05.235 MythUIImage::LoadImage found in cache :shared-directory.png--225x111.png: RefCount = 3
2010-02-27 07:50:05.235 MythUIImage::LoadImage(166571056, shared/directory.png) Object icon
2010-02-27 07:50:05.236 MythUIImage::LoadImage found in cache :shared-directory.png--225x111.png: RefCount = 4
2010-02-27 07:50:05.236 MythUIImage::LoadImage(166574168, shared/directory.png) Object icon
2010-02-27 07:50:05.236 MythUIImage::LoadImage found in cache :shared-directory.png--225x111.png: RefCount = 5
2010-02-27 07:50:05.237 NOT IN RAM CACHE, Adding, and adding to size :shared-updirectory.png--225x111.png: :67488:
2010-02-27 07:50:05.237 MythUIHelper::CacheImage : Cache Count = :54: size :67488:
2010-02-27 07:50:05.237 MythUIImage::LoadImage found in cache :shared-updirectory.png--225x111.png: RefCount = 2
2010-02-27 07:50:05.237 MythUIImage(166574168): Load(), spawning thread to load 'shared/file.png'
2010-02-27 07:50:05.237 MythUIImage::LoadImage(166574168, shared/file.png) Object icon
2010-02-27 07:50:05.238 NOT IN RAM CACHE, Adding, and adding to size :shared-executable.png--225x111.png: :49728:
2010-02-27 07:50:05.238 MythUIHelper::CacheImage : Cache Count = :55: size :49728:
2010-02-27 07:50:05.238 MythUIImage::LoadImage found in cache :shared-executable.png--225x111.png: RefCount = 2
2010-02-27 07:50:05.238 MythUIImage(166580616): Load(), loading 'shared/directory.png' in foreground
2010-02-27 07:50:05.238 MythUIImage::LoadImage(166580616, shared/directory.png) Object icon
2010-02-27 07:50:05.239 MythUIImage::LoadImage found in cache :shared-directory.png--225x111.png: RefCount = 5
2010-02-27 07:50:05.239 MythUIImage(-1419570536): Load(), loading 'shared/updirectory.png' in foreground
2010-02-27 07:50:05.239 MythUIImage::LoadImage(-1419570536, shared/updirectory.png) Object icon
2010-02-27 07:50:05.240 MythUIImage::LoadImage found in cache :shared-updirectory.png--225x111.png: RefCount = 3
2010-02-27 07:50:05.240 MythUIImage(-1419569072): Load(), loading 'shared/executable.png' in foreground
2010-02-27 07:50:05.240 MythUIImage::LoadImage(-1419569072, shared/executable.png) Object icon
2010-02-27 07:50:05.240 MythUIImage::LoadImage found in cache :shared-executable.png--225x111.png: RefCount = 3
2010-02-27 07:50:05.241 MythUIImage(166582232): Load(), spawning thread to load 'shared/file.png'
2010-02-27 07:50:05.242 MythUIImage(167094008): Load(), loading 'shared/directory.png' in foreground
2010-02-27 07:50:05.242 MythUIImage::LoadImage(167094008, shared/directory.png) Object icon
2010-02-27 07:50:05.242 MythUIImage::LoadImage found in cache :shared-directory.png--225x111.png: RefCount = 6
2010-02-27 07:50:05.243 MythUIImage(167096136): Load(), loading 'shared/updirectory.png' in foreground
2010-02-27 07:50:05.243 MythUIImage::LoadImage(167096136, shared/updirectory.png) Object icon
2010-02-27 07:50:05.243 MythUIImage::LoadImage found in cache :shared-updirectory.png--225x111.png: RefCount = 4
2010-02-27 07:50:05.243 MythUIImage(167097512): Load(), loading 'shared/executable.png' in foreground
2010-02-27 07:50:05.244 MythUIImage::LoadImage(167097512, shared/executable.png) Object icon
2010-02-27 07:50:05.244 MythUIImage::LoadImage found in cache :shared-executable.png--225x111.png: RefCount = 4
2010-02-27 07:50:05.244 MythUIImage(167099240): Load(), spawning thread to load 'shared/file.png'
2010-02-27 07:50:05.245 MythUIImage(167092240): Auto-generated gradient filename of 'gradient-247x157-153-153-153-102-102-102-220-1'
2010-02-27 07:50:05.245 MythUIImage(167092240): Load(), spawning thread to load 'gradient-247x157-153-153-153-102-102-102-220-1'
2010-02-27 07:50:05.245 MythUIImage::LoadImage(167092240, gradient-247x157-153-153-153-102-102-102-220-1) Object buttonbackground
2010-02-27 07:50:05.249 NOT IN RAM CACHE, Adding, and adding to size :gradient-247x157-153-153-153-102-102-102-220-1--247x157.png: :155116:
2010-02-27 07:50:05.249 MythUIHelper::CacheImage : Cache Count = :56: size :155116:
2010-02-27 07:50:05.249 MythUIImage::LoadImage found in cache :gradient-247x157-153-153-153-102-102-102-220-1--247x157.png: RefCount = 2
2010-02-27 07:50:05.261 NOT IN RAM CACHE, Adding, and adding to size :shared-file.png--225x111.png: :35076:
2010-02-27 07:50:05.261 MythUIHelper::CacheImage : Cache Count = :57: size :35076:
2010-02-27 07:50:05.261 MythUIImage::LoadImage found in cache :shared-file.png--225x111.png: RefCount = 2
2010-02-27 07:50:05.261 MythUIImage::LoadImage(166582232, shared/file.png) Object icon
2010-02-27 07:50:05.262 MythUIImage::LoadImage found in cache :shared-file.png--225x111.png: RefCount = 3
2010-02-27 07:50:05.262 MythUIImage::LoadImage(167099240, shared/file.png) Object icon
2010-02-27 07:50:05.262 MythUIImage::LoadImage found in cache :shared-file.png--225x111.png: RefCount = 4
2010-02-27 07:50:05.265 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-02-27 07:50:05.288 Warning, already have a global font called: basesmall
2010-02-27 07:50:05.289 Warning, already have a global font called: basemedium
2010-02-27 07:50:05.290 Warning, already have a global font called: baselarge
2010-02-27 07:50:05.292 Warning, already have a global font called: baseextralarge
2010-02-27 07:50:05.293 Warning, already have a global font called: basesmallgrey
2010-02-27 07:50:05.294 Warning, already have a global font called: basesmallpurple
2010-02-27 07:50:05.296 Warning, already have a global font called: basesmallblack
2010-02-27 07:50:05.297 Warning, already have a global font called: basesmallyellow
2010-02-27 07:50:05.298 Warning, already have a global font called: basesmallgreen
2010-02-27 07:50:05.300 Warning, already have a global font called: basesmallblue
2010-02-27 07:50:05.301 Warning, already have a global font called: basesmallred
2010-02-27 07:50:05.302 Warning, already have a global font called: basemediumgrey
2010-02-27 07:50:05.304 Warning, already have a global font called: basemediumgreen
2010-02-27 07:50:05.305 Warning, already have a global font called: basemediumred
2010-02-27 07:50:05.306 Warning, already have a global font called: basemediumpurple
2010-02-27 07:50:05.307 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-02-27 07:50:05.327 Warning, already have a global font called: basesmall
2010-02-27 07:50:05.328 Warning, already have a global font called: basemedium
2010-02-27 07:50:05.330 Warning, already have a global font called: baselarge
2010-02-27 07:50:05.331 Warning, already have a global font called: baseextralarge
2010-02-27 07:50:05.332 Warning, already have a global font called: basesmallgrey
2010-02-27 07:50:05.334 Warning, already have a global font called: basesmallpurple
2010-02-27 07:50:05.335 Warning, already have a global font called: basesmallblack
2010-02-27 07:50:05.336 Warning, already have a global font called: basesmallyellow
2010-02-27 07:50:05.338 Warning, already have a global font called: basesmallgreen
2010-02-27 07:50:05.339 Warning, already have a global font called: basesmallblue
2010-02-27 07:50:05.340 Warning, already have a global font called: basesmallred
2010-02-27 07:50:05.342 Warning, already have a global font called: basemediumgrey
2010-02-27 07:50:05.343 Warning, already have a global font called: basemediumgreen
2010-02-27 07:50:05.344 Warning, already have a global font called: basemediumred
2010-02-27 07:50:05.346 MythUIImage(167670824): Load(), spawning thread to load 'blankbutton_off.png'
2010-02-27 07:50:05.346 MythUIImage::LoadImage(167670824, blankbutton_off.png) Object background
2010-02-27 07:50:05.347 MythUIImage(167636384): Load(), spawning thread to load 'blankbutton_off.png'
2010-02-27 07:50:05.348 MythUIImage(167636384): Load(), spawning thread to load 'blankbutton_on.png'
2010-02-27 07:50:05.348 MythUIImage::LoadImage(167636384, blankbutton_on.png) Object background
2010-02-27 07:50:05.348 MythUIImage(167637808): Load(), spawning thread to load 'blankbutton_off.png'
2010-02-27 07:50:05.349 NOT IN RAM CACHE, Adding, and adding to size :blankbutton_off.png---1x-1.png: :9216:
2010-02-27 07:50:05.349 MythUIHelper::CacheImage : Cache Count = :58: size :9216:
2010-02-27 07:50:05.349 MythUIImage::LoadImage found in cache :blankbutton_off.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.349 MythUIImage::LoadImage(167636384, blankbutton_off.png) Object background
2010-02-27 07:50:05.349 MythUIImage(167639680): Load(), loading 'blankbutton_off.png' in foreground
2010-02-27 07:50:05.349 NOT IN RAM CACHE, Adding, and adding to size :blankbutton_on.png---1x-1.png: :9216:
2010-02-27 07:50:05.349 MythUIHelper::CacheImage : Cache Count = :59: size :9216:
2010-02-27 07:50:05.350 MythUIImage::LoadImage found in cache :blankbutton_on.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.350 MythUIImage::LoadImage found in cache :blankbutton_off.png---1x-1.png: RefCount = 3
2010-02-27 07:50:05.350 MythUIImage::LoadImage(167639680, blankbutton_off.png) Object background
2010-02-27 07:50:05.350 MythUIImage::LoadImage found in cache :blankbutton_off.png---1x-1.png: RefCount = 4
2010-02-27 07:50:05.350 MythUIImage::LoadImage(167637808, blankbutton_off.png) Object background
2010-02-27 07:50:05.351 MythUIImage::LoadImage found in cache :blankbutton_off.png---1x-1.png: RefCount = 4
2010-02-27 07:50:05.358 MythUIImage(167639680): Load(), spawning thread to load 'blankbutton_pushed.png'
2010-02-27 07:50:05.358 MythUIImage::LoadImage(167639680, blankbutton_pushed.png) Object background
2010-02-27 07:50:05.360 NOT IN RAM CACHE, Adding, and adding to size :blankbutton_pushed.png---1x-1.png: :9216:
2010-02-27 07:50:05.360 MythUIHelper::CacheImage : Cache Count = :60: size :9216:
2010-02-27 07:50:05.360 MythUIImage::LoadImage found in cache :blankbutton_pushed.png---1x-1.png: RefCount = 2
2010-02-27 07:50:05.360 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-02-27 07:50:05.360 No theme file /tmp/base.xml
2010-02-27 07:50:05.360 Unable to load window 'backgroundwindow' from base
2010-02-27 07:50:05.361 MythUIImage(-1383940944): Load(), spawning thread to load '/usr/share/mythtv/themes/Mythbuntu/background.png'
2010-02-27 07:50:05.361 MythUIImage::LoadImage(-1383940944, /usr/share/mythtv/themes/Mythbuntu/background.png) Object backimg
2010-02-27 07:50:05.366 Current MythTV Schema Version (DBSchemaVer): 1244
2010-02-27 07:50:05.579 NOT IN RAM CACHE, Adding, and adding to size :-usr-share-mythtv-themes-Mythbuntu-background.png---1x-1.png: :8294400:
2010-02-27 07:50:05.579 MythUIHelper::CacheImage : Cache Count = :61: size :8294400:
2010-02-27 07:50:05.580 MythUIImage::LoadImage found in cache :-usr-share-mythtv-themes-Mythbuntu-background.png---1x-1.png: RefCount = 2
2010-02-27 07:50:06.370 Desktop video mode: 1920x1080 59.9413 Hz
2010-02-27 07:50:06.388 Dynamic Twinview not enabled, ignoring
2010-02-27 07:50:06.389 max_width: 1920 max_height: 1080
2010-02-27 07:50:06.632 Registering Internal as a media playback plugin.
2010-02-27 07:50:06.699 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-02-27 07:50:06.757 Creating inactive MediaMonitor and static device list
2010-02-27 07:50:06.757 IgnoreDevices=
2010-02-27 07:50:06.759 MythCDROMLinux::testMedia - Opened device
2010-02-27 07:50:06.764 MMUnix::AddDevice() - Added /dev/scd0
2010-02-27 07:50:06.767 MMUnix::CheckRemovable(/sys/block/loop0)/removable 0
2010-02-27 07:50:06.768 MMUnix::CheckRemovable(/sys/block/loop1)/removable 0
2010-02-27 07:50:06.768 MMUnix::CheckRemovable(/sys/block/loop2)/removable 0
2010-02-27 07:50:06.768 MMUnix::CheckRemovable(/sys/block/loop3)/removable 0
2010-02-27 07:50:06.768 MMUnix::CheckRemovable(/sys/block/loop4)/removable 0
2010-02-27 07:50:06.769 MMUnix::CheckRemovable(/sys/block/loop5)/removable 0
2010-02-27 07:50:06.769 MMUnix::CheckRemovable(/sys/block/loop6)/removable 0
2010-02-27 07:50:06.769 MMUnix::CheckRemovable(/sys/block/loop7)/removable 0
2010-02-27 07:50:06.770 MMUnix::CheckRemovable(/sys/block/ram0)/removable 0
2010-02-27 07:50:06.770 MMUnix::CheckRemovable(/sys/block/ram1)/removable 0
2010-02-27 07:50:06.770 MMUnix::CheckRemovable(/sys/block/ram10)/removable 0
2010-02-27 07:50:06.771 MMUnix::CheckRemovable(/sys/block/ram11)/removable 0
2010-02-27 07:50:06.771 MMUnix::CheckRemovable(/sys/block/ram12)/removable 0
2010-02-27 07:50:06.771 MMUnix::CheckRemovable(/sys/block/ram13)/removable 0
2010-02-27 07:50:06.771 MMUnix::CheckRemovable(/sys/block/ram14)/removable 0
2010-02-27 07:50:06.772 MMUnix::CheckRemovable(/sys/block/ram15)/removable 0
2010-02-27 07:50:06.772 MMUnix::CheckRemovable(/sys/block/ram2)/removable 0
2010-02-27 07:50:06.772 MMUnix::CheckRemovable(/sys/block/ram3)/removable 0
2010-02-27 07:50:06.773 MMUnix::CheckRemovable(/sys/block/ram4)/removable 0
2010-02-27 07:50:06.773 MMUnix::CheckRemovable(/sys/block/ram5)/removable 0
2010-02-27 07:50:06.773 MMUnix::CheckRemovable(/sys/block/ram6)/removable 0
2010-02-27 07:50:06.774 MMUnix::CheckRemovable(/sys/block/ram7)/removable 0
2010-02-27 07:50:06.774 MMUnix::CheckRemovable(/sys/block/ram8)/removable 0
2010-02-27 07:50:06.774 MMUnix::CheckRemovable(/sys/block/ram9)/removable 0
2010-02-27 07:50:06.774 MMUnix::CheckRemovable(/sys/block/sda)/removable 0
2010-02-27 07:50:06.775 MMUnix::CheckRemovable(/sys/block/sr0)/removable 1
2010-02-27 07:50:06.780 MMUnix::GetDeviceFile(/sys/block/sr0/bdi), Error - udevinfo failed to start!
2010-02-27 07:50:06.780 MMUnix::GetCDROMBlockDevices()->'sr0'
2010-02-27 07:50:06.781 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-02-27 07:50:06.788 MMUnix::GetDeviceFile(/sys/block/sr0/power), Error - udevinfo failed to start!
2010-02-27 07:50:06.788 MMUnix::GetCDROMBlockDevices()->'sr0'
2010-02-27 07:50:06.788 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-02-27 07:50:06.795 MMUnix::GetDeviceFile(/sys/block/sr0/trace), Error - udevinfo failed to start!
2010-02-27 07:50:06.796 MMUnix::GetCDROMBlockDevices()->'sr0'
2010-02-27 07:50:06.796 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-02-27 07:50:06.803 MMUnix::GetDeviceFile(/sys/block/sr0), Error - udevinfo failed to start!
2010-02-27 07:50:06.804 MMUnix::GetCDROMBlockDevices()->'sr0'
2010-02-27 07:50:06.804 MMUnix::AddDevice() - not adding /dev/sr0
                        because it appears to be a duplicate of /dev/scd0
2010-02-27 07:50:06.804 Initial device list...
/dev/scd0->/dev/sr0 (ATAPI    iHOS104          )
2010-02-27 07:50:06.804 Registering 'MythDVD DVD Media Handler'
 as a media handler for MEDIATYPE_DVD
2010-02-27 07:50:06.805 Registering 'MythDVD VCD Media Handler'
 as a media handler for MEDIATYPE_VCD
2010-02-27 07:50:06.809 No theme dir: /home/xbmc/.mythtv/themes/Mythbuntu
2010-02-27 07:50:06.810 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-02-27 07:50:06.844 MythUIImage(171155600): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:50:06.844 MythUIImage::LoadImage(171155600, shared/uparrow.png) Object upon
2010-02-27 07:50:06.844 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 7
2010-02-27 07:50:06.845 MythUIImage(171157160): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:50:06.845 MythUIImage::LoadImage(171157160, shared/downarrow.png) Object dnon
2010-02-27 07:50:06.845 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 7
2010-02-27 07:50:06.862 MythUIImage(171162776): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.862 MythUIImage::LoadImage(171162776, watermark/dvd.png) Object watermark
2010-02-27 07:50:06.862 MythUIImage(-1423895424): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.863 MythUIImage(-1423894448): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.863 MythUIImage(171167640): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.864 MythUIImage(171440704): Load(), spawning thread to load 'watermark/eject.png'
2010-02-27 07:50:06.864 MythUIImage(171441168): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.865 MythUIImage(171442768): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.865 MythUIImage(171444200): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.865 MythUIImage(171167640): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.866 MythUIImage(171440704): Load(), spawning thread to load 'watermark/eject.png'
2010-02-27 07:50:06.866 MythUIImage(171448856): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.867 MythUIImage(171450360): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.867 MythUIImage(171451528): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.867 MythUIImage(171453560): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.868 MythUIImage(171455016): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.868 MythUIImage(171457200): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.869 MythUIImage(171458576): Load(), spawning thread to load 'watermark/radio.png'
2010-02-27 07:50:06.869 MythUIImage(171460160): Load(), spawning thread to load 'watermark/gallery.png'
2010-02-27 07:50:06.869 MythUIImage(171461480): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.870 MythUIImage(171463672): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.870 MythUIImage(171465144): Load(), spawning thread to load 'watermark/guide.png'
2010-02-27 07:50:06.871 MythUIImage(171466808): Load(), spawning thread to load 'watermark/web.png'
2010-02-27 07:50:06.871 MythUIImage(171468400): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.871 MythUIImage(171470152): Load(), spawning thread to load 'watermark/power.png'
2010-02-27 07:50:06.872 MythUIImage(171472040): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.872 MythUIImage(171473520): Load(), spawning thread to load 'watermark/config.png'
2010-02-27 07:50:06.873 MythUIImage(171475088): Load(), spawning thread to load 'watermark/config.png'
2010-02-27 07:50:06.873 MythUIImage(171477792): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.874 MythUIImage(171478864): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.874 MythUIImage(171481176): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.874 MythUIImage(171482152): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.875 MythUIImage(171483784): Load(), spawning thread to load 'watermark/radio.png'
2010-02-27 07:50:06.875 MythUIImage(171485856): Load(), spawning thread to load 'watermark/gallery.png'
2010-02-27 07:50:06.876 MythUIImage(166486456): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.876 MythUIImage(171490520): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.876 MythUIImage(171492456): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.877 MythUIImage(171494208): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.877 MythUIImage(171495896): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.877 MythUIImage(171497520): Load(), spawning thread to load 'watermark/guide.png'
2010-02-27 07:50:06.878 MythUIImage(171499552): Load(), spawning thread to load 'watermark/web.png'
2010-02-27 07:50:06.878 MythUIImage(171501192): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.879 MythUIImage(171502608): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.879 MythUIImage(171504464): Load(), spawning thread to load 'watermark/music_playlist.png'
2010-02-27 07:50:06.879 MythUIImage(171505808): Load(), spawning thread to load 'watermark/music_rip.png'
2010-02-27 07:50:06.880 MythUIImage(171507872): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.880 MythUIImage(171509464): Load(), spawning thread to load 'watermark/music_playlist.png'
2010-02-27 07:50:06.881 MythUIImage(171510952): Load(), spawning thread to load 'watermark/music_rip.png'
2010-02-27 07:50:06.881 MythUIImage(171512504): Load(), spawning thread to load 'watermark/music_scan.png'
2010-02-27 07:50:06.882 MythUIImage(171514104): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.882 MythUIImage(171516096): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.882 MythUIImage(171517560): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.883 MythUIImage(171519376): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.883 MythUIImage(171520888): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.884 MythUIImage(171522560): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.884 MythUIImage(171524208): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.885 MythUIImage(171525848): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.885 MythUIImage(171527616): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.885 MythUIImage(171529272): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.886 MythUIImage(171530720): Load(), spawning thread to load 'watermark/seek.png'
2010-02-27 07:50:06.886 MythUIImage(171533360): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.887 MythUIImage(171534504): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.887 MythUIImage(171536736): Load(), spawning thread to load 'watermark/tv_custom_record.png'
2010-02-27 07:50:06.888 MythUIImage(171537544): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.888 MythUIImage(171539032): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.888 MythUIImage(171540840): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.889 MythUIImage(171542608): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.889 MythUIImage(171543848): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.890 MythUIImage(171545472): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.890 MythUIImage(171547336): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.891 MythUIImage(171549184): Load(), spawning thread to load 'watermark/search_new_titles.png'
2010-02-27 07:50:06.891 MythUIImage(171550688): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.891 MythUIImage(171552496): Load(), spawning thread to load 'watermark/search_categories.png'
2010-02-27 07:50:06.892 MythUIImage(171553888): Load(), spawning thread to load 'watermark/seek.png'
2010-02-27 07:50:06.892 MythUIImage(171555832): Load(), spawning thread to load 'watermark/search_time.png'
2010-02-27 07:50:06.893 MythUIImage(171557080): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.893 MythUIImage(171559160): Load(), spawning thread to load 'watermark/tv_searchlistings.png'
2010-02-27 07:50:06.894 MythUIImage(171561112): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.894 MythUIImage(171563272): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.894 MythUIImage(171563824): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.895 MythUIImage(171565952): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.895 MythUIImage(171567448): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.896 MythUIImage(171568888): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.896 MythUIImage(171570952): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.897 MythUIImage(171572176): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.897 MythUIImage(171573808): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.897 MythUIImage(171575952): Load(), spawning thread to load 'watermark/tv_delete.png'
2010-02-27 07:50:06.898 MythUIImage(171577456): Load(), spawning thread to load 'watermark/seek.png'
2010-02-27 07:50:06.898 MythUIImage(171578840): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.899 MythUIImage(171580848): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.899 MythUIImage(171582448): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.900 MythUIImage(171583624): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.900 MythUIImage(171585656): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.900 MythUIImage(171587344): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.901 MythUIImage(171588680): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.901 MythUIImage(171590592): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.902 MythUIImage(171592000): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.902 MythUIImage(171593840): Load(), spawning thread to load 'watermark/search_new_titles.png'
2010-02-27 07:50:06.902 MythUIImage(171595192): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.903 MythUIImage(171597104): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.903 MythUIImage(171598352): Load(), spawning thread to load 'watermark/search_new_titles.png'
2010-02-27 07:50:06.904 MythUIImage(171600288): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.904 MythUIImage(171601752): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.905 MythUIImage(171603984): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.905 MythUIImage(171605784): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.906 MythUIImage(171607416): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.906 MythUIImage(171609152): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.906 MythUIImage(171610720): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.907 MythUIImage(171612216): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.907 MythUIImage(171613896): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.908 MythUIImage(171615576): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.908 MythUIImage(171617256): Load(), spawning thread to load 'watermark/cctv.png'
2010-02-27 07:50:06.909 MythUIImage(171618624): Load(), spawning thread to load 'watermark/cctv.png'
2010-02-27 07:50:06.909 MythUIImage(171620320): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.910 MythUIImage(171622040): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.910 MythUIImage(171623696): Auto-generated gradient filename of 'gradient-1950x15-255-255-255-0-0-0-50-1'
2010-02-27 07:50:06.910 MythUIImage(171623696): Load(), spawning thread to load 'gradient-1950x15-255-255-255-0-0-0-50-1'
2010-02-27 07:50:06.910 MythUIImage(171624936): Load(), spawning thread to load 'panels-with-drop.png'
2010-02-27 07:50:06.915 MythUIImage(171630496): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:50:06.915 MythUIImage::LoadImage(171630496, shared/uparrow.png) Object upon
2010-02-27 07:50:06.915 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 8
2010-02-27 07:50:06.916 MythUIImage(171631896): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:50:06.916 MythUIImage::LoadImage(171631896, shared/downarrow.png) Object dnon
2010-02-27 07:50:06.916 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 8
2010-02-27 07:50:06.916 MythUIImage(171632640): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.917 MythUIImage(171633512): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.917 MythUIImage(171634952): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.917 MythUIImage(171634232): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.918 MythUIImage(171399024): Load(), spawning thread to load 'watermark/eject.png'
2010-02-27 07:50:06.918 MythUIImage(171399728): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.918 MythUIImage(171400448): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.919 MythUIImage(171335336): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.919 MythUIImage(171265664): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.920 MythUIImage(171240408): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.920 MythUIImage(171376336): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.920 MythUIImage(171372000): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.921 MythUIImage(171380752): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.921 MythUIImage(171323960): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.921 MythUIImage(171364704): Load(), spawning thread to load 'watermark/radio.png'
2010-02-27 07:50:06.922 MythUIImage(171345568): Load(), spawning thread to load 'watermark/gallery.png'
2010-02-27 07:50:06.922 MythUIImage(171375208): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.922 MythUIImage(171373808): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.923 MythUIImage(171372408): Load(), spawning thread to load 'watermark/guide.png'
2010-02-27 07:50:06.923 MythUIImage(171302464): Load(), spawning thread to load 'watermark/web.png'
2010-02-27 07:50:06.923 MythUIImage(171344872): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.924 MythUIImage(171207416): Load(), spawning thread to load 'watermark/power.png'
2010-02-27 07:50:06.924 MythUIImage(171377696): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.924 MythUIImage(171321280): Load(), spawning thread to load 'watermark/config.png'
2010-02-27 07:50:06.925 MythUIImage(171310344): Load(), spawning thread to load 'watermark/config.png'
2010-02-27 07:50:06.925 MythUIImage(171220192): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.925 MythUIImage(171204336): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.926 MythUIImage(171378624): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.926 MythUIImage(171368080): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.926 MythUIImage(171366616): Load(), spawning thread to load 'watermark/radio.png'
2010-02-27 07:50:06.927 MythUIImage(171370712): Load(), spawning thread to load 'watermark/gallery.png'
2010-02-27 07:50:06.927 MythUIImage(171360856): Load(), spawning thread to load 'watermark/game.png'
2010-02-27 07:50:06.927 MythUIImage(171346008): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.928 MythUIImage(171343520): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.928 MythUIImage(171321744): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.928 MythUIImage(171286968): Load(), spawning thread to load 'watermark/weather.png'
2010-02-27 07:50:06.929 MythUIImage(171234800): Load(), spawning thread to load 'watermark/guide.png'
2010-02-27 07:50:06.929 MythUIImage(171238032): Load(), spawning thread to load 'watermark/web.png'
2010-02-27 07:50:06.929 MythUIImage(171213472): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.930 MythUIImage(171338592): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.930 MythUIImage(171312040): Load(), spawning thread to load 'watermark/music_playlist.png'
2010-02-27 07:50:06.930 MythUIImage(171300408): Load(), spawning thread to load 'watermark/music_rip.png'
2010-02-27 07:50:06.931 MythUIImage(171248888): Load(), spawning thread to load 'watermark/music.png'
2010-02-27 07:50:06.931 MythUIImage(171384208): Load(), spawning thread to load 'watermark/music_playlist.png'
2010-02-27 07:50:06.931 MythUIImage(171383304): Load(), spawning thread to load 'watermark/music_rip.png'
2010-02-27 07:50:06.932 MythUIImage(171374720): Load(), spawning thread to load 'watermark/music_scan.png'
2010-02-27 07:50:06.932 MythUIImage(171373320): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.932 MythUIImage(171312520): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.933 MythUIImage(171284168): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.933 MythUIImage(171267872): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.933 MythUIImage(171221880): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.934 MythUIImage(171306784): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.934 MythUIImage(171370224): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.934 MythUIImage(171337424): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.935 MythUIImage(171273192): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.935 MythUIImage(171344000): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.935 MythUIImage(171334736): Load(), spawning thread to load 'watermark/seek.png'
2010-02-27 07:50:06.936 MythUIImage(171023568): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.936 MythUIImage(171328736): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.936 MythUIImage(171339560): Load(), spawning thread to load 'watermark/tv_custom_record.png'
2010-02-27 07:50:06.937 MythUIImage(171329520): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.937 MythUIImage(171292024): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.938 MythUIImage(171272568): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.938 MythUIImage(171263640): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.938 MythUIImage(171262240): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.939 MythUIImage(171239520): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.939 MythUIImage(171361408): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.939 MythUIImage(171349888): Load(), spawning thread to load 'watermark/search_new_titles.png'
2010-02-27 07:50:06.940 MythUIImage(171354896): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.940 MythUIImage(171265112): Load(), spawning thread to load 'watermark/search_categories.png'
2010-02-27 07:50:06.940 MythUIImage(171246664): Load(), spawning thread to load 'watermark/seek.png'
2010-02-27 07:50:06.941 MythUIImage(171245264): Load(), spawning thread to load 'watermark/search_time.png'
2010-02-27 07:50:06.941 MythUIImage(171222496): Load(), spawning thread to load 'watermark/list.png'
2010-02-27 07:50:06.941 MythUIImage(171293432): Load(), spawning thread to load 'watermark/tv_searchlistings.png'
2010-02-27 07:50:06.942 MythUIImage(171340256): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.942 MythUIImage(171203664): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.942 MythUIImage(171357792): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.943 MythUIImage(171283520): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.943 MythUIImage(171241752): Load(), spawning thread to load 'watermark/volts.png'
2010-02-27 07:50:06.944 MythUIImage(171336064): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.944 MythUIImage(171314072): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.944 MythUIImage(171333584): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.945 MythUIImage(171218752): Load(), spawning thread to load 'watermark/tv.png'
2010-02-27 07:50:06.945 MythUIImage(171347960): Load(), spawning thread to load 'watermark/tv_delete.png'
2010-02-27 07:50:06.945 MythUIImage(171206816): Load(), spawning thread to load 'watermark/seek.png'
2010-02-27 07:50:06.946 MythUIImage(171295960): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.946 MythUIImage(171210920): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.946 MythUIImage(171213952): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.947 MythUIImage(171338112): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.947 MythUIImage(171311384): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.947 MythUIImage(171353184): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.948 MythUIImage(171278336): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.948 MythUIImage(171284656): Load(), spawning thread to load 'watermark/tv_schedule.png'
2010-02-27 07:50:06.948 MythUIImage(171250792): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.949 MythUIImage(171020600): Load(), spawning thread to load 'watermark/search_new_titles.png'
2010-02-27 07:50:06.949 MythUIImage(171305736): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.949 MythUIImage(171342320): Load(), spawning thread to load 'watermark/search_lists.png'
2010-02-27 07:50:06.950 MythUIImage(171276808): Load(), spawning thread to load 'watermark/search_new_titles.png'
2010-02-27 07:50:06.950 MythUIImage(171315416): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.951 MythUIImage(171330944): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.951 MythUIImage(171023120): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.951 MythUIImage(171351288): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.952 MythUIImage(171024416): Load(), spawning thread to load 'watermark/settings.png'
2010-02-27 07:50:06.952 MythUIImage(171231216): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.952 MythUIImage(171019216): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.953 MythUIImage(171317952): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.953 MythUIImage(171021344): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.954 MythUIImage(171160384): Load(), spawning thread to load 'watermark/netflix.png'
2010-02-27 07:50:06.954 MythUIImage(171209528): Load(), spawning thread to load 'watermark/cctv.png'
2010-02-27 07:50:06.954 MythUIImage(171401424): Load(), spawning thread to load 'watermark/cctv.png'
2010-02-27 07:50:06.955 MythUIImage(171403096): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.955 MythUIImage(171404552): Load(), spawning thread to load 'watermark/dvd.png'
2010-02-27 07:50:06.957 MythUIImage(171406600): Auto-generated gradient filename of 'gradient-1950x15-255-255-255-0-0-0-50-1'
2010-02-27 07:50:06.957 MythUIImage(171406600): Load(), spawning thread to load 'gradient-1950x15-255-255-255-0-0-0-50-1'
2010-02-27 07:50:06.958 MythUIImage(171636232): Load(), spawning thread to load 'panels-with-drop.png'
2010-02-27 07:50:06.959 No menu file /home/xbmc/.mythtv/mainmenu.xml
2010-02-27 07:50:06.970 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-02-27 07:50:06.972 No menu file /home/xbmc/.mythtv/mythmusic
2010-02-27 07:50:06.972 No menu file /usr/share/mythtv/themes/defaultmenu//mythmusic
2010-02-27 07:50:06.972 No menu file /usr/share/mythtv/themes/Mythbuntu//mythmusic
2010-02-27 07:50:06.972 No menu file /usr/share/mythtv/mythmusic
2010-02-27 07:50:06.972 No menu file ../mythfrontend/mythmusic
2010-02-27 07:50:06.973 No menu file /home/xbmc/.mythtv/mythvideo
2010-02-27 07:50:06.973 No menu file /usr/share/mythtv/themes/defaultmenu//mythvideo
2010-02-27 07:50:06.973 No menu file /usr/share/mythtv/themes/Mythbuntu//mythvideo
2010-02-27 07:50:06.974 Found mainmenu.xml for theme 'Mythbuntu'
2010-02-27 07:50:07.058 NOT IN RAM CACHE, Adding, and adding to size :watermark-dvd.png---1x-1.png: :8294400:
2010-02-27 07:50:07.059 MythUIHelper::CacheImage : Cache Count = :62: size :8294940:
2010-02-27 07:50:07.059 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.059 MythUIImage::LoadImage(171440704, watermark/eject.png) Object watermark
2010-02-27 07:50:07.059 MythUIImage::LoadImage(-1423895424, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.059 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.060 MythUIImage::LoadImage(-1423894448, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.060 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.060 MythUIImage::LoadImage(171441168, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.060 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.060 MythUIImage::LoadImage(171444200, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.061 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 6
2010-02-27 07:50:07.061 MythUIImage::LoadImage(171167640, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.061 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 7
2010-02-27 07:50:07.061 MythUIImage::LoadImage(watermark/eject.png), this file is already being loaded by this same MythUIImage in another thread.
2010-02-27 07:50:07.061 MythUIImage::LoadImage(171167640, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.062 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 8
2010-02-27 07:50:07.062 MythUIImage::LoadImage(171448856, watermark/game.png) Object watermark
2010-02-27 07:50:07.062 MythUIImage::LoadImage(171442768, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.062 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 9
2010-02-27 07:50:07.062 MythUIImage::LoadImage(171451528, watermark/tv.png) Object watermark
2010-02-27 07:50:07.068 NOT IN RAM CACHE, Adding, and adding to size :watermark-eject.png---1x-1.png: :4:
2010-02-27 07:50:07.068 MythUIHelper::CacheImage : Cache Count = :63: size :544:
2010-02-27 07:50:07.068 MythUIImage::LoadImage found in cache :watermark-eject.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.068 NOT IN RAM CACHE, Adding, and adding to size :watermark-game.png---1x-1.png: :4:
2010-02-27 07:50:07.069 MythUIImage::LoadImage(171453560, watermark/music.png) Object watermark
2010-02-27 07:50:07.069 MythUIHelper::CacheImage : Cache Count = :64: size :544:
2010-02-27 07:50:07.069 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.069 MythUIImage::LoadImage(171450360, watermark/game.png) Object watermark
2010-02-27 07:50:07.069 MythUIImage::LoadImage(171455016, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.069 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.069 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 10
2010-02-27 07:50:07.070 MythUIImage::LoadImage(171457200, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.070 MythUIImage::LoadImage(171458576, watermark/radio.png) Object watermark
2010-02-27 07:50:07.070 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 11
2010-02-27 07:50:07.070 MythUIImage::LoadImage(171460160, watermark/gallery.png) Object watermark
2010-02-27 07:50:07.078 NOT IN RAM CACHE, Adding, and adding to size :watermark-gallery.png---1x-1.png: :4:
2010-02-27 07:50:07.078 MythUIHelper::CacheImage : Cache Count = :65: size :544:
2010-02-27 07:50:07.078 MythUIImage::LoadImage found in cache :watermark-gallery.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.078 NOT IN RAM CACHE, Adding, and adding to size :watermark-radio.png---1x-1.png: :4:
2010-02-27 07:50:07.078 MythUIImage::LoadImage(171461480, watermark/game.png) Object watermark
2010-02-27 07:50:07.078 MythUIHelper::CacheImage : Cache Count = :66: size :544:
2010-02-27 07:50:07.079 MythUIImage::LoadImage found in cache :watermark-radio.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.079 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.079 MythUIImage::LoadImage(171465144, watermark/guide.png) Object watermark
2010-02-27 07:50:07.079 MythUIImage::LoadImage(171463672, watermark/weather.png) Object watermark
2010-02-27 07:50:07.093 NOT IN RAM CACHE, Adding, and adding to size :watermark-guide.png---1x-1.png: :4:
2010-02-27 07:50:07.093 MythUIHelper::CacheImage : Cache Count = :67: size :544:
2010-02-27 07:50:07.094 MythUIImage::LoadImage found in cache :watermark-guide.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.094 MythUIImage::LoadImage(171466808, watermark/web.png) Object watermark
2010-02-27 07:50:07.095 NOT IN RAM CACHE, Adding, and adding to size :watermark-weather.png---1x-1.png: :4:
2010-02-27 07:50:07.095 MythUIHelper::CacheImage : Cache Count = :68: size :544:
2010-02-27 07:50:07.095 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.095 MythUIImage::LoadImage(171468400, watermark/settings.png) Object watermark
2010-02-27 07:50:07.124 NOT IN RAM CACHE, Adding, and adding to size :watermark-web.png---1x-1.png: :4:
2010-02-27 07:50:07.124 MythUIHelper::CacheImage : Cache Count = :69: size :544:
2010-02-27 07:50:07.124 MythUIImage::LoadImage found in cache :watermark-web.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.124 MythUIImage::LoadImage(171470152, watermark/power.png) Object watermark
2010-02-27 07:50:07.164 NOT IN RAM CACHE, Adding, and adding to size :watermark-power.png---1x-1.png: :4:
2010-02-27 07:50:07.164 MythUIHelper::CacheImage : Cache Count = :70: size :544:
2010-02-27 07:50:07.164 MythUIImage::LoadImage found in cache :watermark-power.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.300 NOT IN RAM CACHE, Adding, and adding to size :watermark-settings.png---1x-1.png: :8294400:
2010-02-27 07:50:07.300 MythUIHelper::CacheImage : Cache Count = :71: size :8294940:
2010-02-27 07:50:07.300 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.300 MythUIImage::LoadImage(171473520, watermark/config.png) Object watermark
2010-02-27 07:50:07.301 NOT IN RAM CACHE, Adding, and adding to size :watermark-config.png---1x-1.png: :4:
2010-02-27 07:50:07.301 MythUIHelper::CacheImage : Cache Count = :72: size :544:
2010-02-27 07:50:07.301 MythUIImage::LoadImage found in cache :watermark-config.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.301 MythUIImage::LoadImage(171475088, watermark/config.png) Object watermark
2010-02-27 07:50:07.302 MythUIImage::LoadImage found in cache :watermark-config.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.312 MythUIImage::LoadImage(171472040, watermark/settings.png) Object watermark
2010-02-27 07:50:07.312 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.350 NOT IN RAM CACHE, Adding, and adding to size :watermark-tv.png---1x-1.png: :8294400:
2010-02-27 07:50:07.350 MythUIHelper::CacheImage : Cache Count = :73: size :8294940:
2010-02-27 07:50:07.350 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.350 MythUIImage::LoadImage(171481176, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.351 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 12
2010-02-27 07:50:07.351 MythUIImage::LoadImage(171482152, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.351 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 13
2010-02-27 07:50:07.351 MythUIImage::LoadImage(171483784, watermark/radio.png) Object watermark
2010-02-27 07:50:07.351 MythUIImage::LoadImage found in cache :watermark-radio.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.351 MythUIImage::LoadImage(171485856, watermark/gallery.png) Object watermark
2010-02-27 07:50:07.352 MythUIImage::LoadImage found in cache :watermark-gallery.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.352 MythUIImage::LoadImage(166486456, watermark/game.png) Object watermark
2010-02-27 07:50:07.352 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.352 MythUIImage::LoadImage(171490520, watermark/weather.png) Object watermark
2010-02-27 07:50:07.352 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.353 MythUIImage::LoadImage(171492456, watermark/weather.png) Object watermark
2010-02-27 07:50:07.353 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.353 MythUIImage::LoadImage(171494208, watermark/weather.png) Object watermark
2010-02-27 07:50:07.353 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.353 MythUIImage::LoadImage(171495896, watermark/weather.png) Object watermark
2010-02-27 07:50:07.354 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 6
2010-02-27 07:50:07.354 MythUIImage::LoadImage(171497520, watermark/guide.png) Object watermark
2010-02-27 07:50:07.354 MythUIImage::LoadImage found in cache :watermark-guide.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.354 MythUIImage::LoadImage(171499552, watermark/web.png) Object watermark
2010-02-27 07:50:07.354 MythUIImage::LoadImage found in cache :watermark-web.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.354 MythUIImage::LoadImage(171501192, watermark/settings.png) Object watermark
2010-02-27 07:50:07.355 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.355 MythUIImage::LoadImage(171477792, watermark/tv.png) Object watermark
2010-02-27 07:50:07.355 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.355 MythUIImage::LoadImage(171504464, watermark/music_playlist.png) Object watermark
2010-02-27 07:50:07.356 NOT IN RAM CACHE, Adding, and adding to size :watermark-music_playlist.png---1x-1.png: :4:
2010-02-27 07:50:07.356 MythUIHelper::CacheImage : Cache Count = :74: size :544:
2010-02-27 07:50:07.356 MythUIImage::LoadImage found in cache :watermark-music_playlist.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.357 MythUIImage::LoadImage(171505808, watermark/music_rip.png) Object watermark
2010-02-27 07:50:07.358 NOT IN RAM CACHE, Adding, and adding to size :watermark-music_rip.png---1x-1.png: :4:
2010-02-27 07:50:07.358 MythUIHelper::CacheImage : Cache Count = :75: size :544:
2010-02-27 07:50:07.358 MythUIImage::LoadImage found in cache :watermark-music_rip.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.372 NOT IN RAM CACHE, Adding, and adding to size :watermark-music.png---1x-1.png: :8294400:
2010-02-27 07:50:07.373 MythUIHelper::CacheImage : Cache Count = :76: size :8294940:
2010-02-27 07:50:07.373 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.373 MythUIImage::LoadImage(171509464, watermark/music_playlist.png) Object watermark
2010-02-27 07:50:07.373 MythUIImage::LoadImage(171478864, watermark/music.png) Object watermark
2010-02-27 07:50:07.373 MythUIImage::LoadImage found in cache :watermark-music_playlist.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.373 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.373 MythUIImage::LoadImage(171510952, watermark/music_rip.png) Object watermark
2010-02-27 07:50:07.374 MythUIImage::LoadImage(171507872, watermark/music.png) Object watermark
2010-02-27 07:50:07.374 MythUIImage::LoadImage(171512504, watermark/music_scan.png) Object watermark
2010-02-27 07:50:07.374 MythUIImage::LoadImage found in cache :watermark-music_rip.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.374 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.374 MythUIImage::LoadImage(171514104, watermark/volts.png) Object watermark
2010-02-27 07:50:07.374 MythUIImage::LoadImage(171502608, watermark/music.png) Object watermark
2010-02-27 07:50:07.375 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.375 MythUIImage::LoadImage(171517560, watermark/settings.png) Object watermark
2010-02-27 07:50:07.375 NOT IN RAM CACHE, Adding, and adding to size :watermark-music_scan.png---1x-1.png: :4:
2010-02-27 07:50:07.375 MythUIHelper::CacheImage : Cache Count = :77: size :544:
2010-02-27 07:50:07.375 MythUIImage::LoadImage found in cache :watermark-music_scan.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.375 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.375 MythUIImage::LoadImage(171519376, watermark/settings.png) Object watermark
2010-02-27 07:50:07.376 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 6
2010-02-27 07:50:07.376 MythUIImage::LoadImage(171520888, watermark/settings.png) Object watermark
2010-02-27 07:50:07.376 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 7
2010-02-27 07:50:07.376 MythUIImage::LoadImage(171522560, watermark/settings.png) Object watermark
2010-02-27 07:50:07.377 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 8
2010-02-27 07:50:07.377 MythUIImage::LoadImage(171524208, watermark/settings.png) Object watermark
2010-02-27 07:50:07.377 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 9
2010-02-27 07:50:07.377 MythUIImage::LoadImage(171527616, watermark/tv.png) Object watermark
2010-02-27 07:50:07.377 MythUIImage::LoadImage(171525848, watermark/settings.png) Object watermark
2010-02-27 07:50:07.377 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.378 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 10
2010-02-27 07:50:07.378 MythUIImage::LoadImage(171529272, watermark/search_lists.png) Object watermark
2010-02-27 07:50:07.378 MythUIImage::LoadImage(171530720, watermark/seek.png) Object watermark
2010-02-27 07:50:07.620 NOT IN RAM CACHE, Adding, and adding to size :watermark-search_lists.png---1x-1.png: :8294400:
2010-02-27 07:50:07.620 MythUIHelper::CacheImage : Cache Count = :78: size :8294940:
2010-02-27 07:50:07.620 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.620 MythUIImage::LoadImage(171533360, watermark/list.png) Object watermark
2010-02-27 07:50:07.657 NOT IN RAM CACHE, Adding, and adding to size :watermark-volts.png---1x-1.png: :8294400:
2010-02-27 07:50:07.657 MythUIHelper::CacheImage : Cache Count = :79: size :8294940:
2010-02-27 07:50:07.658 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.658 MythUIImage::LoadImage(171534504, watermark/search_lists.png) Object watermark
2010-02-27 07:50:07.658 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.658 MythUIImage::LoadImage(171536736, watermark/tv_custom_record.png) Object watermark
2010-02-27 07:50:07.659 MythUIImage::LoadImage(171516096, watermark/volts.png) Object watermark
2010-02-27 07:50:07.659 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.659 MythUIImage::LoadImage(171537544, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:07.676 NOT IN RAM CACHE, Adding, and adding to size :watermark-tv_custom_record.png---1x-1.png: :4:
2010-02-27 07:50:07.677 MythUIHelper::CacheImage : Cache Count = :80: size :544:
2010-02-27 07:50:07.677 MythUIImage::LoadImage found in cache :watermark-tv_custom_record.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.677 MythUIImage::LoadImage(171539032, watermark/volts.png) Object watermark
2010-02-27 07:50:07.677 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.677 MythUIImage::LoadImage(171540840, watermark/volts.png) Object watermark
2010-02-27 07:50:07.678 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.678 MythUIImage::LoadImage(171542608, watermark/search_lists.png) Object watermark
2010-02-27 07:50:07.678 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.680 NOT IN RAM CACHE, Adding, and adding to size :watermark-seek.png---1x-1.png: :8294400:
2010-02-27 07:50:07.680 MythUIHelper::CacheImage : Cache Count = :81: size :8294940:
2010-02-27 07:50:07.680 MythUIImage::LoadImage found in cache :watermark-seek.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.805 NOT IN RAM CACHE, Adding, and adding to size :watermark-list.png---1x-1.png: :8294400:
2010-02-27 07:50:07.805 MythUIHelper::CacheImage : Cache Count = :82: size :8294940:
2010-02-27 07:50:07.805 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.805 MythUIImage::LoadImage(171547336, watermark/tv.png) Object watermark
2010-02-27 07:50:07.805 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.806 MythUIImage::LoadImage(171549184, watermark/search_new_titles.png) Object watermark
2010-02-27 07:50:07.809 MythUIImage::LoadImage(171543848, watermark/list.png) Object watermark
2010-02-27 07:50:07.809 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.809 MythUIImage::LoadImage(171550688, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.810 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 14
2010-02-27 07:50:07.810 MythUIImage::LoadImage(171552496, watermark/search_categories.png) Object watermark
2010-02-27 07:50:07.811 MythUIImage::LoadImage(171545472, watermark/list.png) Object watermark
2010-02-27 07:50:07.811 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.811 MythUIImage::LoadImage(171553888, watermark/seek.png) Object watermark
2010-02-27 07:50:07.812 MythUIImage::LoadImage found in cache :watermark-seek.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.812 MythUIImage::LoadImage(171555832, watermark/search_time.png) Object watermark
2010-02-27 07:50:07.836 NOT IN RAM CACHE, Adding, and adding to size :watermark-search_time.png---1x-1.png: :4:
2010-02-27 07:50:07.836 MythUIHelper::CacheImage : Cache Count = :83: size :544:
2010-02-27 07:50:07.836 MythUIImage::LoadImage found in cache :watermark-search_time.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.836 MythUIImage::LoadImage(171557080, watermark/list.png) Object watermark
2010-02-27 07:50:07.837 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.837 MythUIImage::LoadImage(171559160, watermark/tv_searchlistings.png) Object watermark
2010-02-27 07:50:07.954 NOT IN RAM CACHE, Adding, and adding to size :watermark-tv_schedule.png---1x-1.png: :8294400:
2010-02-27 07:50:07.954 MythUIHelper::CacheImage : Cache Count = :84: size :8294940:
2010-02-27 07:50:07.954 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.954 MythUIImage::LoadImage(171561112, watermark/tv.png) Object watermark
2010-02-27 07:50:07.954 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 6
2010-02-27 07:50:07.955 MythUIImage::LoadImage(171563272, watermark/search_lists.png) Object watermark
2010-02-27 07:50:07.955 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.955 MythUIImage::LoadImage(171563824, watermark/tv.png) Object watermark
2010-02-27 07:50:07.955 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 7
2010-02-27 07:50:07.955 MythUIImage::LoadImage(171565952, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:07.956 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 3
2010-02-27 07:50:07.956 MythUIImage::LoadImage(171567448, watermark/volts.png) Object watermark
2010-02-27 07:50:07.956 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 6
2010-02-27 07:50:07.956 MythUIImage::LoadImage(171568888, watermark/tv.png) Object watermark
2010-02-27 07:50:07.957 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 8
2010-02-27 07:50:07.957 MythUIImage::LoadImage(171570952, watermark/tv.png) Object watermark
2010-02-27 07:50:07.957 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 9
2010-02-27 07:50:07.957 MythUIImage::LoadImage(171572176, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:07.958 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.958 MythUIImage::LoadImage(171573808, watermark/tv.png) Object watermark
2010-02-27 07:50:07.958 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 10
2010-02-27 07:50:07.958 MythUIImage::LoadImage(171575952, watermark/tv_delete.png) Object watermark
2010-02-27 07:50:07.991 NOT IN RAM CACHE, Adding, and adding to size :watermark-tv_delete.png---1x-1.png: :4:
2010-02-27 07:50:07.991 MythUIHelper::CacheImage : Cache Count = :85: size :544:
2010-02-27 07:50:07.991 MythUIImage::LoadImage found in cache :watermark-tv_delete.png---1x-1.png: RefCount = 2
2010-02-27 07:50:07.991 MythUIImage::LoadImage(171577456, watermark/seek.png) Object watermark
2010-02-27 07:50:07.992 MythUIImage::LoadImage found in cache :watermark-seek.png---1x-1.png: RefCount = 4
2010-02-27 07:50:07.992 MythUIImage::LoadImage(171578840, watermark/settings.png) Object watermark
2010-02-27 07:50:07.992 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 11
2010-02-27 07:50:07.992 MythUIImage::LoadImage(171580848, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.993 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 15
2010-02-27 07:50:07.993 MythUIImage::LoadImage(171582448, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.993 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 16
2010-02-27 07:50:07.993 MythUIImage::LoadImage(171583624, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.994 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 17
2010-02-27 07:50:07.994 MythUIImage::LoadImage(171585656, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.994 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 18
2010-02-27 07:50:07.994 MythUIImage::LoadImage(171587344, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.995 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 19
2010-02-27 07:50:07.995 MythUIImage::LoadImage(171588680, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.995 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 20
2010-02-27 07:50:07.995 MythUIImage::LoadImage(171590592, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:07.996 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 5
2010-02-27 07:50:07.996 MythUIImage::LoadImage(171592000, watermark/dvd.png) Object watermark
2010-02-27 07:50:07.996 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 21
2010-02-27 07:50:08.013 NOT IN RAM CACHE, Adding, and adding to size :watermark-search_new_titles.png---1x-1.png: :8294400:
2010-02-27 07:50:08.013 MythUIHelper::CacheImage : Cache Count = :86: size :8294940:
2010-02-27 07:50:08.013 MythUIImage::LoadImage found in cache :watermark-search_new_titles.png---1x-1.png: RefCount = 2
2010-02-27 07:50:08.013 MythUIImage::LoadImage(171595192, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.013 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 22
2010-02-27 07:50:08.013 MythUIImage::LoadImage(171597104, watermark/search_lists.png) Object watermark
2010-02-27 07:50:08.014 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.014 MythUIImage::LoadImage(171598352, watermark/search_new_titles.png) Object watermark
2010-02-27 07:50:08.014 MythUIImage::LoadImage found in cache :watermark-search_new_titles.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.014 MythUIImage::LoadImage(171600288, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.014 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 23
2010-02-27 07:50:08.015 MythUIImage::LoadImage(171601752, watermark/settings.png) Object watermark
2010-02-27 07:50:08.015 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 12
2010-02-27 07:50:08.015 MythUIImage::LoadImage(171603984, watermark/settings.png) Object watermark
2010-02-27 07:50:08.015 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 13
2010-02-27 07:50:08.015 MythUIImage::LoadImage(171605784, watermark/settings.png) Object watermark
2010-02-27 07:50:08.016 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 14
2010-02-27 07:50:08.016 MythUIImage::LoadImage(171607416, watermark/settings.png) Object watermark
2010-02-27 07:50:08.016 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 15
2010-02-27 07:50:08.016 MythUIImage::LoadImage(171609152, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.015 MythUIImage::LoadImage(171593840, watermark/search_new_titles.png) Object watermark
2010-02-27 07:50:08.017 MythUIImage::LoadImage found in cache :watermark-search_new_titles.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.017 NOT IN RAM CACHE, Adding, and adding to size :watermark-netflix.png---1x-1.png: :4:
2010-02-27 07:50:08.017 MythUIHelper::CacheImage : Cache Count = :87: size :544:
2010-02-27 07:50:08.017 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 2
2010-02-27 07:50:08.017 MythUIImage::LoadImage(171610720, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.018 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.018 MythUIImage::LoadImage(171612216, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.018 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.018 MythUIImage::LoadImage(171613896, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.018 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.019 MythUIImage::LoadImage(171615576, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.019 MythUIImage::LoadImage(171617256, watermark/cctv.png) Object watermark
2010-02-27 07:50:08.019 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.020 NOT IN RAM CACHE, Adding, and adding to size :watermark-cctv.png---1x-1.png: :4:
2010-02-27 07:50:08.020 MythUIHelper::CacheImage : Cache Count = :88: size :544:
2010-02-27 07:50:08.020 MythUIImage::LoadImage found in cache :watermark-cctv.png---1x-1.png: RefCount = 2
2010-02-27 07:50:08.020 MythUIImage::LoadImage(171618624, watermark/cctv.png) Object watermark
2010-02-27 07:50:08.020 MythUIImage::LoadImage(171620320, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.021 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 24
2010-02-27 07:50:08.021 MythUIImage::LoadImage found in cache :watermark-cctv.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.021 MythUIImage::LoadImage(171622040, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.021 MythUIImage::LoadImage(171623696, gradient-1950x15-255-255-255-0-0-0-50-1) Object titleboxshadow
2010-02-27 07:50:08.021 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 25
2010-02-27 07:50:08.021 MythUIImage::LoadImage(171624936, panels-with-drop.png) Object overlay
2010-02-27 07:50:08.030 NOT IN RAM CACHE, Adding, and adding to size :gradient-1950x15-255-255-255-0-0-0-50-1--1950x15.png: :117000:
2010-02-27 07:50:08.031 MythUIHelper::CacheImage : Cache Count = :89: size :117540:
2010-02-27 07:50:08.031 MythUIImage::LoadImage found in cache :gradient-1950x15-255-255-255-0-0-0-50-1--1950x15.png: RefCount = 2
2010-02-27 07:50:08.031 MythUIImage::LoadImage(171632640, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.031 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 26
2010-02-27 07:50:08.031 MythUIImage::LoadImage(171633512, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.032 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 27
2010-02-27 07:50:08.032 MythUIImage::LoadImage(171634952, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.032 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 28
2010-02-27 07:50:08.032 MythUIImage::LoadImage(171634232, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.033 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 29
2010-02-27 07:50:08.033 MythUIImage::LoadImage(171399024, watermark/eject.png) Object watermark
2010-02-27 07:50:08.033 MythUIImage::LoadImage found in cache :watermark-eject.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.033 MythUIImage::LoadImage(171399728, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.034 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 30
2010-02-27 07:50:08.034 MythUIImage::LoadImage(171400448, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.034 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 31
2010-02-27 07:50:08.034 MythUIImage::LoadImage(171335336, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.035 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 32
2010-02-27 07:50:08.035 MythUIImage::LoadImage(171265664, watermark/game.png) Object watermark
2010-02-27 07:50:08.035 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.035 MythUIImage::LoadImage(171240408, watermark/game.png) Object watermark
2010-02-27 07:50:08.036 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.036 MythUIImage::LoadImage(171376336, watermark/tv.png) Object watermark
2010-02-27 07:50:08.036 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 11
2010-02-27 07:50:08.036 MythUIImage::LoadImage(171372000, watermark/music.png) Object watermark
2010-02-27 07:50:08.037 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.037 MythUIImage::LoadImage(171380752, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.037 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 33
2010-02-27 07:50:08.037 MythUIImage::LoadImage(171323960, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.038 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 34
2010-02-27 07:50:08.038 MythUIImage::LoadImage(171364704, watermark/radio.png) Object watermark
2010-02-27 07:50:08.038 MythUIImage::LoadImage found in cache :watermark-radio.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.038 MythUIImage::LoadImage(171345568, watermark/gallery.png) Object watermark
2010-02-27 07:50:08.039 MythUIImage::LoadImage found in cache :watermark-gallery.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.039 MythUIImage::LoadImage(171375208, watermark/game.png) Object watermark
2010-02-27 07:50:08.039 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.039 MythUIImage::LoadImage(171373808, watermark/weather.png) Object watermark
2010-02-27 07:50:08.040 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.040 MythUIImage::LoadImage(171372408, watermark/guide.png) Object watermark
2010-02-27 07:50:08.040 MythUIImage::LoadImage found in cache :watermark-guide.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.040 MythUIImage::LoadImage(171302464, watermark/web.png) Object watermark
2010-02-27 07:50:08.041 MythUIImage::LoadImage found in cache :watermark-web.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.041 MythUIImage::LoadImage(171344872, watermark/settings.png) Object watermark
2010-02-27 07:50:08.041 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 16
2010-02-27 07:50:08.041 MythUIImage::LoadImage(171207416, watermark/power.png) Object watermark
2010-02-27 07:50:08.042 MythUIImage::LoadImage found in cache :watermark-power.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.042 MythUIImage::LoadImage(171377696, watermark/settings.png) Object watermark
2010-02-27 07:50:08.042 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 17
2010-02-27 07:50:08.042 MythUIImage::LoadImage(171321280, watermark/config.png) Object watermark
2010-02-27 07:50:08.042 MythUIImage::LoadImage found in cache :watermark-config.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.043 MythUIImage::LoadImage(171310344, watermark/config.png) Object watermark
2010-02-27 07:50:08.043 MythUIImage::LoadImage found in cache :watermark-config.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.043 MythUIImage::LoadImage(171220192, watermark/tv.png) Object watermark
2010-02-27 07:50:08.043 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 12
2010-02-27 07:50:08.044 MythUIImage::LoadImage(171204336, watermark/music.png) Object watermark
2010-02-27 07:50:08.044 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.044 MythUIImage::LoadImage(171378624, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.044 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 35
2010-02-27 07:50:08.045 MythUIImage::LoadImage(171368080, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.045 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 36
2010-02-27 07:50:08.045 MythUIImage::LoadImage(171366616, watermark/radio.png) Object watermark
2010-02-27 07:50:08.045 MythUIImage::LoadImage found in cache :watermark-radio.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.046 MythUIImage::LoadImage(171370712, watermark/gallery.png) Object watermark
2010-02-27 07:50:08.046 MythUIImage::LoadImage found in cache :watermark-gallery.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.046 MythUIImage::LoadImage(171360856, watermark/game.png) Object watermark
2010-02-27 07:50:08.046 MythUIImage::LoadImage found in cache :watermark-game.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.046 MythUIImage::LoadImage(171346008, watermark/weather.png) Object watermark
2010-02-27 07:50:08.047 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.047 MythUIImage::LoadImage(171343520, watermark/weather.png) Object watermark
2010-02-27 07:50:08.047 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.047 MythUIImage::LoadImage(171321744, watermark/weather.png) Object watermark
2010-02-27 07:50:08.048 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 10
2010-02-27 07:50:08.048 MythUIImage::LoadImage(171286968, watermark/weather.png) Object watermark
2010-02-27 07:50:08.048 MythUIImage::LoadImage found in cache :watermark-weather.png---1x-1.png: RefCount = 11
2010-02-27 07:50:08.048 MythUIImage::LoadImage(171234800, watermark/guide.png) Object watermark
2010-02-27 07:50:08.049 MythUIImage::LoadImage found in cache :watermark-guide.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.049 MythUIImage::LoadImage(171238032, watermark/web.png) Object watermark
2010-02-27 07:50:08.049 MythUIImage::LoadImage found in cache :watermark-web.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.049 MythUIImage::LoadImage(171213472, watermark/settings.png) Object watermark
2010-02-27 07:50:08.049 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 18
2010-02-27 07:50:08.050 MythUIImage::LoadImage(171338592, watermark/music.png) Object watermark
2010-02-27 07:50:08.050 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.050 MythUIImage::LoadImage(171312040, watermark/music_playlist.png) Object watermark
2010-02-27 07:50:08.050 MythUIImage::LoadImage found in cache :watermark-music_playlist.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.050 MythUIImage::LoadImage(171300408, watermark/music_rip.png) Object watermark
2010-02-27 07:50:08.051 MythUIImage::LoadImage found in cache :watermark-music_rip.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.051 MythUIImage::LoadImage(171248888, watermark/music.png) Object watermark
2010-02-27 07:50:08.051 MythUIImage::LoadImage found in cache :watermark-music.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.051 MythUIImage::LoadImage(171384208, watermark/music_playlist.png) Object watermark
2010-02-27 07:50:08.052 MythUIImage::LoadImage found in cache :watermark-music_playlist.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.052 MythUIImage::LoadImage(171383304, watermark/music_rip.png) Object watermark
2010-02-27 07:50:08.052 MythUIImage::LoadImage found in cache :watermark-music_rip.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.052 MythUIImage::LoadImage(171374720, watermark/music_scan.png) Object watermark
2010-02-27 07:50:08.053 MythUIImage::LoadImage found in cache :watermark-music_scan.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.053 MythUIImage::LoadImage(171373320, watermark/volts.png) Object watermark
2010-02-27 07:50:08.053 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.053 MythUIImage::LoadImage(171312520, watermark/volts.png) Object watermark
2010-02-27 07:50:08.054 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.054 MythUIImage::LoadImage(171284168, watermark/settings.png) Object watermark
2010-02-27 07:50:08.054 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 19
2010-02-27 07:50:08.054 MythUIImage::LoadImage(171267872, watermark/settings.png) Object watermark
2010-02-27 07:50:08.055 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 20
2010-02-27 07:50:08.055 MythUIImage::LoadImage(171221880, watermark/settings.png) Object watermark
2010-02-27 07:50:08.055 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 21
2010-02-27 07:50:08.056 MythUIImage::LoadImage(171306784, watermark/settings.png) Object watermark
2010-02-27 07:50:08.056 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 22
2010-02-27 07:50:08.056 MythUIImage::LoadImage(171370224, watermark/settings.png) Object watermark
2010-02-27 07:50:08.056 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 23
2010-02-27 07:50:08.057 MythUIImage::LoadImage(171337424, watermark/settings.png) Object watermark
2010-02-27 07:50:08.057 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 24
2010-02-27 07:50:08.057 MythUIImage::LoadImage(171273192, watermark/tv.png) Object watermark
2010-02-27 07:50:08.057 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 13
2010-02-27 07:50:08.058 MythUIImage::LoadImage(171344000, watermark/search_lists.png) Object watermark
2010-02-27 07:50:08.058 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.058 MythUIImage::LoadImage(171334736, watermark/seek.png) Object watermark
2010-02-27 07:50:08.058 MythUIImage::LoadImage found in cache :watermark-seek.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.059 MythUIImage::LoadImage(171023568, watermark/list.png) Object watermark
2010-02-27 07:50:08.059 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.059 MythUIImage::LoadImage(171328736, watermark/search_lists.png) Object watermark
2010-02-27 07:50:08.059 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.060 MythUIImage::LoadImage(171339560, watermark/tv_custom_record.png) Object watermark
2010-02-27 07:50:08.060 MythUIImage::LoadImage found in cache :watermark-tv_custom_record.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.060 MythUIImage::LoadImage(171329520, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:08.060 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.061 MythUIImage::LoadImage(171292024, watermark/volts.png) Object watermark
2010-02-27 07:50:08.061 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.061 MythUIImage::LoadImage(171272568, watermark/volts.png) Object watermark
2010-02-27 07:50:08.061 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 10
2010-02-27 07:50:08.062 MythUIImage::LoadImage(171263640, watermark/search_lists.png) Object watermark
2010-02-27 07:50:08.062 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.062 MythUIImage::LoadImage(171262240, watermark/list.png) Object watermark
2010-02-27 07:50:08.062 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.063 MythUIImage::LoadImage(171239520, watermark/list.png) Object watermark
2010-02-27 07:50:08.063 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.063 MythUIImage::LoadImage(171361408, watermark/tv.png) Object watermark
2010-02-27 07:50:08.063 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 14
2010-02-27 07:50:08.064 MythUIImage::LoadImage(171349888, watermark/search_new_titles.png) Object watermark
2010-02-27 07:50:08.064 MythUIImage::LoadImage found in cache :watermark-search_new_titles.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.064 MythUIImage::LoadImage(171354896, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.065 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 37
2010-02-27 07:50:08.100 NOT IN RAM CACHE, Adding, and adding to size :watermark-search_categories.png---1x-1.png: :8294400:
2010-02-27 07:50:08.100 MythUIHelper::CacheImage : Cache Count = :90: size :8294940:
2010-02-27 07:50:08.100 MythUIImage::LoadImage found in cache :watermark-search_categories.png---1x-1.png: RefCount = 2
2010-02-27 07:50:08.100 MythUIImage::LoadImage(171246664, watermark/seek.png) Object watermark
2010-02-27 07:50:08.100 MythUIImage::LoadImage(171265112, watermark/search_categories.png) Object watermark
2010-02-27 07:50:08.101 MythUIImage::LoadImage found in cache :watermark-seek.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.101 MythUIImage::LoadImage(171245264, watermark/search_time.png) Object watermark
2010-02-27 07:50:08.101 MythUIImage::LoadImage found in cache :watermark-search_categories.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.101 MythUIImage::LoadImage(171222496, watermark/list.png) Object watermark
2010-02-27 07:50:08.101 MythUIImage::LoadImage found in cache :watermark-search_time.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.101 MythUIImage::LoadImage found in cache :watermark-list.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.102 MythUIImage::LoadImage(171340256, watermark/tv.png) Object watermark
2010-02-27 07:50:08.102 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 15
2010-02-27 07:50:08.102 MythUIImage::LoadImage(171203664, watermark/search_lists.png) Object watermark
2010-02-27 07:50:08.103 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 10
2010-02-27 07:50:08.103 MythUIImage::LoadImage(171357792, watermark/tv.png) Object watermark
2010-02-27 07:50:08.103 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 16
2010-02-27 07:50:08.103 MythUIImage::LoadImage(171283520, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:08.104 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.104 MythUIImage::LoadImage(171241752, watermark/volts.png) Object watermark
2010-02-27 07:50:08.104 MythUIImage::LoadImage found in cache :watermark-volts.png---1x-1.png: RefCount = 11
2010-02-27 07:50:08.104 MythUIImage::LoadImage(171336064, watermark/tv.png) Object watermark
2010-02-27 07:50:08.105 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 17
2010-02-27 07:50:08.105 MythUIImage::LoadImage(171314072, watermark/tv.png) Object watermark
2010-02-27 07:50:08.105 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 18
2010-02-27 07:50:08.105 MythUIImage::LoadImage(171333584, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:08.106 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.106 MythUIImage::LoadImage(171218752, watermark/tv.png) Object watermark
2010-02-27 07:50:08.106 MythUIImage::LoadImage found in cache :watermark-tv.png---1x-1.png: RefCount = 19
2010-02-27 07:50:08.106 MythUIImage::LoadImage(171347960, watermark/tv_delete.png) Object watermark
2010-02-27 07:50:08.107 MythUIImage::LoadImage found in cache :watermark-tv_delete.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.107 MythUIImage::LoadImage(171206816, watermark/seek.png) Object watermark
2010-02-27 07:50:08.107 MythUIImage::LoadImage found in cache :watermark-seek.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.107 MythUIImage::LoadImage(171295960, watermark/settings.png) Object watermark
2010-02-27 07:50:08.108 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 25
2010-02-27 07:50:08.108 MythUIImage::LoadImage(171210920, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.108 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 38
2010-02-27 07:50:08.108 MythUIImage::LoadImage(171213952, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.109 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 39
2010-02-27 07:50:08.109 MythUIImage::LoadImage(171338112, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.109 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 40
2010-02-27 07:50:08.109 MythUIImage::LoadImage(171311384, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.110 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 41
2010-02-27 07:50:08.110 MythUIImage::LoadImage(171353184, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.110 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 42
2010-02-27 07:50:08.111 MythUIImage::LoadImage(171278336, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.111 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 43
2010-02-27 07:50:08.111 MythUIImage::LoadImage(171284656, watermark/tv_schedule.png) Object watermark
2010-02-27 07:50:08.111 MythUIImage::LoadImage found in cache :watermark-tv_schedule.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.112 MythUIImage::LoadImage(171250792, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.112 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 44
2010-02-27 07:50:08.112 MythUIImage::LoadImage(171020600, watermark/search_new_titles.png) Object watermark
2010-02-27 07:50:08.112 MythUIImage::LoadImage found in cache :watermark-search_new_titles.png---1x-1.png: RefCount = 6
2010-02-27 07:50:08.113 MythUIImage::LoadImage(171305736, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.113 NOT IN RAM CACHE, Adding, and adding to size :panels-with-drop.png--1920x1080.png: :8294400:
2010-02-27 07:50:08.113 MythUIHelper::CacheImage : Cache Count = :91: size :8294940:
2010-02-27 07:50:08.113 MythUIImage::LoadImage found in cache :panels-with-drop.png--1920x1080.png: RefCount = 2
2010-02-27 07:50:08.113 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 45
2010-02-27 07:50:08.113 MythUIImage::LoadImage(171342320, watermark/search_lists.png) Object watermark
2010-02-27 07:50:08.113 MythUIImage::LoadImage(171276808, watermark/search_new_titles.png) Object watermark
2010-02-27 07:50:08.114 MythUIImage::LoadImage found in cache :watermark-search_lists.png---1x-1.png: RefCount = 11
2010-02-27 07:50:08.114 MythUIImage::LoadImage found in cache :watermark-search_new_titles.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.114 MythUIImage::LoadImage(171315416, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.114 MythUIImage::LoadImage(171330944, watermark/settings.png) Object watermark
2010-02-27 07:50:08.114 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 46
2010-02-27 07:50:08.115 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 26
2010-02-27 07:50:08.115 MythUIImage::LoadImage(171351288, watermark/settings.png) Object watermark
2010-02-27 07:50:08.115 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 27
2010-02-27 07:50:08.115 MythUIImage::LoadImage(171024416, watermark/settings.png) Object watermark
2010-02-27 07:50:08.115 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 28
2010-02-27 07:50:08.115 MythUIImage::LoadImage(171231216, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.115 MythUIImage::LoadImage(171023120, watermark/settings.png) Object watermark
2010-02-27 07:50:08.116 MythUIImage::LoadImage found in cache :watermark-settings.png---1x-1.png: RefCount = 29
2010-02-27 07:50:08.116 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 7
2010-02-27 07:50:08.116 MythUIImage::LoadImage(171317952, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.116 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 8
2010-02-27 07:50:08.116 MythUIImage::LoadImage(171021344, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.117 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 9
2010-02-27 07:50:08.117 MythUIImage::LoadImage(171160384, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.117 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 10
2010-02-27 07:50:08.117 MythUIImage::LoadImage(171209528, watermark/cctv.png) Object watermark
2010-02-27 07:50:08.117 MythUIImage::LoadImage(171019216, watermark/netflix.png) Object watermark
2010-02-27 07:50:08.118 MythUIImage::LoadImage found in cache :watermark-cctv.png---1x-1.png: RefCount = 4
2010-02-27 07:50:08.118 MythUIImage::LoadImage found in cache :watermark-netflix.png---1x-1.png: RefCount = 11
2010-02-27 07:50:08.118 MythUIImage::LoadImage(171401424, watermark/cctv.png) Object watermark
2010-02-27 07:50:08.118 MythUIImage::LoadImage(171403096, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.118 MythUIImage::LoadImage found in cache :watermark-cctv.png---1x-1.png: RefCount = 5
2010-02-27 07:50:08.118 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 47
2010-02-27 07:50:08.118 MythUIImage::LoadImage(171406600, gradient-1950x15-255-255-255-0-0-0-50-1) Object titleboxshadow
2010-02-27 07:50:08.118 MythUIImage::LoadImage(171404552, watermark/dvd.png) Object watermark
2010-02-27 07:50:08.119 MythUIImage::LoadImage found in cache :watermark-dvd.png---1x-1.png: RefCount = 48
2010-02-27 07:50:08.119 MythUIImage::LoadImage found in cache :gradient-1950x15-255-255-255-0-0-0-50-1--1950x15.png: RefCount = 3
2010-02-27 07:50:08.119 MythUIImage::LoadImage(171636232, panels-with-drop.png) Object overlay
2010-02-27 07:50:08.119 MythUIImage::LoadImage found in cache :panels-with-drop.png--1920x1080.png: RefCount = 3
2010-02-27 07:50:08.166 NOT IN RAM CACHE, Adding, and adding to size :watermark-tv_searchlistings.png---1x-1.png: :8294400:
2010-02-27 07:50:08.167 MythUIHelper::CacheImage : Cache Count = :92: size :8294940:
2010-02-27 07:50:08.167 MythUIImage::LoadImage found in cache :watermark-tv_searchlistings.png---1x-1.png: RefCount = 2
2010-02-27 07:50:08.167 MythUIImage::LoadImage(171293432, watermark/tv_searchlistings.png) Object watermark
2010-02-27 07:50:08.167 MythUIImage::LoadImage found in cache :watermark-tv_searchlistings.png---1x-1.png: RefCount = 3
2010-02-27 07:50:08.176 Using NV NPOT texture extension
2010-02-27 07:50:08.484 MythContext: Connecting to backend server: 192.168.1.199:6543 (try 1 of 1)
2010-02-27 07:50:08.484 MythSocket(9ed1020:43): new socket
2010-02-27 07:50:08.484 MythSocket(9ed1020:43): attempting connect() to (192.168.1.199:6543)
2010-02-27 07:50:08.484 MythSocket(9ed1020:43): state change Idle -> Connected
2010-02-27 07:50:08.485 MythSocket(9ed1020:43): write -> 43 21      MYTH_PROTO_VERSION 50
2010-02-27 07:50:08.485 MythSocket(9ed1020:43): writeBlock(0x171753456, 29)
2010-02-27 07:50:08.490 MythSocket(9ed1020:43): readBlock(0x171540352, 8) called
2010-02-27 07:50:08.490 MythSocket(9ed1020:43): readBlock(0x171753520, 13) called
2010-02-27 07:50:08.490 MythSocket(9ed1020:43): read  <- 43 13      ACCEPT[]:[]50
2010-02-27 07:50:08.490 Using protocol version 50
2010-02-27 07:50:08.490 Empty FD_SET, woken up
2010-02-27 07:50:08.490 MythSocket(9ed1020:43): write -> 43 24      ANN Monitor feantecion 0
2010-02-27 07:50:08.490 ProcessAddRemoveQueues
2010-02-27 07:50:08.490 MythSocket(9ed1020:43): writeBlock(0x18446744072289873952, 32)
2010-02-27 07:50:08.490 Construct FD_SET
2010-02-27 07:50:08.490 Empty FD_SET, sleeping
2010-02-27 07:50:08.495 MythSocket(9ed1020:43): readBlock(0x18446744072289867040, 8) called
2010-02-27 07:50:08.495 MythSocket(9ed1020:43): readBlock(0x18446744072288105920, 2) called
2010-02-27 07:50:08.495 MythSocket(9ed1020:43): read  <- 43 2       OK
2010-02-27 07:50:08.495 Empty FD_SET, woken up
2010-02-27 07:50:08.495 ProcessAddRemoveQueues
2010-02-27 07:50:08.495 MythSocket(ffffffffab4677b8:44): new socket
2010-02-27 07:50:08.495 Construct FD_SET
2010-02-27 07:50:08.495 MythSocket(ffffffffab4677b8:44): attempting connect() to (192.168.1.199:6543)
2010-02-27 07:50:08.495 Empty FD_SET, sleeping
2010-02-27 07:50:08.496 MythSocket(ffffffffab4677b8:44): state change Idle -> Connected
2010-02-27 07:50:08.496 Empty FD_SET, woken up
2010-02-27 07:50:08.496 MythSocket(ffffffffab4677b8:44): write -> 44 24      ANN Monitor feantecion 1
2010-02-27 07:50:08.496 ProcessAddRemoveQueues
2010-02-27 07:50:08.496 MythSocket(ffffffffab4677b8:44): writeBlock(0x18446744072325596136, 32)
2010-02-27 07:50:08.496 Construct FD_SET
2010-02-27 07:50:08.496 Empty FD_SET, sleeping
2010-02-27 07:50:08.504 MythSocket(ffffffffab4677b8:44): readBlock(0x18446744072361436456, 8) called
2010-02-27 07:50:08.504 MythSocket(ffffffffab4677b8:44): readBlock(0x18446744072361737232, 2) called
2010-02-27 07:50:08.504 MythSocket(ffffffffab4677b8:44): read  <- 44 2       OK
2010-02-27 07:50:08.504 Empty FD_SET, woken up
2010-02-27 07:50:08.504 ProcessAddRemoveQueues
2010-02-27 07:50:08.504 Construct FD_SET
2010-02-27 07:50:08.504 Empty FD_SET, sleeping
2010-02-27 07:50:08.504 Empty FD_SET, woken up
2010-02-27 07:50:08.504 ProcessAddRemoveQueues
2010-02-27 07:50:08.504 Construct FD_SET
2010-02-27 07:50:08.505 Empty FD_SET, sleeping
2010-02-27 07:50:08.505 MythSocket(ffffffffab4677b8:44): UpRef: 1
2010-02-27 07:50:08.505 Empty FD_SET, woken up
2010-02-27 07:50:08.505 MythSocket(9ed1020:43): write -> 43 15      QUERY_TIME_ZONE
2010-02-27 07:50:08.505 ProcessAddRemoveQueues
2010-02-27 07:50:08.505 MythSocket(9ed1020:43): writeBlock(0x18446744072325454144, 23)
2010-02-27 07:50:08.505 Construct FD_SET
2010-02-27 07:50:08.505 Waiting on select..
2010-02-27 07:50:08.505 MythSocket(9ed1020:43): readBlock(0x18446744072326116408, 8) called
2010-02-27 07:50:08.506 MythSocket(9ed1020:43): readBlock(0x18446744072362117976, 50) called
2010-02-27 07:50:08.506 MythSocket(9ed1020:43): read  <- 43 50      America/Toronto[]:[]-18000[]:[]2010-02-27T07:50:08
2010-02-27 07:50:08.506 Got data on select
2010-02-27 07:50:08.506 Deleting stale sockets
2010-02-27 07:50:08.507 MythSocket(9db2dc8:21): DownRef: -1
2010-02-27 07:50:08.507 MSocketDevice::close: Closed socket 21
2010-02-27 07:50:08.507 MythSocket(9db2dc8:-1): delete socket
2010-02-27 07:50:08.507 MythSocket(ffffffffafa015f0:26): DownRef: -1
2010-02-27 07:50:08.507 MSocketDevice::close: Closed socket 26
2010-02-27 07:50:08.507 MythSocket(ffffffffafa015f0:-1): delete socket
2010-02-27 07:50:08.507 MythSocket(ffffffffafa019a0:27): DownRef: -1
2010-02-27 07:50:08.507 MSocketDevice::close: Closed socket 27
2010-02-27 07:50:08.507 MythSocket(ffffffffafa019a0:-1): delete socket
2010-02-27 07:50:08.507 MythSocket(ffffffffafa01b50:28): DownRef: -1
2010-02-27 07:50:08.507 MSocketDevice::close: Closed socket 28
2010-02-27 07:50:08.507 MythSocket(ffffffffafa01b50:-1): delete socket
2010-02-27 07:50:08.507 MythSocket(ffffffffafa01c50:29): DownRef: -1
2010-02-27 07:50:08.508 MSocketDevice::close: Closed socket 29
2010-02-27 07:50:08.508 MythSocket(ffffffffafa01c50:-1): delete socket
2010-02-27 07:50:08.508 MythSocket(ffffffffafa01f68:30): DownRef: -1
2010-02-27 07:50:08.508 MSocketDevice::close: Closed socket 30
2010-02-27 07:50:08.508 MythSocket(ffffffffafa01f68:-1): delete socket
2010-02-27 07:50:08.508 MythSocket(ffffffffafa02130:31): DownRef: -1
2010-02-27 07:50:08.508 MSocketDevice::close: Closed socket 31
2010-02-27 07:50:08.508 MythSocket(ffffffffafa02130:-1): delete socket
2010-02-27 07:50:08.508 MythSocket(ffffffffafa02310:32): DownRef: -1
2010-02-27 07:50:08.508 MSocketDevice::close: Closed socket 32
2010-02-27 07:50:08.508 MythSocket(ffffffffafa02310:-1): delete socket
2010-02-27 07:50:08.508 MythSocket(9db60e0:33): DownRef: -1
2010-02-27 07:50:08.508 MSocketDevice::close: Closed socket 33
2010-02-27 07:50:08.509 MythSocket(9db60e0:-1): delete socket
2010-02-27 07:50:08.509 MythSocket(9d23450:34): DownRef: -1
2010-02-27 07:50:08.509 MSocketDevice::close: Closed socket 34
2010-02-27 07:50:08.509 MythSocket(9d23450:-1): delete socket
2010-02-27 07:50:08.509 Processing ready reads
2010-02-27 07:50:08.509 MythSocketThread: Total read time: 0ms, on sockets {downref, 2ms}
2010-02-27 07:50:08.509 Reacquired ready read lock
2010-02-27 07:50:08.509 ProcessAddRemoveQueues
2010-02-27 07:50:08.509 Construct FD_SET
2010-02-27 07:50:08.509 Waiting on select..
2010-02-27 07:55:13.692 MythSocket(9ed1020:43): write -> 43 38      QUERY_IS_ACTIVE_BACKEND[]:[]feantecion
2010-02-27 07:55:13.692 MythSocket(9ed1020:43): writeBlock(0x166318640, 46)
2010-02-27 07:55:13.693 MythSocket(9ed1020:43): readBlock(0x165276400, 8) called
2010-02-27 07:55:13.693 MythSocket(9ed1020:43): readBlock(0x171628528, 5) called
2010-02-27 07:55:13.693 MythSocket(9ed1020:43): read  <- 43 5       FALSE
2010-02-27 07:55:13.693 Got data on select
2010-02-27 07:55:13.693 Processing ready reads
2010-02-27 07:55:13.693 MythSocketThread: Total read time: 0ms, on sockets
2010-02-27 07:55:13.693 Reacquired ready read lock
2010-02-27 07:55:13.694 ProcessAddRemoveQueues
2010-02-27 07:55:13.694 Construct FD_SET
2010-02-27 07:55:13.694 Waiting on select..
2010-02-27 07:55:13.695 MythUIImage(167465584): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.695 MythUIImage::LoadImage(167465584, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.696 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 14
2010-02-27 07:55:13.696 MythUIImage(167465952): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.696 MythUIImage::LoadImage(167465952, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.696 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 14
2010-02-27 07:55:13.697 MythUIImage(167472664): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.697 MythUIImage::LoadImage(167472664, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.697 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 14
2010-02-27 07:55:13.698 MythUIImage(171765264): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.698 MythUIImage::LoadImage(171765264, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.698 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 14
2010-02-27 07:55:13.699 MythUIImage(170892472): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.699 MythUIImage::LoadImage(170892472, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.699 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 15
2010-02-27 07:55:13.699 MythUIImage(170992696): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.699 MythUIImage::LoadImage(170992696, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.700 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 15
2010-02-27 07:55:13.700 MythUIImage(167384272): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.700 MythUIImage::LoadImage(167384272, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.700 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 15
2010-02-27 07:55:13.701 MythUIImage(170900216): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.701 MythUIImage::LoadImage(170900216, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.701 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 15
2010-02-27 07:55:13.702 MythUIImage(167462872): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.702 MythUIImage::LoadImage(167462872, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.702 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 16
2010-02-27 07:55:13.703 MythUIImage(167391520): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.703 MythUIImage::LoadImage(167391520, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.703 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 16
2010-02-27 07:55:13.703 MythUIImage(167565840): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.703 MythUIImage::LoadImage(167565840, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.704 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 16
2010-02-27 07:55:13.704 MythUIImage(167621952): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.704 MythUIImage::LoadImage(167621952, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.705 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 16
2010-02-27 07:55:13.705 MythUIImage(167368328): Load(), loading 'shared/uparrow.png' in foreground
2010-02-27 07:55:13.705 MythUIImage::LoadImage(167368328, shared/uparrow.png) Object upoff
2010-02-27 07:55:13.705 MythUIImage::LoadImage found in cache :shared-uparrow.png---1x-1.png: RefCount = 9
2010-02-27 07:55:13.706 MythUIImage(167584872): Load(), loading 'shared/downarrow.png' in foreground
2010-02-27 07:55:13.706 MythUIImage::LoadImage(167584872, shared/downarrow.png) Object dnoff
2010-02-27 07:55:13.706 MythUIImage::LoadImage found in cache :shared-downarrow.png---1x-1.png: RefCount = 9
2010-02-27 07:55:13.706 Warning: container 'exit prompt' is missing child 'title'
2010-02-27 07:55:13.747 MythUIImage(170971568): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.747 MythUIImage::LoadImage(170971568, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.747 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 17
2010-02-27 07:55:13.748 MythUIImage(167369960): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.748 MythUIImage::LoadImage(167369960, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.748 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 17
2010-02-27 07:55:13.748 MythUIImage(167587656): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.748 MythUIImage::LoadImage(167587656, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.749 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 17
2010-02-27 07:55:13.749 MythUIImage(167153464): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.749 MythUIImage::LoadImage(167153464, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.749 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 17
2010-02-27 07:55:13.750 MythUIImage(167652944): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.750 MythUIImage::LoadImage(167652944, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.751 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 18
2010-02-27 07:55:13.751 MythUIImage(170881256): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.751 MythUIImage::LoadImage(170881256, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.751 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 18
2010-02-27 07:55:13.752 MythUIImage(167569632): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.752 MythUIImage::LoadImage(167569632, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.752 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 18
2010-02-27 07:55:13.753 MythUIImage(167509544): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.753 MythUIImage::LoadImage(167509544, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.753 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 18
2010-02-27 07:55:13.754 MythUIImage(170887368): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.754 MythUIImage::LoadImage(170887368, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.754 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 19
2010-02-27 07:55:13.754 MythUIImage(178720208): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.755 MythUIImage::LoadImage(178720208, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.755 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 19
2010-02-27 07:55:13.755 MythUIImage(178721184): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.755 MythUIImage::LoadImage(178721184, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.756 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 19
2010-02-27 07:55:13.756 MythUIImage(178722232): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.756 MythUIImage::LoadImage(178722232, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.756 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 19
2010-02-27 07:55:13.757 MythUIImage(178723984): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.757 MythUIImage::LoadImage(178723984, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.757 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 20
2010-02-27 07:55:13.758 MythUIImage(178725160): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.758 MythUIImage::LoadImage(178725160, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.758 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 20
2010-02-27 07:55:13.759 MythUIImage(178726216): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.759 MythUIImage::LoadImage(178726216, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.759 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 20
2010-02-27 07:55:13.759 MythUIImage(178727264): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.759 MythUIImage::LoadImage(178727264, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.760 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 20
2010-02-27 07:55:13.760 MythUIImage(178728976): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.760 MythUIImage::LoadImage(178728976, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.761 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 21
2010-02-27 07:55:13.761 MythUIImage(178730072): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.761 MythUIImage::LoadImage(178730072, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.762 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 21
2010-02-27 07:55:13.762 MythUIImage(178731168): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.762 MythUIImage::LoadImage(178731168, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.762 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 21
2010-02-27 07:55:13.763 MythUIImage(178732216): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.763 MythUIImage::LoadImage(178732216, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.763 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 21
2010-02-27 07:55:13.764 MythUIImage(178733928): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.764 MythUIImage::LoadImage(178733928, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.764 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 22
2010-02-27 07:55:13.766 MythUIImage(178735136): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.766 MythUIImage::LoadImage(178735136, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.766 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 22
2010-02-27 07:55:13.767 MythUIImage(178736192): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.767 MythUIImage::LoadImage(178736192, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.767 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 22
2010-02-27 07:55:13.768 MythUIImage(178737200): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.768 MythUIImage::LoadImage(178737200, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.768 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 22
2010-02-27 07:55:13.769 MythUIImage(178738952): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.769 MythUIImage::LoadImage(178738952, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.769 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 23
2010-02-27 07:55:13.770 MythUIImage(178739824): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.770 MythUIImage::LoadImage(178739824, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.770 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 23
2010-02-27 07:55:13.770 MythUIImage(178741000): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.770 MythUIImage::LoadImage(178741000, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.771 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 23
2010-02-27 07:55:13.771 MythUIImage(178742648): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.771 MythUIImage::LoadImage(178742648, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.771 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 23
2010-02-27 07:55:13.772 MythUIImage(178745752): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.772 MythUIImage::LoadImage(178745752, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.772 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 24
2010-02-27 07:55:13.773 MythUIImage(180601128): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.773 MythUIImage::LoadImage(180601128, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.773 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 24
2010-02-27 07:55:13.774 MythUIImage(180601864): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.774 MythUIImage::LoadImage(180601864, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.774 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 24
2010-02-27 07:55:13.774 MythUIImage(180603648): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.775 MythUIImage::LoadImage(180603648, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.775 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 24
2010-02-27 07:55:13.775 MythUIImage(180606832): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.776 MythUIImage::LoadImage(180606832, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.776 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 25
2010-02-27 07:55:13.776 MythUIImage(180608408): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.776 MythUIImage::LoadImage(180608408, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.777 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 25
2010-02-27 07:55:13.777 MythUIImage(180609976): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.777 MythUIImage::LoadImage(180609976, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.777 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 25
2010-02-27 07:55:13.778 MythUIImage(180611824): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.778 MythUIImage::LoadImage(180611824, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.778 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 25
2010-02-27 07:55:13.779 MythUIImage(180615608): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.779 MythUIImage::LoadImage(180615608, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.779 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 26
2010-02-27 07:55:13.780 MythUIImage(180616688): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.780 MythUIImage::LoadImage(180616688, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.780 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 26
2010-02-27 07:55:13.780 MythUIImage(180619304): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.780 MythUIImage::LoadImage(180619304, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.781 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 26
2010-02-27 07:55:13.781 MythUIImage(180620224): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.781 MythUIImage::LoadImage(180620224, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.781 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 26
2010-02-27 07:55:13.782 MythUIImage(180624160): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.782 MythUIImage::LoadImage(180624160, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.782 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 27
2010-02-27 07:55:13.783 MythUIImage(180625696): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.783 MythUIImage::LoadImage(180625696, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.783 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 27
2010-02-27 07:55:13.783 MythUIImage(180627224): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.784 MythUIImage::LoadImage(180627224, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.784 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 27
2010-02-27 07:55:13.784 MythUIImage(180628864): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.784 MythUIImage::LoadImage(180628864, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.785 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 27
2010-02-27 07:55:13.785 MythUIImage(180632720): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.785 MythUIImage::LoadImage(180632720, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.786 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 28
2010-02-27 07:55:13.786 MythUIImage(180634720): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.786 MythUIImage::LoadImage(180634720, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.786 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 28
2010-02-27 07:55:13.787 MythUIImage(180635184): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.787 MythUIImage::LoadImage(180635184, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.787 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 28
2010-02-27 07:55:13.787 MythUIImage(180636800): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.787 MythUIImage::LoadImage(180636800, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.788 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 28
2010-02-27 07:55:13.789 MythUIImage(180640664): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.789 MythUIImage::LoadImage(180640664, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.789 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 29
2010-02-27 07:55:13.789 MythUIImage(180641584): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.789 MythUIImage::LoadImage(180641584, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.790 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 29
2010-02-27 07:55:13.790 MythUIImage(180643664): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.790 MythUIImage::LoadImage(180643664, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.790 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 29
2010-02-27 07:55:13.791 MythUIImage(180645336): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.791 MythUIImage::LoadImage(180645336, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.791 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 29
2010-02-27 07:55:13.792 MythUIImage(180648832): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.792 MythUIImage::LoadImage(180648832, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.792 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 30
2010-02-27 07:55:13.793 MythUIImage(180649816): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.793 MythUIImage::LoadImage(180649816, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.793 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 30
2010-02-27 07:55:13.793 MythUIImage(180651736): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.793 MythUIImage::LoadImage(180651736, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.794 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 30
2010-02-27 07:55:13.794 MythUIImage(180653344): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.794 MythUIImage::LoadImage(180653344, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.794 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 30
2010-02-27 07:55:13.795 MythUIImage(180656808): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.795 MythUIImage::LoadImage(180656808, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.795 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 31
2010-02-27 07:55:13.796 MythUIImage(180659168): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.796 MythUIImage::LoadImage(180659168, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.796 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 31
2010-02-27 07:55:13.796 MythUIImage(180658664): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.797 MythUIImage::LoadImage(180658664, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.797 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 31
2010-02-27 07:55:13.797 MythUIImage(180661192): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.797 MythUIImage::LoadImage(180661192, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.798 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 31
2010-02-27 07:55:13.798 MythUIImage(180665112): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.798 MythUIImage::LoadImage(180665112, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.799 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 32
2010-02-27 07:55:13.799 MythUIImage(180666192): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.799 MythUIImage::LoadImage(180666192, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.799 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 32
2010-02-27 07:55:13.800 MythUIImage(180668160): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.800 MythUIImage::LoadImage(180668160, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.800 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 32
2010-02-27 07:55:13.801 MythUIImage(180669808): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.801 MythUIImage::LoadImage(180669808, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.801 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 32
2010-02-27 07:55:13.802 MythUIImage(180670520): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.802 MythUIImage::LoadImage(180670520, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.802 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 33
2010-02-27 07:55:13.802 MythUIImage(180673640): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.802 MythUIImage::LoadImage(180673640, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.803 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 33
2010-02-27 07:55:13.803 MythUIImage(180677000): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.803 MythUIImage::LoadImage(180677000, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.803 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 33
2010-02-27 07:55:13.804 MythUIImage(180675888): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.804 MythUIImage::LoadImage(180675888, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.804 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 33
2010-02-27 07:55:13.805 MythUIImage(177397816): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.805 MythUIImage::LoadImage(177397816, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.805 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 34
2010-02-27 07:55:13.806 MythUIImage(177398968): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.806 MythUIImage::LoadImage(177398968, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.806 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 34
2010-02-27 07:55:13.806 MythUIImage(177401904): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.807 MythUIImage::LoadImage(177401904, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.807 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 34
2010-02-27 07:55:13.807 MythUIImage(177401072): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.807 MythUIImage::LoadImage(177401072, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.808 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 34
2010-02-27 07:55:13.808 MythUIImage(177406688): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.808 MythUIImage::LoadImage(177406688, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.809 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 35
2010-02-27 07:55:13.809 MythUIImage(177407840): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.809 MythUIImage::LoadImage(177407840, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.809 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 35
2010-02-27 07:55:13.810 MythUIImage(177410776): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.810 MythUIImage::LoadImage(177410776, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.810 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 35
2010-02-27 07:55:13.811 MythUIImage(177409944): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.811 MythUIImage::LoadImage(177409944, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.811 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 35
2010-02-27 07:55:13.812 MythUIImage(177414368): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.812 MythUIImage::LoadImage(177414368, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.812 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 36
2010-02-27 07:55:13.812 MythUIImage(177415656): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.813 MythUIImage::LoadImage(177415656, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.813 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 36
2010-02-27 07:55:13.813 MythUIImage(177417544): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.813 MythUIImage::LoadImage(177417544, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.814 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 36
2010-02-27 07:55:13.814 MythUIImage(177419376): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.814 MythUIImage::LoadImage(177419376, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.814 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 36
2010-02-27 07:55:13.815 MythUIImage(177422208): Load(), loading 'shared/lb-check-empty.png' in foreground
2010-02-27 07:55:13.815 MythUIImage::LoadImage(177422208, shared/lb-check-empty.png) Object checkoff
2010-02-27 07:55:13.815 MythUIImage::LoadImage found in cache :shared-lb-check-empty.png---1x-1.png: RefCount = 37
2010-02-27 07:55:13.816 MythUIImage(177423360): Load(), loading 'shared/lb-check-half.png' in foreground
2010-02-27 07:55:13.816 MythUIImage::LoadImage(177423360, shared/lb-check-half.png) Object checkhalf
2010-02-27 07:55:13.816 MythUIImage::LoadImage found in cache :shared-lb-check-half.png---1x-1.png: RefCount = 37
2010-02-27 07:55:13.816 MythUIImage(177425784): Load(), loading 'shared/lb-check-full.png' in foreground
2010-02-27 07:55:13.817 MythUIImage::LoadImage(177425784, shared/lb-check-full.png) Object checkfull
2010-02-27 07:55:13.817 MythUIImage::LoadImage found in cache :shared-lb-check-full.png---1x-1.png: RefCount = 37
2010-02-27 07:55:13.817 MythUIImage(177427400): Load(), loading 'shared/lb-arrow.png' in foreground
2010-02-27 07:55:13.817 MythUIImage::LoadImage(177427400, shared/lb-arrow.png) Object buttonarrow
2010-02-27 07:55:13.818 MythUIImage::LoadImage found in cache :shared-lb-arrow.png---1x-1.png: RefCount = 37
2010-02-27 07:55:15.530 Deleting UPnP client...
2010-02-27 07:55:15.531 WorkerThread:Run - Exiting: HTTP_WorkerThread
2010-02-27 07:55:15.532 UPnp - Destructor
2010-02-27 07:55:15.532 UPnp::CleanUp() - disabling SSDP notifications
2010-02-27 07:55:15.533 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.533 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::upnp:rootdevice
Cache  =max-age=3600
2010-02-27 07:55:15.697 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.697 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =upnp:rootdevice
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::upnp:rootdevice
Cache  =max-age=3600
2010-02-27 07:55:15.697 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.697 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
Cache  =max-age=3600
2010-02-27 07:55:15.846 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.846 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6
Cache  =max-age=3600
2010-02-27 07:55:15.846 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.846 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-02-27 07:55:15.921 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.921 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:device:MediaRenderer:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:device:MediaRenderer:1
Cache  =max-age=3600
2010-02-27 07:55:15.921 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:15.922 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-02-27 07:55:16.016 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:16.016 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-mythtv-org:service:MythTv:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-mythtv-org:service:MythTv:1
Cache  =max-age=3600
2010-02-27 07:55:16.016 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:16.016 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-02-27 07:55:16.064 MSocketDevice::close: Closed socket 9
2010-02-27 07:55:16.064 SSDP::ProcessData - requestLine: NOTIFY * HTTP/1.1
2010-02-27 07:55:16.064 SSDP::ProcessNotify ...
DescURL=http://192.168.1.198:6547/getDeviceDesc
NTS    =ssdp:byebye
NT     =urn:schemas-upnp-org:service:ConnectionManager:1
USN    =uuid:5a4d948e-ef19-483b-8f1b-dbf60fa8cba6::urn:schemas-upnp-org:service:ConnectionManager:1
Cache  =max-age=3600
2010-02-27 07:55:16.065 MSocketDevice::close: Closed socket 14
2010-02-27 07:55:16.065 MSocketDevice::close: Closed socket 15
2010-02-27 07:55:16.065 MSocketDevice::close: Closed socket 16
2010-02-27 07:55:16.066 UPnp::CleanUp() - deleted SSDP
2010-02-27 07:55:16.116 MythSocket(9ed1020:43): DownRef: -1
2010-02-27 07:55:16.116 MythSocket(9ed1020:43): state change Connected -> Idle
2010-02-27 07:55:16.116 MSocketDevice::close: Closed socket 43
2010-02-27 07:55:16.117 MythSocket(9ed1020:-1): delete socket
2010-02-27 07:55:16.117 MythSocket(ffffffffab4677b8:44): DownRef: 0
2010-02-27 07:55:16.117 Got data on select
2010-02-27 07:55:16.117 Processing ready reads
2010-02-27 07:55:16.118 MythSocketThread: Total read time: 0ms, on sockets
2010-02-27 07:55:16.118 Reacquired ready read lock
2010-02-27 07:55:16.118 ProcessAddRemoveQueues
2010-02-27 07:55:16.118 Construct FD_SET
2010-02-27 07:55:16.118 Empty FD_SET, sleeping
2010-02-27 07:55:16.154 Empty FD_SET, woken up
2010-02-27 07:55:16.154 MythSocketThread: readyread thread exit

```

 Dave

---

### Post by ian dobson on 2010-02-28
Hi Dave,

Thanks for the log file, unfortunatly there's not much of interest in it.

Could you try starting your frontend nornally, go to the ternimal 
1) kill mythlcdserver if it's still running 
2) then manually start mythlcdserver with:-
/usr/bin/mythlcdserver -v all

And dump the debug info here.

Regards
Ian Dobson

---

### Post by rodercot on 2010-02-28
Hi Ian,

 Here you are again so I launched mythfrontend autostart then via ssh I killall mythlcdserver and then re-started mythlcdserver with your options. This does not get the LCD working properly by the way. The only way to do that is shutdown the frontend and restart it manually. 

 ```
xbmc@feantecion:~$ killall mythlcdserver
xbmc@feantecion:~$ /usr/bin/mythlcdserver -v all
2010-02-28 08:35:00.333 (old)Settings::ReadSettings(settings.txt) - No such file
2010-02-28 08:35:00.334 Using runtime prefix = /usr
2010-02-28 08:35:00.334 Using configuration directory = /home/xbmc/.mythtv
2010-02-28 08:35:00.335 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt)                                                                                                         - 'DBHostName' = 'xxx.xxx.x.xxx'.
2010-02-28 08:35:00.335 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt)                                                                                                         - 'DBUserName' = 'mythtv'.
2010-02-28 08:35:00.335 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt)                                                                                                         - 'DBName' = 'mythconverg'.
2010-02-28 08:35:00.335 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt)                                                                                                         - 'DBType' = 'QMYSQL3'.
2010-02-28 08:35:00.335 (old)Settings::ReadSettings(/usr/share/mythtv/mysql.txt)                                                                                                         - 'DBPassword' = 'xxxxxxxx'.
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(/usr/etc/mythtv/mysql.txt) -                                                                                                         No such file
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt                                                                                                        ) - 'DBHostName' = 'xxx.xxx.x.xx'.
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt                                                                                                        ) - 'DBUserName' = 'mythtv'.
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt                                                                                                        ) - 'DBName' = 'mythconverg'.
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt                                                                                                        ) - 'DBType' = 'QMYSQL3'.
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(/home/xbmc/.mythtv/mysql.txt                                                                                                        ) - 'DBPassword' = 'xxxxxxxx'.
2010-02-28 08:35:00.336 (old)Settings::ReadSettings(./mysql.txt) - No such file
2010-02-28 08:35:00.337 Empty LocalHostName.
2010-02-28 08:35:00.337 Using localhost value of feantecion
2010-02-28 08:35:00.338 MCP::DefaultUPnP() - No default UPnP backend
2010-02-28 08:35:00.338 Testing network connectivity to '192.168.1.199'
2010-02-28 08:35:00.344 Clearing Settings Cache.
2010-02-28 08:35:00.359 New DB connection, total: 1
2010-02-28 08:35:05.414 Connected to database 'mythconverg' at host: 192.168.1.199
2010-02-28 08:35:05.414 Closing DB connection named 'DBManager0'
2010-02-28 08:35:05.415 Clearing Settings Cache.
2010-02-28 08:35:05.415 Enabling Settings Cache.
2010-02-28 08:35:05.415 Clearing Settings Cache.
2010-02-28 08:35:10.467 Connected to database 'mythconverg' at host: 192.168.1.199
2010-02-28 08:35:10.468 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname = 'feantecio                                                           n' ;"
2010-02-28 08:35:10.470 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MasterServerIP' AND hostname IS NULL;"
2010-02-28 08:35:10.471 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname = 'feantec                                                           ion' ;"
2010-02-28 08:35:10.472 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'MasterServerPort' AND hostname IS NULL;"
2010-02-28 08:35:10.473 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'WOLbackendCommand' AND hostname = 'feante                                                           cion' ;"
2010-02-28 08:35:10.474 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'WOLbackendCommand' AND hostname IS NULL;"
2010-02-28 08:35:10.474 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'BackendConnectRetry' AND hostname = 'fean                                                           tecion' ;"
2010-02-28 08:35:10.475 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'BackendConnectRetry' AND hostname IS NULL                                                           ;"
2010-02-28 08:35:10.476 MythContext: Connecting to backend server: 192.168.1.199:6543 (try 1 of 1)
2010-02-28 08:35:10.476 MythSocket(874f648:8): new socket
2010-02-28 08:35:10.476 MythSocket(874f648:8): attempting connect() to (192.168.1.199:6543)
2010-02-28 08:35:10.477 MythSocket(874f648:8): state change Idle -> Connected
2010-02-28 08:35:10.477 MythSocket(874f648:8): write ->  8 21      MYTH_PROTO_VERSION 50
2010-02-28 08:35:10.477 MythSocket(874f648:8): writeBlock(0x141844496, 29)
2010-02-28 08:35:10.477 MythSocket(874f648:8): readBlock(0x141883048, 8) called
2010-02-28 08:35:10.478 MythSocket(874f648:8): readBlock(0x141932208, 13) called
2010-02-28 08:35:10.478 MythSocket(874f648:8): read  <-  8 13      ACCEPT[]:[]50
2010-02-28 08:35:10.478 Using protocol version 50
2010-02-28 08:35:10.478 MythSocket(874f648:8): write ->  8 24      ANN Monitor feantecion 0
2010-02-28 08:35:10.478 MythSocket(874f648:8): writeBlock(0x141883648, 32)
2010-02-28 08:35:10.484 MythSocket(874f648:8): readBlock(0x141883176, 8) called
2010-02-28 08:35:10.484 MythSocket(874f648:8): readBlock(0x141883808, 2) called
2010-02-28 08:35:10.484 MythSocket(874f648:8): read  <-  8 2       OK
2010-02-28 08:35:10.485 MythSocket(874fa70:9): new socket
2010-02-28 08:35:10.485 MythSocket(874fa70:9): attempting connect() to (192.168.1.199:6543)
2010-02-28 08:35:10.485 MythSocket(874fa70:9): state change Idle -> Connected
2010-02-28 08:35:10.485 MythSocket(874fa70:9): write ->  9 24      ANN Monitor feantecion 1
2010-02-28 08:35:10.485 MythSocket(874fa70:9): writeBlock(0x141844360, 32)
2010-02-28 08:35:10.487 MythSocket(874fa70:9): readBlock(0x141884512, 8) called
2010-02-28 08:35:10.487 MythSocket(874fa70:9): readBlock(0x141844560, 2) called
2010-02-28 08:35:10.487 MythSocket(874fa70:9): read  <-  9 2       OK
2010-02-28 08:35:10.488 MythSocketThread: readyread thread start
2010-02-28 08:35:10.488 ProcessAddRemoveQueues
2010-02-28 08:35:10.488 Construct FD_SET
2010-02-28 08:35:10.488 Empty FD_SET, sleeping
2010-02-28 08:35:10.489 MythSocket(874fa70:9): UpRef: 1
2010-02-28 08:35:10.489 Empty FD_SET, woken up
2010-02-28 08:35:10.489 ProcessAddRemoveQueues
2010-02-28 08:35:10.489 Construct FD_SET
2010-02-28 08:35:10.489 Waiting on select..
2010-02-28 08:35:10.490 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDServerPort' AND hostname = 'feantecion                                                           ' ;"
2010-02-28 08:35:10.490 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDServerPort' AND hostname IS NULL;"
2010-02-28 08:35:10.492 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDHost' AND hostname = 'feantecion' ;"
2010-02-28 08:35:10.493 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDHost' AND hostname IS NULL;"
2010-02-28 08:35:10.494 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDPort' AND hostname = 'feantecion' ;"
2010-02-28 08:35:10.495 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDPort' AND hostname IS NULL;"
2010-02-28 08:35:10.496 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDEnable' AND hostname = 'feantecion' ;"
2010-02-28 08:35:10.895 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDBigClock' AND hostname = 'feantecion'                                                            ;"
2010-02-28 08:35:10.896 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDTimeFormat' AND hostname = 'feantecion                                                           ' ;"
2010-02-28 08:35:10.897 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDTimeFormat' AND hostname IS NULL;"
2010-02-28 08:35:10.898 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'TimeFormat' AND hostname = 'feantecion' ;                                                           "
2010-02-28 08:35:10.899 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'DateFormat' AND hostname = 'feantecion' ;                                                           "
2010-02-28 08:35:10.900 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowMusic' AND hostname = 'feantecion'                                                            ;"
2010-02-28 08:35:10.901 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowMusicItems' AND hostname = 'feante                                                           cion' ;"
2010-02-28 08:35:10.902 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowTime' AND hostname = 'feantecion'                                                            ;"
2010-02-28 08:35:10.902 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowChannel' AND hostname = 'feantecio                                                           n' ;"
2010-02-28 08:35:10.904 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowGeneric' AND hostname = 'feantecio                                                           n' ;"
2010-02-28 08:35:10.905 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowVolume' AND hostname = 'feantecion                                                           ' ;"
2010-02-28 08:35:10.906 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowMenu' AND hostname = 'feantecion'                                                            ;"
2010-02-28 08:35:10.907 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDShowRecStatus' AND hostname = 'feantec                                                           ion' ;"
2010-02-28 08:35:10.908 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDBacklightOn' AND hostname = 'feantecio                                                           n' ;"
2010-02-28 08:35:10.909 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDHeartBeatOn' AND hostname = 'feantecio                                                           n' ;"
2010-02-28 08:35:10.910 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDPopupTime' AND hostname = 'feantecion'                                                            ;"
2010-02-28 08:35:10.911 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'LCDKeyString' AND hostname = 'feantecion'                                                            ;"
2010-02-28 08:35:10.912 MSqlQuery::exec() "SELECT cardid FROM capturecard ORDER BY cardid"
2010-02-28 08:35:10.913 MythSocket(874f648:8): write ->  8 35      QUERY_REMOTEENCODER 1[]:[]GET_STATE
2010-02-28 08:35:10.913 MythSocket(874f648:8): writeBlock(0x18446744072373725256, 43)
2010-02-28 08:35:10.913 MythSocket(874f648:8): readBlock(0x18446744072373685816, 8) called
2010-02-28 08:35:10.913 MythSocket(874f648:8): readBlock(0x18446744072373690984, 1) called
2010-02-28 08:35:10.914 MythSocket(874f648:8): read  <-  8 1       0
2010-02-28 08:35:10.914 Got data on select
2010-02-28 08:35:10.914 Processing ready reads
2010-02-28 08:35:10.914 MythSocketThread: Total read time: 0ms, on sockets
2010-02-28 08:35:10.914 Reacquired ready read lock
2010-02-28 08:35:10.914 ProcessAddRemoveQueues
2010-02-28 08:35:10.914 Construct FD_SET
2010-02-28 08:35:10.914 Waiting on select..
```

 Thanks,

 Dave

---

### Post by ian dobson on 2010-02-28
Hi Dave,

Sorry but I have no idea what's wrong. Maybe someone else has an idea.

Regards
Ian Dobson

---

### Post by Neon Dusk on 2010-02-28
Can we recap where we're at :-

**Automatic Login & Auto Frontend start**
(set with a login delay of 10 secs)
LCD doesn't display info unless mythfrontend is restarted
Is the mythlcdserver process started ( ps aux | grep -v grep | grep mythlcdserver
)? Can you manually telnet to 127.0.0.1 6545?

**Auto Frontend start disabled**
If you manually start mythfrontend do you still get the same issue?
Manually starting mythlcdserver then mythfrontend works?

---

### Post by rodercot on 2010-03-01
> **Neon Dusk said:**
> Can we recap where we're at :-

**Automatic Login & Auto Frontend start**
(set with a login delay of 10 secs)
LCD doesn't display info unless mythfrontend is restarted
Is the mythlcdserver process started ( ps aux | grep -v grep | grep mythlcdserver
)? Can you manually telnet to 127.0.0.1 6545?

**Auto Frontend start disabled**
If you manually start mythfrontend do you still get the same issue?
Manually starting mythlcdserver then mythfrontend works?

 If I set the auto-login delay any higher I get a login window at bootup with a countdown of the login delay and then it logs in with no differnce in the process. Same results.

 Correct - Lcd does not display anything upon first boot it loads the frontend and lcdproc finds a client but only displays the time and nothing else, I use appswitch to switch btween myth and xbmc so if I proceed to switch to xbmc and then back to mythfrontend I have a display with information. On a fresh boot after mythfrontend has tried to connect and IS running this is what grep mythlcdserver says.
 
 ```
xbmc@feantecion:~$ ps aux | grep -v grep | grep mythlcdserver
xbmc      1706  0.3  1.1 116560 42564 ?        Sl   07:19   0:00 /usr/bin/mythlcdserver -v none
xbmc@feantecion:~$
```

 Starting manually via the command line produces the same results. if I close myth and restart it again via command line the display connects on the first try and it works.

 manually starting mythlcdserver FIRST before mythfrontend like so

 ```
xbmc@feantecion:~$ mythlcdserver
2010-03-01 07:28:22.720 Using runtime prefix = /usr
2010-03-01 07:28:22.720 Using configuration directory = /home/xbmc/.mythtv
2010-03-01 07:28:22.721 Empty LocalHostName.
2010-03-01 07:28:22.742 New DB connection, total: 1
2010-03-01 07:28:27.792 Closing DB connection named 'DBManager0'
2010-03-01 07:28:32.869 Using protocol version 50
```

 then starting mythfrontend via the command line yes that works and the lcd displays information. 

 So the problem seems to be that mythlcdserver is not starting on cold boots at all or is delayed until the system is running.

 I have changed LCDd rc.d defaults from 10 - 99 and it makes no difference and remember this has been tested against two different lcd devices and two different version of lcdproc 
 
 cvs 5.2 on my Vlsys Mplay hd44780 in my Zalman chassis and the imon lcd with the vanilla deb that is included with mythbuntu 9.10 neither system works as it should indicating the problem is with mythbuntu.

 rgds,

 Dave

---

### Post by ian dobson on 2010-03-01
Hi,

So does xbmc start on login, as well as mythfrontend, sorry I don't know "appswitch".

If yes could you try disabling xbmc and testing.

Regards
Ian Dobson

---

### Post by rodercot on 2010-03-01
> **ian dobson said:**
> Hi,

So does xbmc start on login, as well as mythfrontend, sorry I don't know "appswitch".

If yes could you try disabling xbmc and testing.

Regards
Ian Dobson

 Hi Ian,

 No XBMC does not run at startup at all. I have it setup to autostart as a test only but it is not enabled by default. 
 
 appwitch is a script that runs via irexec and it tied to the Live TV button on a remote. So if mythfrontend is running and I hit LiveTV button then the script killsall mythfrontend.real and starts xbmc then the same in reverse if I hit LiveTV button again. I do not have the LCD enabled in XBMC at all. 
 
 Here is some info about appswitch

 [http://www.xpmediacentre.com.au/community/linux-tutorials-guides/33370-myth-tweak-switch-between-myth-xbmc-via-remote.html](http://www.xpmediacentre.com.au/community/linux-tutorials-guides/33370-myth-tweak-switch-between-myth-xbmc-via-remote.html)

 rgds,

 Dave

---

### Post by Neon Dusk on 2010-03-01
> **rodercot said:**
> If I set the auto-login delay any higher I get a login window at bootup with a countdown of the login delay and then it logs in with no differnce in the process. Same results.


You should still see the login window & countdown timer with a delay of 10s.

Unable to test this at the moment but you could try starting mythlcdserver before mythfrontend.real in the mythbuntu /usr/bin/mythfrontend wrapper script.

---

### Post by x-wolf on 2010-03-01
I have tried almost all ideas above, but none are working for me. I even tried to suspend the login with 30 seconds, but still mythlcdserver did not startup. As soon as I have closed mythfrontend and openend it again, mythlcdserver is working. 
 
What else can I try? (I also tried to change the things in /etc/hosts as shown above, but that is also not working for me)

---

### Post by x-wolf on 2010-03-01
I just fixed my problem, sort of....
 
I've changed the ip adress of mythbackend back to localhost (on my machine mythfrontend and mythbackend are running on the same machine) and that fixes the problem after a reboot. So now I'm sure it is something with the ip adress. What I don't understand is what mythbackend has to do with it. Anyone?

---

### Post by rodercot on 2010-03-01
> **Neon Dusk said:**
> You should still see the login window & countdown timer with a delay of 10s.

Unable to test this at the moment but you could try starting mythlcdserver before mythfrontend.real in the mythbuntu /usr/bin/mythfrontend wrapper script.

 At 10 seconds I do not see the login screen at 11 seconds I do. I will try the other option tonight and reply. 

 @x-wolf, I am not sure how that would be an option with separate machines unless every F/E address was added to the table and dhcp was turned off on each frontend so they stayed fixed addresses. 

 Dave

---

### Post by Neon Dusk on 2010-03-01
@x-wolf mythlcdserver will use the ip address to connect to BE database and retrieve settings. You could try removing the ubuntu network-manager and setting a static IP in /etc/network/interfaces (this would just need to be done the backend). Edit: Although if rodercot has the same issue with a remote frontend it kind of rules out network-manager being a problem.

@rodercot
I think putting
```

/usr/bin/mythlcdserver --logfile /var/log/mythtv/mythlcdserver.log -v all &
```

into /usr/bin/mythfrontend before the ```
exec /usr/bin/mythfrontend.real --logfile "${MYTHFELOG}" ${MYTHFRONTEND_OPTS}
``` line should work and give a full mythlcdserver log. Backup the original /usr/bin/mythfrontend file first.

---

### Post by rodercot on 2010-03-01
> **Neon Dusk said:**
> @x-wolf mythlcdserver will use the ip address to connect to BE database and retrieve settings. You could try removing the ubuntu network-manager and setting a static IP in /etc/network/interfaces (this would just need to be done the backend). Edit: Although if rodercot has the same issue with a remote frontend it kind of rules out network-manager being a problem.

@rodercot
I think putting
```

/usr/bin/mythlcdserver --logfile /var/log/mythtv/mythlcdserver.log -v all &
```

into /usr/bin/mythfrontend before the ```
exec /usr/bin/mythfrontend.real --logfile "${MYTHFELOG}" ${MYTHFRONTEND_OPTS}
``` line should work and give a full mythlcdserver log. Backup the original /usr/bin/mythfrontend file first.

 Neon Dusk,

 Thanks for that tid_bit, and to you and Ian for the assistance along the way. That worked and it shows no adverse affect by looking at the log files. the lcd log shows everything starting and connecting fine and the mythfrontend log shows it connecting on try 1 as it should be.
 
 it looks like the the bug report that you posted of which I have kept up to date with my findings and this thread has been accepted so lets hope by .23 it gets figured out. 
 
 Regards,

 Dave

---

### Post by x-wolf on 2010-03-04
@Neon Dusk: I've considered to setup a static address in networkinterfaces, but the machine uses wlan instead of lan. As far as I know you can only setup wlan using the network manager. And please do say that I have to change it to a wired solution, my girlfriend will not like that in our living room! :D

---

### Post by ian dobson on 2010-03-04
> **x-wolf said:**
> @Neon Dusk: I've considered to setup a static address in networkinterfaces, but the machine uses wlan instead of lan. As far as I know you can only setup wlan using the network manager. And please do say that I have to change it to a wired solution, my girlfriend will not like that in our living room! :D

Can't you just setup your wireless connection from the terminal (no X) by configuring /etc/network/interfaces and wpasupplement. I've never done this on ubuntu but I've done it on several embeded linux systems.

Have a look here [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) it's abit outdated bt things shouldn't have changed that much.

Regards
Ian Dobson

---

### Post by bgiannes on 2010-04-20
just readed through this thread, as i have the same problem.

until this is fixed, in .23?

to start the LCD service correct i just....

Utilities/Setup->Setup->Appearance->LCD device display and hit "finished"  This then restarts the LCD services and the LCD read out starts working.  So you have to do this manual every reboot.

---

### Post by x-wolf on 2010-08-17
Just to complete this thread. I finally fixed my problem with the LCDd daemon at startup. It had nothing todo with LCDd but with a bug in the startupscripts of Ubuntu. 
 
In #54 I found the answer to fix my startup problem:L [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506/+index?comments=all)
 
Man, this bug has cost me so much time to fix!

---

