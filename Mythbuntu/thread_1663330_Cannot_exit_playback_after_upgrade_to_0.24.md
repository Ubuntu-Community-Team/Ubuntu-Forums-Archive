---
title: "Cannot exit playback after upgrade to 0.24"
date: 2011-01-09
forum: Mythbuntu
---

### Post by Sctmon on 2011-01-09
I have just tried upgraging my Backend/Frontend and remote frontends to 0.24 from 0.23.1 but when I play a recording or something from the video library and then press escape to exit playback the frontend crashed (or seems to).

I upgraded the whole system, backend/frontend and 2 remote frontends at the same time and the same is happeing on all machines.
The log file is pasted below.. sorry but I could not get the file to attach - invalid file?

Starting mythfrontend.real..
2011-01-09 18:02:16.030 mythfrontend version: fixes/0.24 [v0.24-101-gc6c50df] [www.mythtv.org]("http://www.mythtv.org")
2011-01-09 18:02:16.031 Using runtime prefix = /usr
2011-01-09 18:02:16.031 Using configuration directory = /home/scott/.mythtv
2011-01-09 18:02:16.032 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-01-09 18:02:16.616 Empty LocalHostName.
2011-01-09 18:02:16.617 Using localhost value of MythtvMain
2011-01-09 18:02:16.617 Testing network connectivity to '192.168.0.6'
2011-01-09 18:02:16.726 New DB connection, total: 1
2011-01-09 18:02:16.730 Connected to database 'mythconverg' at host: 192.168.0.6
2011-01-09 18:02:16.736 Closing DB connection named 'DBManager0'
2011-01-09 18:02:16.737 Connected to database 'mythconverg' at host: 192.168.0.6
2011-01-09 18:02:16.739 Current locale EN_GB
2011-01-09 18:02:16.739 Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2011-01-09 18:02:16.920 ScreenSaverX11Private: Gnome screen saver support enabled
2011-01-09 18:02:16.921 DPMS is disabled.
2011-01-09 18:02:16.941 Desktop video mode: 1280x1024 75.025 Hz
2011-01-09 18:02:16.959 Enabled verbose msgs:  important general
2011-01-09 18:02:16.981 Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
2011-01-09 18:02:16.984 New DB connection, total: 2
2011-01-09 18:02:16.984 Loading en_us translation for module mythfrontend
2011-01-09 18:02:16.985 Connected to database 'mythconverg' at host: 192.168.0.6
2011-01-09 18:02:16.997 LIRC: Successfully initialized '/dev/lircd' using '/home/scott/.mythtv/lircrc' config
2011-01-09 18:02:16.998 JoystickMenuThread: Joystick disabled - Failed to read /home/scott/.mythtv/joystickmenurc
2011-01-09 18:02:17.029 Using Frameless Window
2011-01-09 18:02:17.029 Using Full Screen Window
2011-01-09 18:02:17.245 Using the Qt painter
2011-01-09 18:02:17.421 New DB connection, total: 3
2011-01-09 18:02:17.423 Connected to database 'mythconverg' at host: 192.168.0.6
2011-01-09 18:02:17.427 Current MythTV Schema Version (DBSchemaVer): 1264
2011-01-09 18:02:17.664 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-01-09 18:02:17.664 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-01-09 18:02:17.666 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-01-09 18:02:17.666 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-01-09 18:02:17.908 Pulse: PulseAudio suspend OK
2011-01-09 18:02:18.103 Pulse: PulseAudio resume OK
2011-01-09 18:02:18.219 Registering Internal as a media playback plugin.
2011-01-09 18:02:18.258 Loading en_us translation for module mytharchive
2011-01-09 18:02:18.264 Registering WebBrowser as a media playback plugin.
2011-01-09 18:02:18.264 Loading en_us translation for module mythbrowser
2011-01-09 18:02:18.291 MediaMonitorUnix::AddDevice() - empty device path.
2011-01-09 18:02:18.291 MediaMonitorUnix::AddDevice() - empty device path.
2011-01-09 18:02:18.292 MediaMonitorUnix::AddDevice() - empty device path.
2011-01-09 18:02:18.292 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-01-09 18:02:18.293 Loading en_us translation for module mythgallery
2011-01-09 18:02:18.310 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-01-09 18:02:18.345 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-01-09 18:02:18.351 Loading en_us translation for module mythmusic
2011-01-09 18:02:18.356 Loading en_us translation for module mythnetvision
2011-01-09 18:02:18.363 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-01-09 18:02:18.380 Loading en_us translation for module mythvideo
2011-01-09 18:02:18.386 Loading en_us translation for module mythweather
2011-01-09 18:02:18.388 NetworkControl: Listening for remote connections on port 6546
2011-01-09 18:02:18.555 Found mainmenu.xml for theme 'Mythbuntu'
2011-01-09 18:02:18.682 MythCoreContext: Connecting to backend server: 192.168.0.6:6543 (try 1 of 1)
2011-01-09 18:02:18.683 Using protocol version 63
2011-01-09 18:02:38.483 TV: Attempting to change from None to WatchingPreRecorded
2011-01-09 18:02:38.624 Pulse: PulseAudio suspend OK
2011-01-09 18:02:38.752 AFD: Opened codec 0x2ec1c20, id(MPEG2VIDEO) type(Video)
2011-01-09 18:02:38.752 AFD: codec MP2 has 2 channels
2011-01-09 18:02:38.752 AFD: Opened codec 0x2e9ae00, id(MP2) type(Audio)
2011-01-09 18:02:38.752 AFD: codec MP3 has 0 channels
2011-01-09 18:02:38.752 AFD: Opened codec 0x2e9b260, id(MP3) type(Audio)
2011-01-09 18:02:38.752 AFD: Opened codec 0x23c60d0, id(DVB_SUBTITLE) type(Subtitle)
2011-01-09 18:02:38.924 Pulse: PulseAudio resume OK
2011-01-09 18:02:39.025 Pulse: PulseAudio suspend OK
2011-01-09 18:02:39.048 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-01-09 18:02:39.051 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-01-09 18:02:39.064 AudioPlayer: Enabling Audio
2011-01-09 18:02:39.330 VDPAU: Created 2 output surfaces.
2011-01-09 18:02:39.330 VDPAU: Version 1
2011-01-09 18:02:39.330 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 19:52:55 PDT 2010
2011-01-09 18:02:39.330 VDPAU: Created VDPAU render device 1280x1024
2011-01-09 18:02:39.362 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-01-09 18:02:39.432 Player(0): Video timing method: USleep with busy wait
2011-01-09 18:02:39.433 TV: Changing from None to WatchingPreRecorded
2011-01-09 18:02:39.444 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-01-09 18:02:44.712 TV: Attempting to change from WatchingPreRecorded to None
2011-01-09 18:02:44.725 VDPAU Painter: Clearing VDPAU painter cache.
2011-01-09 18:02:44.725 MythPainter: 2 images not yet de-allocated.



The other front end log files are much the same as this. I have disabled VDPAU and changed to CPU++ but the only difference is the last log entry  is

TV: Attempting to change from WatchingPreRecorded to None

and the front end still seems to crash.

I have restored the system backups I maded before the uprage to 0.24 so back to 0.23 now and working again. Any auggestions as to what the problem may be?

---

### Post by BicyclerBoy on 2011-01-09
Did you rescan the audio devices with the nice new audio config tool ?
This is a common symptom of audio device error.

It's a good idea to read the release notes of packages before installing.

---

### Post by Sctmon on 2011-01-09
I did not but will...How do I do that? I have restored my 0.23 backups and have limited time to do upgrades between my wife recording stuff and wanting to watch things again. It will probably be tomorrow sometime before I can have another attempt.

Audio seemed to be working on one of my frontends but it crashed when I tried to exit playback. The audio was not working on the backend but it wasnt working before the upgrade, part of the reason I wanted to do it was to see if it fixed it.

---

### Post by BicyclerBoy on 2011-01-09
frontend 
Utilities/playback/audio

Allow multi-channel speaker testing & all sorts of stuff..

(I'm using mythtv0.24+fixes JYA not mythbuntu)


Remember to first run mythtv-setup (from terminal) on all backend machines after upgrades/updates.

---

### Post by wjohnsaunders on 2011-01-10
I had the same problem. I have usually had "ALSA:default" as my audio device. However I had to scan the audio and use "ALSA:pulse" to get everything working properly. I then set my mixer setting to "software" and volume also works now.

I think the issue is probably a contention between mythtv trying to directly access the audio, via ALSA, and PulseAudio doing the same thing.

This problem doesn't occur on Mythbuntu which doesn't use PulseAudio, but does on Ubuntu which does.

---

### Post by Sctmon on 2011-01-11
I just tried to upgrade to 0.24 again after reading the release notes throughly:D but this time the database will not upgrade. Any thoughts on the attached log?
I think the key part is

DB Error (Performing database upgrade): 
Query was: CREATE TABLE internetcontent ( name VARCHAR(255) NOT NULL,  thumbnail VARCHAR(255),  type SMALLINT(3) NOT NULL,  author VARCHAR(128) NOT NULL,  description TEXT NOT NULL,  commandline TEXT NOT NULL,  version DOUBLE NOT NULL,  updated TIMESTAMP NOT NULL,  search BOOL NOT NULL,  tree BOOL NOT NULL,  podcast BOOL NOT NULL,  download BOOL NOT NULL,  host  VARCHAR(128)); 
Error was: Driver error was [2/1050]:
QMYSQL: Unable to execute query
Database error was:
Table 'internetcontent' already exists

---

### Post by BicyclerBoy on 2011-01-11
You have a database backup made just before the upgrade right ?
You have both the backup & restore scripts ?

(There are older auto backups to be found)

Only if both above are true.
The latest restore script can drop the database tables. (deletes everything) & then regenerates the database tables.

mythconverg_restore.pl --drop_database --create_database --filename mythconverg-somename.sql.gz

Always run mythtv-setup (from terminal) after upgrade.

If you have changed the mix of myth-plugins you can get some schema upgrade stoppages.

---

### Post by Sctmon on 2011-01-11
I did make a database backup using the backup script and a full system backup to a network drive just before the upgrade but I assumed that because I restored the full system image afterwards that the database would have been back the way it was.

I just dropped the database and restored the backup and will try the upgrade again (the computer is in use again now so won't get another shot until the morning)

---

### Post by BicyclerBoy on 2011-01-11
I think the database error relates to one of the internet plugins. 

I have read that there has been/ is going to be changes to the triggering/initiator of updates to the schema parts.

AFAIK It is not just one schema but many, all at different versions.

You could try to remove all plugins & then install all plugins.
Rerun the mythtv-setup a couple of times before & after all steps.

With an update from 0.22-0.23 (?) I had a schema update error with mythvideo that persisted for months until I re-installed one the new plugins.

---

### Post by Sctmon on 2011-01-12
Thanks for all the help. Restoring the database worked and I have now successfully updated to 0.24. I like the theme chooser but a little disappointed that I have list the ability to select an independent OSD theme. I liked retro for that.

---

### Post by thatguruguy on 2011-01-12
> **Sctmon said:**
> Thanks for all the help. Restoring the database worked and I have now successfully updated to 0.24. I like the theme chooser but a little disappointed that I have list the ability to select an independent OSD theme. I liked retro for that.

That's a common complaint.  

You may want to mark this thread as "solved."

---

