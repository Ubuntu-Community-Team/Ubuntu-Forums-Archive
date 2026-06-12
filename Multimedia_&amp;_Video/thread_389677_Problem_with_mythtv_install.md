---
title: "Problem with mythtv install"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-03-21
I just installed mythtv and I'm trying to get it working. 

I used this tutorial. [www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150](www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150)

When I try testing out my ivtv after installing it, i tested it with mplayer. The video is static. I know the connections should be working because it is the same as my previous windows setup. By the way, I am using a PVR-150

Also, I changed the theme from the default and the render to OpenGL and now my mythfrontend is a black screen. How can I restore defaults? I try running mythtv-setup and i get the same blank screen.

Also, I tried to get my Nvidia 5200 tvout working, and now my whole ubuntu doesn't start up because of X.  I think I am just going to reinstall everything all over again.

Thank you for the help
-Hans

---

### Post by fenian on 2007-03-21
If you choose to reinstall and start over use [this]("https://help.ubuntu.com/community/Install_IVTV_Edgy?highlight=%28ivtv%29") guide to install ivtv and [this]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop?highlight=%28mythtv%29") guide to install mythtv.
To get tvout working,install the latest nvidia drivers  with the envy script which can be found [here]("http://albertomilone.com/nvidia_scripts1.html").

After you install the new drivers  run in a terminal 

> gksudo nvidia-settings

A window will pop up which will allow you to detect the T.V. and set it up for twinview or as a seperate x screen,make sure to save to X configuration before you quit.

---

### Post by hansoffate on 2007-03-21
I followed the tutorial and I have this problem.

root@mythtv:/home/hansoffate# sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
QSettings: error creating /home/mythtv/.qt
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
root@mythtv:/home/hansoffate# ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD

What should I do?  My backend isn't starting.

Thank you
-Hans

---

### Post by SyvanX on 2007-03-21
Your mythbackend log might have some information about why the backend can't start. 

```
cat /var/log/mythtv/mythbackend.log
```

---

### Post by bdogg64 on 2007-03-21
I had the same problem. I used the following command

sudo nano /etc/init.d/mythtv-backend 

and changed the user to my username

then i was able to start the mythtv-backend

I hope this helps

---

### Post by majoridiot on 2007-03-21
> **bdogg64 said:**
> I had the same problem. I used the following command

sudo nano /etc/init.d/mythtv-backend 

and changed the user to my username

then i was able to start the mythtv-backend

I hope this helps

i would **not** recommend making this change to the init script.  adding your main user to the
mythtv group will allow you to run all mythtv apps as your "regular" user.  do:

```
# sudo usermod -a -G mythtv USERNAME
```

where USERNAME is your main account.  **LOG OUT** and then back in for the changes to
take effect.

---

### Post by bdogg64 on 2007-03-21
> **majoridiot said:**
> i would **not** recommend making this change to the init script.  adding your main user to the
mythtv group will allow you to run all mythtv apps as your "regular" user.  do:

```
# sudo usermod -a -G mythtv USERNAME
```

where USERNAME is your main account.  **LOG OUT** and then back in for the changes to
take effect.

thanks for the tip

---

### Post by hansoffate on 2007-03-21
I tried what bdogg64 said during my lunch break while I was at home.  My front end still can not connect to the backend.

I think partially why I ran into this problem is because when I installed the system and mythtv, I already had a mythtv folder.  When I tried logging in as mythtv, it wouldn't allow me to saying that the $HOME directory should only be accessed by mythtv (apparrently other users could access it).  

I think I have messed around with mythtv settings to much and I just want to go through the whole process over again.  Is there a way to completely remove mythtv so that when I install it again it was as if I didn't install it before?

I tried doing a removal of all the myth components i have on my box but that didn't do the trick. (It didnt re-setup the mythtv user).

I don't want to reformat again and reinstall Ubuntu for the 4th time in 24 hours.  I finally got my Nvidia FX5200 card working with TV-Out and I think I setup my PVR-150 with LIRC correctly so that the IR Blaster works.  I would hate to do all of that again.

What do you think I should do?

Thank you for the help,
-Hans

---

### Post by majoridiot on 2007-03-21
> **hansoffate said:**
> I tried what bdogg64 said during my lunch break while I was at home.  My front end still can not connect to the backend.
Thank you for the help,
-Hans

to completely remove:

if the frontend and backend are on the same machine:

```
 # sudo apt-get remove --purge mythtv*
```

if not, do that command on both the frontend and backend machines.

then, on both machines if needed, check these: 

delete any remaining /home/mythtv folder
delete the /home/<your regular username>/.mythtv hidden folder
delete /etc/mythtv

also see fenian's post- top of the next page.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by hansoffate on 2007-03-21
MajorIdiot-  Thank you.  I will try that when I get home tonight at 5 PST.  I'll post back with my results.

:EDIT IN:
How do I make sure the recordings folder has the correct permissions?  I have my big recordings partition mounted to /home.  Should I make a new folder so it stores recordings like this /home/recordings?  How would I do this?

Thank you everyone for all the help,
-Hans

---

### Post by fenian on 2007-03-21
In addition to the command majoridiot posted I would also run this
> 
sudo apt-get remove --purge mysql-server mysql-client mysql-common

---

### Post by majoridiot on 2007-03-21
> **fenian said:**
> In addition to the command majoridiot posted I would also run this

good call.  edited my post, as the DB drop would be redundant.

---

### Post by hansoffate on 2007-03-21
Mythtv won't uninstall with that command.  Here is the error

root@mythtv:/home# sudo apt-get remove --purge mythtv*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mythtv is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mythtv:/home# 

So instead i did a complete removal of all things that have myth in it from the synaptic package manager.  Will that work?

Also when I did the other command I get this.
root@mythtv:/home# sudo apt-get remove --purge mysql-server mysql-client mysql-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-client is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 libopenexr2c2a pwgen libarts1c2a kdelibs4c2a libdc1394-13
  libxml-libxml-common-perl libnet-daemon-perl libvorbisfile3 libqt3-mt-mysql
  libxml-namespacesupport-perl python-mysqldb fftw2 php5-mysqli kdelibs-data
  libdbi-perl libdbd-mysql-perl libjack0.100.0-0 mysql-server-5.0 liblualib50
  mysql-client-5.0 mysql-common gcc-3.4-base libavformat0d libplrpc-perl
  dvdauthor libmysqlclient15off python-imaging libavahi-qt3-1
  libxml-libxml-perl libapache2-mod-auth-mysql mysql-server libxml-sax-perl
  ffmpeg libmjpegtools0c2a phpmyadmin libcdaudio1 libxml-simple-perl
  libavcodec0d mjpegtools php5-mysql liblua50 libg2c0 libquicktime0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libapache2-mod-auth-mysql* libdbd-mysql-perl* libmysqlclient15off*
  libqt3-mt-mysql* mysql-client-5.0* mysql-common* mysql-server*
  mysql-server-5.0* php5-mysql* php5-mysqli* phpmyadmin* python-mysqldb*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 103MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

ALthough it seems like it removes alot more then just that.  Is that ok?

Thanks for the help
-Hans

---

### Post by majoridiot on 2007-03-21
> **hansoffate said:**
> Mythtv won't uninstall with that command.  Here is the error

root@mythtv:/home# sudo apt-get remove --purge mythtv*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mythtv is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@mythtv:/home# 

So instead i did a complete removal of all things that have myth in it from the synaptic package manager.  Will that work?

Thanks for the help
-Hans

of course not, wildcard expansion would be too easy. ;)

```
# sudo apt-get remove --purge libmyth-0.20 mythtv-common mythtv-frontend mythtv-database mythtv-backend
```

or open synaptic package manager (if you have a regular desktop), search for **myth** and deselect anything you see 
installed that is mythtv related.


and then the rest...

---

### Post by hansoffate on 2007-03-21
Do I have to do the mysql related purging?  If so how would i do it?  I posted above what I get when i try that command line.

Thank you
-Hans

---

### Post by majoridiot on 2007-03-21
> **hansoffate said:**
> Do I have to do the mysql related purging?  If so how would i do it?  I posted above what I get when i try that command line.

Thank you
-Hans

if mythtv is the only app using mysql, then yes- remove it.

when you get everything removed and follow the guide from the link i posted, everything that you
need will be re-installed.

---

### Post by fenian on 2007-03-21
The message you got when trying to purge mysql is just notifying you of all the packages to be removed these are the packages installed when you install mysql.You want to remove/purge all these or mythtv might have database problems.So when it asks if you want to continue answer yes.

---

### Post by hansoffate on 2007-03-21
It seemed like alot more packages then I wanted and I thought it would break my system.  (I used to have Sabayon Linux, you can't do a emerge world without being in fear that it will break something)

Anyways, I deleted everything myth related now.  I am following the tutorial now step by step.  I really hope this works.

Thank you for your help.  I'll post back later if I finish successfully.  ::crosses fingers::

Thank you,
-Hans

---

### Post by hansoffate on 2007-03-21
Sorry for the double post.  Should I do this again if I need to?
When I was setting up with mythtv-setup, when I tried exiting the setup I get this error.

```
Cannot create a file /home/recordings/.test - directory is not writable?
```

What should I do? do I do a chmod ugo=rwx recordings?

Also Here is my ls -l :
```
drwxr-xr-x  2 root       root          6 2007-03-21 18:17 recordings
```

Thank you,
-Hans

---

### Post by SyvanX on 2007-03-21
Your recordings directory needs to be writeable by the mythtv user, or whichever user is running mythbackend.

```
sudo chown -R mythtv:mythtv /home/recordings
```

...based on the directory you have below, and if your mythtv user is running mythbackend.

---

### Post by hansoffate on 2007-03-21
That fixed that problem.  Now when I try to exit, I get this error:
Card 0 (type) is set to start on channel 3, which does not exist.

Channel three should exist.  It is on my satellite companys package, and its the channel that the tv needs to be tunned to in order for it to get the statelite signal or something.  (Basically when I had it hooked up to my tv I had to leave it on channel 3 in order for me to get the singal.  With GBPVR, a windows HTPC, I had the option of selecting a static channel 3, so that the statelite would work.

What should I do?

Thank you for the help
-Hans

---

### Post by majoridiot on 2007-03-21
go back into mythtv-setup
delete ALL cards  (#2)
delete ALL inputs  (#4)
exit back to command line
run mythtv-setup
set-up card
set up the input- make sure you have it bound to a valid source (from #3)
exit
fill the database

---

### Post by hansoffate on 2007-03-21
Now I have two of the same error upon exiting, but I only have 1 card configured on #2 and #4.  If I ignore the problem, and I fill the database and try to restart the backend, it still doesn't load.  When checking the log, this is what I found.

```
hansoffate@mythtv:/home$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
hansoffate@mythtv:/home$ more /var/log/mythtv/mythbackend.log
2007-03-21 18:10:41.259 Using runtime prefix = /usr
2007-03-21 18:10:41.612 New DB connection, total: 1
2007-03-21 18:10:41.822 Unable to connect to database!
2007-03-21 18:10:42.021 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-21 18:10:42.621 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-21 18:10:42.677 Failed to init MythContext, exiting.
2007-03-21 20:42:06.079 Using runtime prefix = /usr
2007-03-21 20:42:06.285 New DB connection, total: 1
2007-03-21 20:42:06.295 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:42:06.305 Current Schema Version: 1160
Starting up as the master server.
2007-03-21 20:42:06.334 New DB connection, total: 2
2007-03-21 20:42:06.336 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:42:06.342 EITHelper: localtime offset -7:00:00 
2007-03-21 20:42:06.537 New DB connection, total: 3
2007-03-21 20:42:06.538 Connected to database 'mythconverg' at host: localhost
sh: change_channel.pl: Permission denied
2007-03-21 20:42:07.576 ret_pid(5428) child(5428) status(0x7e00)
2007-03-21 20:42:07.581 ChannelBase: external tuning program exited with error 1
26
sh: change_channel.pl: Permission denied
2007-03-21 20:42:08.592 ret_pid(5430) child(5430) status(0x7e00)
2007-03-21 20:42:08.597 ChannelBase: external tuning program exited with error 1
26
2007-03-21 20:42:08.603 TVRec(1) Error: Setting start channel '3' failed, 
                        and backup '3' failed as well.
2007-03-21 20:42:08.628 New DB scheduler connection
2007-03-21 20:42:08.629 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:42:08.635 Main::Starting HttpServer
2007-03-21 20:42:08.646 Main::Registering HttpStatus Extension
2007-03-21 20:42:08.666 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-03-21 20:42:08.676 Enabled verbose msgs:  important general
/home/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/recordings' exists and that both 
the directory and that file are writeable by this user.
2007-03-21 20:42:37.019 Using runtime prefix = /usr
2007-03-21 20:42:37.143 New DB connection, total: 1
2007-03-21 20:42:37.153 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:42:37.171 Current Schema Version: 1160
Starting up as the master server.
2007-03-21 20:42:37.190 New DB connection, total: 2
2007-03-21 20:42:37.192 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:42:37.196 EITHelper: localtime offset -7:00:00 
2007-03-21 20:42:37.397 New DB connection, total: 3
2007-03-21 20:42:37.399 Connected to database 'mythconverg' at host: localhost
sh: change_channel.pl: Permission denied
2007-03-21 20:42:38.433 ret_pid(5461) child(5461) status(0x7e00)
2007-03-21 20:42:38.437 ChannelBase: external tuning program exited with error 1
26
sh: change_channel.pl: Permission denied
2007-03-21 20:42:39.453 ret_pid(5463) child(5463) status(0x7e00)
2007-03-21 20:42:39.457 ChannelBase: external tuning program exited with error 1
26
2007-03-21 20:42:39.458 TVRec(1) Error: Setting start channel '3' failed, 
                        and backup '3' failed as well.
2007-03-21 20:42:39.481 New DB scheduler connection
2007-03-21 20:42:39.483 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:42:39.487 Main::Starting HttpServer
2007-03-21 20:42:39.499 Main::Registering HttpStatus Extension
2007-03-21 20:42:39.512 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-03-21 20:42:39.521 Enabled verbose msgs:  important general
/home/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/recordings' exists and that both 
the directory and that file are writeable by this user.
2007-03-21 20:53:59.167 Using runtime prefix = /usr
2007-03-21 20:53:59.231 New DB connection, total: 1
2007-03-21 20:53:59.241 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:53:59.251 Current Schema Version: 1160
Starting up as the master server.
2007-03-21 20:53:59.267 New DB connection, total: 2
2007-03-21 20:53:59.280 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:53:59.286 EITHelper: localtime offset -7:00:00 
2007-03-21 20:53:59.475 New DB connection, total: 3
2007-03-21 20:53:59.477 Connected to database 'mythconverg' at host: localhost
sh: channel-changer.pl: not found
2007-03-21 20:54:00.509 ret_pid(5813) child(5813) status(0x7f00)
2007-03-21 20:54:00.514 ChannelBase: external tuning program exited with error 1
27
sh: channel-changer.pl: not found
2007-03-21 20:54:01.525 ret_pid(5816) child(5816) status(0x7f00)
2007-03-21 20:54:01.530 ChannelBase: external tuning program exited with error 1
27
2007-03-21 20:54:01.530 TVRec(1) Error: Setting start channel '3' failed, 
                        and backup '3' failed as well.
2007-03-21 20:54:01.555 New DB scheduler connection
2007-03-21 20:54:01.558 Connected to database 'mythconverg' at host: localhost
2007-03-21 20:54:01.562 Main::Starting HttpServer
2007-03-21 20:54:01.574 Main::Registering HttpStatus Extension
2007-03-21 20:54:01.587 mythbackend version: 0.20.20060828-3 www.mythtv.org
2007-03-21 20:54:01.592 Enabled verbose msgs:  important general
/home/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/home/recordings' exists and that both 
the directory and that file are writeable by this user.

```

Thank you for all the help guys,
-Hans

---

### Post by majoridiot on 2007-03-22
you've got all kinds of permission issues....

which of the install guides did you follow?

---

### Post by hansoffate on 2007-03-22
I followed 1 tutorial at first.  Then I tried to follow another.  Then I tried following a combination of an old one and this one on the help.ubuntu pages.  Now I will try and follow this purely.  I'll post back later.

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

:EDIT:  When setting up IVTV I can never get the test video capture to look like any tv.  I have it connected the same as my Windows setup used to be.  It is in the Tuner coax cable.  Any ideas why?

:EDIT2: Also, for LIRC I want the IRBlaster to work on my pvr 150.  Should I follow this HOWTO from another website?  I already tried it both ways and they both ran into problems.  When I tried following the ubuntu way on the buntu help pages, when i got to running IRW, it wouldn't run to test the input.  I couldn't read anything in dmesg.

Thanks for the help
-Hans

---

### Post by SyvanX on 2007-03-22
The important part of the video capture is that you get something like static.  That means your video card is doing something, Mythtv should handle the rest.  If you're really interested in manually tweaking ivtv, check out:

```

ivtvctl --help
ivtv-tune
```

As for the IR Blaster, i would try to use the documentation from the community help pages.  That got me set up pretty well.

---

### Post by hansoffate on 2007-03-22
After following the HOWTO on the ubuntu help pages again.  I got the same problem. The backend won't start.  Here is what I get

```
hansoffate@mythlinux:~$ # sudo /etc/init.d/mythtv-backend start
hansoffate@mythlinux:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
hansoffate@mythlinux:~$ more /var/log/mythtv/mythbackend.log
2007-03-22 02:11:50.651 Using runtime prefix = /usr
2007-03-22 02:11:50.837 New DB connection, total: 1
2007-03-22 02:11:50.943 Unable to connect to database!
2007-03-22 02:11:50.995 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-22 02:11:51.396 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-22 02:11:51.596 Failed to init MythContext, exiting.
hansoffate@mythlinux:~$ 
```

Here is some more things i did while trouble shooting.

```
hansoffate@mythlinux:~$ sudo /etc/init.d/mythtv-backend start
Password:
mythbackend already running, use restart instead.
hansoffate@mythlinux:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
hansoffate@mythlinux:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
hansoffate@mythlinux:~$ grep mythtv: /etc/group
mythtv:x:117:hansoffate
```


Thank you for the help
-Hans

---

### Post by bengalsfan74 on 2007-03-22
:popcorn: 

Ok. You have mysql issues. When you setup your MythTV originally, you created a user/pass combo for mysql.

Now that you've re-installed, it seems that the authentication is incorrect.

You need to log in to your Mysql Database with root, and reset your Mysql password for the mythtv user.

Then re-run mythtv-setup and make sure you put the proper user/pass in the setup fields.

---

### Post by majoridiot on 2007-03-22
> **bengalsfan74 said:**
> :popcorn: 

Ok. You have mysql issues. When you setup your MythTV originally, you created a user/pass combo for mysql.

Now that you've re-installed, it seems that the authentication is incorrect.

You need to log in to your Mysql Database with root, and reset your Mysql password for the mythtv user.

Then re-run mythtv-setup and make sure you put the proper user/pass in the setup fields.

no, this is incorrect.  if he followed the instructions for removal, the db and everything else 
was installed fresh.

first:

make sure you did the step where you commented out the bind address in /etc/mysql/my.cnf
and restart mysql

then, 

```
# cat /etc/mythtv/mysql.txt
```

to show you the password for the database.

then, run mythtv-setup and be sure that the address for the database is 127.0.0.1 (since you 
are running a combined frontend/backend) and set the db password to the one you just got.

then:

```
# cp /etc/mythtv/mysql.txt ~/.mythtv/
```


restart the backend and start the frontend.  the settings should be correct now for the FE, so
just continue through with no changes.


personally, i would get one thing at a time working.  ivtv, then mythtv, then play with the rest.
doing more than one at a time when none are working all of the way leads to trouble. ;)

---

### Post by hansoffate on 2007-03-22
I double checked to make sure I had bind commented out and mysql password.  Both were set correctly.  

Now when I try running mythtv-setup, I get this problem.

Access denied for user 'mythtv'@'localhost' (using password: YES)

```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-22 09:37:19.975 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-22 09:37:23.039 Unable to connect to database!
2007-03-22 09:37:23.039 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-22 09:37:23.178 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-03-22 09:37:23.234 Failed to init MythContext, exiting.
```

Major or anyone else who has helped me, if you're willing to help me though vnc, I'll install VNC on my box or my box already has openssh installed.  I'll let you look around and see what you find.  Would any of you be willing to do that?

If so, perhaps we could set-up a time we can meet on some messenger service so you can tell me what your doing.  If that is too much to ask or if you have too little time and just want to do it fast, I will just give you the information to be able to connect.

Thank you for all the help.  It is much appreciated.  Every time I have tried to install mythtv, it has never worked.  However, this time I am going to stay persistent and try to get this done before my monday.

Again, thank you all very much,
-Hans

---

### Post by fenian on 2007-03-22
> no, this is incorrect. if he followed the instructions for removal, the db and everything else
was installed fresh.

Actually I have had problems when purging mythtv and mysql that some of the configuration files in the directory /var/lib/mysql/mythconverg (I think thats the one) were not removed and thus caused errors.


> personally, i would get one thing at a time working. ivtv, then mythtv, then play with the rest.
doing more than one at a time when none are working all of the way leads to trouble.

I agree though I would go even farther and set up mysql,phpmyadmin and apache before continuing with the mythtv install.

---

### Post by majoridiot on 2007-03-23
as a follow-up... hansoffatate's db access problem was due to not having the .mythtv/mysql.txt
file in his home directory.  
he had added his main user to the mythtv group 
the problem was fixed by:

```
# cp /etc/mythtv/mysql.txt ~/.mythtv
```

that allowed him to start mythv-setup without error as his main user and begin the process of getting the rest of
setup and config underway.

---

### Post by uric on 2007-03-23
I have similer problem and get "Access denied for user 'mythtv'@'localhost' (using password: YES)"
nothing I have tried works, I have deleted, reinstalled, changed passwords, users, groups, rigths. Its a mess, I have no clue what to do...

---

### Post by hansoffate on 2007-03-26
I had that same problem.

Did you try following the Help Docs?   [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162)

Anyways,  after about 3 days of trouble shooting majoridiot and I got mythtv working.  It also resulted in a new PVR150 ubuntu install, if I understood correctly, that makes the IRBlaster work and easier to configure.

Thank you for all the help
-Hans

---

### Post by majoridiot on 2007-03-26
the starting page for the install guides are at: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by pulpinator on 2007-03-27
Today after Ubuntu froze and then crashed (during MythTV), when it rebooted I got the error:
```

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

I found this thread but I didn't want to uninstall and reinstall. So I changed /etc/init.d/mythtv-backend to run as my username instead of mythtv (I know, not recommended, but just for now!). restart backend, and the mysql database is broken:

```

Table './mythconverg/recordedseek' is marked as crashed and should be repaired

```

So I ran:

```

mysql -u mythtv -pmythtv
use mythconverg ;
REPAIR TABLE recordseek;
exit

```

Restart backend, and frontend, and everything works great now. So I put mythtv back as the username on /etc/init.d/mythtv-backend, and try a backend restart, same issue as the original.

Then I noticed that the mythtv username was not in the mythtv group. So...

```

sudo usermod -a -G mythtv mythtv

```

Reboot the system, and now everything works great!

I hope it helps someone else. Thanks for all the tips on this thread I was able to fix mine (for now)!

---

### Post by pulpinator on 2007-03-27
After another reboot (to move it to the living room), I again get the Authentication error. But the backend seems to be recording fine, and the frontend can connect to it without a problem. So I'm not sure what the effect of the Authentication error is right now!

---

### Post by majoridiot on 2007-03-27
> **pulpinator said:**
> Today after Ubuntu froze and then crashed (during MythTV), when it rebooted I got the error:
```

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```

this is a common error, causes no problems and can be safely ignored. :)

---

### Post by hansoffate on 2007-03-28
Second.  I get this every time I start with no problem.

-Hans

---

### Post by bdogg64 on 2007-03-28
I already have mythtv setup successfully, so I don't know if I should post this as a new thread or not, but the answer may be simple.  Is there a way to use cron to launch mythtv everyday like an alarm clock :) . I tried using this in KCron

```
mythtv --display :0.0
```

But that didn't work. Any help would be great

Thanks

---Nevermind, I install KAlarm, which works great..

---

