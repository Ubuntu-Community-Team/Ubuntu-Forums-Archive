---
title: "no upnp can't login to database"
date: 2011-08-04
forum: Multimedia Software
---

### Post by ulric on 2011-08-04
after installing mythtv 0.23+fixes24158 mythtv-setup. gives me a no UPNP warning.

on the mythtv wiki i found that the cause might be multiple mysql.txt files.
[http://www.mythtv.org/wiki/UPnP](http://www.mythtv.org/wiki/UPnP) 

but after deleting all doubles but /home/user/.mythtv/mysql.txt the problem still persists.

content of mysql.txt

```

DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

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

```more reasons i found were missing dependencies but i don't know what more to install. 



result of dpkg -l | grep myth

```
ii  libmyth-0.23-0                                 0.23.0+fixes24158-0ubuntu2                      Common library code for MythTV and add-on modules (runtim
ii  libmyth-python                                 0.23.0+fixes24158-0ubuntu2                      A python library to access some MythTV features
ii  libmythtv-perl                                 0.23.0+fixes24158-0ubuntu2                      A PERL library to access some MythTV features
ii  mytharchive                                    0.23.0+fixes24104-0ubuntu2                      create and burn DVD's from MythTV - binary file
ii  mythbrowser                                    0.23.0+fixes24104-0ubuntu2                      A web browser for MythTV
ii  mythbuntu-common                               0.50-0ubuntu1                                   Mythbuntu application support functions
ii  mythbuntu-control-centre                       0.62-0ubuntu1                                   Mythbuntu Configuration Application
rc  mythbuntu-default-settings                     0.96-0ubuntu1                                   default settings for Mythbuntu
ii  mythbuntu-gdm-theme                            0.6-0ubuntu1                                    Mythbuntu GDM theme
ii  mythbuntu-lirc-generator                       0.24-0ubuntu1                                   Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                          0.7-0ubuntu1                                    Mythbuntu repos installer
ii  mythexport                                     2.1.5-0ubuntu1                                  Export MythTV recording to portable media players
ii  mythgallery                                    0.23.0+fixes24104-0ubuntu2                      Image gallery/slideshow add-on module for MythTV
ii  mythgame                                       0.23.0+fixes24104-0ubuntu2                      Emulator & PC Game frontend module for MythTV
ii  mythmovies                                     0.23.0+fixes24104-0ubuntu2                      Find nearby movies and cinema listings
ii  mythmusic                                      0.23.0+fixes24104-0ubuntu2                      Music add-on module for MythTV
ii  mythnettv                                      7+dfsg-0ubuntu2                                 Plugin to download video from RSS feeds
ii  mythnettv-gui                                  1.0-0ubuntu3                                    Gui frontend for MythNetTV
ii  mythnetvision                                  0.23.0+fixes24104-0ubuntu2                      A Internet Video Player plugin for MythTV
ii  mythnews                                       0.23.0+fixes24104-0ubuntu2                      An RSS feed news reader module for MythTV
ii  mythplugins                                    0.23.0+fixes24104-0ubuntu2                      Wrapper package for MythTV plugins
ii  mythtv                                         0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (client and server)
ii  mythtv-backend                                 0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (server)
ii  mythtv-backend-master                          0.23.0+fixes24158-0ubuntu2                      Metapackage to setup and configure a "Master Backend" pro
ii  mythtv-common                                  0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (common data)
ii  mythtv-database                                0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (database)
ii  mythtv-frontend                                0.23.0+fixes24158-0ubuntu2                      A personal video recorder application (client)
ii  mythtv-theme-arclight                          1:0.23.0+fixes23872-0ubuntu1                    The arclight MythTV Theme
ii  mythtv-theme-blootube-osd                      1:0.23.0+fixes23872-0ubuntu1                    The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                           1:0.23.0+fixes23872-0ubuntu1                    The blueosd MythTV Theme
ii  mythtv-theme-graphite                          1:0.23.0+fixes23872-0ubuntu1                    The graphite MythTV Theme
ii  mythtv-theme-iulius-osd                        1:0.23.0+fixes23872-0ubuntu1                    The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy                        1:0.23.0+fixes23872-0ubuntu1                    The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                          1:0.23.0+fixes23872-0ubuntu1                    The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu                         1:0.23.0+fixes23872-0ubuntu1                    The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd                1:0.23.0+fixes23872-0ubuntu1                    The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd                         1:0.23.0+fixes23872-0ubuntu1                    The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd                    1:0.23.0+fixes23872-0ubuntu1                    The titivillus-osd MythTV Theme
ii  mythtv-themes                                  1:0.23.0+fixes23872-0ubuntu1                    Themes for MythTV
ii  mythtv-transcode-utils                         0.23.0+fixes24158-0ubuntu2                      Utilities used for transcoding MythTV tasks
ii  mythvideo                                      0.23.0+fixes24104-0ubuntu2                      A generic video player frontend module for MythTV
ii  mythweather                                    0.23.0+fixes24104-0ubuntu2                      Weather add-on module for MythTV
ii  mythweb                                        0.23.0+fixes24104-0ubuntu2                      Web interface add-on module for MythTV


```contents of /var/log/mythtv/mythbackend.log

```


2011-08-04 22:24:28.140 UPnPautoconf() - No UPnP backends found
2011-08-04 22:24:28.158 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-08-04 22:24:28.224 Deleting UPnP client...
2011-08-04 22:24:28.850 Failed to init MythContext, exiting.
2011-08-04 22:24:28.993 mythbackend version: branches/release-0-23-fixes [24158] www.mythtv.org
2011-08-04 22:24:28.994 Using runtime prefix = /usr
2011-08-04 22:24:28.998 Using configuration directory = /home/mythtv/.mythtv
2011-08-04 22:24:29.009 Unable to read configuration file mysql.txt
2011-08-04 22:24:29.020 Empty LocalHostName.
2011-08-04 22:24:29.031 Using localhost value of pc-erwin
2011-08-04 22:24:29.050 New DB connection, total: 1
2011-08-04 22:24:29.056 Unable to connect to database!
2011-08-04 22:24:29.064 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

```any suggestions on what might be wrong?

regards Ulric

---

### Post by BillFann on 2011-08-29
ulric,
I had the same  "no UPnP" message. It turned out that the front-end couldn't see the back-end.
In order to fix it I got  help from markackerman8 on this list. He walked me through the setup.
Basically it went like this:

[LIST=1]
[*]Start with the Mythbuntu control panel. Go through **each** step.
[*]Do the frontend setup next.
[*]Do the backend setup last.
[/LIST]
Mr. Ackerman helped me with this and it all worked. He has created a step by step instruction sheet. If you contact him he'll likely provide it.
Good luck. 
Bill

---

### Post by ulric on 2011-08-29
Thanks for the answer. It turned out that in the mythbuntu configuration the computer wasn't set as the master backend. therfore the frontend couldn't find the server.
 

regards Ulric

---

