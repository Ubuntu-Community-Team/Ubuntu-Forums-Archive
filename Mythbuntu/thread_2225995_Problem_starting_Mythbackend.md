---
title: "Problem starting Mythbackend"
date: 2014-05-24
forum: Mythbuntu
---

### Post by nainsurvolte on 2014-05-24
I upgraded this morning my MythTv backend to 0.27
I have a MythBuntu server that started as a 11.10 but has now been upgraded to 12.04 since (when it got out). Upgrade did not go smoothly and I had to upgrade manually as MythBuntu Command Center did not launch the upgrade when setup to do so with new repository. I was at 0.25 and went to 0.27 with the following command line

```
[COLOR=#000000][FONT=sans-serif]$ sudo apt-get build-dep mythtv[/FONT][/COLOR]
```

Installation crashed before the backend could get configured. I did some research on what could cause this issue and found out some thread that said deleting the "mythtv" user solved their problem. After I did backup of the folder I tried it but to no avail. Did some more search and found somethings about the having conflicting configuration file. I manage to the align proper information, address, password and user name to my Mythconverg database and fix the data in the new config.xml in the folder /etc/mythtv. Using the following solved the rest of the install.

```
 sudo apt-get -f install 
```

I recreated the mythtv user reassinging it to the same user ID. I did a complete reconfigure of the backend (delete the card, the group, the line up, rescan channel) and manage to get it running or... so I thought. It stars but then close. When I run it in command line, here is what I get

```
owner@TV-server:/etc/default$ mythbackend2014-05-24 12:50:52.906656 C  mythbackend version: fixes/0.27 [v0.27-232-gf4825ca] www.mythtv.org
2014-05-24 12:50:52.906687 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2014-05-24 12:50:52.906695 N  Enabled verbose msgs:  general
2014-05-24 12:50:52.906712 N  Setting Log Level to LOG_INFO
2014-05-24 12:50:52.918544 I  Setup Interrupt handler
2014-05-24 12:50:52.918560 I  Setup Terminated handler
2014-05-24 12:50:52.918573 I  Setup Segmentation fault handler
2014-05-24 12:50:52.918585 I  Setup Aborted handler
2014-05-24 12:50:52.918597 I  Setup Bus error handler
2014-05-24 12:50:52.918609 I  Setup Floating point exception handler
2014-05-24 12:50:52.918620 I  Setup Illegal instruction handler
2014-05-24 12:50:52.918637 I  Setup Real-time signal 0 handler
2014-05-24 12:50:52.918703 N  Using runtime prefix = /usr
2014-05-24 12:50:52.918725 N  Using configuration directory = /home/owner/.mythtv
2014-05-24 12:50:52.918835 I  Assumed character encoding: en_CA.UTF-8
2014-05-24 12:50:52.919347 N  Empty LocalHostName.
2014-05-24 12:50:52.919358 I  Using localhost value of TV-server
2014-05-24 12:50:52.926840 I  Added logging to the console
2014-05-24 12:50:52.946593 N  Setting QT default locale to EN_CA
2014-05-24 12:50:52.946686 I  Current locale EN_CA
2014-05-24 12:50:52.946767 N  Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2014-05-24 12:50:52.956160 I  Current MythTV Schema Version (DBSchemaVer): 1317
2014-05-24 12:50:52.956868 I  Loading en_us translation for module mythfrontend
2014-05-24 12:50:52.957669 N  MythBackend: Starting up as the master server.
2014-05-24 12:50:53.029032 I  New Client:  (#1)
2014-05-24 12:50:53.088348 I  Found 1 distinct programid authorities
2014-05-24 12:50:53.088950 I  Registering HouseKeeperTask 'LogClean'.
2014-05-24 12:50:53.088991 I  Registering HouseKeeperTask 'DBCleanup'.
2014-05-24 12:50:53.089020 I  Registering HouseKeeperTask 'ThemeUpdateNotifications'.
2014-05-24 12:50:53.089054 I  Registering HouseKeeperTask 'RecordedArtworkUpdate'.
2014-05-24 12:50:53.092445 I  New static DB connectionSchedCon
2014-05-24 12:50:53.093911 I  Registering HouseKeeperTask 'MythFillDB'.
2014-05-24 12:50:53.093954 I  Registering HouseKeeperTask 'JobQueueRecover'.
2014-05-24 12:50:53.093973 I  Registering HouseKeeperTask 'HardwareProfiler'.
2014-05-24 12:50:53.103880 I  Starting HouseKeeper.
2014-05-24 12:50:53.121773 I  Listening on TCP 127.0.0.1:6544
2014-05-24 12:50:53.121853 I  Listening on TCP 192.168.1.111:6544
2014-05-24 12:50:53.121960 I  Listening on TCP [::1]:6544
2014-05-24 12:50:53.122177 I  Listening on TCP [fe80::2e0:4cff:fe68:f71c%eth2]:6544
2014-05-24 12:50:54.612029 I  Main::Registering HttpStatus Extension
2014-05-24 12:50:54.623308 I  Listening on TCP 127.0.0.1:6543
2014-05-24 12:50:54.623428 I  Listening on TCP 192.168.1.111:6543
2014-05-24 12:50:54.623589 I  Listening on TCP [::1]:6543
2014-05-24 12:50:54.623735 I  Listening on TCP [fe80::2e0:4cff:fe68:f71c%eth2]:6543
2014-05-24 12:50:54.630314 N  AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2014-05-24 12:50:55.366390 I  Bonjour: Service registration complete: name 'Mythbackend on TV-server' type '_mythbackend._tcp.' domain: 'local.'
2014-05-24 12:50:55.571542 C  MainServer::HandleVersion - Client speaks protocol version 8 but we speak 77!
2014-05-24 12:50:56.108678 I  Reschedule requested for MATCH 0 0 0 - SchedulerInit
2014-05-24 12:50:56.286536 I  Scheduled 0 items in 0.1 = 0.05 match + 0.00 check + 0.01 place
2014-05-24 12:50:56.292218 I  Scheduler: Seem to be woken up by USER
2014-05-24 12:50:56.598205 C  MainServer::HandleVersion - Client speaks protocol version 8 but we speak 77!
2014-05-24 12:50:57.628893 C  MainServer::HandleVersion - Client speaks protocol version 8 but we speak 77!
```

After that, the last line just keeps repeating until It stops or I stop it manually.

Any thoughts?

---

### Post by blm-ubunet on 2014-05-24
That message means the connecting FE (or other app) is a different/broken version than the BE.
What is trying to connect ?
XBMC?

What happens with mythfrontend?

After changing the mythbuntu repo:
apt-get update
apt-get dist-upgrade
(you can do a simulated dummy run with "-s" option)

What do you mean by "upgrade manually":-
- build from source ?
- git clone
- git tarball
- deb/tar from somewhere?
- use apt-get in terminal ?

Just FYI in case you have not noticed:
[http://www.mythtv.org/wiki/Release_Notes_-_0.27.1](http://www.mythtv.org/wiki/Release_Notes_-_0.27.1)
Guess that will appear in mythbuntu in hours/days.

---

### Post by nainsurvolte on 2014-05-24
> What is trying to connect ?
XBMC?


I have 2 Openelec (XBMC) client. But one was closed and the other in sleep. In doubt, following your answer, I disconnected the last onet and now I don't get the message anymore. But... mythbackend as a service does not stay active.

If I do

```
start mythtv-backend
```

and then check the service running, it is not there.

If I manually start it by simply calling "mythbackend", it now stays active, but still cannot have mythweb...

> What happens with mythfrontend?

It was installed on the same machine but not used. Before I got your answer, I completely uninstalled it with 

```
sudo apt-get purge mythtv-frontend
```

It did nothing at the time to improve the situation.

> 
After changing the mythbuntu repo:
apt-get update
apt-get dist-upgrade
(you can do a simulated dummy run with "-s" option)

Interesting, but what exactly does it give or prevent?

> What do you mean by "upgrade manually":-
- build from source ?
- git clone
- git tarball
- deb/tar from somewhere?
- use apt-get in terminal ?

The last one, through command line in a terminal window. From the Mythbuntu page, its seems that it can update "automatically" from the Mythbuntu Contol Center once you activate the repository, but it did not. So I got to use command line in place.

> Just FYI in case you have not noticed:
[http://www.mythtv.org/wiki/Release_Notes_-_0.27.1](http://www.mythtv.org/wiki/Release_Notes_-_0.27.1)
Guess that will appear in mythbuntu in hours/days.

Interesting, I am even at a point to think about re installing mythtv from scratch... I have made a backup of the database before all of that.

What is it that we need to erase. unsintall to start from a simple ubuntu PC?

---

### Post by dannyboy79 on 2014-05-24
do you have a file named mythtv-backend located within /etc/init.d/ and if not, is there something similarly named in /etc/init/? we need to view the logs of the mythtv-backend after you attempt to start it up with no clients trying to access it to find out why the backend isn't starting

---

### Post by blm-ubunet on 2014-05-24
The XBMC cmyth plugin uses made-up version numbering & a strongly discouraged interface to BE.
All a bit sad really c.f. rest of XBMC.

Try upstart:
```
sudo service mythtv-backend start
```
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

should be a symlink (to upstart-job) called mythtv-backend in /etc/init.d/
& mythtv-backend.conf in /etc/init/

I would read the mythtv 0.26/0.27/0.27.1 release notes especially:
- config.xml
- timezone
- icon file path/names
- mysql .cnf file changes

From memory you need to:
apt-get dist-upgrade
after changing mythbunti repos from 0.25-->0.27

The "-s" is a safe way to see how much damage is planned.

---

### Post by nainsurvolte on 2014-05-25
> **dannyboy79 said:**
> do you have a file named mythtv-backend located within /etc/init.d/ and if not, is there something similarly named in /etc/init/?

There is a symlink for mythtv-backend located within **/etc/init.d/**, which point to the one in [B]lib/init/upstart-job

[/B]> **dannyboy79 said:**
>  we need to view the logs of the mythtv-backend after you attempt to start it up with no clients trying to access it to find out why the backend isn't starting

If you refer to a log in the **/var/log/mythtv**, there are none created following a start attempt of the backend, The last log it created is a mythtv-setup.log and I simply went in and out to make him start the service and see the result. The last log it created was when the config.xml had bad information for the access to the databasase. If there are others, then you will have to tell me where they might be.

---

### Post by nainsurvolte on 2014-05-25
> **blm-ubunet said:**
> The XBMC cmyth plugin uses made-up version numbering & a strongly discouraged interface to BE.
All a bit sad really c.f. rest of XBMC.


Yeah, I know, last time I upgraded I had to wait 6-8 months until a version of XBMC could "speak" to my MythTv backend which I only use to record TV and watch TV. The server on which it runs is also a file server for my films, videos and music for which I use XBMC. 

I learned from my mistake... Before going to 0.26 or 0.27 I made some search. Apparently the 0.25 I was running was no longer supported, and apparently, there was a known bug I was experiencing (recording that do not stop when done and that prevent any other recording to go...). So I made some search on what it takes to go from 0.25 to 0.27. I saw that thing about the config.xml file that replaces the mysql.txt. I also saw the time zone command that had to be run in mysql. The two other point your refer to, I`ll keep in mind. When re-configuring the card, recording group and all, I saw that I lost all the channel images...

> **blm-ubunet said:**
> 
should be a symlink (to upstart-job) called mythtv-backend in /etc/init.d/
& mythtv-backend.conf in /etc/init/


Yes, they are all there.

> **blm-ubunet said:**
> 
From memory you need to:
apt-get dist-upgrade
after changing mythbunti repos from 0.25-->0.27

The "-s" is a safe way to see how much damage is planned.

Well then, I did it right, and I will keep in mind that -s flag.

> **blm-ubunet said:**
> 
Try upstart:
```
sudo service mythtv-backend start
```
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

Just tried it... It says it start as process wxyz, but then when I check the process running it is not there, and in addition...no log.

This is way over my level of understanding :confused:

Let me know what ever I would have to post (file, log, etc) to see or, as stated above, what do I need to do to eradicate anything that could mess up with a clean install of MythTv.

---

### Post by blm-ubunet on 2014-05-25
Mythtv has stopped logging to files by default (except to stdout/err).
So if want logs you have to use cmd line options..

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][http://www.mythtv.org/wiki/Logging](http://www.mythtv.org/wiki/Logging) 
 there are:
- mythlogserver (compile option; default off now)
- syslog
- syslog-ng

Here are 2 examples for the FE: 
 
     mythfrontend --quiet --logpath /var/log/mythtv 
     mythfrontend --quiet --syslog local7

-quiet suppresses console/terminal stdout/err logging that would appear if you invoke from terminal.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
The backend command line would have other stuff like making sure it runs as user="mythtv"
The upstart wiki link has a good working example command line.

Mythbuntu does some script wrapping around FE executable for auto-respawn..

Note that /home/"user"/.mythtv/ folder is used to (try to) find a config.xml file..
So you can have 3 copies in a combined FE & BE (another in /etc/mythtv/??)

There should be some log file for upstart-job
/var/log/upstart/mythtv-backend.log

---

### Post by nainsurvolte on 2014-05-25
Bingo, now we have something... and I thought it would be link with that mythtv user I had to recreate.

Here is the content of the "**mythtv-backend.log**" in the **/var/log/upstart** folder which was created about around the time I tried to  upstart the service

```
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
Invalid user 'mythtv' specified with --user
```

Made some verification and ... :oops:, mythtv did not exist. I possibly deleted yesterday when trying some things around.

I recreated it and tied to the the original user id. Now this was added to the log...

```
Cannot login to database

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']


Cannot login to database


Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']


Cannot login to database


Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
```

Now that I know what it is, I just don`t know hoe to fix it. Somewhere during the configuration I provided the wrong password. Now for some reason the password for mythtv to mythconverg is not the one it use to be. I tried to change the mythconverg database password for mythtv to what it used to be but it is not working. I have started another thread here
[http://ubuntuforums.org/showthread.php?t=2226104](http://ubuntuforums.org/showthread.php?t=2226104)

I guess once I can manage that change we could go one step further. On the other hand, I am wondering what the mythtv-backend is using for password because I have change the different config.xml with that password I know works but that I want to change.

---

### Post by blm-ubunet on 2014-05-25
[http://www.mythtv.org/wiki/Category:MySQL](http://www.mythtv.org/wiki/Category:MySQL)

especially grants & flushing & restarting mysql service..

The BE will use the credentials in its own home folder (if it exists), else it uses the fallback in /etc/mythtv/ or similar..
So the BE needs to be started as a consistent "mythtv" (the right) user.

Can always check the user ID in /etc/users & /etc/groups still matches the permissions/owner of /home/mythtv/* folder.

---

### Post by nainsurvolte on 2014-05-26
Thanks, it all turned good.

It was all about the mythtv user access to mythconverg. I tried this new query in mysql to change the password and it was all good.

I also updated my XBMC client to Gotham 13.1 and I don`t have that protocol disconnect error message.

Now, I need to fix my Mythweb who has some issue.

See this thread [http://ubuntuforums.org/showthread.php?t=2226201](http://ubuntuforums.org/showthread.php?t=2226201)

Thanks for the help, it got me looking at the right places.

---

