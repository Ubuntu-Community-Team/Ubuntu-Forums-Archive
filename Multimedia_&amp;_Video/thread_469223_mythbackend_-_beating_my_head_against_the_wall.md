---
title: "mythbackend - beating my head against the wall"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by Seantiago on 2007-06-09
So I'm trying to set up a combination frontend/backend mythtv box on an oldish dell running dapper. The specs are well above the minimum levels, and I have a hauppage pvr-500 for a tuner. But don't worry about that because this, I believe, is a hardware issue.

Anyway, after following a mixture of setup instructions from[ this site]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation#Install_services:_Apache.2C_Openssh") and[ this site]("http://hyams.webhop.net/mythtv/myth_ubuntu.html") (the wiki for everything leading up to the actual mythtv install, and hyams for everything after) I seem to have run into a wall once I try to run mythbackend.

I do what they say, run mythbackend, open another terminal window and run mythfrontend, the mythtv screen pops up, and I try to watch tv. I get a black screen. If I hit ESC, after about 2 minutes the black screen goes away and I'm back to the mythtv start page. If I hit ESC again after about 10 minutes I get a pop up saying "Could not connect to master backend server -- is it running? Is the IP address set for it in the set up program correct?"

Then I click 'OK' and it drops me back into the ubuntu desktop after asking me if I really want to quit mythtv.

So that's my tale of woe. I've read several other threads on this forum and others with similar problems but I'm far too stupid to get anything out of them. Please help!

Here's the terminal output for mythbackend:

```
sh-3.1$ mythbackend
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2007-06-09 16:52:21.382 New DB connection, total: 1
Starting up as the master server.
2007-06-09 16:52:21.419 New DB connection, total: 2
2007-06-09 16:52:21.444 New DB connection, total: 3
2007-06-09 16:52:26.648 New DB scheduler connection
2007-06-09 16:52:26.665 mythbackend version: 0.18.1.20050510-1 www.mythtv.org
2007-06-09 16:52:26.666 Enabled verbose msgs : important general
2007-06-09 16:52:28.661 Reschedule requested for id -1.
2007-06-09 16:52:28.686 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2007-06-09 16:52:28.693 Seem to be woken up by USER
2007-06-09 17:07:03.220 MainServer::HandleAnnounce Playback
2007-06-09 17:07:03.232 adding: gray-tivo as a client (events: 0)
2007-06-09 17:07:03.264 MainServer::HandleAnnounce Playback
2007-06-09 17:07:03.265 adding: gray-tivo as a client (events: 1)
2007-06-09 17:07:03.284 MainServer::HandleAnnounce Playback
2007-06-09 17:07:03.285 adding: gray-tivo as a client (events: 0)
2007-06-09 17:07:03.324 MainServer::HandleAnnounce Playback
2007-06-09 17:07:03.325 adding: gray-tivo as a client (events: 0)
2007-06-09 17:07:03.341 adding: gray-tivo as a remote ringbuffer
2007-06-09 17:07:03.364 Changing from None to WatchingLiveTV
2007-06-09 17:07:08.509 Error: Desired subchannel not specified in freqid "3", Using 1.
2007-06-09 17:07:09.513 HD5 Error: could not obtain sync
2007-06-09 17:07:23.607 Couldn't read data from the capture card in 15 seconds. Stopping.
2007-06-09 17:07:55.730 Changing from WatchingLiveTV to None
Segmentation fault
```


and for mythfrontend:
```
sh-3.1$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2007-06-09 17:06:25.253 New DB connection, total: 1
Total desktop width=1280, height=1024, numscreens=1
2007-06-09 17:06:25.274 Using screen 0, 1280x1024 at 0,0
2007-06-09 17:06:25.287 mythfrontend version: 0.18.1.20050510-1 www.mythtv.org
2007-06-09 17:06:25.288 Enabled verbose msgs : important general
2007-06-09 17:06:25.822 Switching to square mode (G.A.N.T.)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-06-09 17:06:26.619 Joystick disabled.
2007-06-09 17:06:26.796 Registering Internal as a media playback plugin.
2007-06-09 17:06:26.829 Registering MythDVD DVD Media Handler as a media handler2007-06-09 17:07:03.099 New DB connection, total: 2
2007-06-09 17:07:03.186 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-06-09 17:07:03.211 Using protocol version 15
2007-06-09 17:07:03.277 Using protocol version 15
2007-06-09 17:07:13.608 taking too long to be allowed to read..
2007-06-09 17:07:18.612 taking too long to be allowed to read..
2007-06-09 17:07:27.611 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:31.615 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:35.619 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:39.623 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:43.627 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:47.631 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:51.635 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:55.639 Waited 4 seconds for data to become available, waiting again...
2007-06-09 17:07:55.639 Waited 14 seconds for data to become available, abortingCouldn't read file: rbuf://127.0.0.1:6543/var/cache/mythtv//ringbuf1.nuv
2007-06-09 17:07:55.695 Changing from None to WatchingLiveTV
2007-06-09 17:07:55.695 Decoder not alive, and trying to play..
2007-06-09 17:08:15.702 ReadStringList timeout (quick).
Remote encoder not responding.
2007-06-09 17:08:15.712 Changing from None to None
2007-06-09 17:08:15.722 Changing from None to None
2007-06-09 17:08:25.866 ReadStringList timeout (quick).
2007-06-09 17:08:25.866 RemoteFile::Read(): No response from control socket.
2007-06-09 17:08:25.866 RemoteFile::Read() failed in RingBuffer::safe_read().
2007-06-09 17:08:25.874 WriteStringList: Bad socket
2007-06-09 17:08:25.874 ReadStringList: Bad socket
2007-06-09 17:08:25.875 Remote file timeout.
2007-06-09 17:13:44.732 ReadStringList timeout.
2007-06-09 17:13:44.732 Connection to backend server lost
2007-06-09 17:13:44.756 Event socket closed. No connection to the backend.
```


Thank you for listening

---

### Post by tgm4883 on 2007-06-09
I have to run so I cannot give your thread the attention it deserves, but can I ask why you choose dapper to go with?

Also, if you decide to try and reinstall it, I suggest this guide, as it is superior to all others
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by newlinux on 2007-06-09
You are also trying to run a fairly old version of myth. A new version has been made available via dapper-backports repository. Follow the link presented above for Dapper. I suggest uninstalling and installling using these instructions. If you do not, please let us now how you setup your capture card, video source, and input connection.

thanks.

---

### Post by Seantiago on 2007-06-09
> **tgm4883 said:**
> I have to run so I cannot give your thread the attention it deserves, but can I ask why you choose dapper to go with?

Also, if you decide to try and reinstall it, I suggest this guide, as it is superior to all others
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Heh. I chose dapper because there was something wrong with the Feisty installation disc I'd burned - it wasn't working, so I got frustrated and used my old dapper disc that I got from the ubuntu foundation with all the people of varying ages and ethnicities holding hands and smiling on the cover.

Is feisty much better for installing mythtv? Because I'll try again if makes it that much easier. I just figured that dapper is the long-term support version and would have less bugs, but then again I *am* a pretty stupid guy.

Thank you for that link. I've noticed the other guides are occasionally a bit...lacking. Would I be better off trying dapper with your how-to or just retrying with feisty?


@newlinux

Is the new version pretty good? I will try that too. Thanks,

---

### Post by tgm4883 on 2007-06-09
Although not my guide, I feel that this guide is vastly superior to any other mythtv ubuntu guide out there.  The new version of MythTV is pretty good, I don't know about version .18 (I never used it) but I would assume that it isn't kept up anymore.  

As for feisty, my PVR-150 has support built in.  I would bet that the PVR-500 also has support built in.

Either one you go with, you should use the guide I posted.  Although I would recommend feisty.

---

### Post by newlinux on 2007-06-09
I recommend Feisty as well, but as tgm4883 said - either way, go with the tutorial listed above... It's pretty much the "official" tutorial. Driver support is much better Feisty for many things...

---

### Post by newlinux on 2007-06-09
Oh, and in my opinion myth .20 is more stable than .18, and it has quite a few features that .18 does not have (better internal player which supports more file types, UPnP server, MythArchive, H.264 support, AC3/DTS passthrough, and a whole bunch of other things).

---

### Post by Seantiago on 2007-06-11
UPDATE:

I've stuck with dapper because it's the only installation disc I have and I think there's something wrong with my computer's burner. I've got a Feisty disc in the mail from the ubuntu foundation that should arrive in a week or two, so I'm not completely out of luck if Dapper totally sucks.

Anyway, following that new tutorial I've been able to run mythfilldatabase in a way that doesn't suck, but once again I've hit a wall with mythbackend. Here's the output from running mythbackend:

```
gray@gray-tivo:~$ mythbackend
2007-06-11 15:00:58.140 Using runtime prefix = /usr
2007-06-11 15:00:58.196 New DB connection, total: 1
2007-06-11 15:00:58.209 Unable to connect to database!
2007-06-11 15:00:58.209 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-06-11 15:00:58.267 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-06-11 15:00:58.323 Failed to init MythContext, exiting.
gray@gray-tivo:~$




```

It seems the problem is with granting permissions to mythtv, but everything there should be set to the defaults from myth-setup. Any ideas?

---

### Post by Seantiago on 2007-06-11
Oh, and I've tried to troubleshoot using this page:

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

but to no avail.

---

### Post by newlinux on 2007-06-11
did you run mythtv-setup once as the mythtv user?

---

### Post by Seantiago on 2007-06-12
I had run it as the normal user initially, but I just ran it as mythtv now. Seems to be the same problem.

---

### Post by newlinux on 2007-06-12
and you have your mysql.txt file setup with the right information and password? you may want to find all of them and change them. Sometimes they cause problems...

---

### Post by Seantiago on 2007-06-12
Ok. I've just reinstalled and done everything exactly according to the how-to.

I've also done this:

When I got to the mythtv-setup step, I couldn't su to mythtv so I ran passwd mythtv as the superuser and changed the password to mythtv. This worked, and the setup went off without any issue.

After mythtv-setup was done I switched over to the superuser again and ran mythfilldatabase, which went well, up until the end (when it starts mythbackend, I believe) and I got the same error as always:

```
2007-06-12 15:23:47.271 Marking episode last showings.
2007-06-12 15:24:19.790     Found 11985
2007-06-12 15:24:20.153 Grabbing next suggested grabbing time
2007-06-12 15:24:20.621 DataDirect: BlockedTime is: 2007-06-12T15:24:25
2007-06-12 15:24:20.623 DataDirect: NextSuggestedTime is: 2007-06-13T13:39:39
2007-06-12 15:24:20.722
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-06-12 15:24:20.735 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-06-12 15:24:20.737 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.
2007-06-12 15:24:20.738 Error rescheduling id -1 in ScheduledRecording::signalChange
2007-06-12 15:24:20.738 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-06-12 15:24:20.738 Connection timed out.
                        You probably should modify the Master Server
                        settings in the setup program and set the
                        proper IP address.
2007-06-12 15:24:20.743 mythfilldatabase run complete.

```

Now I am doing that thing you suggested where I change /etc/mythtv/mysql.txt so that the DBPassword is 'mythtv'.

Now I am running mythbackend as the mythtv user.

```
sh-3.1$ mythbackend
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2007-06-12 15:33:53.120 Using runtime prefix = /usr
2007-06-12 15:33:53.193 New DB connection, total: 1
2007-06-12 15:33:53.207 Unable to connect to database!
2007-06-12 15:33:53.207 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-06-12 15:33:53.268 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-06-12 15:33:53.324 Failed to init MythContext, exiting.
sh-3.1$

```

Any ideas?

---

### Post by newlinux on 2007-06-13
can you verify that mysqld is even running? If it isn't try starting it.
```

pgrep mysqld

```

If it returns nothing mysqld isn't running.


You could try:
```


sudo /etc/init.d/mysql start

```


to start it if it wasn't running. Just another guess...

---

### Post by tgm4883 on 2007-06-13
Your database password isn't mythtv, so that may be your problem.

---

### Post by Seantiago on 2007-06-13
> **tgm4883 said:**
> Your database password isn't mythtv, so that may be your problem.

That sounds likely. How can I change it?

---

### Post by newlinux on 2007-06-13
your password should have been randomly generated and placed in /etc/mythtv/mysql.txt. You can change it by doing:
```

sudo dpkg-reconfigure mythtv-common

```

And as noted before, you should make sure all appropriate mysql.txt files contain the right password, especially the the ~/.mythtv/mysql.txt

---

### Post by Seantiago on 2007-06-14
> **newlinux said:**
> can you verify that mysqld is even running? If it isn't try starting it.
```

pgrep mysqld

```

If it returns nothing mysqld isn't running.


You could try:
```


sudo /etc/init.d/mysql start

```


to start it if it wasn't running. Just another guess...



Tried both of these, both confirm that mysql is running.

> **newlinux said:**
> your password should have been randomly generated and placed in /etc/mythtv/mysql.txt. You can change it by doing:
```

sudo dpkg-reconfigure mythtv-common

```

And as noted before, you should make sure all appropriate mysql.txt files contain the right password, especially the the ~/.mythtv/mysql.txt

I've already changed the password in /etc/mythtv/mysql.txt to 'mythtv', and ~/.mythtv.mysql.txt doesn't appear to exist.

There *is*, however, a mysql.txt file in /usr/share/mythtv (found it using locate) and the password in it is also already changed to 'mythtv'.

There's also a mysql.txt file called /usr/share/mythtv/mysql.txt.dist, that has a *blank* password value. I tried changing that as well but I'm still getting the same errors.

I must be missing something REALLY obvious, right?

---

### Post by tgm4883 on 2007-06-14
The thing is, you never changed your mysql password.  So when mythtv is trying to access the database it is using the password 'mythtv', but the password for the mysql database is still the randomly generated one.

---

### Post by Seantiago on 2007-06-14
And how about this crazy crap:

```
mysql -u mythtv -pmythtv mythconverg
```

gets me into the database as the mythtv user just fine.

---

### Post by Seantiago on 2007-06-14
> **tgm4883 said:**
> The thing is, you never changed your mysql password.  So when mythtv is trying to access the database it is using the password 'mythtv', but the password for the mysql database is still the randomly generated one.

You mean I should do something like this:

```
mysql -u root mysql
```



And then do this while in mysql:

```
UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
FLUSH PRIVILEGES;
```

?


Because I've already done that.

---

### Post by Seantiago on 2007-06-15
I just got my Feisty discs in the mail. Hopefully this is some weird Dapper problem and not entirely due to my own incompetence. I'll let you guys know how it goes.

---

### Post by tgm4883 on 2007-06-15
Install Feisty, use the guide, it starts from scratch (bare HD).  Follow it close and you wont have a problem.  Don't manually change any passwords (unless the guide says so) as the guide is very very good.  I have followed it many times and made sure of its accuracy

---

### Post by Seantiago on 2007-06-15
What can I say? Feisty completely rules! I can't believe I spent so many hours fiddling with Dapper when this was so freakin' easy.

Thank you for all your help, guys.

---

