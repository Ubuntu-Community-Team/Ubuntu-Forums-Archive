---
title: "[SOLVED] LiveTV will not start"
date: 2008-06-27
forum: Mythbuntu
---

### Post by jrhaws on 2008-06-27
LiveTV will not start.  I just installed Mythbuntu 8.04.  Some system specs:

Intel P4 3.0Ghz
1GB RAM
ATI All-in-Wonder Video card (only using for display - none of the other features)
pcHDTV HD-5500 Tuner card (two of them)

I finally figured out my mySQL issue (the install didn't setup a clean DB and I had to fix that).

Now I have most everything working (except the remote, but that isn't crucial right now).

The issue is as stated above:  LiveTV will not start.  Here is the frontend log:

Starting mythfrontend.real..
2008-06-26 21:38:13.398 New DB connection, total: 2
2008-06-26 21:38:13.398 Connected to database 'mythconverg' at host: localhost
2008-06-26 21:38:13.401 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-06-26 21:38:13.401 Enabled verbose msgs:  important general
2008-06-26 21:38:13.879 Unable to parse themeinfo.xml for glass-wide
2008-06-26 21:38:13.879 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-26 21:38:14.503 Unable to parse themeinfo.xml for glass-wide
2008-06-26 21:38:14.503 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-26 21:38:16.077 Writing settings file /home/jrhaws/.mythtv/mysql.txt
2008-06-26 21:38:16.078 Closing DB connection named 'DBManager1'
2008-06-26 21:38:16.078 Closing DB connection named 'DBManager0'
2008-06-26 21:38:16.078 Connected to database 'mythconverg' at host: localhost
2008-06-26 21:38:16.130 Primary screen 0.
2008-06-26 21:38:16.131 Using screen 0, 1280x1024 at 0,0
2008-06-26 21:38:16.134 Switching to square mode (G.A.N.T)
2008-06-26 21:38:16.152 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-06-26 21:38:16.153 lirc_init failed for mythtv, see preceding messages
2008-06-26 21:38:16.153 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jrhaws/.mythtv/joystickmenurc
2008-06-26 21:38:17.453 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-06-26 21:38:17.556 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-26 21:38:17.733 Registering Internal as a media playback plugin.
2008-06-26 21:38:17.765 Inserting MythArchive initial database information.
2008-06-26 21:38:17.765 Upgrading to MythArchive schema version 1000
2008-06-26 21:38:17.768 Connected to database 'mythconverg' at host: localhost
2008-06-26 21:38:17.769 Upgrading to MythArchive schema version 1001
2008-06-26 21:38:17.863 Inserting MythFlix initial database information.
2008-06-26 21:38:17.863 Upgrading to MythFlix schema version 1000
2008-06-26 21:38:17.866 Upgrading to MythFlix schema version 1001
2008-06-26 21:38:17.932 Inserting MythGallery initial database information.
2008-06-26 21:38:17.932 Upgrading to MythGallery schema version 1000
2008-06-26 21:38:18.030 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-26 21:38:18.049 Inserting MythGame initial database information.
2008-06-26 21:38:18.050 Upgrading to MythGame schema version 1011
2008-06-26 21:38:18.062 New DB connection, total: 3
2008-06-26 21:38:18.062 Connected to database 'mythconverg' at host: localhost
2008-06-26 21:38:18.063 Upgrading to MythGame schema version 1012
2008-06-26 21:38:18.097 Setting Up MythMovies Database Tables
2008-06-26 21:38:18.124 MythMovies Database Setup Complete
2008-06-26 21:38:18.374 Inserting MythMusic initial database information.
2008-06-26 21:38:18.374 Upgrading to MythMusic schema version 1000
2008-06-26 21:38:18.385 Upgrading to MythMusic schema version 1001
2008-06-26 21:38:18.387 Upgrading to MythMusic schema version 1002
2008-06-26 21:38:18.996 Updating music metadata to be UTF-8 in the database
2008-06-26 21:38:18.997 Done updating music metadata to UTF-8
2008-06-26 21:38:18.997 Upgrading to MythMusic schema version 1003
2008-06-26 21:38:18.998 Upgrading to MythMusic schema version 1004
2008-06-26 21:38:19.013 Upgrading to MythMusic schema version 1005
2008-06-26 21:38:19.022 Upgrading to MythMusic schema version 1006
2008-06-26 21:38:19.471 Upgrading to MythMusic schema version 1007
2008-06-26 21:38:19.478 Upgrading to MythMusic schema version 1008
2008-06-26 21:38:19.525 Upgrading to MythMusic schema version 1009
2008-06-26 21:38:19.532 Upgrading to MythMusic schema version 1010
2008-06-26 21:38:19.581 Updating music_albumart image types
2008-06-26 21:38:19.584 Upgrading to MythMusic schema version 1011
2008-06-26 21:38:19.584 Upgrading to MythMusic schema version 1012
2008-06-26 21:38:19.593 Upgrading to MythMusic schema version 1013
2008-06-26 21:38:19.689 Failed to run 'cdrecord --scanbus'
2008-06-26 21:38:19.692 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-26 21:38:19.695 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-26 21:38:19.788 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-06-26 21:38:19.948 Inserting MythVideo initial database information.
2008-06-26 21:38:19.948 Upgrading to MythVideo schema version 1000
2008-06-26 21:38:19.974 Upgrading to MythVideo schema version 1000
2008-06-26 21:38:19.976 Upgrading to MythVideo schema version 1001
2008-06-26 21:38:20.171 Upgrading to MythVideo schema version 1002
2008-06-26 21:38:20.178 Upgrading to MythVideo schema version 1003
2008-06-26 21:38:20.227 Upgrading to MythVideo schema version 1004
2008-06-26 21:38:20.237 Upgrading to MythVideo schema version 1005
2008-06-26 21:38:20.239 Upgrading to MythVideo schema version 1006
2008-06-26 21:38:20.240 Upgrading to MythVideo schema version 1007
2008-06-26 21:38:20.302 Upgrading to MythVideo schema version 1008
2008-06-26 21:38:20.304 Upgrading to MythVideo schema version 1009
2008-06-26 21:38:20.305 Upgrading to MythVideo schema version 1010
2008-06-26 21:38:20.308 Inserting MythDVD initial database information.
2008-06-26 21:38:20.308 Upgrading to MythVideo schema version 1000
2008-06-26 21:38:20.314 Upgrading to MythVideo schema version 1000
2008-06-26 21:38:20.323 Upgrading to MythVideo schema version 1001
2008-06-26 21:38:20.324 Upgrading to MythVideo schema version 1002
2008-06-26 21:38:20.332 Upgrading to MythVideo schema version 1011
2008-06-26 21:38:20.333 Updated from old MythDVD/MythVideo schema to combined version: 1011.
2008-06-26 21:38:20.334 Upgrading to MythVideo schema version 1012
2008-06-26 21:38:20.378 Upgrading to MythVideo schema version 1013
2008-06-26 21:38:20.379 Upgrading to MythVideo schema version 1014
2008-06-26 21:38:20.686 Upgrading to MythVideo schema version 1015
2008-06-26 21:38:20.756 Upgrading to MythVideo schema version 1016
2008-06-26 21:38:20.879 Inserting MythWeather initial database information.
2008-06-26 21:38:20.880 Upgrading to MythWeather schema version 1000
2008-06-26 21:38:26.640 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-26 21:38:26.641 Using protocol version 40
2008-06-26 21:38:26.648 TV: Attempting to change from None to WatchingLiveTV
2008-06-26 21:38:26.649 Using protocol version 40
2008-06-26 21:38:27.772 GetEntryAt(-1) failed.
2008-06-26 21:38:27.774 EntryToProgram(0@Wed Dec 31 17:00:00 1969) failed to get pginfo
2008-06-26 21:38:27.775 TV Error: LiveTV not successfully started
2008-06-26 21:38:27.775 TV Error: LiveTV not successfully started
2008-06-26 21:38:27.856 TV: Deleting TV Chain in destructor
2008-06-26 21:38:27.880 DPMS Deactivated 
2008-06-26 21:38:27.881 DPMS Reactivated.
2008-06-26 21:38:33.315 Deleting UPnP client...


Does anyone have any ideas?  I have been able to watch TV on these cards in the past using a Fedora installation of MythTV, but none of the plugins seemed to work in Fedora.  Now in Mythbuntu, the plugins seem to work (I can watch trailers, listen to internet radio, play DVDs, etc.) but watching TV doesn't work.

Any ideas?

Thanks in advance for the help!

---

### Post by larsolav on 2008-06-27
I'm no expert, so I'don't know why this happened. Are you able to record shows? Maybe the backend log at 21:38:26 may provide some hints, as this may be a backend problem more than a frontend problem.

Edit:
Here is a link to someone who had a similar problem:
[http://www.gossamer-threads.com/lists/mythtv/users/194241](http://www.gossamer-threads.com/lists/mythtv/users/194241)

It may be that you need to go to mythtv setup in MCC and make sure you set up the tuners correctly and that they are set to a working start channel.

---

### Post by rhpot1991 on 2008-06-27
Double check the folder you have your recordings set to store in.  I see you are using your home dir a lot, thats not the greatest idea and may give you permission errors.  The directories for your recordings should be owned by mythtv:mythtv and be chmod'd 2775.  You can test them by doing `sudo su mythtv` and trying to make a file in them.

---

### Post by netslacker on 2008-06-27
> **rhpot1991 said:**
> Double check the folder you have your recordings set to store in.  I see you are using your home dir a lot, thats not the greatest idea and may give you permission errors.  The directories for your recordings should be owned by mythtv:mythtv and be chmod'd 2775.  You can test them by doing `sudo su mythtv` and trying to make a file in them.

I would agree that folder permission is the most likely cause of this problem.  In backend setup, note the folder that you are using for "LiveTV" (most likely the default).  Then exit the setup program and navigate to where the folder is and make sure the folder exists and has proper permissions.  If the folder is not writable by mythtv then live tv cannot start (since live TV involves writing the tv stream to the disk and simultaneously playing it back from the disk).

---

### Post by jrhaws on 2008-06-28
New log:

2008-06-28 16:00:31.418 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-28 16:00:31.950 XScreenSaver support enabled
2008-06-28 16:00:31.950 DPMS is disabled.
2008-06-28 16:00:31.951 Empty LocalHostName.
2008-06-28 16:00:31.951 Using localhost value of kronk
2008-06-28 16:00:31.970 New DB connection, total: 1
2008-06-28 16:00:31.976 Connected to database 'mythconverg' at host: localhost
2008-06-28 16:00:31.979 Closing DB connection named 'DBManager0'
2008-06-28 16:00:31.987 Primary screen 0.
2008-06-28 16:00:31.988 Connected to database 'mythconverg' at host: localhost
2008-06-28 16:00:31.990 Using screen 0, 1280x1024 at 0,0
2008-06-28 16:00:32.000 New DB connection, total: 2
2008-06-28 16:00:32.001 Connected to database 'mythconverg' at host: localhost
2008-06-28 16:00:32.004 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-06-28 16:00:32.004 Enabled verbose msgs:  important general
2008-06-28 16:00:32.147 Unable to parse themeinfo.xml for glass-wide
2008-06-28 16:00:32.147 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-28 16:00:32.391 Unable to parse themeinfo.xml for glass-wide
2008-06-28 16:00:32.391 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-28 16:00:33.772 Primary screen 0.
2008-06-28 16:00:33.772 Using screen 0, 1280x1024 at 0,0
2008-06-28 16:00:33.775 Switching to square mode (Mythbuntu-8.04)
2008-06-28 16:00:33.795 Using the Qt painter
2008-06-28 16:00:33.833 lirc init success using configuration file: /home/jrhaws/.mythtv/lircrc
2008-06-28 16:00:33.833 JoystickMenuClient Error: Joystick disabled - Failed to read /home/jrhaws/.mythtv/joystickmenurc
2008-06-28 16:00:35.751 Specified base font 'medium' does not exist for font clock
2008-06-28 16:00:35.752 Specified base font 'medium' does not exist for font small
2008-06-28 16:00:35.752 Specified base font 'medium' does not exist for font medium
2008-06-28 16:00:35.752 Specified base font 'medium' does not exist for font large
2008-06-28 16:00:35.756 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-06-28 16:00:35.935 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-28 16:00:36.037 Registering Internal as a media playback plugin.
2008-06-28 16:00:36.152 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-28 16:00:36.236 Failed to run 'cdrecord --scanbus'
2008-06-28 16:00:36.240 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-28 16:00:36.244 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-28 16:00:36.299 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-06-28 16:00:40.182 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-06-28 16:00:40.183 Using protocol version 40
2008-06-28 16:00:40.188 TV: Attempting to change from None to WatchingLiveTV
2008-06-28 16:00:40.189 Using protocol version 40
2008-06-28 16:00:41.333 NVP: Disabling Audio, params(-1,2,44100)
Segmentation fault



Now I am able to start LiveTV, but as soon as it starts, I get a Segmentation Fault.  Why the last thing before the Seg Fault is Disabling Audio, I have no idea.

The problem starting LiveTV was a permissions issue, BTW.  My user owned the folder, not the mythtv user.  Go figure.

---

### Post by netslacker on 2008-06-28
> **jrhaws said:**
> 
2008-06-28 16:00:40.183 Using protocol version 40
2008-06-28 16:00:40.188 TV: Attempting to change from None to WatchingLiveTV
2008-06-28 16:00:40.189 Using protocol version 40
2008-06-28 16:00:41.333 NVP: Disabling Audio, params(-1,2,44100)
Segmentation fault

Now I am able to start LiveTV, but as soon as it starts, I get a Segmentation Fault.  Why the last thing before the Seg Fault is Disabling Audio, I have no idea.

The problem starting LiveTV was a permissions issue, BTW.  My user owned the folder, not the mythtv user.  Go figure.

Have you checked syslog and messages for other hints? also, do other videos (or recorded TV) play using mplayer or VLC?

---

### Post by jrhaws on 2008-06-29
> **netslacker said:**
> Have you checked syslog and messages for other hints? also, do other videos (or recorded TV) play using mplayer or VLC?

That is what I was headed for, and it paid off.

The problem was that my audio drivers were not working correctly, so I had to reinstall them according to instructions at a thread I can't find anymore.  In a nutshell, this is what I had to do:

```
 sudo vim /etc/modprobe.d/alsa-base 
```

Change options snd-intel8x0m = -2 to options snd-intel8x0m index=0

```
 sudo apt-get install module-assistant
 sudo m-a update
 sudo m-a prepare
 sudo m-a a-i alsa
```

Once the sound was working, my proprietary ATI drivers were causing VERY choppy video and audio, so I disabled them in the Proprietary drivers section of the MCC and everything is happy.

Thank you all for your help.  I really appreciate it!

Jon

---

