---
title: "Mythfrontend 0.28 Does not start after 0.27-&gt;0.28"
date: 2016-04-28
forum: Mythbuntu
---

### Post by clueo8 on 2016-04-28
I upgraded both my backend and 2 frontends (all different machines) from 0.27 to 0.28.  For the backend, I just added the 0.28 ppa and did a dist-upgrade which succeeded, its running on ubuntu-server 14.04.  For the 2 frontends, I installed the latest mythbuntu 16.04 fresh from an ISO.

Each frontend is experiencing the same issue, when I open mythfrontend, nothing appears to happen.  The mythfrontend.log file says that its taking a backup of the DB, but once that is complete, the process just ends and it will do the exact same thing the next time I try to open mythfrontend.

Here is the mythfrontend.log from one of the machines (hostname is orange):
```
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 1 handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User defined signal 2 handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythfrontend version: fixes/0.28 [v0.28-2-g15cf421] www.mythtv.org
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/clue/.mythtv
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I Logger logging.cpp:313 (run) Added logging to the console
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of orange
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythcontext.cpp:694 (TestDBconnection) Testing network connectivity to '192.168.1.250'
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I SystemManager mythsystemunix.cpp:276 (run) Starting process manager
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I SystemIOHandlerR mythsystemunix.cpp:92 (run) Starting IO manager (read)
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I SystemSignalManager mythsystemunix.cpp:509 (run) Starting process signal handler
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I SystemIOHandlerW mythsystemunix.cpp:92 (run) Starting IO manager (write)
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.freedesktop.ScreenSaver was not provided by any .service files
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.freedesktop.PowerManagement.Inhibit was not provided by any .service files
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.mate.SessionManager was not provided by any .service files
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: W CoreContext screensaver-dbus.cpp:57 (ScreenSaverDBusPrivate) ScreenSaverDBus: Could not connect to dbus: The name org.gnome.SessionManager was not provided by any .service files
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Apr 28 22:30:28 orange mythfrontend.real: mythfrontend[5371]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1280x720 60.000 Hz
Apr 28 22:30:29 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:407 (listen) Listening on TCP 127.0.0.1:6547
Apr 28 22:30:29 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:407 (listen) Listening on TCP 192.168.1.103:6547
Apr 28 22:30:29 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:407 (listen) Listening on TCP [::1]:6547
Apr 28 22:30:29 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:407 (listen) Listening on TCP [fe80::ae52:81c6:4a2c:1f8d%enp0s10]:6547
Apr 28 22:30:30 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Apr 28 22:30:30 orange mythfrontend.real: mythfrontend[5371]: I CoreContext lirc.cpp:320 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/clue/.lircrc' config
Apr 28 22:30:30 orange mythfrontend.real: mythfrontend[5371]: I CoreContext jsmenu.cpp:153 (ReadConfig) No joystick configuration found, not enabling joystick control
Apr 28 22:30:30 orange mythfrontend.real: mythfrontend[5371]: E CoreContext cecadapter.cpp:134 (Open) CECAdapter: Failed to find any CEC devices.
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext cecadapter.cpp:195 (Close) CECAdapter: Closing down CEC.
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 127.0.0.1:6948
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.1.103:6948
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [::1]:6948
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP [fe80::ae52:81c6:4a2c:1f8d%enp0s10]:6948
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext serverpool.cpp:508 (bind) Binding to UDP 192.168.1.255:6948
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythmainwindow.cpp:1041 (Init) Using Frameless Window
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythmainwindow.cpp:1079 (Init) UI Screen Resolution: 1180 x 663
Apr 28 22:30:31 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythmainwindow.cpp:1185 (Init) Using the Qt painter
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I SendMessage mythcorecontext.cpp:436 (ConnectCommandSocket) MythCoreContext::ConnectCommandSocket(): Connecting to backend server: 192.168.1.250:6543 (try 1 of 1)
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I SendMessage mythcorecontext.cpp:1578 (CheckProtoVersion) MythCoreContext::CheckProtoVersion(): Using protocol version 88 XmasGift
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythuiwebbrowser.cpp:1085 (LoadUserStyleSheet) MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythuiwebbrowser.cpp:992 (Init) MythUIWebBrowser: enabling plugins
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: E CoreContext AirPlay/mythraopdevice.cpp:30 (Create) RAOP Device: Aborting startup - no key found.
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I CoreContext AirPlay/mythairplayserver.cpp:387 (Create) AirPlay: Created airplay objects.
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown serverpool.cpp:407 (listen) Listening on TCP 127.0.0.1:5100
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown serverpool.cpp:407 (listen) Listening on TCP 192.168.1.103:5100
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown serverpool.cpp:407 (listen) Listening on TCP [::1]:5100
Apr 28 22:30:32 orange mythfrontend.real: mythfrontend[5371]: I thread_unknown serverpool.cpp:407 (listen) Listening on TCP [fe80::ae52:81c6:4a2c:1f8d%enp0s10]:5100
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: N CoreContext mythmainwindow.cpp:2087 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: A CoreContext mediamonitor-unix.cpp:210 (CheckMountable) MMUnix:CheckMountable: DBus interface error: The name org.freedesktop.UDisks was not provided by any .service files
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: W CoreContext mediamonitor-unix.cpp:217 (CheckMountable) MMUnix:UDisks2 service found. Media Monitor does not support this yet!
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythgallery
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: I AirplayServer bonjourregister.cpp:118 (BonjourCallback) Bonjour: Service registration complete: name 'MythTV on orange' type '_airplay._tcp.' domain: 'local.'
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: I CoreContext schemawizard.cpp:120 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1020
Apr 28 22:30:33 orange mythfrontend.real: mythfrontend[5371]: E CoreContext dbutil.cpp:604 (DoBackup) Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
Apr 28 22:32:15 orange mythfrontend.real: mythfrontend[5371]: C CoreContext dbutil.cpp:625 (DoBackup) Database Backup complete.
Apr 28 22:32:15 orange mythfrontend.real: mythfrontend[5371]: C CoreContext dbutil.cpp:656 (DoBackup) Backed up database to file: '/mnt/cLue-NAS/mythtv/db_backups/mythconverg-1344-20160429023033.sql.gz'
```

The mythbackend.log says that my host joined, but drops after the DB backup is complete...

```
Apr 28 22:30:32 Ubuntu-Server mythbackend: mythbackend[8858]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Frontend
Apr 28 22:30:32 Ubuntu-Server mythbackend: mythbackend[8858]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: orange(1e29e60) as a client (events: 0)
Apr 28 22:30:32 Ubuntu-Server mythbackend: mythbackend[8858]: I ProcessRequest backendcontext.cpp:56 (SetFrontendConnected) BackendContext: Frontend 'orange' connected.
Apr 28 22:30:32 Ubuntu-Server mythbackend: mythbackend[8858]: I ProcessRequest mainserver.cpp:1698 (HandleAnnounce) MainServer: MainServer::ANN Monitor
Apr 28 22:30:32 Ubuntu-Server mythbackend: mythbackend[8858]: I ProcessRequest mainserver.cpp:1703 (HandleAnnounce) MainServer: adding: orange(1e9a5c0) as a client (events: 1)
...
Apr 28 22:32:15 Ubuntu-Server mythbackend: mythbackend[8858]: I MythSocketThread(95) mainserver.cpp:7629 (connectionClosed) Monitor sock(1e9a5c0) 'orange' disconnected
Apr 28 22:32:15 Ubuntu-Server mythbackend: mythbackend[8858]: I MythSocketThread(73) backendcontext.cpp:102 (SetFrontendDisconnected) BackendContext: Frontend 'orange' disconnected.
Apr 28 22:32:15 Ubuntu-Server mythbackend: mythbackend[8858]: I MythSocketThread(73) mainserver.cpp:7629 (connectionClosed) Playback sock(1e29e60) 'orange' disconnected

```

---

### Post by blm-ubunet on 2016-04-28
After all major mythtv updates:
Shutdown all frontends & stop all slave BEs & the MBE.

run mythtv-setup as user "mythtv"..

Let it do the dB updates/backups.
Restart the MBE.

---

### Post by clueo8 on 2016-04-29
I did stop all FE/BE and ran mythtv-setup.  I run my BE as the primary user created during Ubuntu install, not mythtv user... Don't think that's the issue tho.  Is mythtv-setup supposed to say it's updating the database?  It didn't appear to when I ran it... It prompted me to stop the backend which I did but after that and running mythfilldatabase, it didn't say anything about updating the db.

Looking at my mythbackend.log, it appears to have upgraded the DB, but why would my frontends constantly want to backup the DB and not run:

```
Apr 28 21:41:22 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1318
Apr 28 21:41:22 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1319
Apr 28 21:41:26 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1320
Apr 28 21:41:29 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1321
Apr 28 21:41:29 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1322
Apr 28 21:41:29 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1323
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1324
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1325
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1326
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1327
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1328
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1329
Apr 28 21:41:32 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1330
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:2846 (doUpgradeTVDatabaseSchema) Upgrading to MythTV schema version 1332
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1333
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1334
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1335
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1336
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1337
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1338
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1339
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1341
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1342
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:3224 (doUpgradeTVDatabaseSchema) Upgrading to MythTV schema version 1343
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: C CoreContext dbcheck.cpp:437 (performActualUpdate) Upgrading to MythTV schema version 1344
Apr 28 21:41:33 Ubuntu-Server mythbackend: mythbackend[8858]: I CoreContext dbcheck.cpp:523 (UpgradeTVDatabaseSchema) Database schema upgrade complete.

```

---

### Post by blm-ubunet on 2016-04-29
On the mailing list you said you upgraded the FE before the MBE.. And the FE was run .. Did it tryto do an upgrade of some part of the dB ??
It could have modified mythmusic tables.. Someone else in mailing list appears to have the same issues. See MikeD reply.

mythtv-setup always does upgrades here, except for those plugin schemas (I think).
Some of the schema upgrades have taken some time to complete.

The normal mythtv install (from packages) sets up BE to run as service launched by init/upstart/systemd as user "mythtv".
AFAIK
14.04-LTS still uses upstart.
sudo initctl start mythtv-backend

If you start the BE (directly) from terminal in user session it will run as the wrong user; have to set user to "mythtv".
sudo -u mythtv mythbackend

Potential config.xml files for the BE are in /home/mythtv/.mythtv/ or /etc/mythtv/ .
If you start BE as user session it will look in ~/.mythtv/ .

If it's the GUI not able to display a dialogue..
Could try start mythtv-setup or FEs with override to force painter to qt (failsafe).
"-O ThemePainter=qt"

---

### Post by clueo8 on 2016-04-30
> Did it tryto do an upgrade of some part of the dB ??
I've restored the server back to a backup (clonezilla) so many times, I lost any logging from previous attempts.  Would there be something to look for in the Music tables that would be for 0.28?

> If you start the BE (directly) from terminal in user session it will run as the wrong user; have to set user to "mythtv".

I normally start my backend from 14.04 with sudo service mythbackend start and it does run as the mythtv user.  I will double check my config.xml files to make sure they look ok and aren't getting messed up with the upgrade.

I setup a test BE using a VM with a fresh install of 0.28 without my DB or anything.  I was able to connect one of my frontends to that without issue... But in this case, its was a fresh DB, so its definitely narrowed down to BE and/or DB migration which is causing me grief.

I'm wondering if the FE config that's in my DB from 0.27 is causing the display issues with the FEs connecting when they are now 0.28... I want to try changing a hostname of a FE so that it sets up the FE as new and see if that has anything to do with it...

> If it's the GUI not able to display a dialogue..
Could try start mythtv-setup or FEs with override to force painter to qt (failsafe).
"-O ThemePainter=qt"
The -O is a neat trick; I will have to try that.  Where are the key/value override pairs defined?  I don't see them listed in the --help/-h.

---

### Post by blm-ubunet on 2016-04-30
Finding the overrides is hard.. basically grep the source code almost..
The painter & mpegts parser overrides are handy for debugging.

Have seen an override to allow later version FE to run without doing any dB upgrade.

I always use mythtv-setup to do upgrades because it is interactive & no other dB stuff is going on.
And there is logging into terminal that launched mythtv-setup.

People (at least one) are having problems with music schema update.
In the past there have been dB upgrade problems with plugins that were installed once (dB tables) & then removed (no upgrades).

There was a post on the mailing list (MikeD) that listed the SQL to purge the music tables.
Could try to purge music tables & then run mythtv-setup..

or you could run 0.27 & install mythmusic plugin (is it actually a separate package?)

Yes, a new FE host name gives you a clean slate.

Could try starting FE from terminal with logging:
mythfrontend(.real) -v all --loglevel debug

---

### Post by clueo8 on 2016-05-02
I made some progress over the weekend and finally got 0.28 working.  The thing which solved it for me was to remove mythmusic (sudo apt-get purge mythmusic) and then the frontend was able to start.  I also removed mythgallery as I do not use that either.  Unless my DB got messed up with the music tables from a prior upgrade attempt, I'm wondering if mythbuntu 16.04 (which includes mythmusic ootb) would cause other users this issue.  If a user was simply upgrading to 0.28 with dist-upgrade and they never had mythmusic installed, this issue was most likely non-existent... But that still may not be true if my DB was messed up around the music tables... Thanks all for the help.

---

