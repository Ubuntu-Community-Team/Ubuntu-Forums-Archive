---
title: "Update Manager and MythTV Backend Setup failing in Mythbuntu 14.04"
date: 2014-10-25
forum: Mythbuntu
---

### Post by DanBender on 2014-10-25
I haven't been able to update any of my packages in some time; pretty much since I upgraded to 14.04.

Software Updater tells me that the updates have already been downloaded, so it isn't a repository problem, I don't think. It goes:

"Applying changes..."
"Configuring mythtv-database..."

...and then it craps out and says

"Package Operation Failed
The installation or removal of a software package failed."

Running apt-get upgrade:
```
Preconfiguring packages ...
Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing package mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It's pretty obvious there's something wrong with my MythTV configuration that's knocking the package manager on it's face (though why that would happen is beyond me), but it's not clear to me what it is or how to fix it. When I try to run the MythTV Backend Setup, it drops me into a blue screen (consistent with my theme)...and then drops me back to the desktop and asks me if I want to start mythbackend. Without any option to configure anything, in particular the path to mythconverg.

I tried starting the frontend too, but that just said something like the database is 28 versions out of date, then crashed and kept trying to restart. It's almost like I don't have any valid database. I have backups, but if I can't even get mythtv-setup to *start,* it's kind of hard to address this. Any thoughts?

Thanks in advance,
Dan

---

### Post by tgm4883 on 2014-10-25
> **DanBender said:**
> I haven't been able to update any of my packages in some time; pretty much since I upgraded to 14.04.

Software Updater tells me that the updates have already been downloaded, so it isn't a repository problem, I don't think. It goes:

"Applying changes..."
"Configuring mythtv-database..."

...and then it craps out and says

"Package Operation Failed
The installation or removal of a software package failed."

Running apt-get upgrade:
```
Preconfiguring packages ...
Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing package mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mythtv-database
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It's pretty obvious there's something wrong with my MythTV configuration that's knocking the package manager on it's face (though why that would happen is beyond me), but it's not clear to me what it is or how to fix it. When I try to run the MythTV Backend Setup, it drops me into a blue screen (consistent with my theme)...and then drops me back to the desktop and asks me if I want to start mythbackend. Without any option to configure anything, in particular the path to mythconverg.

I tried starting the frontend too, but that just said something like the database is 28 versions out of date, then crashed and kept trying to restart. It's almost like I don't have any valid database. I have backups, but if I can't even get mythtv-setup to *start,* it's kind of hard to address this. Any thoughts?

Thanks in advance,
Dan

You have the wrong info in /etc/mythtv/config.xml. Please check it against /etc/mythtv/mysql.txt

---

### Post by DanBender on 2014-10-26
> **tgm4883 said:**
> You have the wrong info in /etc/mythtv/config.xml. Please check it against /etc/mythtv/mysql.txt

Okay, looked at those two files. They were not matching:
They WERE:
mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBPort=3306
DBUserName=mythtv
DBPassword=9d2keLTL
DBName=mythconverg
DBType=QMYSQL

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
```
config.xml
```
<Configuration>
  <Database>
    <PingHost>1</PingHost>
    <Host></Host>
    <UserName></UserName>
    <Password></Password>
    <DatabaseName></DatabaseName>
    <Port></Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>
```

I changed them to be:
mysql.txt
```
DBHostName=tv-computer

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBPort=3306
DBUserName=mythtv
DBPassword=9d2keLTL
DBName=mythconverg
DBType=QMYSQL

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
```
config.xml
```
<Configuration>
  <Database>
    <PingHost>1</PingHost>
    <Host>tv-computer</Host>
    <UserName>mythtv</UserName>
    <Password>9d2keLTL</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
</Configuration>
```

**That didn't do anything - no change in behavior, at least for backend setup.** I was about to try starting mythfrontend to see if *that* acted any differently, but since I'm trying to run configuration over VNC, I can't jump to a true terminal using Ctl-Alt-F1 or whatever to reboot the computer in case of the crash-restart loop I was getting last time. I figured I'd try to SSH in if that happened again (though, since I've never logged in using SSH from another computer, I'm not sure how to do that...)...and went to make sure I had SSH installed.

I did not.

I installed it in Synaptic, and lo and behold, during that operation, it showed configure-mythdatabase as working, and afterwards, it opened mythtv-setup just fine. And then software updater worked too.

It's not obvious if the changes to the database settings were necessary to fix that, but they WERE something that needed to be fixed.

tl,dr: - **MAKE SURE ALL YOUR SERVICES ARE INSTALLED.**

---

### Post by tgm4883 on 2014-10-27
> **DanBender said:**
> <snip>

tl,dr: - **MAKE SURE ALL YOUR SERVICES ARE INSTALLED.**

The TL;DR should be "make sure you have the right credentials in config.xml". Installing SSH had nothing to do with it other than it fired up apt and finished installing your half configured packages.

---

