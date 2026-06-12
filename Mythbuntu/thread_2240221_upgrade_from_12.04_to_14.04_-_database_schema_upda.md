---
title: "upgrade from 12.04 to 14.04 - database schema update didn't occur"
date: 2014-08-18
forum: Mythbuntu
---

### Post by neutron68 on 2014-08-18
A friend whose Mythbuntu system I maintain, decided to click the Upgrade button in the Software Updater window, without me handy to advise.
It did not finish well, and no backup was made prior to starting.

He is getting an GUI error box that says: 
> This version of MythTV requires an updated database. (schema is 18 versions behind).  
Please run mythtv-setup or mythbackend to update your database
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-08-17230138_zps10120fbc.jpg[/IMG]

To see if I could duplicate his situation, I ran an update on a Mythbuntu 12.04 virtual machine.  
During the update process, I was asked to allow the replacement of existing config files (of various services such as apache2, and SAMBA) with stock config files from the developers.  
Towards the end of the update process, I got a screen asking for permission to update the database from 1019 to 1020.  
I had to choose Exit or Upgrade in order to continue.
Next, I got a screen saying:
> If your system becomes unstable, a database backup file called mythconverg-1317-20140818164933.sql.gz is located in /var/lib/mythtv/db_backups.  
There are also other clients using this database.  They should be shut down first.
Again, I had to choose Exit or Upgrade in order to continue.

My friend says he was never shown these screens regarding the database update.

Is there a way to activate the database schema update, manually?  
For example, is there a script file I could run to make it happen?

Also, is there a log file that shows the steps of the upgrade process?

Thanks,
Eric

---

### Post by tgm4883 on 2014-08-18
> **neutron68 said:**
> A friend whose Mythbuntu system I maintain, decided to click the Upgrade button in the Software Updater window, without me handy to advise.
It did not finish well, and no backup was made prior to starting.

He is getting an GUI error box that says: 


To see if I could duplicate his situation, I ran an update on a Mythbuntu 12.04 virtual machine.  
During the update process, I was asked to allow the replacement of existing config files (of various services such as apache2, and SAMBA) with stock config files from the developers.  
Towards the end of the update process, I got a screen asking for permission to update the database from 1019 to 1020.  
I had to choose Exit or Upgrade in order to continue.
Next, I got a screen saying:

Again, I had to choose Exit or Upgrade in order to continue.

My friend says he was never shown these screens regarding the database update.

Is there a way to activate the database schema update, manually?  
For example, is there a script file I could run to make it happen?

Also, is there a log file that shows the steps of the upgrade process?

Thanks,
Eric

You don't get those screens during upgrade. You get them during the first start after upgrade of mythtv-setup and mythfrontend. I'd try that first.

---

### Post by neutron68 on 2014-08-19
> **tgm4883 said:**
> You don't get those screens during upgrade. You get them during the first start after upgrade of mythtv-setup and mythfrontend. I'd try that first.
Thanks for the reply.  That sounds like a good place to start.

How do I activate those steps?   
Can I do it for my friend remotely via SSH (which still works)?  Type "mythtv-setup" into a command line, via SSH?
Or do I need to activate them directly via his keyboard/mouse?  If via his keyboard/mouse, how do I activate?

Today as I was trying to figure out what to do, I typed "mythtv-setup" into a command line on my updated Mythbuntu 14.04 virtual machine, and the Mythtv Backend Setup utility started.  
Is this was you would expect to happen?  There were no buttons or check boxes for database update in the Mythtv Backend Setup on the virtual machine.  Do you think it would be different on my friend's updated Mythbuntu 14.04 machine?

**As a backup plan, how easy would it be to force the 14.04 upgrade process to run again and hope it completes all the steps this time?**
"sudo apt-get -f dist-upgrade"?

Eric

---

### Post by tgm4883 on 2014-08-19
> **neutron68 said:**
> Thanks for the reply.  That sounds like a good place to start.

How do I activate those steps?   
Can I do it for my friend remotely via SSH (which still works)?  Type "mythtv-setup" into a command line, via SSH?
Or do I need to activate them directly via his keyboard/mouse?  If via his keyboard/mouse, how do I activate?

Today as I was trying to figure out what to do, I typed "mythtv-setup" into a command line on my updated Mythbuntu 14.04 virtual machine, and the Mythtv Backend Setup utility started.  Is this was you would expect to happen?  There were no buttons or check boxes for database update in the Mythtv Backend Setup on the virtual machine.  Do you think it would be different on my friend's updated Mythbuntu 14.04 machine?

As a backup plan, how easy would it be to force the 14.04 upgrade process to run again and hope it completes all the steps this time?
"sudo apt-get -f dist-upgrade"?

Eric

He would have to run it. It will start the mythbackend setup and will prompt for upgrade if it needs it. You should get a similar prompt when starting the frontend.

What you should also do is verify all of the mythtv packages are the same version by running "dpkg -l | grep myth"

---

### Post by neutron68 on 2014-08-19
> **tgm4883 said:**
> He would have to run it. It will start the mythbackend setup and will prompt for upgrade if it needs it. You should get a similar prompt when starting the frontend.

What you should also do is verify all of the mythtv packages are the same version by running "dpkg -l | grep myth"
Here is the output ot the dpkg grep command:
```
rc  libmyth-0.25-0                        2:0.25.3+fixes.20130813.b5adf03-0ubuntu0mythbuntu2 amd64        Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.27-0                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          A python library to access some MythTV features
ii  libmythtv-perl                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          A PERL library to access some MythTV features
ii  mytharchive                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        create and burn DVD's from MythTV - binary file
ii  mythbrowser                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        A web browser for MythTV
ii  mythbuntu-bare-client                 2.6                                                all          Mythbuntu Bare Client
ii  mythbuntu-common                      0.74                                               all          Mythbuntu application support functions
ii  mythbuntu-control-centre              0.64.1                                             all          Mythbuntu Configuration Application
ii  mythbuntu-default-settings            1.11                                               all          default settings for Mythbuntu
ii  mythbuntu-desktop                     0.82                                               amd64        The Mythbuntu standalone system
ii  mythbuntu-lightdm-theme               1.01                                               all          Mythbuntu LightDM setup
ii  mythbuntu-lirc-generator              0.26-0ubuntu2                                      all          Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                 0.11-0ubuntu2                                      all          Mythbuntu diagnostic utility
iU  mythexport                            2.2.4-0ubuntu2                                     amd64        Export MythTV recording to portable media players
ii  mythgallery                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Image gallery/slideshow add-on module for MythTV
ii  mythgame                              2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Emulator & PC Game frontend module for MythTV
ii  mythmusic                             2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Music add-on module for MythTV
ii  mythnetvision                         2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        A Internet Video Player plugin for MythTV
ii  mythnews                              2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        An RSS feed news reader module for MythTV
iU  mythtv                                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Personal video recorder application (client and server)
ii  mythtv-backend                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (server)
iU  mythtv-backend-master                 2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                         2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (common data)
iF  mythtv-database                       2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Personal video recorder application (database)
ii  mythtv-dbg                            2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Debug symbols for mythtv packages
ii  mythtv-frontend                       2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (client)
ii  mythtv-theme-mythbuntu                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Utilities used for transcoding MythTV tasks
ii  mythweather                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Weather add-on module for MythTV
ii  mythweb                               2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Web interface add-on module for MythTV
ii  php-mythtv                            2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          PHP Bindings for MythTV
```

The package list looks like there is a mix of 0.25 and 0.27 packages, as if the upgrade didn't get to the end.

As you implied, I was not able to run mythtv-setup via SSH (because it depends on GUI windows, which aren't visible over SSH).

My friend said he was able to run Mythtv Backend Setup from the menu icon.  
I think it failed and then Mythfilldatabase wanted to run so he let it try.
Then he saw the message "Waiting for database schema upgrade lock" over and over.
see movie:
[https://www.youtube.com/watch?v=bHd8eNZzkAE]("https://www.youtube.com/watch?v=bHd8eNZzkAE")

Later, I was able to run the mythbackend command via SSH and get some different output.  
It's not happy about Time Zone support?  Did it get removed during the upgrade process?
```
user@Mythbuntu:~$ mythbackend
2014-08-19 17:50:02.097784 C  mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
2014-08-19 17:50:02.097820 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2014-08-19 17:50:02.097828 N  Enabled verbose msgs:  general
2014-08-19 17:50:02.097846 N  Setting Log Level to LOG_INFO
2014-08-19 17:50:02.109011 I  Added logging to the console
2014-08-19 17:50:02.109687 I  Setup Interrupt handler
2014-08-19 17:50:02.109703 I  Setup Terminated handler
2014-08-19 17:50:02.109717 I  Setup Segmentation fault handler
2014-08-19 17:50:02.109729 I  Setup Aborted handler
2014-08-19 17:50:02.109741 I  Setup Bus error handler
2014-08-19 17:50:02.109755 I  Setup Floating point exception handler
2014-08-19 17:50:02.109768 I  Setup Illegal instruction handler
2014-08-19 17:50:02.109785 I  Setup Real-time signal 0 handler
2014-08-19 17:50:02.109847 N  Using runtime prefix = /usr
2014-08-19 17:50:02.109869 N  Using configuration directory = /home/user/.mythtv
2014-08-19 17:50:02.109989 I  Assumed character encoding:
2014-08-19 17:50:02.110002 W  This application expects to be running a locale that specifies a UTF-8 codeset, and many features may behave improperly with your current language settings. Please set the LC_ALL or LC_CTYPE, and LANG variable(s) in the environment in which this program is executed to include a UTF-8 codeset (such as 'en_US.UTF-8').
2014-08-19 17:50:02.110522 N  Empty LocalHostName.
2014-08-19 17:50:02.110537 I  Using localhost value of Mythbuntu
2014-08-19 17:50:02.142044 N  Setting QT default locale to EN_US
2014-08-19 17:50:02.142142 I  Current locale EN_US
2014-08-19 17:50:02.142225 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2014-08-19 17:50:02.148287 E  MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.
2014-08-19 17:50:02.211924 I  New Client:  (#1)
```

I found the answer to my question in my previous message (where the log file for the upgrade is).
I found it in /var/log/dist-upgrade.  
There are several logs in there - main.log, history.log, lspci.txt, term.log, apt-term.log, apt.log.
Here's the main.log.  You can see the database update failed at 00:22:53.
```
2014-08-17 00:20:59,329 INFO Using config files '['./DistUpgrade.cfg.precise']'
2014-08-17 00:20:59,329 INFO uname information: 'Linux Mythbuntu 3.2.0-59-generic #90-Ubuntu SMP Tue Jan 7 22:43:51 UTC 2014 x86_64'
2014-08-17 00:20:59,329 INFO apt version: '0.8.16~exp12ubuntu10.16'
2014-08-17 00:20:59,329 INFO release-upgrader version '0.220.2' started
2014-08-17 00:21:01,138 DEBUG Using 'DistUpgradeViewGtk3' view
2014-08-17 00:21:01,254 DEBUG aufsOptionsAndEnvironmentSetup()
2014-08-17 00:21:01,255 DEBUG using '/tmp/upgrade-rw-M84Ar4' as aufs_rw_dir
2014-08-17 00:21:01,255 DEBUG using '/tmp/upgrade-chroot-KrIWKH' as aufs chroot dir
2014-08-17 00:21:01,255 DEBUG enable dpkg --force-overwrite
2014-08-17 00:21:01,346 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2014-08-17 00:21:05,310 DEBUG lsb-release: 'precise'
2014-08-17 00:21:05,311 DEBUG _pythonSymlinkCheck run
2014-08-17 00:21:05,330 DEBUG openCache()
2014-08-17 00:21:05,331 DEBUG No such plugin directory: ./plugins
2014-08-17 00:21:05,331 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2014-08-17 00:21:05,332 DEBUG plugins for condition 'trustyPreCacheOpen' are '[]'
2014-08-17 00:21:05,332 DEBUG plugins for condition 'from_precisePreCacheOpen' are '[]'
2014-08-17 00:21:05,332 DEBUG quirks: running PreCacheOpen
2014-08-17 00:21:05,332 DEBUG running Quirks.PreCacheOpen
2014-08-17 00:21:06,631 DEBUG /openCache(), new cache size 63410
2014-08-17 00:21:06,632 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'mythbuntu-desktop')
2014-08-17 00:21:06,632 DEBUG checkViewDepends()
2014-08-17 00:21:06,648 DEBUG running doUpdate() (showErrors=False)
2014-08-17 00:21:16,157 DEBUG openCache()
2014-08-17 00:21:25,039 DEBUG /openCache(), new cache size 63430
2014-08-17 00:21:25,040 DEBUG doPostInitialUpdate
2014-08-17 00:21:25,040 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2014-08-17 00:21:25,040 DEBUG plugins for condition 'trustyPostInitialUpdate' are '[]'
2014-08-17 00:21:25,040 DEBUG plugins for condition 'from_precisePostInitialUpdate' are '[]'
2014-08-17 00:21:25,040 DEBUG quirks: running from_precisePostInitialUpdate
2014-08-17 00:21:25,040 DEBUG _checkPae
2014-08-17 00:21:33,613 DEBUG Foreign: mythtv-transcode-utils libxmltv-perl mythtv-frontend mythbuntu-bare-client xmltv-util xmltv-gui xmltv libmyth-0.25-0 mythnetvision mythweb mythgame psensor-common mythbuntu-log-grabber php-mythtv libmyth-python mythmusic mythtv-common psensor mythweather mythgallery mytharchive mythtv-backend mythnews mythtv-theme-mythbuntu mythtv mythtv-database libmythtv-perl mythbrowser mythtv-backend-master
2014-08-17 00:21:33,613 DEBUG Obsolete: libdvdcss2
2014-08-17 00:21:33,614 DEBUG updateSourcesList()
2014-08-17 00:21:33,910 DEBUG rewriteSourcesList()
2014-08-17 00:21:33,919 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted'
2014-08-17 00:21:33,919 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted' updated to new dist
2014-08-17 00:21:33,919 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties'
2014-08-17 00:21:33,920 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty restricted main multiverse universe #Added by software-properties' updated to new dist
2014-08-17 00:21:33,920 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted'
2014-08-17 00:21:33,920 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted' updated to new dist
2014-08-17 00:21:33,920 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties'
2014-08-17 00:21:33,920 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates restricted main multiverse universe #Added by software-properties' updated to new dist
2014-08-17 00:21:33,920 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise universe'
2014-08-17 00:21:33,920 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty universe' updated to new dist
2014-08-17 00:21:33,921 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe'
2014-08-17 00:21:33,921 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe' updated to new dist
2014-08-17 00:21:33,921 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse'
2014-08-17 00:21:33,921 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse' updated to new dist
2014-08-17 00:21:33,921 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse'
2014-08-17 00:21:33,921 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse' updated to new dist
2014-08-17 00:21:33,921 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse'
2014-08-17 00:21:33,922 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse' updated to new dist
2014-08-17 00:21:33,922 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties'
2014-08-17 00:21:33,922 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse #Added by software-properties' updated to new dist
2014-08-17 00:21:33,922 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security main restricted'
2014-08-17 00:21:33,922 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security main restricted' updated to new dist
2014-08-17 00:21:33,922 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties'
2014-08-17 00:21:33,922 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security restricted main multiverse universe #Added by software-properties' updated to new dist
2014-08-17 00:21:33,923 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security universe'
2014-08-17 00:21:33,923 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security universe' updated to new dist
2014-08-17 00:21:33,923 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security multiverse'
2014-08-17 00:21:33,923 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security multiverse' updated to new dist
2014-08-17 00:21:33,923 DEBUG examining: 'deb http://archive.canonical.com/ubuntu precise partner'
2014-08-17 00:21:33,923 DEBUG entry 'deb http://archive.canonical.com/ubuntu trusty partner' updated to new dist
2014-08-17 00:21:33,924 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu precise partner'
2014-08-17 00:21:33,924 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu trusty partner' updated to new dist
2014-08-17 00:21:33,924 DEBUG examining: 'deb http://extras.ubuntu.com/ubuntu precise main'
2014-08-17 00:21:33,924 DEBUG entry 'deb http://extras.ubuntu.com/ubuntu trusty main' updated to new dist
2014-08-17 00:21:33,924 DEBUG examining: 'deb-src http://extras.ubuntu.com/ubuntu precise main'
2014-08-17 00:21:33,925 DEBUG entry 'deb-src http://extras.ubuntu.com/ubuntu trusty main' updated to new dist
2014-08-17 00:21:33,925 DEBUG examining: 'deb http://ppa.launchpad.net/mythbuntu/xmltv/ubuntu precise main'
2014-08-17 00:21:33,930 DEBUG entry '# deb http://ppa.launchpad.net/mythbuntu/xmltv/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,930 DEBUG examining: 'deb-src http://ppa.launchpad.net/mythbuntu/xmltv/ubuntu precise main'
2014-08-17 00:21:33,935 DEBUG entry '# deb-src http://ppa.launchpad.net/mythbuntu/xmltv/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,935 DEBUG examining: 'deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main'
2014-08-17 00:21:33,940 DEBUG entry '# deb http://ppa.launchpad.net/mythbuntu/0.25/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,941 DEBUG examining: 'deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu precise main'
2014-08-17 00:21:33,946 DEBUG entry '# deb-src http://ppa.launchpad.net/mythbuntu/0.25/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,946 DEBUG examining: 'deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main'
2014-08-17 00:21:33,951 DEBUG entry '# deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,951 DEBUG examining: 'deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu precise main'
2014-08-17 00:21:33,956 DEBUG entry '# deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,956 DEBUG examining: 'deb http://ppa.launchpad.net/jfi/ppa/ubuntu precise main'
2014-08-17 00:21:33,961 DEBUG entry '# deb http://ppa.launchpad.net/jfi/ppa/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:33,962 DEBUG examining: 'deb-src http://ppa.launchpad.net/jfi/ppa/ubuntu precise main'
2014-08-17 00:21:33,967 DEBUG entry '# deb-src http://ppa.launchpad.net/jfi/ppa/ubuntu trusty main # disabled on upgrade to trusty' was disabled (unknown mirror)
2014-08-17 00:21:39,288 DEBUG running doUpdate() (showErrors=True)
2014-08-17 00:22:25,529 DEBUG openCache()
2014-08-17 00:22:25,530 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-08-17 00:22:34,317 DEBUG /openCache(), new cache size 70919
2014-08-17 00:22:34,319 DEBUG need_server_mode(): run in 'desktop' mode, (because of pkg 'mythbuntu-desktop')
2014-08-17 00:22:45,723 DEBUG Running KeepInstalledSection rules
2014-08-17 00:22:47,793 DEBUG Kernel uname: '3.2.0-59-generic' 
2014-08-17 00:22:47,835 DEBUG nvidiaUpdate()
2014-08-17 00:22:50,985 INFO no old nvidia driver installed, installing no new
2014-08-17 00:22:50,986 DEBUG Upgrading 'brasero' (Distro PostUpgradeUpgrade rule)
2014-08-17 00:22:50,986 DEBUG Upgrading 'edubuntu-desktop' (Distro PostUpgradeUpgrade rule)
2014-08-17 00:22:50,987 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'kvm-source' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'gtk-qt-engine' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'libparted1.8-12' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'usplash' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'printconf' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'foomatic-db-gutenprint' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,987 DEBUG Removing 'ebox-printers' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,988 DEBUG Removing 'kbluetooth' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,988 DEBUG Removing 'kde-plasmoid-cwp' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,988 DEBUG Removing 'kdm' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,988 DEBUG Removing 'xsettings-kde' (Distro PostUpgradeRemove rule)
2014-08-17 00:22:50,988 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2014-08-17 00:22:50,989 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2014-08-17 00:22:50,989 DEBUG Purging 'linux-restricted-modules-common' (Distro PostUpgradePurge rule)
2014-08-17 00:22:50,989 DEBUG plugins for condition 'PostDistUpgradeCache' are '[]'
2014-08-17 00:22:50,989 DEBUG plugins for condition 'trustyPostDistUpgradeCache' are '[]'
2014-08-17 00:22:50,989 DEBUG plugins for condition 'from_precisePostDistUpgradeCache' are '[]'
2014-08-17 00:22:50,990 DEBUG Marking 'mythbuntu-desktop' for upgrade
2014-08-17 00:22:51,838 DEBUG About to apply the following changes
2014-08-17 00:22:53,561 DEBUG Keep at same version: atomicparsley cmap-adobe-japan1 ffmpeg friendly-recovery gir1.2-launchpad-integration-3.0 grub-gfxpayload-lists gs-cjk-resource gsfonts hunspell-en-us laptop-detect launchpad-integration libapt-inst1.4 libattica0.3 libavcodec-extra-53 libavformat-extra-53 libavutil-extra-51 libbind9-80 libcarp-clan-perl libclass-factory-util-perl libclass-singleton-perl libclucene0ldbl libdatetime-format-w3cdtf-perl libdconf0 libdigest-hmac-perl libdns81 libdrm-nouveau1a libdvbpsi7 libdvdcss2 libebml3 libexiv2-11 libexporter-lite-perl libfile-basedir-perl libfile-copy-recursive-perl libfont-afm-perl libgd2-xpm libgdu0 libgnome-bluetooth8 libgphoto2-2 libgphoto2-port0 libhtml-tableextract-perl libhtml-tagset-perl libhttp-cookies-perl libhttp-negotiate-perl libhttp-server-simple-perl libicu48 libimobiledevice2 libio-stringy-perl libisc83 libisccc80 libisccfg82 libkipi8 liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libllvm3.0 liblwres80 libmagickcore4 libmagickwand4 libmatroska5 libmjpegtools-1.9 libmng1 libmpc2 libnepomukdatamanagement4 libnepomuksync4 libnet-daemon-perl libnet-upnp-perl liboobs-1-5 libplrpc-perl libpoppler19 libqapt-runtime libqapt1 libsox1b libswitch-perl libtasn1-3 libtext-wrapi18n-perl libtiff4 libudev0 libusbmuxd1 libuser1 libwww-robotrules-perl libx264-120 libxatracker1 libxfce4util4 libxml-dom-perl libxml-perl libxml-sax-base-perl libxml-sax-expat-perl libxml-xpath-perl libyajl1 linux-headers-3.2.0-23 linux-headers-3.2.0-23-generic linux-headers-3.2.0-25 linux-headers-3.2.0-25-generic linux-headers-3.2.0-26 linux-headers-3.2.0-26-generic linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic linux-headers-3.2.0-36 linux-headers-3.2.0-36-generic linux-headers-3.2.0-38 linux-headers-3.2.0-38-generic linux-headers-3.2.0-55 linux-headers-3.2.0-55-generic linux-headers-3.2.0-59 linux-headers-3.2.0-59-generic linux-image-3.2.0-23-generic linux-image-3.2.0-25-generic linux-image-3.2.0-26-generic linux-image-3.2.0-30-generic linux-image-3.2.0-36-generic linux-image-3.2.0-38-generic linux-image-3.2.0-55-generic linux-image-3.2.0-59-generic mythbuntu-lightdm-theme pppoeconf psensor psensor-common python-central python-gnupginterface python-libuser system-tools-backends ubuntu-extras-keyring xfonts-base xfonts-encodings xfonts-scalable
2014-08-17 00:22:53,561 DEBUG Upgradable, but held- back: 
2014-08-17 00:22:53,562 DEBUG Remove: apache2.2-common jockey-common jockey-gtk language-pack-kde-en-base libavfilter2 libgtksourceview-3.0-0 libmyth-0.25-0 libperl5.14 libpostproc-extra-52 libupnp3 libvlccore5 ubuntu-sso-client-gtk xfce4-utils xz-lzma
2014-08-17 00:22:53,562 DEBUG Install: apache2 apache2-bin apache2-data apport-noui at-spi2-core attr cdparanoia cdrdao colord cpp-4.8 desktop-base dh-python diffstat dtv-scan-tables ethtool fonts-dejavu fonts-dejavu-core fonts-dejavu-extra fonts-freefont-ttf fonts-tlwg-purisa gcc-4.8 gcc-4.8-base gcc-4.9-base gcr gdisk gettext gir1.2-gstreamer-1.0 gir1.2-wnck-3.0 gnome-accessibility-themes gnome-icon-theme-full gnome-icon-theme-symbolic gnome-themes-standard gnome-themes-standard-data gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x gvfs-backends hardening-includes init-system-helpers intltool-debian iproute2 k3b k3b-data k3b-i18n kmod libaio1 libao-common libao4 libapparmor-perl libapparmor1 libapt-inst1.5 libapt-pkg-perl libarchive-extract-perl libarchive13 libasan0 libasound2-data libasprintf-dev libasprintf0c2 libatk-bridge2.0-0 libatm1 libatomic1 libatspi2.0-0 libattica0.4 libaudit-common libaudit1 libauthen-sasl-perl libautodie-perl libavahi-glib1 libavcodec-extra-54 libavdevice53 libavfilter3 libavformat-extra-54 libavformat54 libavresample1 libavutil-extra-52 libavutil52 libbaloocore4 libbaloofiles4 libbalooxapian4 libbasicusageenvironment0 libbind9-90 libbit-vector-perl libblas3 libbluetooth3 libc6-dbg libcgmanager0 libchromaprint0 libclass-accessor-perl libclone-perl libcloog-isl4 libclucene-core1 libcolord1 libcolorhug1 libcuda1-304 libcupsfilters1 libdate-calc-perl libdate-calc-xs-perl libdb5.3 libdconf1 libdebconfclient0 libdist-checkconflicts-perl libdns100 libdpkg-perl libdrm-nouveau2 libdvbpsi8 libebml4 libegl1-mesa libegl1-mesa-drivers libelfg0 libepub0 libestr0 libexiv2-12 libfakeroot libfftw3-double3 libfftw3-long3 libfftw3-single3 libfile-fcntllock-perl libflac++6 libfreerdp1 libgbm1 libgcc-4.8-dev libgcr-base-3-1 libgcr-ui-3-1 libgd3 libgettextpo-dev libgettextpo0 libglamor0 libgnome-bluetooth11 libgnutls-openssl27 libgnutls28 libgphoto2-6 libgphoto2-port10 libgraphite2-3 libgroupsock1 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtksourceview-3.0-1 libgusb2 libharfbuzz-icu0 libharfbuzz0b libhdb9-heimdal libhogweed2 libicu52 libido3-0.1-0 libimobiledevice4 libio-html-perl libio-pty-perl libio-sessiondata-perl libio-string-perl libipc-run-perl libipc-system-simple-perl libisc95 libisccc90 libisccfg90 libisl10 libitm1 libjbig0 libjson-c2 libjson-glib-1.0-0 libjson-glib-1.0-common libk3b6 libkactivities-bin libkactivities-models1 libkactivities6 libkcddb4 libkcompactdisc4 libkdc2-heimdal libkipi11 libkmod2 libkubuntu0 libkxmlrpcclient4 liblavfile-2.1-0 liblavjpeg-2.1-0 liblavplay-2.1-0 libldb1 liblinear-tools liblinear1 liblivemedia23 libllvm3.4 liblog-message-simple-perl liblua5.2-0 liblwres90 libmagickcore5 libmagickwand5 libmatroska6 libmbim-glib0 libmjpegutils-2.1-0 libmm-glib0 libmnl0 libmodule-implementation-perl libmodule-pluggable-perl libmpc3 libmpdec2 libmpeg2encpp-2.1-0 libmplex2-2.1-0 libmusicbrainz5-0 libmyth-0.27-0 libneon27-gnutls libnepomukcleaner4 libnepomukcore4abi1 libnet-smtp-ssl-perl libnettle4 libnss3-nssdb libntdb1 libnuma1 libopenvg1-mesa libopus0 libp11-kit-gnome-keyring libpam-systemd libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangox-1.0-0 libpangoxft-1.0-0 libparse-debianchangelog-perl libperl4-corelibs-perl libperl5.18 libperlio-gzip-perl libpod-latex-perl libpoppler-qt4-4 libpoppler44 libpostproc52 libprocps3 libproxy-tools libpython-stdlib libpython2.7-minimal libpython2.7-stdlib libpython3-stdlib libpython3.4 libpython3.4-minimal libpython3.4-stdlib libqapt2 libqapt2-runtime libqjson0 libqmi-glib0 libqmobipocket1 libqtdbus4 libreadline5 libsasl2-modules-db libsecret-1-0 libsecret-common libsemanage-common libsemanage1 libsepol1 libsox2 libspice-server1 libssh2-1 libsub-identify-perl libsub-name-perl libswscale2 libsystemd-daemon0 libsystemd-login0 libtasn1-6 libtcl8.5 libtcl8.6 libtelepathy-glib0 libterm-ui-perl libtevent0 libtext-levenshtein-perl libtext-soundex-perl libtiff5 libtk8.5 libtk8.6 libtsan0 libtxc-dxtn-s2tc0 libudev1 libudisks2-0 libunistring0 libunity-protocol-private0 libunity-scopes-json-def-desktop libupnp6 libusageenvironment1 libusbmuxd2 libustr-1.0-1 libvlccore7 libwayland-client0 libwayland-cursor0 libwayland-egl1-mesa libwayland-server0 libwebp5 libwebpmux1 libx264-142 libxatracker2 libxcb-dri3-0 libxcb-present0 libxcb-sync1 libxcb-xfixes0 libxfce4ui-common libxfce4util6 libxkbcommon0 libxmlrpc-lite-perl libxshmfence1 libxtables10 libyajl2 libzeitgeist-2.0-0 libzip2 lintian linux-headers-3.13.0-34 linux-headers-3.13.0-34-generic linux-image-3.13.0-34-generic linux-image-extra-3.13.0-34-generic m2vrequantiser mjpegtools-gtk mythtv-dbg ncurses-term nepomuk-core-data nepomuk-core-runtime nvidia-libopencl1-304 nvidia-opencl-icd-304 oneconf-common openssh-sftp-server p11-kit p11-kit-modules patchutils phonon-backend-gstreamer-common php5-json php5-readline python-commandnotfound python-dirspec python-dnspython python-ldb python-ntdb python-oauthlib python-oneconf python-pil python-pyinotify python-requests python-samba python-secretstorage python-six python-talloc python-tdb python-urllib3 python3 python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets python3-commandnotfound python3-crypto python3-dbus python3-defer python3-distupgrade python3-gdbm python3-gi python3-httplib2 python3-minimal python3-oauthlib python3-oneconf python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pycurl python3-software-properties python3-update-manager python3-xdg python3-xkit python3.4 python3.4-minimal qtchooser qtcore4-l10n samba-dsdb-modules samba-libs samba-vfs-modules systemd-services systemd-shim t1utils tcl8.6 tk8.6 ubuntu-drivers-common ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk udisks2 vcdimager wodim xserver-xorg-video-glamoregl xserver-xorg-video-modesetting
2014-08-17 00:22:53,562 DEBUG Upgrade: accountsservice acl acpi-support acpid adduser alsa-base alsa-utils anacron apache2-mpm-prefork apache2-utils apache2.2-bin app-install-data apparmor apport apport-gtk apport-symptoms apt apt-transport-https apt-utils apt-xapian-index aptdaemon aptdaemon-data aspell aspell-en at avahi-autoipd avahi-daemon base-files base-passwd bash bash-completion bc bind9-host binutils bsdmainutils bsdutils busybox-initramfs busybox-static bzip2 ca-certificates chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg command-not-found command-not-found-data console-setup consolekit coreutils cpio cpp cpp-4.6 cpufrequtils crda cron cryptsetup-bin dash dbus dbus-x11 dconf-gsettings-backend dconf-service debconf debconf-i18n debianutils desktop-file-utils dictionaries-common diffutils dkms dmidecode dmsetup dmz-cursor-theme dnsmasq-base dnsutils docbook-xml docbook-xsl dosfstools dpkg dvb-apps dvd+rw-tools dvdauthor e2fslibs e2fsprogs ed eject enchant exo-utils fail2ban fakeroot file findutils firefox-locale-en flashplugin-installer fontconfig fontconfig-config fonts-droid fonts-liberation ftp fuse gamin gawk gcc gcc-4.6 gcc-4.6-base gconf-service gconf-service-backend gconf2 gconf2-common gdb gedit gedit-common genisoimage geoip-database gettext-base ghostscript gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gir1.2-dee-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gmenu-3.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-soup-2.4 gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gksu glib-networking glib-networking-common glib-networking-services gnome-icon-theme gnome-keyring gnome-system-tools gnome-time-admin gnome-user-guide gnupg gpgv grep groff-base growisofs grub-common grub-pc grub-pc-bin grub2-common gsettings-desktop-schemas gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-x gtk2-engines-murrine gtk2-engines-pixbuf gtk3-engines-unico gvfs gvfs-common gvfs-daemons gvfs-libs gzip hddtemp hdhomerun-config hdhomerun-config-gui hdparm hicolor-icon-theme hostname humanity-icon-theme hunspell-en-ca icoutils ifupdown imagemagick-common indicator-application info initramfs-tools initramfs-tools-bin initscripts insserv install-info iproute iptables iputils-arping iputils-ping iputils-tracepath irqbalance isc-dhcp-client isc-dhcp-common iso-codes iw kate-data katepart kbd kde-l10n-engb kde-runtime kde-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools keyboard-configuration klibc-utils krb5-locales ksnapshot kubuntu-debug-installer language-pack-en language-pack-en-base language-pack-kde-en language-selector-common less lib32gcc1 liba52-0.7.4 libaa1 libaacs0 libaccountsservice0 libacl1 libapache2-mod-php5 libappindicator3-1 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libapt-pkg4.12 libarchive-zip-perl libasn1-8-heimdal libasound2 libasound2-plugins libaspell15 libass4 libasyncns0 libatasmart4 libatk1.0-0 libatk1.0-data libattr1 libaudio2 libav-tools libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core7 libavc1394-0 libavdevice-extra-53 libblkid1 libbluray1 libbsd0 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libcaca0 libcairo-gobject2 libcairo2 libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcap2-bin libcddb2 libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libck-connector0 libclass-inspector-perl libclass-isa-perl libclass-load-perl libclass-methodmaker-perl libcomerr2 libcommon-sense-perl libconfig-simple-perl libconvert-binhex-perl libcpufreq0 libcroco3 libcrypt-ssleay-perl libcryptsetup4 libcrystalhd3 libcups2 libcupsimage2 libcurl3 libcurl3-gnutls libdaemon0 libdata-dump-perl libdata-optlist-perl libdate-manip-perl libdatetime-format-builder-perl libdatetime-format-iso8601-perl libdatetime-format-mail-perl libdatetime-format-strptime-perl libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl libdatrie1 libdb5.1 libdbd-mysql-perl libdbi-perl libdbus-1-3 libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdbusmenu-qt2 libdc1394-22 libdca0 libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1 libdirac-encoder0 libdirectfb-1.2-9 libdlrestrictions1 libdrm-intel1 libdrm-radeon1 libdrm2 libdv4 libdvdnav4 libdvdread4 libedit2 libelf1 libemail-address-perl libemail-find-perl libemail-valid-perl libenca0 libenchant1c2a libencode-locale-perl libevent-2.0-5 libexif12 libexo-1-0 libexo-common libexo-helpers libexpat1 libfaac0 libfaad2 libfcgi-perl libffi6 libfftw3-3 libfile-desktopentry-perl libfile-listing-perl libfile-mimeinfo-perl libfile-slurp-perl libflac8 libfontconfig1 libfontenc1 libfreetype6 libfribidi0 libfs6 libftdi1 libfuse2 libgail-3-0 libgamin0 libgarcon-1-0 libgarcon-common libgcc1 libgck-1-0 libgconf-2-4 libgconf2-4 libgcr-3-1 libgcr-3-common libgcrypt11 libgdbm3 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgee2 libgeoclue0 libgeoip1 libgif4 libgirepository-1.0-1 libgksu2-0 libgl1-mesa-dri libgl1-mesa-glx libglade2-0 libglapi-mesa libglib2.0-0 libglib2.0-bin libglib2.0-data libglu1-mesa libgmp10 libgnome-keyring-common libgnome-keyring0 libgnome-menu-3-0 libgnutls26 libgomp1 libgpg-error0 libgphoto2-l10n libgpm2 libgs9 libgs9-common libgsm1 libgssapi-krb5-2 libgssapi3-heimdal libgssglue1 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtksourceview-3.0-common libgtop2-7 libgtop2-common libgudev-1.0-0 libhcrypto4-heimdal libhdhomerun1 libheimbase1-heimdal libheimntlm0-heimdal libhtml-form-perl libhtml-format-perl libhtml-fromtext-perl libhtml-parser-perl libhtml-template-perl libhtml-tree-perl libhttp-cache-transparent-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhunspell-1.3-0 libhx509-5-heimdal libice6 libidn11 libiec61883-0 libieee1284-3 libijs-0.35 libilmbase6 libimage-size-perl libindicator3-7 libio-socket-inet6-perl libio-socket-ssl-perl libiso9660-8 libiw30 libjack-jackd2-0 libjasper1 libjavascriptcoregtk-3.0-0 libjbig2dec0 libjpeg-progs libjpeg-turbo-progs libjpeg-turbo8 libjpeg8 libjs-jquery libjson-perl libjson-xs-perl libjson0 libk5crypto3 libkate1 libkatepartinterfaces4 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkeybinder0 libkeyutils1 libkfile4 libkhtml5 libkidletime4 libkio5 libkipi-data libkjsapi4 libkjsembed4 libklibc libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrb5-26-heimdal libkrb5-3 libkrb5support0 libkrosscore4 libktexteditor4 liblcms1 liblcms2-2 libldap-2.4-2 liblightdm-gobject-1-0 liblingua-preferred-perl liblircclient0 liblist-moreutils-perl liblocale-gettext-perl liblockfile-bin liblockfile1 liblog-dispatch-perl liblog-tracemessages-perl liblqr-1-0 libltdl7 liblua5.1-0 liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl liblzma5 liblzo2-2 libmad0 libmagic1 libmailtools-perl libmath-round-perl libmhash2 libmime-tools-perl libmodplug1 libmodule-runtime-perl libmount1 libmp3lame0 libmpcdec6 libmpeg2-4 libmpfr4 libmtdev1 libmtp-common libmtp-runtime libmtp9 libmysqlclient18 libmyth-python libmythtv-perl libncurses5 libncursesw5 libnepomuk4 libnepomukquery4a libnepomukutils4 libnet-dbus-perl libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl libnet-ssleay-perl libnetfilter-conntrack3 libnewt0.52 libnfnetlink0 libnfsidmap2 libnih-dbus1 libnih1 libnl-3-200 libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnspr4-0d libnss-mdns libnss3 libnss3-1d libntrack-qt4-1 libntrack0 libogg0 libopencore-amrnb0 libopencore-amrwb0 libopenexr6 libopenjpeg2 libopts25 liborc-0.4-0 libossp-uuid-perl libossp-uuid16 libp11-kit0 libpackage-deprecationmanager-perl libpackage-stash-perl libpackage-stash-xs-perl libpam-cap libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime libpam0g libpango1.0-0 libpaper-utils libpaper1 libparams-classify-perl libparams-util-perl libparams-validate-perl libparse-recdescent-perl libparted0debian1 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1 libpeas-1.0-0 libpeas-common libphonon4 libpipeline1 libpixman-1-0 libplasma3 libplist1 libplymouth2 libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-1 libpoppler-glib8 libpopt0 libportaudio2 libproc-daemon-perl libproc-pid-file-perl libproc-processtable-perl libproxy1 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpython2.7 libqca2 libqt4-dbus libqt4-declarative libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4 libquadmath0 libquicktime2 libraptor2-0 librasqal3 libraw1394-11 librdf0 libreadline6 libregexp-common-perl libresid-builder0c2a libroken18-heimdal librsvg2-2 librsvg2-common librtmp0 libsamplerate0 libsane libsane-common libsasl2-2 libsasl2-modules libschroedinger-1.0-0 libsdl-image1.2 libsdl1.2debian libselinux1 libsensors4 libsgutils2-2 libshout3 libsidplay2 libsigsegv2 libslang2 libsm6 libsmbclient libsndfile1 libsoap-lite-perl libsocket6-perl libsolid4 libsoprano4 libsoup-gnome2.4-1 libsoup2.4-1 libsox-fmt-alsa libsox-fmt-base libspeex1 libspeexdsp1 libsqlite3-0 libss2 libssh-4 libssl1.0.0 libstartup-notification0 libstdc++6 libstreamanalyzer0 libstreams0 libsub-install-perl libswscale-extra-2 libsysfs2 libtag1-vanilla libtag1c2a libtalloc2 libtar0 libtask-weaken-perl libtdb1 libterm-progressbar-perl libterm-readkey-perl libtext-bidi-perl libtext-charwidth-perl libtext-iconv-perl libthai-data libthai0 libtheora0 libthreadweaver4 libthunarx-2-0 libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libtinfo5 libtirpc1 libtk-tablematrix-perl libtry-tiny-perl libts-0.0-0 libtumbler-1-0 libtwolame0 libunicode-string-perl libunity9 libupower-glib1 liburi-perl libusb-0.1-4 libusb-1.0-0 libutempter0 libuuid1 libv4l-0 libv4lconvert0 libva-glx1 libva-x11-1 libva1 libvcdinfo0 libvdpau1 libvirtodbc0 libvisual-0.4-0 libvisual-0.4-plugins libvlc5 libvncserver0 libvo-aacenc0 libvo-amrwbenc0 libvorbis0a libvorbisenc2 libvorbisfile3 libvpx1 libvte-2.90-9 libvte-2.90-common libvte-common libvte9 libwavpack1 libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwind0-heimdal libwnck-3-0 libwnck-3-common libwnck-common libwnck22 libwrap0 libwww-mechanize-perl libwww-perl libx11-6 libx11-data libx11-xcb1 libx86-1 libxapian22 libxau6 libxaw7 libxcb-composite0 libxcb-dri2-0 libxcb-glx0 libxcb-keysyms1 libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-util0 libxcb-xv0 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxext6 libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfconf-0-2 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxklavier16 libxml-libxml-perl libxml-libxslt-perl libxml-namespacesupport-perl libxml-parser-perl libxml-regexp-perl libxml-rss-perl libxml-sax-perl libxml-simple-perl libxml-twig-perl libxml-writer-perl libxml2 libxml2-utils libxmltv-perl libxmu6 libxmuu1 libxpm4 libxrandr2 libxrender1 libxres1 libxslt1.1 libxss1 libxt6 libxtst6 libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86vm1 libyaml-syck-perl libyelp0 libzeitgeist-1.0-1 libzvbi-common libzvbi0 lightdm lightdm-gtk-greeter linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev linux-sound-base lirc locales lockfile-progs login logrotate lsb-base lsb-release lshw lsof ltrace make makedev man-db manpages manpages-dev mawk memtest86+ mime-support miscfiles mjpegtools mlocate mobile-broadband-provider-info modemmanager module-init-tools mount mountall mtools mtr-tiny multiarch-support mysql-client mysql-client-5.5 mysql-client-core-5.5 mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 mytharchive mythbrowser mythbuntu-bare-client mythbuntu-common mythbuntu-control-centre mythbuntu-default-settings mythbuntu-desktop mythbuntu-lirc-generator mythbuntu-log-grabber mythexport mythgallery mythgame mythmusic mythnetvision mythnews mythtv mythtv-backend mythtv-backend-master mythtv-common mythtv-database mythtv-frontend mythtv-theme-mythbuntu mythtv-transcode-utils mythweather mythweb nano ncurses-base ncurses-bin net-tools netbase netcat-openbsd network-manager network-manager-gnome network-manager-pptp network-manager-pptp-gnome nfs-common nfs-kernel-server nmap notify-osd notify-osd-icons ntfs-3g ntp ntpdate ntrack-module-libnl-0 nvidia-304 nvidia-common nvidia-current nvidia-settings nvidia-settings-304 odbcinst odbcinst1debian2 oneconf openssh-client openssh-server openssl os-prober oxygen-icon-theme parted passwd patch pciutils perl perl-base perl-modules perl-tk perlmagick phonon phonon-backend-gstreamer php-mythtv php5 php5-cli php5-common php5-mysql pkg-config plasma-scriptengine-javascript plymouth plymouth-label plymouth-theme-ubuntu-text pm-utils policykit-1 policykit-1-gnome popularity-contest powermgmt-base ppp pppconfig pptp-linux procps psmisc pulseaudio pulseaudio-module-x11 pulseaudio-utils pwgen python python-apport python-apt python-apt-common python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-bzrlib python-cairo python-chardet python-configobj python-crypto python-cups python-dbus python-dbus-dev python-debian python-debtagshw python-defer python-feedparser python-gamin python-gconf python-gdbm python-gi python-gi-cairo python-glade2 python-gobject python-gobject-2 python-gst0.10 python-gtk2 python-httplib2 python-imaging python-imdbpy python-keyring python-launchpadlib python-lazr.restfulclient python-lazr.uri python-libxml2 python-lxml python-minimal python-mysqldb python-oauth python-openssl python-pam python-paramiko python-pexpect python-piston-mini-client python-pkg-resources python-problem-report python-pycurl python-serial python-simplejson python-software-properties python-support python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client python-urlgrabber python-utidylib python-vte python-wadllib python-xapian python-xdg python-xkit python-zeitgeist python-zope.interface python2.7 python2.7-minimal qapt-batch qdbus radeontool readline-common resolvconf rpcbind rsync rsyslog rtkit samba samba-common samba-common-bin sane-utils screen-resolution-extra sed sensible-utils sessioninstaller setserial sgml-base sgml-data shared-desktop-ontologies shared-mime-info software-center software-center-aptdaemon-plugins software-properties-common software-properties-gtk soprano-daemon sound-theme-freedesktop sox ssh-import-id ssl-cert strace sudo system-config-samba sysv-rc sysvinit-utils tar tcl tcl8.5 tcpd tcpdump tdb-tools telnet thunar thunar-data thunar-volman time tk tk8.5 toshset traceroute transcode transcode-doc tsconf ttf-dejavu ttf-dejavu-core ttf-dejavu-extra ttf-freefont ttf-ubuntu-font-family tumbler tumbler-common twolame tzdata ubuntu-keyring ubuntu-minimal ubuntu-sso-client ubuntu-standard ucf udev udisks ufw unattended-upgrades update-inetd update-manager update-manager-core update-notifier update-notifier-common upower upstart ureadahead usb-modeswitch usb-modeswitch-data usbmuxd usbutils util-linux uuid-runtime vbetool vim-common vim-tiny virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse vnc4server wget whiptail whois wireless-regdb wireless-tools wmctrl wpasupplicant x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils x11vnc x11vnc-data xauth xbase-clients xbitmaps xdg-user-dirs xdg-utils xfce-keyboard-shortcuts xfce4-panel xfce4-session xfce4-settings xfce4-terminal xfce4-volumed xfconf xfdesktop4 xfdesktop4-data xfonts-utils xfwm4 xinit xinput xkb-data xml-core xmltv xmltv-gui xmltv-util xorg xorg-docs-core xscreensaver xscreensaver-data xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xterm xz-utils yelp yelp-xsl zeitgeist zeitgeist-core zeitgeist-datahub zenity zenity-common zlib1g
2014-08-17 00:22:53,567 DEBUG apt btrfs snapshots supported: False
2014-08-17 00:22:53,567 DEBUG cache aufs_rw_dir: /tmp/
2014-08-17 00:22:53,568 DEBUG Free space on /: 881025662976
2014-08-17 00:22:53,568 DEBUG Dir /usr mounted on /
2014-08-17 00:22:53,568 DEBUG Dir /var mounted on /
2014-08-17 00:22:53,568 DEBUG Dir /boot mounted on /
2014-08-17 00:22:53,568 DEBUG Dir /var/cache/apt/archives mounted on /
2014-08-17 00:22:53,569 DEBUG Dir /tmp mounted on /
2014-08-17 00:22:53,569 DEBUG Dir /home mounted on /
2014-08-17 00:22:53,569 DEBUG Dir /tmp mounted on /
2014-08-17 00:22:53,569 DEBUG fs_free contains: '{'/var': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>, '/tmp': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>, '/usr': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>, '/boot': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>, '/home': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>, '/': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>, '/var/cache/apt/archives': <DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>}'
2014-08-17 00:22:54,787 DEBUG linux-image-3.13.0-34-generic (new-install) added with 24118683 to boot space
2014-08-17 00:22:56,061 DEBUG dir '/var/cache/apt/archives' needs '750777418' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (881025662976.000000)
2014-08-17 00:22:56,061 DEBUG dir '/usr' needs '1018093568' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (880274885558.000000)
2014-08-17 00:22:56,061 DEBUG dir '/usr' needs '52428800' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (879256791990.000000)
2014-08-17 00:22:56,061 DEBUG dir '/boot' needs '48237366' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (879204363190.000000)
2014-08-17 00:22:56,061 DEBUG dir '/tmp' needs '5242880' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (879156125824.000000)
2014-08-17 00:22:56,062 DEBUG dir '/' needs '10485760' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (879150882944.000000)
2014-08-17 00:22:56,062 DEBUG dir '/tmp' needs '0.0' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (879140397184.000000)
2014-08-17 00:22:56,062 DEBUG dir '/usr' needs '0.0' of '<DistUpgrade.DistUpgradeCache.FreeSpace object at 0x691fcd0>' (879140397184.000000)
2014-08-17 00:23:06,008 DEBUG disabling apt cron job (0755)
2014-08-17 00:47:52,196 DEBUG plugins for condition 'StartUpgrade' are '[]'
2014-08-17 00:47:52,197 DEBUG plugins for condition 'trustyStartUpgrade' are '[]'
2014-08-17 00:47:52,197 DEBUG plugins for condition 'from_preciseStartUpgrade' are '[]'
2014-08-17 00:47:52,197 DEBUG quirks: running StartUpgrade
2014-08-17 00:47:52,215 DEBUG skipping 'README' (no '.')
2014-08-17 00:47:52,251 DEBUG killing update-notifier
2014-08-17 00:47:52,330 DEBUG killing kblueplugd kbluetooth4
2014-08-17 00:47:52,372 DEBUG killing gnome-screensaver
2014-08-17 00:47:52,424 DEBUG setup poke timer for the scrensaver
2014-08-17 00:47:52,521 DEBUG apt btrfs snapshots supported: False
2014-08-17 00:47:52,522 INFO cache.commit()
2014-08-17 00:47:52,522 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-08-17 00:55:38,762 WARNING no activity on terminal for 300 seconds (Preparing apt)
2014-08-17 17:29:48,255 WARNING no activity on terminal for 300 seconds (Installed python-samba)
2014-08-17 21:59:50,702 DEBUG got a conffile-prompt from dpkg for file: '/etc/apache2/ports.conf'
2014-08-17 22:10:58,878 ERROR got an error from dpkg for pkg: 'mythtv-database': 'subprocess installed post-installation script returned error exit status 1'
2014-08-17 22:10:58,879 DEBUG running apport_pkgfailure() mythtv-database: subprocess installed post-installation script returned error exit status 1
2014-08-17 22:10:59,307 WARNING Failed to determine apport version (No module named pyexpat)
2014-08-17 22:10:59,352 ERROR got an error from dpkg for pkg: 'mythtv-database': 'subprocess installed post-installation script returned error exit status 1'
2014-08-17 22:30:38,266 WARNING no activity on terminal for 300 seconds (Installed mjpegtools-gtk)
2014-08-17 22:30:38,298 ERROR got an error from dpkg for pkg: 'mythtv': 'dependency problems - leaving unconfigured'
2014-08-17 22:30:38,298 DEBUG running apport_pkgfailure() mythtv: dependency problems - leaving unconfigured
2014-08-17 22:30:38,298 ERROR got an error from dpkg for pkg: 'mythtv': 'dependency problems - leaving unconfigured'
2014-08-17 22:30:38,317 ERROR got an error from dpkg for pkg: 'mythtv-backend-master': 'dependency problems - leaving unconfigured'
2014-08-17 22:30:38,318 DEBUG running apport_pkgfailure() mythtv-backend-master: dependency problems - leaving unconfigured
2014-08-17 22:30:38,318 ERROR got an error from dpkg for pkg: 'mythtv-backend-master': 'dependency problems - leaving unconfigured'
2014-08-17 22:30:40,818 ERROR got an error from dpkg for pkg: 'mythexport': 'dependency problems - leaving unconfigured'
2014-08-17 22:30:40,818 DEBUG running apport_pkgfailure() mythexport: dependency problems - leaving unconfigured
2014-08-17 22:30:40,818 ERROR got an error from dpkg for pkg: 'mythexport': 'dependency problems - leaving unconfigured'
2014-08-17 22:30:40,994 DEBUG got a conffile-prompt from dpkg for file: '/etc/lirc/hardware.conf'
2014-08-17 22:35:26,460 DEBUG cache.commit() returned None
2014-08-17 22:35:26,461 DEBUG enabling apt cron job
2014-08-17 22:35:26,469 DEBUG icon theme changed, re-reading
2014-08-17 22:35:26,492 DEBUG openCache()
2014-08-17 22:35:26,501 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-08-17 22:35:28,119 DEBUG /openCache(), new cache size 70916
2014-08-17 22:35:28,121 DEBUG plugins for condition 'PostUpgrade' are '[]'
2014-08-17 22:35:28,121 DEBUG plugins for condition 'trustyPostUpgrade' are '[]'
2014-08-17 22:35:28,121 DEBUG plugins for condition 'from_precisePostUpgrade' are '[]'
2014-08-17 22:35:33,046 DEBUG Obsolete: linux-headers-3.2.0-59-generic libmng1 linux-headers-3.2.0-59 libx264-120 linux-image-3.2.0-30-generic libisccc80 libisccfg82 linux-headers-3.2.0-55 libudev0 libavutil-extra-51 libavcodec-extra-53 linux-headers-3.2.0-25-generic libsox1b linux-headers-3.2.0-30-generic libyajl1 libtiff4 libgd2-xpm libqapt1 libnepomuksync4 linux-image-3.2.0-26-generic linux-headers-3.2.0-25 linux-image-3.2.0-55-generic libattica0.3 libgphoto2-port0 gs-cjk-resource python-central libdvbpsi7 libgphoto2-2 libkipi8 libimobiledevice2 libdrm-nouveau1a linux-headers-3.2.0-38-generic linux-headers-3.2.0-26 libexiv2-11 libclucene0ldbl libgdu0 linux-headers-3.2.0-23 libmpc2 gir1.2-launchpad-integration-3.0 libxatracker1 libllvm3.0 linux-image-3.2.0-36-generic libxfce4util4 libmagickcore4 libqapt-runtime linux-headers-3.2.0-55-generic libdvdcss2 linux-headers-3.2.0-36-generic libgnome-bluetooth8 linux-headers-3.2.0-38 libisc83 libebml3 libmjpegtools-1.9 linux-image-3.2.0-38-generic cmap-adobe-japan1 libnepomukdatamanagement4 libdns81 linux-image-3.2.0-23-generic libicu48 linux-image-3.2.0-59-generic libapt-inst1.4 ffmpeg liblwres80 linux-headers-3.2.0-36 libmatroska5 libmagickwand4 liblaunchpad-integration-3.0-1 libbind9-80 libpoppler19 libdconf0 liblaunchpad-integration-common libusbmuxd1 linux-headers-3.2.0-30 linux-headers-3.2.0-26-generic libtasn1-3 launchpad-integration libavformat-extra-53 linux-image-3.2.0-25-generic linux-headers-3.2.0-23-generic
2014-08-17 22:35:33,047 DEBUG Foreign: 
2014-08-17 22:35:33,047 DEBUG identifyObsoleteKernels()
2014-08-17 22:35:36,935 DEBUG removing obsolete kernel 'linux-headers-3.2.0-23-generic'
2014-08-17 22:35:36,936 DEBUG removing obsolete kernel 'linux-headers-3.2.0-25-generic'
2014-08-17 22:35:36,936 DEBUG removing obsolete kernel 'linux-headers-3.2.0-26-generic'
2014-08-17 22:35:36,936 DEBUG removing obsolete kernel 'linux-headers-3.2.0-30-generic'
2014-08-17 22:35:36,936 DEBUG removing obsolete kernel 'linux-headers-3.2.0-36-generic'
2014-08-17 22:35:36,937 DEBUG removing obsolete kernel 'linux-headers-3.2.0-38-generic'
2014-08-17 22:35:36,937 DEBUG removing obsolete kernel 'linux-headers-3.2.0-55-generic'
2014-08-17 22:35:36,937 DEBUG skipping running kernel linux-headers-3.2.0-59-generic
2014-08-17 22:35:36,942 DEBUG removing obsolete kernel 'linux-image-3.2.0-23-generic'
2014-08-17 22:35:36,942 DEBUG removing obsolete kernel 'linux-image-3.2.0-25-generic'
2014-08-17 22:35:36,942 DEBUG removing obsolete kernel 'linux-image-3.2.0-26-generic'
2014-08-17 22:35:36,942 DEBUG removing obsolete kernel 'linux-image-3.2.0-30-generic'
2014-08-17 22:35:36,942 DEBUG removing obsolete kernel 'linux-image-3.2.0-36-generic'
2014-08-17 22:35:36,943 DEBUG removing obsolete kernel 'linux-image-3.2.0-38-generic'
2014-08-17 22:35:36,943 DEBUG removing obsolete kernel 'linux-image-3.2.0-55-generic'
2014-08-17 22:35:36,943 DEBUG skipping running kernel linux-image-3.2.0-59-generic
2014-08-17 22:35:38,870 DEBUG identifyObsoleteKernels found 'set(['linux-image-3.2.0-23-generic', 'linux-image-3.2.0-30-generic', 'linux-headers-3.2.0-36-generic', 'linux-image-3.2.0-26-generic', 'linux-image-3.2.0-55-generic', 'linux-image-3.2.0-36-generic', 'linux-image-3.2.0-38-generic', 'linux-headers-3.2.0-25-generic', 'linux-headers-3.2.0-23-generic', 'linux-headers-3.2.0-55-generic', 'linux-headers-3.2.0-26-generic', 'linux-headers-3.2.0-38-generic', 'linux-image-3.2.0-25-generic', 'linux-headers-3.2.0-30-generic'])'
2014-08-17 22:35:38,870 DEBUG forced_obsoletes: ['ksplash-engine-moodin', 'powernowd', 'laptop-mode-tools', 'linux-image-3.2.0-23-generic', 'linux-image-3.2.0-30-generic', 'linux-headers-3.2.0-36-generic', 'linux-image-3.2.0-26-generic', 'linux-image-3.2.0-55-generic', 'linux-image-3.2.0-36-generic', 'linux-image-3.2.0-38-generic', 'linux-headers-3.2.0-25-generic', 'linux-headers-3.2.0-23-generic', 'linux-headers-3.2.0-55-generic', 'linux-headers-3.2.0-26-generic', 'linux-headers-3.2.0-38-generic', 'linux-image-3.2.0-25-generic', 'linux-headers-3.2.0-30-generic']
2014-08-17 22:35:40,143 DEBUG Unused dependencies: libmusicbrainz5-0 libkcompactdisc4 k3b-i18n libqapt-runtime libyajl1 libnepomuksync4 tk8.5 libqapt1 libzeitgeist-1.0-1 libperl4-corelibs-perl libattica0.3 libao-common gstreamer0.10-plugins-good libkipi8 libexiv2-11 libclucene0ldbl gstreamer0.10-alsa libtcl8.5 language-pack-en-base libkcddb4 k3b-data language-pack-kde-en libflac++6 vcdimager kde-l10n-engb cdparanoia gstreamer0.10-x libneon27-gnutls libnepomukdatamanagement4 tcl8.5 ffmpeg libk3b6 cdrdao language-pack-en firefox-locale-en k3b libtk8.5 nvidia-settings-304 libao4
2014-08-17 22:35:40,144 DEBUG remove_candidates: 'set(['linux-headers-3.2.0-59-generic', 'libmusicbrainz5-0', 'libkcompactdisc4', 'k3b-i18n', 'libisccfg82', 'libavutil-extra-51', 'libavcodec-extra-53', 'libyajl1', 'ksplash-engine-moodin', 'libtiff4', 'linux-headers-3.2.0-38-generic', 'libzeitgeist-1.0-1', 'linux-image-3.2.0-30-generic', 'powernowd', 'linux-image-3.2.0-55-generic', 'gstreamer0.10-plugins-good', 'libmng1', 'libkipi8', 'libmjpegtools-1.9', 'linux-headers-3.2.0-25', 'libgdu0', 'libmpc2', 'gstreamer0.10-alsa', 'libtcl8.5', 'cdrdao', 'libusbmuxd1', 'libneon27-gnutls', 'libllvm3.0', 'linux-image-3.2.0-36-generic', 'k3b-data', 'libmagickcore4', 'linux-headers-3.2.0-36-generic', 'linux-image-3.2.0-26-generic', 'linux-headers-3.2.0-55', 'linux-headers-3.2.0-59', 'libgnome-bluetooth8', 'vcdimager', 'liblaunchpad-integration-common', 'libao-common', 'cdparanoia', 'linux-image-3.2.0-38-generic', 'cmap-adobe-japan1', 'libnepomukdatamanagement4', 'tcl8.5', 'libdns81', 'libicu48', 'libapt-inst1.4', 'ffmpeg', 'liblwres80', 'linux-headers-3.2.0-36', 'libqapt-runtime', 'libk3b6', 'libbind9-80', 'libpoppler19', 'libdconf0', 'libtk8.5', 'libtasn1-3', 'launchpad-integration', 'libao4', 'linux-headers-3.2.0-25-generic', 'libx264-120', 'libisccc80', 'libudev0', 'libebml3', 'language-pack-kde-en', 'libsox1b', 'linux-headers-3.2.0-30-generic', 'libgd2-xpm', 'tk8.5', 'libqapt1', 'libnepomuksync4', 'python-central', 'libperl4-corelibs-perl', 'libattica0.3', 'gs-cjk-resource', 'language-pack-en', 'libdvbpsi7', 'libgphoto2-2', 'libimobiledevice2', 'libdrm-nouveau1a', 'linux-headers-3.2.0-26', 'libexiv2-11', 'libclucene0ldbl', 'linux-headers-3.2.0-23', 'linux-headers-3.2.0-55-generic', 'libflac++6', 'language-pack-en-base', 'libxatracker1', 'libkcddb4', 'firefox-locale-en', 'libgphoto2-port0', 'kde-l10n-engb', 'linux-headers-3.2.0-23-generic', 'gstreamer0.10-x', 'nvidia-settings-304', 'gir1.2-launchpad-integration-3.0', 'linux-image-3.2.0-23-generic', 'linux-image-3.2.0-59-generic', 'laptop-mode-tools', 'libmatroska5', 'libmagickwand4', 'liblaunchpad-integration-3.0-1', 'linux-headers-3.2.0-38', 'libxfce4util4', 'libisc83', 'linux-headers-3.2.0-30', 'k3b', 'linux-headers-3.2.0-26-generic', 'libavformat-extra-53', 'linux-image-3.2.0-25-generic'])'
2014-08-17 22:35:40,144 DEBUG Start checking for obsolete pkgs
2014-08-17 22:35:40,145 DEBUG skipping running kernel pkg 'linux-headers-3.2.0-59-generic'
2014-08-17 22:35:40,146 DEBUG 'linux-headers-3.2.0-59-generic' scheduled for remove but not safe to remove, skipping
2014-08-17 22:36:03,762 DEBUG package 'gs-cjk-resource' has unwanted removals, skipping
2014-08-17 22:36:10,231 DEBUG 'gs-cjk-resource' scheduled for remove but not safe to remove, skipping
2014-08-17 22:36:10,233 DEBUG skipping 'language-pack-en' (in KeepInstalledSection)
2014-08-17 22:36:10,233 DEBUG 'language-pack-en' scheduled for remove but not safe to remove, skipping
2014-08-17 22:36:13,290 DEBUG skipping 'language-pack-en-base' (in KeepInstalledSection)
2014-08-17 22:36:13,290 DEBUG 'language-pack-en-base' scheduled for remove but not safe to remove, skipping
2014-08-17 22:36:15,719 DEBUG skipping running kernel pkg 'linux-image-3.2.0-59-generic'
2014-08-17 22:36:15,720 DEBUG 'linux-image-3.2.0-59-generic' scheduled for remove but not safe to remove, skipping
2014-08-17 22:36:18,491 DEBUG Finish checking for obsolete pkgs
2014-08-17 22:36:18,552 DEBUG The following packages are marked for removal: k3b-i18n libmjpegtools-1.9 linux-headers-3.2.0-23-generic libavformat-extra-53 libgnome-bluetooth8 libao-common linux-image-3.2.0-55-generic cdparanoia libgphoto2-port0 libk3b6 linux-headers-3.2.0-26-generic libqapt-runtime libicu48 libx264-120 libtk8.5 libnepomuksync4 libkipi8 libmagickcore4 liblaunchpad-integration-common linux-headers-3.2.0-23 linux-headers-3.2.0-25 linux-headers-3.2.0-30 linux-headers-3.2.0-26 linux-headers-3.2.0-36 vcdimager linux-headers-3.2.0-38 linux-headers-3.2.0-55 gstreamer0.10-alsa linux-headers-3.2.0-59 liblaunchpad-integration-3.0-1 libimobiledevice2 libmagickwand4 libavutil-extra-51 linux-headers-3.2.0-55-generic libdns81 libflac++6 libzeitgeist-1.0-1 python-central libapt-inst1.4 libkcddb4 libtasn1-3 libdvbpsi7 libisccc80 gstreamer0.10-plugins-good k3b-data nvidia-settings-304 k3b libattica0.3 libclucene0ldbl libqapt1 launchpad-integration liblwres80 libgdu0 linux-image-3.2.0-38-generic libkcompactdisc4 libnepomukdatamanagement4 libmatroska5 libdrm-nouveau1a linux-image-3.2.0-30-generic linux-image-3.2.0-25-generic cmap-adobe-japan1 libtcl8.5 libneon27-gnutls ffmpeg libxatracker1 libbind9-80 libao4 firefox-locale-en language-pack-kde-en kde-l10n-engb gstreamer0.10-x linux-headers-3.2.0-38-generic cdrdao libdconf0 libgd2-xpm tcl8.5 libtiff4 libperl4-corelibs-perl libusbmuxd1 linux-headers-3.2.0-59-generic libudev0 libexiv2-11 libxfce4util4 libisccfg82 linux-headers-3.2.0-30-generic linux-headers-3.2.0-25-generic tk8.5 linux-image-3.2.0-36-generic libyajl1 gir1.2-launchpad-integration-3.0 libmusicbrainz5-0 linux-image-3.2.0-23-generic libsox1b libisc83 libebml3 libpoppler19 linux-image-3.2.0-26-generic libmng1 linux-headers-3.2.0-36-generic libmpc2 libavcodec-extra-53 libllvm3.0 libgphoto2-2
2014-08-17 22:53:05,881 INFO cache.commit()
2014-08-17 22:53:08,495 ERROR got an error from dpkg for pkg: 'mythtv-database': 'subprocess installed post-installation script returned error exit status 1'
2014-08-17 22:53:08,497 DEBUG running apport_pkgfailure() mythtv-database: subprocess installed post-installation script returned error exit status 1
2014-08-17 22:53:08,504 WARNING Failed to determine apport version (No module named pyexpat)
2014-08-17 22:53:08,528 ERROR got an error from dpkg for pkg: 'mythtv-database': 'subprocess installed post-installation script returned error exit status 1'
2014-08-17 22:56:37,595 ERROR got an error from dpkg for pkg: 'mythexport': 'dependency problems - leaving unconfigured'
2014-08-17 22:56:37,595 DEBUG running apport_pkgfailure() mythexport: dependency problems - leaving unconfigured
2014-08-17 22:56:37,595 ERROR got an error from dpkg for pkg: 'mythexport': 'dependency problems - leaving unconfigured'
2014-08-17 22:56:37,606 ERROR got an error from dpkg for pkg: 'mythtv': 'dependency problems - leaving unconfigured'
2014-08-17 22:56:37,607 DEBUG running apport_pkgfailure() mythtv: dependency problems - leaving unconfigured
2014-08-17 22:56:37,607 ERROR got an error from dpkg for pkg: 'mythtv': 'dependency problems - leaving unconfigured'
2014-08-17 22:56:37,623 ERROR got an error from dpkg for pkg: 'mythtv-backend-master': 'dependency problems - leaving unconfigured'
2014-08-17 22:56:37,624 DEBUG running apport_pkgfailure() mythtv-backend-master: dependency problems - leaving unconfigured
2014-08-17 22:56:37,624 ERROR got an error from dpkg for pkg: 'mythtv-backend-master': 'dependency problems - leaving unconfigured'
2014-08-17 22:56:44,482 DEBUG plugins for condition 'PostCleanup' are '[]'
2014-08-17 22:56:44,483 DEBUG plugins for condition 'trustyPostCleanup' are '[]'
2014-08-17 22:56:44,483 DEBUG plugins for condition 'from_precisePostCleanup' are '[]'
2014-08-17 22:56:44,483 DEBUG quirks: running PostCleanup
2014-08-17 22:56:44,483 DEBUG running Quirks.PostCleanup
2014-08-17 22:56:44,483 DEBUG Running PostInstallScript: './xorg_fix_proprietary.py'
2014-08-17 22:56:44,530 ERROR got error from PostInstallScript ./xorg_fix_proprietary.py (Failed to execute child process "./xorg_fix_proprietary.py" (No such file or directory))
2014-08-17 22:56:44,534 DEBUG icon theme changed, re-reading
2014-08-17 22:56:48,049 DEBUG enabling apt cron job
```

**As a backup plan, how easy would it be to force the 14.04 upgrade process to run again and hope it completes all the steps this time?**
"sudo apt-get -f dist-upgrade"?

Eric

---

### Post by tgm4883 on 2014-08-20
Is this a combined frontend and backend? And is this the master backend? It looks like the database isn't properly installed "iF  mythtv-database". 

A "sudo apt-get -f dist-upgrade" won't do a distribution upgrade, but I'm assuming that "lsb_release -r" returns 14.04 meaning that the distribution upgrade is done and we just need to fix some packages. If that is the case then you can try a "sudo apt-get -f dist-upgrade", but make sure it's not trying to remove a bunch of packages when you do that.

---

### Post by neutron68 on 2014-08-20
> **tgm4883 said:**
> Is this a combined frontend and backend? And is this the master backend? It looks like the database isn't properly installed "iF  mythtv-database". 

A "sudo apt-get -f dist-upgrade" won't do a distribution upgrade, but I'm assuming that "lsb_release -r" returns 14.04 meaning that the distribution upgrade is done and we just need to fix some packages. If that is the case then you can try a "sudo apt-get -f dist-upgrade", but make sure it's not trying to remove a bunch of packages when you do that.

Yes, this is a combined frontend/backend.  It has been up and running since June 2012.  
It was fully functional prior to the upgrade attempt this past weekend.

Correct, "lsb_release -r" returns 14.04.  

**What do you mean by "iF mythtv-database"?  Do you mean try and re-install mythtv-database?**

From what I see from the dist-upgrade log file I posted above, most of the upgrade took place, but not all the steps were successfully completes.  
Note that there is still a myth 0.25 package that didn't get removed - as seen from the output of "dpkg -l | grep myth".

**Is there an install script that lists all the steps performed in an upgrade?  If so, can we just follow down the script and see where the steps stopped getting done?**

**You've seen the movie link showing how the Mythtv Backend Setup does not ask about updating the database?**

We've not tried running "mythtv-setup" yet.  
**Shall we try running "mythtv-setup" and see if it will ask about updating the database, before we try something else?**

Thanks.

---

### Post by tgm4883 on 2014-08-20
> **neutron68 said:**
> Yes, this is a combined frontend/backend.  It has been up and running since June 2012.  
It was fully functional prior to the upgrade attempt this past weekend.

Correct, "lsb_release -r" returns 14.04.  

**What do you mean by "iF mythtv-database"?  Do you mean try and re-install mythtv-database?**

From what I see from the dist-upgrade log file I posted above, most of the upgrade took place, but not all the steps were successfully completes.  
Note that there is still a myth 0.25 package that didn't get removed - as seen from the output of "dpkg -l | grep myth".

**Is there an install script that lists all the steps performed in an upgrade?  If so, can we just follow down the script and see where the steps stopped getting done?**

**You've seen the movie link showing how the Mythtv Backend Setup does not ask about updating the database?**

We've not tried running "mythtv-setup" yet.  
**Shall we try running "mythtv-setup" and see if it will ask about updating the database, before we try something else?**

Thanks.

Ok, so you're already on 14.04, good. Lets continue. Do "apt-get -f upgrade" and see what it tries to do. It should try to fix the package installation (picking up where it left off). It might spit out some errors, and if so please copy them here.

---

### Post by neutron68 on 2014-08-20
> **tgm4883 said:**
> Ok, so you're already on 14.04, good. Lets continue. Do "apt-get -f upgrade" and see what it tries to do. It should try to fix the package installation (picking up where it left off). It might spit out some errors, and if so please copy them here.
You missed all 4 questions in my last message.  Hint: The questions are in BOLD.  ;)

It looks like it the apt-get -f command made some progress.
```
user@Mythbuntu:~$ sudo apt-get -f upgrade
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  language-pack-en language-pack-en-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
Setting up mythexport (2.2.4-0ubuntu2) ...
 * Reloading web server apache2                                                                                              *
 * Starting MythExport Daemon: mythexport                                                                            [ OK ]
Setting up mythtv (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
Setting up mythtv-backend-master (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
```

libmyth 0.25 is still in there...
```
user@Mythbuntu:~$ dpkg -l | grep myth
rc  libmyth-0.25-0                        2:0.25.3+fixes.20130813.b5adf03-0ubuntu0mythbuntu2 amd64        Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.27-0                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          A python library to access some MythTV features
ii  libmythtv-perl                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          A PERL library to access some MythTV features
ii  mytharchive                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        create and burn DVD's from MythTV - binary file
ii  mythbrowser                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        A web browser for MythTV
ii  mythbuntu-bare-client                 2.6                                                all          Mythbuntu Bare Client
ii  mythbuntu-common                      0.74                                               all          Mythbuntu application support functions
ii  mythbuntu-control-centre              0.64.1                                             all          Mythbuntu Configuration Application
ii  mythbuntu-default-settings            1.11                                               all          default settings for Mythbuntu
ii  mythbuntu-desktop                     0.82                                               amd64        The Mythbuntu standalone system
ii  mythbuntu-lightdm-theme               1.01                                               all          Mythbuntu LightDM setup
ii  mythbuntu-lirc-generator              0.26-0ubuntu2                                      all          Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                 0.11-0ubuntu2                                      all          Mythbuntu diagnostic utility
ii  mythexport                            2.2.4-0ubuntu2                                     amd64        Export MythTV recording to portable media players
ii  mythgallery                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Image gallery/slideshow add-on module for MythTV
ii  mythgame                              2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Emulator & PC Game frontend module for MythTV
ii  mythmusic                             2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Music add-on module for MythTV
ii  mythnetvision                         2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        A Internet Video Player plugin for MythTV
ii  mythnews                              2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        An RSS feed news reader module for MythTV
ii  mythtv                                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Personal video recorder application (client and server)
ii  mythtv-backend                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (server)
ii  mythtv-backend-master                 2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                         2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (common data)
ii  mythtv-database                       2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Personal video recorder application (database)
ii  mythtv-dbg                            2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Debug symbols for mythtv packages
ii  mythtv-frontend                       2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (client)
ii  mythtv-theme-mythbuntu                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Utilities used for transcoding MythTV tasks
ii  mythweather                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Weather add-on module for MythTV
ii  mythweb                               2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Web interface add-on module for MythTV
ii  php-mythtv                            2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          PHP Bindings for MythTV
```

---

### Post by tgm4883 on 2014-08-20
> **neutron68 said:**
> You missed all 4 questions in my last message.  Hint: The questions are in BOLD.  ;)


Ok, let me go though and answer them then.

> **neutron68 said:**
> Yes, this is a combined frontend/backend.  It has been up and running since June 2012.  
It was fully functional prior to the upgrade attempt this past weekend.

Correct, "lsb_release -r" returns 14.04.  

**What do you mean by "iF mythtv-database"?  Do you mean try and re-install mythtv-database?**


No, I mean that it's installed and half configured. No need to try reinstalling it yet since it's not configured yet, which is why I didn't say to try reinstalling it.

> **neutron68 said:**
> 
From what I see from the dist-upgrade log file I posted above, most of the upgrade took place, but not all the steps were successfully completes.  
Note that there is still a myth 0.25 package that didn't get removed - as seen from the output of "dpkg -l | grep myth".

**Is there an install script that lists all the steps performed in an upgrade?  If so, can we just follow down the script and see where the steps stopped getting done?**


There are a few scripts that get run during an upgrade. It is possible to set them to be more verbose, but lets not bother doing that yet, lets just try fixing the unconfigured packages.

> **neutron68 said:**
> 
**You've seen the movie link showing how the Mythtv Backend Setup does not ask about updating the database?**


Honestly I didn't bother watching the video. Based on the other info I saw in this thread I don't doubt it didn't show up yet. 

> **neutron68 said:**
> 
We've not tried running "mythtv-setup" yet.  
**Shall we try running "mythtv-setup" and see if it will ask about updating the database, before we try something else?**

Thanks.

You can, but I don't think it would have fixed anything (well, it wouldn't have fixed anything before, now that you've run apt-get -f install it might just work)

> **neutron68 said:**
> 
It looks like it the apt-get -f command made some progress.
```
user@Mythbuntu:~$ sudo apt-get -f upgrade
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  language-pack-en language-pack-en-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mythtv-database (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
Setting up mythexport (2.2.4-0ubuntu2) ...
 * Reloading web server apache2                                                                                              *
 * Starting MythExport Daemon: mythexport                                                                            [ OK ]
Setting up mythtv (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
Setting up mythtv-backend-master (2:0.27.0+fixes.20140324.8ee257c-0ubuntu3) ...
```



Looks like the backend and database finished installing and setting up. Now would be a good time to run mythtv-setup (just go into it, upgrade the schema if it asks and exit) and restart mythfrontend

> **neutron68 said:**
> 
libmyth 0.25 is still in there...
```
user@Mythbuntu:~$ dpkg -l | grep myth
rc  libmyth-0.25-0                        2:0.25.3+fixes.20130813.b5adf03-0ubuntu0mythbuntu2 amd64        Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.27-0                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          A python library to access some MythTV features
ii  libmythtv-perl                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          A PERL library to access some MythTV features
ii  mytharchive                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        create and burn DVD's from MythTV - binary file
ii  mythbrowser                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        A web browser for MythTV
ii  mythbuntu-bare-client                 2.6                                                all          Mythbuntu Bare Client
ii  mythbuntu-common                      0.74                                               all          Mythbuntu application support functions
ii  mythbuntu-control-centre              0.64.1                                             all          Mythbuntu Configuration Application
ii  mythbuntu-default-settings            1.11                                               all          default settings for Mythbuntu
ii  mythbuntu-desktop                     0.82                                               amd64        The Mythbuntu standalone system
ii  mythbuntu-lightdm-theme               1.01                                               all          Mythbuntu LightDM setup
ii  mythbuntu-lirc-generator              0.26-0ubuntu2                                      all          Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                 0.11-0ubuntu2                                      all          Mythbuntu diagnostic utility
ii  mythexport                            2.2.4-0ubuntu2                                     amd64        Export MythTV recording to portable media players
ii  mythgallery                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Image gallery/slideshow add-on module for MythTV
ii  mythgame                              2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Emulator & PC Game frontend module for MythTV
ii  mythmusic                             2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Music add-on module for MythTV
ii  mythnetvision                         2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        A Internet Video Player plugin for MythTV
ii  mythnews                              2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        An RSS feed news reader module for MythTV
ii  mythtv                                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Personal video recorder application (client and server)
ii  mythtv-backend                        2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (server)
ii  mythtv-backend-master                 2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                         2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (common data)
ii  mythtv-database                       2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Personal video recorder application (database)
ii  mythtv-dbg                            2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Debug symbols for mythtv packages
ii  mythtv-frontend                       2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Personal video recorder application (client)
ii  mythtv-theme-mythbuntu                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Utilities used for transcoding MythTV tasks
ii  mythweather                           2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           amd64        Weather add-on module for MythTV
ii  mythweb                               2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          Web interface add-on module for MythTV
ii  php-mythtv                            2:0.27.0+fixes.20140324.8ee257c-0ubuntu3           all          PHP Bindings for MythTV
```

No it isn't. Just because it is in this list doesn't mean it is installed nor configured. As you can see from the line, it says "rc" the r stands for Desired=Remove, and the c stands for Status=Conf-files. So in other words, the package is removed, but there are conf files left over (which is half true, as the conf files are used for 0.27 as well). You're missing the header info in the results from that command (because we used grep to pull out just the info we wanted). See below for the missing header info.

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                        Version                                             Architecture Description
```

---

### Post by neutron68 on 2014-08-21
Thank you.  Thank you.  :)
Your explanations are helpful and really flesh out how the processes work!  I'm sure they will help others get the whole picture, too.

OK.  I will stop the backend (sudo service mythtv-backend stop) and have my friend run mythtv-setup from a command line.  
**Does mythtv-setup need to be run with sudo before it?**

Thanks again for your information and help!

---

### Post by tgm4883 on 2014-08-21
> **neutron68 said:**
> Thank you.  Thank you.  :)
Your explanations are helpful and really flesh out how the processes work!  I'm sure they will help others get the whole picture, too.

OK.  I will stop the backend (sudo service mythtv-backend stop) and have my friend run mythtv-setup from a command line.  
**Does mythtv-setup need to be run with sudo before it?**

Thanks again for your information and help!

No, it will prompt for password if needed.

---

### Post by neutron68 on 2014-09-14
OK.  I've made a house-call to my friend's Mythbuntu machine.

Right after boot, the mythfrontend starts automatically, and gives the message:
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-08-17230138_zps10120fbc.jpg[/IMG]

If you click OK, the frontend crashes, dumps you out on the desktop, and reports "Restarting Frontend:  The front-end crashed unexpectedly(exit code 133) and is restarting.  Please wait.."
At that point, the frontend respawns and we are back to the message shown above.

The only way to get to a command line is to use a different virtual desktop (example CTRL-F2 or CTRL-F3, etc.)

After I get to a command line, I can do a "sudo pkill mythfrontend.re" the frontend is stopped and it then respawns on my new virtual desktop.

Now, I have to switch to a different virtual desktop (CTRL-F1, for example), and try and kill mythfrontend.re again...(ENDLESS LOOP).

If I get to a command line and type "mythtv-setup" I see a terminal window for 1 second and then a brown screen comes up, stays brown for about 3 minutes.
During those 3 minutes, if I switch to a different virtual desktop again and look at the "top" command, I see that mythtv-setup.re is running and mythfrontend.re is running too.

After the 3 minutes is up, if go back to the virtual desktop where mythtv-setup was started, I see that I have been dumped back to a desktop with a decision box that says "Start backend:  Would you like to start the mythtv backend?"
If I click YES, another decision box pops up and says "Fill Database:  Would you like to run mythfilldatabase?"
If I click YES it tries to run  mythfilldatabase and gives the repeating message "Waiting for database schema upgrade lock" over and over.

If I click NO to the Start backend question box:
another decision box pops up and says "Fill Database:  Would you like to run mythfilldatabase?"
If I click NO, the box closes and nothing appears to happen

I'm not sure how to proceed.  It appears like every path is a dead end that leads to an error message.

Eric

---

### Post by tgm4883 on 2014-09-15
If you want to stop the frontend, you need to kill both mythfrontend and mythfrontend.real, in that order. Otherwise the scripts will think that it died and restart it.

It says you can do the update by starting mythbackend, so I would attempt just a restart of it (sudo service mythtv-backend restart). If you still get the schema update message after that then post the /var/log/mythtv/mythbackend.log file

---

### Post by neutron68 on 2014-09-15
OK.  I stoped the frontend and the backend via SSH and my friend sat at the keyboard and started the backend with a command line "sudo service mythtv-backend start".
Then, he got a decision box that asked if he would like to start the mythtv backend?
He clicked Yes.
Next, he saw a screen that told him the database needed to be updated.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115427_zpsb485ca0c.jpg[/IMG]
He was given the choice of Upgrade or Exit.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115438-1_zps95f8326e.jpg[/IMG]
He chose Upgrade, and got this message.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115451_zpsa62c08f1.jpg[/IMG]
He then got a decision box asking if he wanted to run mythfilldatabase?
He clicked Yes.
For a minute or 2, it gave him the repeating message "Waiting for database schema upgrade lock".
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115712_zps5db97224.jpg[/IMG]
I think some progress has been made.
Just yesterday, he got messages saying he was 18 versions behind.  Now, it says he is only 2 versions behind.

I've copied the portion of the mythbackend.log file here.
It shows that a database update is attempted and fails.
Note how it complains "Console is non-interactive, can't prompt user..."

```
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I Logger logging.cpp:315 (run) Added logging to the console
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Mythbuntu
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to EN_US
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale EN_US
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1315
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext dbutil.cpp:604 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext dbutil.cpp:625 (DoBackup) Database Backup complete.
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext dbutil.cpp:656 (DoBackup) Backed up database to file: '/var/lib/mythtv/db_backups/mythconverg-1315-20140915165516.sql.gz'
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext schemawizard.cpp:271 (PromptForUpgrade) Console is non-interactive, can't prompt user...
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext schemawizard.cpp:296 (PromptForUpgrade) Upgrading.
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext dbcheck.cpp:402 (performActualUpdate) Upgrading to MythTV schema version 1316
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext dbcheck.cpp:417 (performActualUpdate) DB Error (Performing database upgrade): #012Query was: ALTER TABLE program ADD INDEX title_subtitle_start (title, subtitle, starttime); #012Error was: Driver error was [2/1061]:#012QMYSQL: Unable to execute query#012Database error was:#012Duplicate key name 'title_subtitle_start'#012 #012new version: 1316
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext dbcheck.cpp:502 (UpgradeTVDatabaseSchema) Database schema upgrade failed.
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext main_helpers.cpp:555 (run_backend) Couldn't upgrade database to new schema
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I Logger logging.cpp:315 (run) Added logging to the console
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Mythbuntu
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to EN_US
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale EN_US
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1315
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext dbutil.cpp:604 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext dbutil.cpp:625 (DoBackup) Database Backup complete.
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext dbutil.cpp:656 (DoBackup) Backed up database to file: '/var/lib/mythtv/db_backups/mythconverg-1315-20140915165535.sql.gz'
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext schemawizard.cpp:271 (PromptForUpgrade) Console is non-interactive, can't prompt user...
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext schemawizard.cpp:296 (PromptForUpgrade) Upgrading.
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext dbcheck.cpp:402 (performActualUpdate) Upgrading to MythTV schema version 1316
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext dbcheck.cpp:417 (performActualUpdate) DB Error (Performing database upgrade): #012Query was: ALTER TABLE program ADD INDEX title_subtitle_start (title, subtitle, starttime); #012Error was: Driver error was [2/1061]:#012QMYSQL: Unable to execute query#012Database error was:#012Duplicate key name 'title_subtitle_start'#012 #012new version: 1316
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext dbcheck.cpp:502 (UpgradeTVDatabaseSchema) Database schema upgrade failed.
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext main_helpers.cpp:555 (run_backend) Couldn't upgrade database to new schema
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I Logger logging.cpp:315 (run) Added logging to the console
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.

```

---

### Post by tgm4883 on 2014-09-15
> **neutron68 said:**
> OK.  I stoped the frontend and the backend via SSH and my friend sat at the keyboard and started the backend with a command line "sudo service mythtv-backend start".
Then, he got a decision box that asked if he would like to start the mythtv backend?
He clicked Yes.
Next, he saw a screen that told him the database needed to be updated.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115427_zpsb485ca0c.jpg[/IMG]
He was given the choice of Upgrade or Exit.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115438-1_zps95f8326e.jpg[/IMG]
He chose Upgrade, and got this message.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115451_zpsa62c08f1.jpg[/IMG]
He then got a decision box asking if he wanted to run mythfilldatabase?
He clicked Yes.
For a minute or 2, it gave him the repeating message "Waiting for database schema upgrade lock".
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/2014-09-15115712_zps5db97224.jpg[/IMG]
I think some progress has been made.
Just yesterday, he got messages saying he was 18 versions behind.  Now, it says he is only 2 versions behind.

I've copied the portion of the mythbackend.log file here.
It shows that a database update is attempted and fails.
Note how it complains "Console is non-interactive, can't prompt user..."

```
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I Logger logging.cpp:315 (run) Added logging to the console
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Mythbuntu
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to EN_US
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale EN_US
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1315
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext dbutil.cpp:604 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Sep 15 11:55:16 Mythbuntu mythbackend: mythbackend[3986]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext dbutil.cpp:625 (DoBackup) Database Backup complete.
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext dbutil.cpp:656 (DoBackup) Backed up database to file: '/var/lib/mythtv/db_backups/mythconverg-1315-20140915165516.sql.gz'
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: I CoreContext schemawizard.cpp:271 (PromptForUpgrade) Console is non-interactive, can't prompt user...
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext schemawizard.cpp:296 (PromptForUpgrade) Upgrading.
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: C CoreContext dbcheck.cpp:402 (performActualUpdate) Upgrading to MythTV schema version 1316
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext dbcheck.cpp:417 (performActualUpdate) DB Error (Performing database upgrade): #012Query was: ALTER TABLE program ADD INDEX title_subtitle_start (title, subtitle, starttime); #012Error was: Driver error was [2/1061]:#012QMYSQL: Unable to execute query#012Database error was:#012Duplicate key name 'title_subtitle_start'#012 #012new version: 1316
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext dbcheck.cpp:502 (UpgradeTVDatabaseSchema) Database schema upgrade failed.
Sep 15 11:55:34 Mythbuntu mythbackend: mythbackend[3986]: E CoreContext main_helpers.cpp:555 (run_backend) Couldn't upgrade database to new schema
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I Logger logging.cpp:315 (run) Added logging to the console
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of Mythbuntu
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default locale to EN_US
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale EN_US
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version (DBSchemaVer): 1315
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext dbutil.cpp:604 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemManager mythsystemunix.cpp:275 (run) Starting process manager
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal handler
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
Sep 15 11:55:35 Mythbuntu mythbackend: mythbackend[4024]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext dbutil.cpp:625 (DoBackup) Database Backup complete.
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext dbutil.cpp:656 (DoBackup) Backed up database to file: '/var/lib/mythtv/db_backups/mythconverg-1315-20140915165535.sql.gz'
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: I CoreContext schemawizard.cpp:271 (PromptForUpgrade) Console is non-interactive, can't prompt user...
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext schemawizard.cpp:296 (PromptForUpgrade) Upgrading.
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: C CoreContext dbcheck.cpp:402 (performActualUpdate) Upgrading to MythTV schema version 1316
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext dbcheck.cpp:417 (performActualUpdate) DB Error (Performing database upgrade): #012Query was: ALTER TABLE program ADD INDEX title_subtitle_start (title, subtitle, starttime); #012Error was: Driver error was [2/1061]:#012QMYSQL: Unable to execute query#012Database error was:#012Duplicate key name 'title_subtitle_start'#012 #012new version: 1316
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext dbcheck.cpp:502 (UpgradeTVDatabaseSchema) Database schema upgrade failed.
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4024]: E CoreContext main_helpers.cpp:555 (run_backend) Couldn't upgrade database to new schema
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: C thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging) mythbackend version: fixes/0.27 [v0.27-193-g8ee257c] www.mythtv.org
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: C thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt version: compile: 4.8.6, runtime: 4.8.6
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:  general
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I Logger logging.cpp:315 (run) Added logging to the console
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix = /usr
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding: en_US.UTF-8
Sep 15 11:55:54 Mythbuntu mythbackend: mythbackend[4052]: N CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty LocalHostName.

```

That is pretty odd, but lets give it an interactive console.

So go ahead and stop the backend again "sudo service mythtv-backend stop"

Then lets switch to the mythtv user by doing "sudo su mythtv"

Then lets run "mythbackend" and see if it tries to upgrade the DB.

---

### Post by neutron68 on 2014-09-18
When you said > Then lets run "mythbackend" and see if it tries to upgrade the DB.
Did you mean to type "mythbackend" at the command prompt, or "sudo service mythtv-backend start"?

If they are both valid ways to start the backend, what is the difference between the two?

Thanks.

---

### Post by neutron68 on 2014-09-18
Running the "mythbackend" command made the difference (whereas "sudo service mythtv-backend start" didn't get as far).  
With the "mythbackend" command we got an interactive session in the command window and could answer yes or no when asked.
The results were the same no matter if we logged in as the mythtv user or the standard user.

[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/IMG_3637_zpsd80a5874.jpg[/IMG]

Note that the backend tried to update the database schema but it bombed out with errors.
Do the errors tell us what direction to go now?
To me, it looks like the database needs fixing before we can go any further.
[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/IMG_3643_zpse91c06c2.jpg[/IMG]

---

### Post by tgm4883 on 2014-09-19
Odd. I've asked in #mythtv-users, so hopefully someone else can give me something to help you with. A quick google search indicates that it's because of the failed DB upgrades first and that we should restore from backup. So I would restore the DB backup from right before the first time it tried to upgrade the DB and then run mythbackend as the mythtv user from the command line again. Do not run it as your user, and don't start it as the service.

---

### Post by neutron68 on 2014-09-25
From what I see in the /var/lib/mythtv/db_backups directory, Mythbuntu only keeps the most recent database backups and deletes older ones.

The oldest database backup in that directory is 9-6-2014.  My friend started his failed upgrade on August 16, so the 9-6-2014 database backup already reflects the database changes from the failed upgrade process.  I'm thinking that 9-6-2014 backup isn't much help?

What options are left?  

Can the database be fixed or manually edited so the schema upgrade can complete?

---

### Post by tgm4883 on 2014-09-25
> **neutron68 said:**
> From what I see in the /var/lib/mythtv/db_backups directory, Mythbuntu only keeps the most recent database backups and deletes older ones.

The oldest database backup in that directory is 9-6-2014.  My friend started his failed upgrade on August 16, so the 9-6-2014 database backup already reflects the database changes from the failed upgrade process.  I'm thinking that 9-6-2014 backup isn't much help?

What options are left?  

Can the database be fixed or manually edited so the schema upgrade can complete?

That is mythtv keeping/managing those backups, not Mythbuntu. I'm not sure of a way to manually edit the DB to what we want it to be, upstream suggested the database restore but I'm unsure whether that DB backup is useful. I would suggest getting on IRC and asking for help in the #mythtv-users channel, as it might be a bit more real time and helpful than a once a day update.

---

### Post by neutron68 on 2014-10-01
OK.  Any idea what times of day people will be in the IRC chat room?

Thanks,
Eric

---

### Post by tgm4883 on 2014-10-02
I think most of them are US based. Currently there are 144 people in there

---

### Post by neutron68 on 2014-10-05
I logged into #mythtv-users via IRC today and saw lots of people logged in, including tgm4883.  
I watched the message screen for about an hour.  NO ONE was sending messages!
I posted a question...NO responses at all.

Why would all these people be logged into IRC if they didn't want to communicate??

---

### Post by neutron68 on 2015-06-27
We gave up on this machine, and reloaded 12.04 to a blank hard drive.

In reviewing the events of the failed upgrade, I discovered that my friend had not pulled down all the updates for Mythtv 0.25, or Mythbuntu 12.04 before hitting the UPGRADE button.
I have since learned that best practice is to apply all the current updates for your current version, BEFORE attempting to upgrade to the next version.
 
Early on in that install of 12.04, I discovered that the graphical Update Manager was broken, and to get it fixed, you had to use command line apt-get commands "sudo apt-get update" and "sudo apt-get upgrade" to have updates actually finish successfully.  After updating, the graphical Update Manager was fixed and could be used from then on.

When he tried to upgrade from 12.04 to 14.04, I think my friend may have still had the broken Update Manager version in the machine.  
Perhaps that contributed to the failed upgrade?

---

