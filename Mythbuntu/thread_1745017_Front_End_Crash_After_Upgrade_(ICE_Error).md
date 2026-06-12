---
title: "Front End Crash After Upgrade (ICE Error?)"
date: 2011-04-30
forum: Mythbuntu
---

### Post by dsbw on 2011-04-30
OK, so I've upgraded my BE/FE combined machine to 11.04 and now it crashes when the front end starts.

Specifically, I get the backdrop with no menu options. (I'm running a retro theme, so it's just a blank gray screen.) After about 90 seconds, crash to desktop.

Looking at my front-end log, I see only one error, and I'm not sure that it's the problem:

ICE default IO error handler doing an exit(), pid = 3197, errno = 32

But it's all I see. Complete front-end log attached. Back-end seems to be fine: I can get to the web-site and view programs from there.

Thoughts?



```
2011-04-30 13:30:41.690 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] www.mythtv.org
2011-04-30 13:30:41.690 Using runtime prefix = /usr
2011-04-30 13:30:41.691 Using configuration directory = /home/william/.mythtv
2011-04-30 13:30:41.691 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-04-30 13:30:42.570 Empty LocalHostName.
2011-04-30 13:30:42.570 Using localhost value of castle
2011-04-30 13:30:42.582 New DB connection, total: 1
2011-04-30 13:30:42.589 Connected to database 'mythconverg' at host: localhost
2011-04-30 13:30:42.601 Closing DB connection named 'DBManager0'
2011-04-30 13:30:42.602 Connected to database 'mythconverg' at host: localhost
2011-04-30 13:30:42.606 Current locale EN_US
2011-04-30 13:30:42.606 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-04-30 13:30:42.828 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-30 13:30:42.828 ScreenSaverX11Private: Gnome screen saver support enabled
2011-04-30 13:30:42.830 DPMS is disabled.
2011-04-30 13:30:42.863 Desktop video mode: 1280x720 60.000 Hz
2011-04-30 13:30:42.900 Enabled verbose msgs:  important general
2011-04-30 13:30:42.905 Loading en_us translation for module mythfrontend
2011-04-30 13:30:42.929 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2011-04-30 13:30:42.929 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2011-04-30 13:30:42.975 Using Frameless Window
2011-04-30 13:30:42.983 Using the Qt painter
2011-04-30 13:30:43.322 Current MythTV Schema Version (DBSchemaVer): 1264
2011-04-30 13:30:44.952 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-04-30 13:30:44.952 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-04-30 13:30:44.953 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-04-30 13:30:44.953 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-04-30 13:30:45.360 Registering Internal as a media playback plugin.
2011-04-30 13:30:45.400 Loading en_us translation for module mytharchive
2011-04-30 13:30:45.409 Registering WebBrowser as a media playback plugin.
2011-04-30 13:30:45.409 Loading en_us translation for module mythbrowser
2011-04-30 13:30:45.458 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-30 13:30:45.458 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-30 13:30:45.459 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-30 13:30:45.460 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-30 13:30:45.460 Loading en_us translation for module mythgallery
2011-04-30 13:30:45.474 Loading en_us translation for module mythgame
2011-04-30 13:30:45.508 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-30 13:30:45.575 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-30 13:30:45.584 Loading en_us translation for module mythmusic
2011-04-30 13:30:45.592 Loading en_us translation for module mythnews
2011-04-30 13:30:45.605 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2011-04-30 13:30:45.605 MythVideo database schema is old. Waiting to see if DB is being upgraded.
2011-04-30 13:30:46.605 New DB connection, total: 2
2011-04-30 13:30:46.607 Connected to database 'mythconverg' at host: localhost
2011-04-30 13:30:46.615 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2011-04-30 13:30:47.618 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2011-04-30 13:30:48.622 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2011-04-30 13:30:48.622 Timed out waiting.
2011-04-30 13:30:48.652 Backing up database with script: '/usr/share/mythtv/mythconverg_backup.pl'
2011-04-30 13:32:10.420 Database Backup complete.
2011-04-30 13:32:10.471 Backed up database to file: '/var/lib/mythtv/recordings1/mythconverg-1264-20110430133048.sql.gz'
ICE default IO error handler doing an exit(), pid = 3197, errno = 32
```

---

### Post by kja999 on 2011-05-01
ICE errors tend to be related to the .ICEAuthority file in your home dir. Not sure what Unity may or may not be doing with this file...
Rename this file so it gets recreated (if needed) and see if that fixes it

---

### Post by dsbw on 2011-05-01
I saw but could not make any sense out of the whole ICEAuthority thing.

Renaming the file did cause it to be re-created. It's much smaller than the one that was there.

No difference as far the front-end though.:confused:

---

### Post by nickrout on 2011-05-01
Why oh why did you upgrade? what did you need in natty that was not available before?

---

### Post by dsbw on 2011-05-03
What did Natty have?

Myth 0.24?

---

### Post by nickrout on 2011-05-03
> **dsbw said:**
> What did Natty have?

Myth 0.24?

so do the previous versions, via mythbuntu-repos.

---

### Post by dsbw on 2011-05-04
In other words, I had to upgrade. 

Yeah, I didn't have to upgrade Ubuntu, but I've never had a problem with it before--and the repos HAVE killed my system often and hard.

---

### Post by nickrout on 2011-05-04
> **dsbw said:**
> In other words, I had to upgrade. 

Yeah, I didn't have to upgrade Ubuntu, but I've never had a problem with it before--and the repos HAVE killed my system often and hard.


Odd, i have never had a problem with the repos.

---

### Post by dsbw on 2011-05-05
I used to run 'em auto but then I was spending every few days trying to figure out how to unbreak what got broke.

None of this, of course, helps me with my current woes.

---

### Post by Panhead Bill on 2011-05-07
I feel your pain. 

 I was testing a new front end/slave backend and tried the reepos to get .24 to fix a sound issue.  The box gave me a database schema error and wanted to upgrade my master backend schema; I declined, but when I checked my desktop frontend it reported that the schema (That was working) was now newer than the one it expected. (How did the new box cause the master to change schema even though I declined the upgrade?)

So now I was forced to upgrade all three boxes to 11.04.  The new box has no sound, but it is still in shakedown so I won't worry about it for now.  The desktop frontend works except that now sound is broken.  (I thought I saw a thread about having to play with sound after .24 was loaded)

The master backend seems to function except that like you I get the frontend splash screen and about 90 seconds later it crashes back to the desktop.  The backend is working as I can access it on the two other boxes.

Time to crash and try again tomorrow evening.

---

### Post by nickrout on 2011-05-07
> **Panhead Bill said:**
> I feel your pain. 

 I was testing a new front end/slave backend and tried the reepos to get .24 to fix a sound issue.  The box gave me a database schema error and wanted to upgrade my master backend schema; I declined, 

why decline? when you upgrade to 0.24, you need to update the database to the 0.24 schema. > but when I checked my desktop frontend it reported that the schema (That was working) was now newer than the one it expected. (How did the new box cause the master to change schema even though I declined the upgrade?)

So now I was forced to upgrade all three boxes to 11.04. what forced you to do that? >   The new box has no sound, have you scanned for audio devices in the audio setup page of general setup? The docos are clear on the need for that >  but it is still in shakedown so I won't worry about it for now.  The desktop frontend works except that now sound is broken.  (I thought I saw a thread about having to play with sound after .24 was loaded)

The master backend seems to function except that like you I get the frontend splash screen and about 90 seconds later it crashes back to the desktop.  The backend is working as I can access it on the two other boxes.

Time to crash and try again tomorrow evening.

have you read any logs? they are essential for diagnosing problems :)

---

### Post by Panhead Bill on 2011-05-07
> **nickrout said:**
> why decline? when you upgrade to 0.24, you need to update the database to the 0.24 schema.:)

(Now, after some needed sleep, let me try and answer you)
 I declined the upgrade as to try and prevent breaking a .23 system that was more or less working.

 The box I was working on is a new front end/slave back end, and being new, is easy to wipe and install the OS from scratch.

Instead of stopping the database change it appeared to put the backend in a strange state where the new box listed the backend an having an older schema but the older desktop frontend listed the backend as having a newer schema. 


> **nickrout said:**
> what forced you to do that?:)

Since neither box would allow me to access my backend's content, it seemed that I was now trapped and needed to upgrade all three boxes to 11.04 to try and get the schema straight.

> **nickrout said:**
> have you scanned for audio devices in the audio setup page of general setup? The docos are clear on the need for that:) 

Not yet, that was what I was referring to when I wrote about playing with sound after .24 was loaded.
(Update: Yes, audio now works, but keyboard control of sound level does not.)

> **nickrout said:**
> have you read any logs? they are essential for diagnosing problems :)

Not yet, after finding that the master backend wouldn't load the frontend I decided it was time to look in the forums to see if this happened to others - and I found this thread.  At this point in the evening, it was time to stop, sleep and retry in the morning.


So any ideas about how _not_ performing a schema upgrade somehow "borked" it anyway?

---

### Post by tgm4883 on 2011-05-07
> **dsbw said:**
> In other words, I had to upgrade. 

Yeah, I didn't have to upgrade Ubuntu, but I've never had a problem with it before--and the repos HAVE killed my system often and hard.

Please explain exactly what you mean by this. The exact same process that creates the mythtv packaging for the Ubuntu repos is used in the mythbuntu-repos. (And I do mean EXACT)

---

### Post by tgm4883 on 2011-05-07
> **Panhead Bill said:**
> I feel your pain. 

 I was testing a new front end/slave backend and tried the reepos to get .24 to fix a sound issue.  The box gave me a database schema error and wanted to upgrade my master backend schema; I declined, but when I checked my desktop frontend it reported that the schema (That was working) was now newer than the one it expected. (How did the new box cause the master to change schema even though I declined the upgrade?)

So now I was forced to upgrade all three boxes to 11.04.  The new box has no sound, but it is still in shakedown so I won't worry about it for now.  The desktop frontend works except that now sound is broken.  (I thought I saw a thread about having to play with sound after .24 was loaded)

The master backend seems to function except that like you I get the frontend splash screen and about 90 seconds later it crashes back to the desktop.  The backend is working as I can access it on the two other boxes.

Time to crash and try again tomorrow evening.

You weren't forced to upgrade all machines to 11.04. You may have been forced to upgrade all machines to mythtv 0.24 (or restore from a database backup to a 0.23.x version).

---

### Post by tgm4883 on 2011-05-07
> **Panhead Bill said:**
> <SNIP>

So any ideas about how _not_ performing a schema upgrade somehow "borked" it anyway?

IDK, I'd have to ask the MythTV dev team. I think a better point is that

Any minor version number bump (eg. 0.23.0 to 0.23.1) usually means a Protocol version bump. This means they are incompatible, but you can revert back by just reverting to the previous package.

Any major version number bump (eg. 0.23.x to 0.24.x) means a Database schema bump. This means the database changes, and the only way to revert is to revert the packages AND restore from a previous database backup.

---

### Post by nickrout on 2011-05-07
Don't forget that there is more than one schema update going on here. When you update the backend, it updates the tables that it is responsible for, like the ones associated with recording TV.

However there are tables that are associated with frontend functions, like mythvide, which are only updated by starting a new version of the frontend, which then connects to the backend's database and updates the mythvideo (and perhaps other) tables.

Please clarify which schema you are referring to.

Also the ICE problem should be solved if you delete ~/.ICEAuthority on the machine that is complaining.

---

### Post by dsbw on 2011-05-10
> **nickrout said:**
> Also the ICE problem should be solved if you delete ~/.ICEAuthority on the machine that is complaining.

Well, I was going to bitch about how this didn't work for me but I thought I'd try it again before I did and...voila!

See? Upgrading's not so bad! :lolflag:

---

