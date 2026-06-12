---
title: "No UPnP"
date: 2010-09-07
forum: Mythbuntu
---

### Post by gonkyouka on 2010-09-07
Im having a no upnp error though I already have a database and checked the user and its permissions. Opening frontend and backend gives me same window.

Distro: Lucid
- Install MythTV from terminal using
 ```
sudo apt-get install mythtv
```

- Language selection followed by a window with filled information (information seems to be correct based on my mysql.txt) then after clicking finish, it shows me another window that says "cannot".

- The error windows are:
1. No UPnP
2. Cannot (yes it only says cannot)

tried running:
```
mythbackend --upnprebuild
```

and gives me the following output:
```
2010-09-08 09:05:30.420 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-09-08 09:05:30.421 Using runtime prefix = /usr
2010-09-08 09:05:30.421 Using configuration directory = /home/gonix/.mythtv
2010-09-08 09:05:30.422 Using localhost value of MYCOOLMYTHTVHOST
2010-09-08 09:05:30.429 New DB connection, total: 1
2010-09-08 09:05:30.432 Unable to connect to database!
2010-09-08 09:05:30.432 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2010-09-08 09:05:30.433 MCP::InitUPnP() - HttpServer Create Error
2010-09-08 09:05:30.433 Deleting UPnP client...
2010-09-08 09:05:30.434 No UPnP backends found

No UPnP backends found
```

mysql.txt
```
# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=7rYxM8gm

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
LocalHostName=MYCOOLMYTHTVHOST

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```

Im using a Philips Semiconductors SAA7130 Video Broadcast Decoder.

If you guys need information about logs, screenshot, mysql password please let me know.

---

### Post by ian dobson on 2010-09-07
Hi,

Do you have all packages installed that mythtv needs? (mythtv-backend,mythtv-common etc)

do a dpkg -l | grep myth and dump the results here. Your problem seems to be that mythtv cannot connect to the sql database for some reason.

Regards
Ian Dobson

---

### Post by gonkyouka on 2010-09-08
> **ian dobson said:**
> Hi,

Do you have all packages installed that mythtv needs? (mythtv-backend,mythtv-common etc)

do a dpkg -l | grep myth and dump the results here. Your problem seems to be that mythtv cannot connect to the sql database for some reason.

Regards
Ian Dobson

hi thanks for the reply.

heres the result:
```
ii  libmyth-0.23-0                            0.23.0+fixes24158-0ubuntu2                      Common library code for MythTV and add-on mo
ii  libmythtv-perl                            0.23.0+fixes24158-0ubuntu2                      A PERL library to access some MythTV feature
ii  mythbuntu-common                          0.50-0ubuntu1                                   Mythbuntu application support functions
ii  mythbuntu-control-centre                  0.62-0ubuntu1                                   Mythbuntu Configuration Application
ii  mythtv                                    0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (clien
ii  mythtv-backend                            0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (serve
ii  mythtv-common                             0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (commo
ii  mythtv-database                           0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (datab
ii  mythtv-frontend                           0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (clien
ii  mythtv-theme-arclight                     1:0.23.0+fixes23872-0ubuntu1                    The arclight MythTV Theme
ii  mythtv-theme-blootube-osd                 1:0.23.0+fixes23872-0ubuntu1                    The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                      1:0.23.0+fixes23872-0ubuntu1                    The blueosd MythTV Theme
ii  mythtv-theme-graphite                     1:0.23.0+fixes23872-0ubuntu1                    The graphite MythTV Theme
ii  mythtv-theme-iulius-osd                   1:0.23.0+fixes23872-0ubuntu1                    The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy                   1:0.23.0+fixes23872-0ubuntu1                    The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                     1:0.23.0+fixes23872-0ubuntu1                    The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu                    1:0.23.0+fixes23872-0ubuntu1                    The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd           1:0.23.0+fixes23872-0ubuntu1                    The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd                    1:0.23.0+fixes23872-0ubuntu1                    The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd               1:0.23.0+fixes23872-0ubuntu1                    The titivillus-osd MythTV Theme
ii  mythtv-themes                             1:0.23.0+fixes23872-0ubuntu1                    Themes for MythTV
ii  mythtv-transcode-utils                    0.23.0+fixes24158-0ubuntu2                      Utilities used for transcoding MythTV tasks

```

EDIT:

I fixed it but now I have another error. When selecting Watch TV in frontend it gives me the following error:
```
ERROR:MythTV is using all inputs, but there are no active recordings?
```

---

### Post by LowSky on 2010-09-08
go to the backend and make sure it is using your PC's correct network adress, do the same on the frontend, and then check to see if the correct login name and password you created when you installed mythtv and mysql is being used.

it should clear up the Upnp issues too.

---

### Post by gonkyouka on 2010-09-08
> **LowSky said:**
> go to the backend and make sure it is using your PC's correct network adress, do the same on the frontend, and then check to see if the correct login name and password you created when you installed mythtv and mysql is being used.

it should clear up the Upnp issues too.
OK thanks! ill go check it when im in my rig. im in my work at the moment. ill post updates here when im done.

---

### Post by markackerman8@gmail.com on 2010-10-26
If you fixed the noUPN error would you be kind enough to say how to help all us others?

---

### Post by nickrout on 2010-10-26
have you run mythtv-setup?

---

### Post by markackerman8@gmail.com on 2010-10-26
Every time I do, it complains:

that it can't connect to the server,
starting mysql complains "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'"
as well the no upnp or something always pops up,

arghhh and i am in the process of purging mythtv and mysqld for the third time, and perhaps I will find a few more files to delete that might make a difference,

arghhhh this is frustrating

thanks for your response,

Mark

---

### Post by nickrout on 2010-10-26
here is my dpkg -l|grep mythtv, you seem to be missing one or two:

```
nick@media:~$ dpkg -l|grep mythtv
ii  libmythtv-perl                       0.23.1+fixes26437-0ubuntu0+mythbuntu2           A PERL library to access some MythTV feature
ii  mythtv                               0.23.1+fixes26437-0ubuntu0+mythbuntu2           A personal video recorder application (clien
ii  mythtv-backend                       0.23.1+fixes26437-0ubuntu0+mythbuntu2           A personal video recorder application (serve
ii  mythtv-backend-master                0.23.1+fixes26437-0ubuntu0+mythbuntu2           Metapackage to setup and configure a "Master
ii  mythtv-common                        0.23.1+fixes26437-0ubuntu0+mythbuntu2           A personal video recorder application (commo
ii  mythtv-database                      0.23.1+fixes26437-0ubuntu0+mythbuntu2           A personal video recorder application (datab
ii  mythtv-frontend                      0.23.1+fixes26437-0ubuntu0+mythbuntu2           A personal video recorder application (clien
ii  mythtv-status                        0.9.2-3                                         Show the status of a MythTV backend
ii  mythtv-theme-arclight                1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The arclight MythTV Theme
ii  mythtv-theme-blootube-osd            1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                 1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The blueosd MythTV Theme
ii  mythtv-theme-childish                1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The childish MythTV Theme
ii  mythtv-theme-graphite                1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The graphite MythTV Theme
ii  mythtv-theme-iulius-osd              1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy              1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu               1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd      1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd               1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd          1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         The titivillus-osd MythTV Theme
ii  mythtv-themes                        1:0.23.1+fixes26437-0ubuntu0+mythbuntu2         Themes for MythTV
ii  mythtv-transcode-utils               0.23.1+fixes26437-0ubuntu0+mythbuntu2           Utilities used for transcoding MythTV tasks

```

try installing mythv-backend-master

---

### Post by markackerman8@gmail.com on 2010-10-26
I tried a purge of mythtv and mysqld for the 5th time, and it even asked me for my root password without complaints.

But, still:

1/ I cant enter mythtv-setup
  no UPnP,
&#8728; Cannot Login, or 
&#8728; Warning: Fake initctl called, doing nothing., or
&#8728; Cannot find (ping) database host  (a new problem), or
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'   (this seems to have been plaguing me).

Can anyone start the troubleshooting process please ,

Mark

---

### Post by bance on 2010-10-26
you could have a look at the log files /var/log/mythtv/mythbackend.log and /../../.../mythfrontend.log

---

### Post by nickrout on 2010-10-27
say again:

try installing mythv-backend-master

---

### Post by caeroe on 2010-11-02
Is there a solution to the "Cannot login" messages?  It's not "cannot login to database".  Been stuck, I never got Mythtv working, ever.

I also only use this on one PC.  So why do I need logins, passwords, and that bloat?  Isn't there something full featured like Windows Media Center?

---

### Post by markackerman8@gmail.com on 2010-11-02
I have HATED this error so many times in the past year and have been stuck for weeks at a time.  So I feel obligated to put my 2 cents worth here.

Solutions that have worked in the past are (Inclusively of course)
1/ check the password in your:
 sudo gedit /etc/mythtv/mysql.txt
&#8728; DBHostName=localhost
&#8728; DBUserName=mythtv
&#8728; DBName=mythconverg
&#8728; DBType=QMYSQL3
&#8728; DBPassword=[B]"could be something Strange here", normally it's mythtv

2/ Check the permissions of your Mythtv Folders that the user and group are both "Myttv", such locations are:
    /Home/Mythtv
    /var/lib/mythtv
3/ Try in the backend setup/ General/ ipadress using 127.0.0.1 or localhost
4/ and the easiest solution is to uninstall mythtv and reinstall (google how to purge it), or 
5/better yet a clean reinstall of your ubuntu which only takes 1-2 hours and can cut your losses and it is the guaranteed way to get a proper mythtv/mysql Database working after screwing it up for months

and that's all that comes to mind right now, I sure hope it helps someone, :P

Mark

---

### Post by nickrout on 2010-11-02
> **markackerman8@gmail.com said:**
> I have HATED this error so many times in the past year and have been stuck for weeks at a time.  So I feel obligated to put my 2 cents worth here.

Solutions that have worked in the past are (Inclusively of course)
1/ check the password in your:
 sudo gedit /etc/mythtv/mysql.txt
&#8728; DBHostName=localhost
&#8728; DBUserName=mythtv
&#8728; DBName=mythconverg
&#8728; DBType=QMYSQL3
&#8728; DBPassword=[B]"could be something Strange here", normally it's mythtv

Not normally mythtv on mythbuntu it is a randomly generated password.> 

2/ Check the permissions of your Mythtv Folders that the user and group are both "Myttv", such locations are:
    /Home/Mythtv
    /var/lib/mythtv
3/ Try in the backend setup/ General/ ipadress using 127.0.0.1 or localhost
4/ and the easiest solution is to uninstall mythtv and reinstall (google how to purge it), or 
5/better yet a clean reinstall of your ubuntu which only takes 1-2 hours and can cut your losses and it is the guaranteed way to get a proper mythtv/mysql Database working after screwing it up for months

and that's all that comes to mind right now, I sure hope it helps someone, :P

Mark

---

### Post by PigPopper on 2011-03-02
I just installed ubuntu (1st time ever) followed closely by mythtv and had the same *No UPnP backends found* problem. 

finally got around the problem when I noticed the password in ect/mythtv config.xml was the randomly generated one from before.

I switched back to that in the mysql.txt and at the system/administration/mythtv backend setup, process and have advanced to the next set-up stage. gl hope this helps others.

---

### Post by markackerman8@gmail.com on 2011-04-05
It seems it has a few causes of which I have experienced these:

incorrect password
my correct one is found in/by:
 sudo gedit /etc/mythtv/mysql.txt

Storage needs universal permissions and user and group are mythtv
&#8728; /var/lib/mythtv

just a few thoughts

---

