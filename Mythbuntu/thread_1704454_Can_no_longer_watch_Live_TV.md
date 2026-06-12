---
title: "Can no longer watch Live TV"
date: 2011-03-10
forum: Mythbuntu
---

### Post by jim.hitch on 2011-03-10
Have just installed the latest 0.24-fixes and can no longer watch live tv, though the program guide etc. is working. This could be coincidental to the updates, I'm not sure.

If I run mythfrontend from the terminal and then head straight to watch tv I get this:

```
2011-03-10 22:47:47.925 mythfrontend version: fixes/0.24 [v0.24-209-g13be9c2] www.mythtv.org
2011-03-10 22:47:47.926 Using runtime prefix = /usr
2011-03-10 22:47:47.926 Using configuration directory = /home/jim/.mythtv
2011-03-10 22:47:47.927 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-03-10 22:47:48.777 Empty LocalHostName.
2011-03-10 22:47:48.777 Using localhost value of master-backend
2011-03-10 22:47:48.781 New DB connection, total: 1
2011-03-10 22:47:48.783 Connected to database 'mythconverg' at host: localhost
2011-03-10 22:47:48.799 Closing DB connection named 'DBManager0'
2011-03-10 22:47:48.800 Connected to database 'mythconverg' at host: localhost
2011-03-10 22:47:48.801 Current locale EN_GB
2011-03-10 22:47:48.802 Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2011-03-10 22:47:49.010 ScreenSaverX11Private: XScreenSaver support enabled
2011-03-10 22:47:49.010 DPMS is disabled.
2011-03-10 22:47:49.026 Desktop video mode: 1024x768 60.004 Hz
2011-03-10 22:47:49.343 Enabled verbose msgs:  important general
2011-03-10 22:47:49.345 Loading en_us translation for module mythfrontend
2011-03-10 22:47:49.351 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-03-10 22:47:49.351 JoystickMenuThread: Joystick disabled - Failed to read /home/jim/.mythtv/joystickmenurc
2011-03-10 22:47:49.387 Using Frameless Window
2011-03-10 22:47:49.388 Using Full Screen Window
2011-03-10 22:47:49.466 Using the Qt painter
2011-03-10 22:47:49.605 MythFontProperties, Warning: Attempting to define 'small'
			with face 'DejaVu Sans', but it already exists with face 'Arial'
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
			Name: 'small'	Type: 'fontdef'
2011-03-10 22:47:49.614 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1013
			Name: 'medium'	Type: 'fontdef'
2011-03-10 22:47:49.622 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1019
			Name: 'large'	Type: 'fontdef'
2011-03-10 22:47:49.629 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1025
			Name: 'clock'	Type: 'fontdef'
2011-03-10 22:47:49.646 New DB connection, total: 2
2011-03-10 22:47:49.646 Current MythTV Schema Version (DBSchemaVer): 1264
2011-03-10 22:47:49.647 Connected to database 'mythconverg' at host: localhost
2011-03-10 22:47:49.767 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-03-10 22:47:49.767 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-03-10 22:47:49.768 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-03-10 22:47:49.768 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-03-10 22:47:50.073 Pulse: PulseAudio suspend OK
2011-03-10 22:47:50.171 Pulse: PulseAudio resume OK
2011-03-10 22:47:50.248 Registering Internal as a media playback plugin.
2011-03-10 22:47:50.248 Error preparing query: DELETE FROM inuseprograms WHERE hostname = :HOSTNAME and recusage = 'player' ;
2011-03-10 22:47:50.248 Driver error was [2/144]:
QMYSQL3: Unable to prepare statement
Database error was:
Table './mythconverg/inuseprograms' is marked as crashed and last (automatic?) repair failed

2011-03-10 22:47:50.249 DB Error (CleanupMyOldInUsePrograms):
Query was:
DELETE FROM inuseprograms WHERE hostname = :HOSTNAME and recusage = 'player' ;
Bindings were:
:HOSTNAME=master-backend
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':HOSTNAME and recusage = 'player'' at line 1

2011-03-10 22:47:50.269 Loading en_us translation for module mytharchive
2011-03-10 22:47:50.273 Registering WebBrowser as a media playback plugin.
2011-03-10 22:47:50.273 Loading en_us translation for module mythbrowser
2011-03-10 22:47:50.295 MediaMonitorUnix::AddDevice() - empty device path.
2011-03-10 22:47:50.295 MediaMonitorUnix::AddDevice() - empty device path.
2011-03-10 22:47:50.295 MediaMonitorUnix::AddDevice() - empty device path.
2011-03-10 22:47:50.296 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-03-10 22:47:50.296 Loading en_us translation for module mythgallery
2011-03-10 22:47:50.307 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-03-10 22:47:50.336 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-03-10 22:47:50.341 Loading en_us translation for module mythmusic
2011-03-10 22:47:50.344 Loading en_us translation for module mythnetvision
2011-03-10 22:47:50.347 Loading en_us translation for module mythnews
2011-03-10 22:47:50.353 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-03-10 22:47:50.367 Loading en_us translation for module mythvideo
2011-03-10 22:47:50.371 Loading en_us translation for module mythweather
2011-03-10 22:47:50.624 Found mainmenu.xml for theme 'MythCenter'
2011-03-10 22:47:50.678 MythCoreContext: Connecting to backend server: 192.168.0.215:6543 (try 1 of 1)
2011-03-10 22:47:50.679 Using protocol version 63
2011-03-10 22:47:52.267 TV: Attempting to change from None to WatchingLiveTV
2011-03-10 22:47:52.267 MythCoreContext: Connecting to backend server: 192.168.0.215:6543 (try 1 of 1)
2011-03-10 22:47:52.267 Using protocol version 63
2011-03-10 22:47:52.352 Spawning LiveTV Recorder -- begin
2011-03-10 22:47:52.704 Spawning LiveTV Recorder -- end
2011-03-10 22:47:52.705 Error preparing query: SELECT r.title,            r.subtitle,     r.description,            r.category,         r.chanid,       c.channum,                c.callsign,         c.name,         c.outputfilters,          r.recgroup,         r.playgroup,    r.storagegroup,           r.basename,         r.hostname,     r.recpriority,            r.seriesid,         r.programid,    r.filesize,               r.progstart,        r.progend,      r.stars,                  r.starttime,        r.endtime,      p.airdate+0,              r.originalairdate,  r.lastmodified, r.recordid,               c.commmethod,       r.commflagged,  r.previouslyshown,        r.transcoder,       r.transcoded,   r.deletepending,          r.preserve,         r.cutlist,      r.autoexpire,             r.editing,          r.bookmark,     r.watched,                p.audioprop+0,      p.videoprop+0,  p.subtitletypes+0,        r.findid,           rec.dupin,      rec.dupmethod      FROM recorded AS r LEFT JOIN channel AS c ON (r.chanid    = c.chanid) LEFT JOIN recordedprogram AS p ON (r.chanid    = p.chanid AND     r.progstart = p.starttime) LEFT JOIN record AS rec ON (r.recordid = rec.recordid) WHERE r.chanid    = :CHANID AND       r.starttime = :RECSTARTTS
2011-03-10 22:47:52.705 Driver error was [2/144]:
QMYSQL3: Unable to prepare statement
Database error was:
Table './mythconverg/recordedprogram' is marked as crashed and last (automatic?) repair failed

2011-03-10 22:47:52.706 DB Error (LoadProgramFromRecorded):
Query was:
SELECT r.title,            r.subtitle,     r.description,            r.category,         r.chanid,       c.channum,                c.callsign,         c.name,         c.outputfilters,          r.recgroup,         r.playgroup,    r.storagegroup,           r.basename,         r.hostname,     r.recpriority,            r.seriesid,         r.programid,    r.filesize,               r.progstart,        r.progend,      r.stars,                  r.starttime,        r.endtime,      p.airdate+0,              r.originalairdate,  r.lastmodified, r.recordid,               c.commmethod,       r.commflagged,  r.previouslyshown,        r.transcoder,       r.transcoded,   r.deletepending,          r.preserve,         r.cutlist,      r.autoexpire,             r.editing,          r.bookmark,     r.watched,                p.audioprop+0,      p.videoprop+0,  p.subtitletypes+0,        r.findid,           rec.dupin,      rec.dupmethod      FROM recorded AS r LEFT JOIN channel AS c ON (r.chanid    = c.chanid) LEFT JOIN recordedprogram AS p ON (r.chanid    = p.chanid AND     r.progstart = p.starttime) LEFT JOIN record AS rec ON (r.recordid = rec.recordid) WHERE r.chanid    = :CHANID AND       r.starttime = :RECSTARTTS
Bindings were:
:CHANID=2080, :RECSTARTTS=2011-03-10T22:47:52
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID AND       r.starttime = :RECSTARTTS' at line 1

2011-03-10 22:47:52.706 EntryToProgram(2080@Thu Mar 10 22:47:52 2011) failed to get pginfo
2011-03-10 22:47:52.706 TV Error: HandleStateChange(): LiveTV not successfully started
2011-03-10 22:47:52.706 We have a RingBuffer
2011-03-10 22:47:52.706 TV Error: LiveTV not successfully started


```

Is this a bug, or something that's happened to my database and no one elses? And help on how to sort this out very much appreciated - I'm still in the very early stages of mythtv and gf remains very sceptical.

---

### Post by tgm4883 on 2011-03-10
> **jim.hitch said:**
> Have just installed the latest 0.24-fixes and can no longer watch live tv, though the program guide etc. is working. This could be coincidental to the updates, I'm not sure.

If I run mythfrontend from the terminal and then head straight to watch tv I get this:

```
2011-03-10 22:47:47.925 mythfrontend version: fixes/0.24 [v0.24-209-g13be9c2] www.mythtv.org
2011-03-10 22:47:47.926 Using runtime prefix = /usr
2011-03-10 22:47:47.926 Using configuration directory = /home/jim/.mythtv
2011-03-10 22:47:47.927 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-03-10 22:47:48.777 Empty LocalHostName.
2011-03-10 22:47:48.777 Using localhost value of master-backend
2011-03-10 22:47:48.781 New DB connection, total: 1
2011-03-10 22:47:48.783 Connected to database 'mythconverg' at host: localhost
2011-03-10 22:47:48.799 Closing DB connection named 'DBManager0'
2011-03-10 22:47:48.800 Connected to database 'mythconverg' at host: localhost
2011-03-10 22:47:48.801 Current locale EN_GB
2011-03-10 22:47:48.802 Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2011-03-10 22:47:49.010 ScreenSaverX11Private: XScreenSaver support enabled
2011-03-10 22:47:49.010 DPMS is disabled.
2011-03-10 22:47:49.026 Desktop video mode: 1024x768 60.004 Hz
2011-03-10 22:47:49.343 Enabled verbose msgs:  important general
2011-03-10 22:47:49.345 Loading en_us translation for module mythfrontend
2011-03-10 22:47:49.351 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-03-10 22:47:49.351 JoystickMenuThread: Joystick disabled - Failed to read /home/jim/.mythtv/joystickmenurc
2011-03-10 22:47:49.387 Using Frameless Window
2011-03-10 22:47:49.388 Using Full Screen Window
2011-03-10 22:47:49.466 Using the Qt painter
2011-03-10 22:47:49.605 MythFontProperties, Warning: Attempting to define 'small'
			with face 'DejaVu Sans', but it already exists with face 'Arial'
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
			Name: 'small'	Type: 'fontdef'
2011-03-10 22:47:49.614 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1013
			Name: 'medium'	Type: 'fontdef'
2011-03-10 22:47:49.622 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1019
			Name: 'large'	Type: 'fontdef'
2011-03-10 22:47:49.629 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1025
			Name: 'clock'	Type: 'fontdef'
2011-03-10 22:47:49.646 New DB connection, total: 2
2011-03-10 22:47:49.646 Current MythTV Schema Version (DBSchemaVer): 1264
2011-03-10 22:47:49.647 Connected to database 'mythconverg' at host: localhost
2011-03-10 22:47:49.767 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-03-10 22:47:49.767 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-03-10 22:47:49.768 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-03-10 22:47:49.768 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-03-10 22:47:50.073 Pulse: PulseAudio suspend OK
2011-03-10 22:47:50.171 Pulse: PulseAudio resume OK
2011-03-10 22:47:50.248 Registering Internal as a media playback plugin.
2011-03-10 22:47:50.248 Error preparing query: DELETE FROM inuseprograms WHERE hostname = :HOSTNAME and recusage = 'player' ;
2011-03-10 22:47:50.248 Driver error was [2/144]:
QMYSQL3: Unable to prepare statement
Database error was:
Table './mythconverg/inuseprograms' is marked as crashed and last (automatic?) repair failed

2011-03-10 22:47:50.249 DB Error (CleanupMyOldInUsePrograms):
Query was:
DELETE FROM inuseprograms WHERE hostname = :HOSTNAME and recusage = 'player' ;
Bindings were:
:HOSTNAME=master-backend
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':HOSTNAME and recusage = 'player'' at line 1

2011-03-10 22:47:50.269 Loading en_us translation for module mytharchive
2011-03-10 22:47:50.273 Registering WebBrowser as a media playback plugin.
2011-03-10 22:47:50.273 Loading en_us translation for module mythbrowser
2011-03-10 22:47:50.295 MediaMonitorUnix::AddDevice() - empty device path.
2011-03-10 22:47:50.295 MediaMonitorUnix::AddDevice() - empty device path.
2011-03-10 22:47:50.295 MediaMonitorUnix::AddDevice() - empty device path.
2011-03-10 22:47:50.296 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-03-10 22:47:50.296 Loading en_us translation for module mythgallery
2011-03-10 22:47:50.307 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-03-10 22:47:50.336 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-03-10 22:47:50.341 Loading en_us translation for module mythmusic
2011-03-10 22:47:50.344 Loading en_us translation for module mythnetvision
2011-03-10 22:47:50.347 Loading en_us translation for module mythnews
2011-03-10 22:47:50.353 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-03-10 22:47:50.367 Loading en_us translation for module mythvideo
2011-03-10 22:47:50.371 Loading en_us translation for module mythweather
2011-03-10 22:47:50.624 Found mainmenu.xml for theme 'MythCenter'
2011-03-10 22:47:50.678 MythCoreContext: Connecting to backend server: 192.168.0.215:6543 (try 1 of 1)
2011-03-10 22:47:50.679 Using protocol version 63
2011-03-10 22:47:52.267 TV: Attempting to change from None to WatchingLiveTV
2011-03-10 22:47:52.267 MythCoreContext: Connecting to backend server: 192.168.0.215:6543 (try 1 of 1)
2011-03-10 22:47:52.267 Using protocol version 63
2011-03-10 22:47:52.352 Spawning LiveTV Recorder -- begin
2011-03-10 22:47:52.704 Spawning LiveTV Recorder -- end
2011-03-10 22:47:52.705 Error preparing query: SELECT r.title,            r.subtitle,     r.description,            r.category,         r.chanid,       c.channum,                c.callsign,         c.name,         c.outputfilters,          r.recgroup,         r.playgroup,    r.storagegroup,           r.basename,         r.hostname,     r.recpriority,            r.seriesid,         r.programid,    r.filesize,               r.progstart,        r.progend,      r.stars,                  r.starttime,        r.endtime,      p.airdate+0,              r.originalairdate,  r.lastmodified, r.recordid,               c.commmethod,       r.commflagged,  r.previouslyshown,        r.transcoder,       r.transcoded,   r.deletepending,          r.preserve,         r.cutlist,      r.autoexpire,             r.editing,          r.bookmark,     r.watched,                p.audioprop+0,      p.videoprop+0,  p.subtitletypes+0,        r.findid,           rec.dupin,      rec.dupmethod      FROM recorded AS r LEFT JOIN channel AS c ON (r.chanid    = c.chanid) LEFT JOIN recordedprogram AS p ON (r.chanid    = p.chanid AND     r.progstart = p.starttime) LEFT JOIN record AS rec ON (r.recordid = rec.recordid) WHERE r.chanid    = :CHANID AND       r.starttime = :RECSTARTTS
2011-03-10 22:47:52.705 Driver error was [2/144]:
QMYSQL3: Unable to prepare statement
Database error was:
Table './mythconverg/recordedprogram' is marked as crashed and last (automatic?) repair failed

2011-03-10 22:47:52.706 DB Error (LoadProgramFromRecorded):
Query was:
SELECT r.title,            r.subtitle,     r.description,            r.category,         r.chanid,       c.channum,                c.callsign,         c.name,         c.outputfilters,          r.recgroup,         r.playgroup,    r.storagegroup,           r.basename,         r.hostname,     r.recpriority,            r.seriesid,         r.programid,    r.filesize,               r.progstart,        r.progend,      r.stars,                  r.starttime,        r.endtime,      p.airdate+0,              r.originalairdate,  r.lastmodified, r.recordid,               c.commmethod,       r.commflagged,  r.previouslyshown,        r.transcoder,       r.transcoded,   r.deletepending,          r.preserve,         r.cutlist,      r.autoexpire,             r.editing,          r.bookmark,     r.watched,                p.audioprop+0,      p.videoprop+0,  p.subtitletypes+0,        r.findid,           rec.dupin,      rec.dupmethod      FROM recorded AS r LEFT JOIN channel AS c ON (r.chanid    = c.chanid) LEFT JOIN recordedprogram AS p ON (r.chanid    = p.chanid AND     r.progstart = p.starttime) LEFT JOIN record AS rec ON (r.recordid = rec.recordid) WHERE r.chanid    = :CHANID AND       r.starttime = :RECSTARTTS
Bindings were:
:CHANID=2080, :RECSTARTTS=2011-03-10T22:47:52
Driver error was [2/1064]:
QMYSQL: Unable to execute query
Database error was:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ':CHANID AND       r.starttime = :RECSTARTTS' at line 1

2011-03-10 22:47:52.706 EntryToProgram(2080@Thu Mar 10 22:47:52 2011) failed to get pginfo
2011-03-10 22:47:52.706 TV Error: HandleStateChange(): LiveTV not successfully started
2011-03-10 22:47:52.706 We have a RingBuffer
2011-03-10 22:47:52.706 TV Error: LiveTV not successfully started


```

Is this a bug, or something that's happened to my database and no one elses? And help on how to sort this out very much appreciated - I'm still in the very early stages of mythtv and gf remains very sceptical.

Other than the recordedprogram table being marked as crashed, we will need to see backend logs from when you tried to watch live tv.

Do recordings work?

Do scheduled recordings record?

---

### Post by jim.hitch on 2011-03-14
Hi

Thanks for getting back to me and sorry I didn't reply to you sooner.

This is a new mythtv set up, so there are no recordings from before I noticed this issue.

I have since scheduled recordings, but they have  not been done, so it's not recording.

Re postings a log, is it best to get backend logs using log grabber?

---

### Post by tgm4883 on 2011-03-15
> **jim.hitch said:**
> Hi

Thanks for getting back to me and sorry I didn't reply to you sooner.

This is a new mythtv set up, so there are no recordings from before I noticed this issue.

I have since scheduled recordings, but they have  not been done, so it's not recording.

Re postings a log, is it best to get backend logs using log grabber?

yea log grabber works for that

---

### Post by jim.hitch on 2011-03-22
I couldn't get the log grabber to bring up anything, which was weird in itself.

I also had an issue with mythmusic, so I decided in the end to do a restore of the db to a previous state.

TV appears to be working now.

Thanks again for your help.

Jim

---

