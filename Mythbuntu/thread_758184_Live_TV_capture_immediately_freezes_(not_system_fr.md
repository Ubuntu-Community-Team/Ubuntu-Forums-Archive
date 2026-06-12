---
title: "Live TV capture immediately freezes (not system freeze)"
date: 2008-04-17
forum: Mythbuntu
---

### Post by thoraxe on 2008-04-17
So after I finally got the remote working, I hook the PC up to the TV only to find out that the TV out on my Radeon card doesn't work.  After doing some research I install the latest ATI drivers and I'm back in business.

So in the hopes of eventually getting my blaster to work with  my Motorola cable box, I set up everything and set the machine to use the composite input on the PVR-150.

As soon as I go into Live TV I can get a few frames in and then the capture freezes.  I tried to switch to the tuner input with the same result.

The system is an Athlon XP 2000+ with a PVR 150 (non MCE non usb) with a Radeon 9600 AGP card running the latest ATI drivers from ATI's website.  I'm using Mythbuntu 8.04 Beta.

Just let me know what logs you want to see and I'd be happy to provide.  Not really sure where to begin looking for this one.

---

### Post by volkswagner on 2008-04-17
Both frontend.log and backend.log.

---

### Post by majoridiot on 2008-04-18
> **thoraxe said:**
> So in the hopes of eventually getting my blaster to work with  my Motorola cable box, I set up everything and set the machine to use the composite input on the PVR-150.

FYI- you can also use firewire to change the channel, if you have firewire on your backend machine.

> **thoraxe said:**
> As soon as I go into Live TV I can get a few frames in and then the capture freezes.  I tried to switch to the tuner input with the same result.

can you get a good recording, instead of using livetv?

also, can you get a good capture from a terminal? assuming your tuner is on video0, you may need to adjust:

```
$ cat /dev/video0 > ~/Desktop/test.mpg
```

and then try to play the test file.

> **thoraxe said:**
> Just let me know what logs you want to see and I'd be happy to provide.  Not really sure where to begin looking for this one.

the two logs volkswagner mentioned are located in /var/log/mythtv

---

### Post by thoraxe on 2008-04-28
Here are the two logfiles requested.

I noticed that if I switch between the tuner and the composite input that both exhibit the same behavior -- a couple of frames and then freeze.  But, as soon as I switch to the other input, the monitor updates for a few seconds, so it's clear that the capture is working.  It's just the display that's freezing.

I'll try to do the capture directly to mpg but I don't think the capture itself is freezing.

Also, when exiting Myth Frontend after the capture it crashes, but I don't think the log is reporting this.

frontend.log
```
thoraxe@festivemyth:/var/log/mythtv$ cat mythfrontend.log
Starting mythfrontend.real..
2008-04-28 17:33:26.900 New DB connection, total: 2
2008-04-28 17:33:26.901 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:33:26.907 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 17:33:26.908 Enabled verbose msgs:  important general
2008-04-28 17:33:27.934 Unable to parse themeinfo.xml for glass-wide
2008-04-28 17:33:27.935 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 17:33:29.209 Unable to parse themeinfo.xml for glass-wide
2008-04-28 17:33:29.209 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 17:33:31.491 Writing settings file /home/thoraxe/.mythtv/mysql.txt
2008-04-28 17:33:31.491 Closing DB connection named 'DBManager1'
2008-04-28 17:33:31.492 Closing DB connection named 'DBManager0'
2008-04-28 17:33:31.492 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:33:31.573 Total desktop dim: 1280x1024, with 1 screen[s].
2008-04-28 17:33:31.576 Using screen 0, 1280x1024 at 0,0
2008-04-28 17:33:31.579 Switching to square mode (Mythbuntu)
2008-04-28 17:33:31.734 Using the Qt painter
2008-04-28 17:33:31.738 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 17:33:31.738 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 17:35:01.314 Specified base font 'medium' does not exist for font clock
2008-04-28 17:35:01.330 Specified base font 'medium' does not exist for font small
2008-04-28 17:35:01.331 Specified base font 'medium' does not exist for font medium
2008-04-28 17:35:01.331 Specified base font 'medium' does not exist for font large
2008-04-28 17:35:01.335 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 17:35:01.533 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 17:35:01.835 Registering Internal as a media playback plugin.
2008-04-28 17:35:01.891 Upgrading to MythArchive schema version 1001
2008-04-28 17:35:01.904 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:35:02.304 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 17:35:02.316 Setting Up MythMovies Database Tables
2008-04-28 17:35:02.327 MythMovies Database Setup Complete
2008-04-28 17:35:02.653 Upgrading to MythMusic schema version 1007
2008-04-28 17:35:02.661 Upgrading to MythMusic schema version 1008
2008-04-28 17:35:02.684 Upgrading to MythMusic schema version 1009
2008-04-28 17:35:02.691 Upgrading to MythMusic schema version 1010
2008-04-28 17:35:02.698 Updating music_albumart image types
2008-04-28 17:35:02.702 Upgrading to MythMusic schema version 1011
2008-04-28 17:35:02.704 Upgrading to MythMusic schema version 1012
2008-04-28 17:35:02.711 Upgrading to MythMusic schema version 1013
2008-04-28 17:35:02.759 Failed to run 'cdrecord --scanbus'
2008-04-28 17:35:02.764 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 17:35:02.769 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 17:35:02.937 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 17:35:03.349 Inserting MythWeather initial database information.
2008-04-28 17:35:03.349 Upgrading to MythWeather schema version 1000
2008-04-28 17:35:09.923 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 17:35:09.925 Using protocol version 40
2008-04-28 17:35:11.556 Deleting UPnP client...
Starting mythfrontend.real..
2008-04-28 17:55:03.056 New DB connection, total: 2
2008-04-28 17:55:03.057 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:55:03.060 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 17:55:03.061 Enabled verbose msgs:  important general
2008-04-28 17:55:03.109 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-28 17:55:03.910 Unable to parse themeinfo.xml for glass-wide
2008-04-28 17:55:03.911 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 17:55:04.937 Unable to parse themeinfo.xml for glass-wide
2008-04-28 17:55:04.937 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 17:55:07.162 Total desktop dim: 1280x1024, with 1 screen[s].
2008-04-28 17:55:07.164 Using screen 0, 1280x1024 at 0,0
2008-04-28 17:55:07.168 Switching to square mode (Mythbuntu)
2008-04-28 17:55:07.320 Using the Qt painter
2008-04-28 17:55:07.323 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 17:55:07.323 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 17:55:10.600 Specified base font 'medium' does not exist for font clock
2008-04-28 17:55:10.624 Specified base font 'medium' does not exist for font small
2008-04-28 17:55:10.624 Specified base font 'medium' does not exist for font medium
2008-04-28 17:55:10.624 Specified base font 'medium' does not exist for font large
2008-04-28 17:55:10.629 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 17:55:10.848 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 17:55:11.040 Registering Internal as a media playback plugin.
2008-04-28 17:55:11.374 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 17:55:11.744 Failed to run 'cdrecord --scanbus'
2008-04-28 17:55:11.749 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 17:55:11.755 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 17:55:11.834 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 17:55:19.029 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 17:55:19.031 Using protocol version 40
2008-04-28 17:55:21.041 Deleting UPnP client...
2008-04-28 17:55:21.041 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-04-28 18:17:47.473 New DB connection, total: 2
2008-04-28 18:17:47.473 Connected to database 'mythconverg' at host: localhost
2008-04-28 18:17:47.477 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 18:17:47.477 Enabled verbose msgs:  important general
2008-04-28 18:17:48.346 Unable to parse themeinfo.xml for glass-wide
2008-04-28 18:17:48.346 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 18:17:49.604 Unable to parse themeinfo.xml for glass-wide
2008-04-28 18:17:49.605 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 18:17:50.323 Total desktop dim: 1280x1024, with 1 screen[s].
2008-04-28 18:17:50.324 Using screen 0, 1280x1024 at 0,0
2008-04-28 18:17:50.327 Switching to square mode (Mythbuntu)
2008-04-28 18:17:50.522 Using the Qt painter
2008-04-28 18:17:50.525 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 18:17:50.525 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 18:17:53.360 Specified base font 'medium' does not exist for font clock
2008-04-28 18:17:53.385 Specified base font 'medium' does not exist for font small
2008-04-28 18:17:53.385 Specified base font 'medium' does not exist for font medium
2008-04-28 18:17:53.385 Specified base font 'medium' does not exist for font large
2008-04-28 18:17:53.387 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 18:17:53.640 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 18:17:53.834 Registering Internal as a media playback plugin.
2008-04-28 18:17:54.169 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 18:17:54.532 Failed to run 'cdrecord --scanbus'
2008-04-28 18:17:54.539 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 18:17:54.545 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 18:17:54.624 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 18:18:00.651 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 18:18:00.653 Using protocol version 40
2008-04-28 18:18:02.191 Deleting UPnP client...
2008-04-28 18:18:02.191 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-04-28 20:10:49.781 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-28 20:10:49.782 New DB connection, total: 2
2008-04-28 20:10:49.783 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:10:49.786 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:10:49.787 Enabled verbose msgs:  important general
2008-04-28 20:10:50.460 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:10:50.461 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:10:51.478 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:10:51.478 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:10:52.550 Total desktop dim: 1280x1024, with 1 screen[s].
2008-04-28 20:10:52.551 Using screen 0, 1280x1024 at 0,0
2008-04-28 20:10:52.554 Switching to square mode (Mythbuntu)
2008-04-28 20:10:52.744 Using the Qt painter
2008-04-28 20:10:52.747 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 20:10:52.747 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 20:10:55.557 Specified base font 'medium' does not exist for font clock
2008-04-28 20:10:55.582 Specified base font 'medium' does not exist for font small
2008-04-28 20:10:55.582 Specified base font 'medium' does not exist for font medium
2008-04-28 20:10:55.582 Specified base font 'medium' does not exist for font large
2008-04-28 20:10:55.584 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 20:10:55.805 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 20:10:55.997 Registering Internal as a media playback plugin.
2008-04-28 20:10:56.333 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 20:10:56.704 Failed to run 'cdrecord --scanbus'
2008-04-28 20:10:56.711 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 20:10:56.717 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 20:10:56.796 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 20:11:01.078 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 20:11:01.081 Using protocol version 40
2008-04-28 20:11:02.039 Deleting UPnP client...
2008-04-28 20:11:02.040 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-04-28 20:38:40.682 New DB connection, total: 2
2008-04-28 20:38:40.683 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:38:40.686 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:38:40.687 Enabled verbose msgs:  important general
2008-04-28 20:38:40.723 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-28 20:38:41.369 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:38:41.369 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:38:42.587 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:38:42.587 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:38:43.268 Total desktop dim: 1280x1024, with 1 screen[s].
2008-04-28 20:38:43.269 Using screen 0, 1280x1024 at 0,0
2008-04-28 20:38:43.272 Switching to square mode (Mythbuntu)
2008-04-28 20:38:43.455 Using the Qt painter
2008-04-28 20:38:43.458 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 20:38:43.458 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 20:38:46.251 Specified base font 'medium' does not exist for font clock
2008-04-28 20:38:46.283 Specified base font 'medium' does not exist for font small
2008-04-28 20:38:46.283 Specified base font 'medium' does not exist for font medium
2008-04-28 20:38:46.284 Specified base font 'medium' does not exist for font large
2008-04-28 20:38:46.286 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 20:38:46.529 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 20:38:46.722 Registering Internal as a media playback plugin.
2008-04-28 20:38:47.058 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 20:38:47.413 Failed to run 'cdrecord --scanbus'
2008-04-28 20:38:47.420 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 20:38:47.426 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 20:38:47.506 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 20:38:51.153 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 20:38:51.155 Using protocol version 40
2008-04-28 20:38:51.926 Deleting UPnP client...
2008-04-28 20:38:51.927 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-04-28 20:44:00.406 New DB connection, total: 2
2008-04-28 20:44:00.406 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:44:00.410 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:44:00.410 Enabled verbose msgs:  important general
2008-04-28 20:44:01.357 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:44:01.357 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:44:02.341 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:44:02.341 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:44:03.534 Total desktop dim: 1280x1024, with 1 screen[s].
2008-04-28 20:44:03.535 Using screen 0, 1280x1024 at 0,0
2008-04-28 20:44:03.539 Switching to square mode (Mythbuntu)
2008-04-28 20:44:03.740 Using the Qt painter
2008-04-28 20:44:03.743 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 20:44:03.743 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 20:44:06.749 Specified base font 'medium' does not exist for font clock
2008-04-28 20:44:06.769 Specified base font 'medium' does not exist for font small
2008-04-28 20:44:06.769 Specified base font 'medium' does not exist for font medium
2008-04-28 20:44:06.769 Specified base font 'medium' does not exist for font large
2008-04-28 20:44:06.771 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 20:44:06.995 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 20:44:07.190 Registering Internal as a media playback plugin.
2008-04-28 20:44:07.529 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 20:44:07.881 Failed to run 'cdrecord --scanbus'
2008-04-28 20:44:07.888 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 20:44:07.894 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 20:44:07.978 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 20:44:13.100 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 20:44:13.102 Using protocol version 40
2008-04-28 20:44:14.463 Deleting UPnP client...
2008-04-28 20:44:14.464 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-04-28 20:47:47.561 New DB connection, total: 2
2008-04-28 20:47:47.563 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:47:47.566 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:47:47.566 Enabled verbose msgs:  important general
2008-04-28 20:47:47.576 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2008-04-28 20:47:48.332 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:47:48.332 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:47:49.416 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:47:49.416 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:47:50.296 Total desktop dim: 640x480, with 1 screen[s].
2008-04-28 20:47:50.297 Using screen 0, 640x480 at 0,0
2008-04-28 20:47:50.300 Switching to square mode (Mythbuntu)
2008-04-28 20:47:50.486 Using the Qt painter
2008-04-28 20:47:50.489 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 20:47:50.490 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 20:47:51.055 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024
2008-04-28 20:47:51.110 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/conflicts
2008-04-28 20:47:51.115 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/details
2008-04-28 20:47:51.126 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/keyboard
2008-04-28 20:47:51.165 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/music
2008-04-28 20:47:51.240 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/priorities
2008-04-28 20:47:51.254 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/programfind
2008-04-28 20:47:51.274 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/programguide
2008-04-28 20:47:51.322 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/recordoptions
2008-04-28 20:47:51.330 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/shared
2008-04-28 20:47:51.343 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/status
2008-04-28 20:47:51.349 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/title
2008-04-28 20:47:51.429 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/tvplayback
2008-04-28 20:47:51.435 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/type
2008-04-28 20:47:51.447 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/video
2008-04-28 20:47:51.451 Removing stale cache dir: /home/thoraxe/.mythtv/themecache/Mythbuntu.1280.1024/watermark
2008-04-28 20:48:18.882 Specified base font 'medium' does not exist for font clock
2008-04-28 20:48:18.888 Specified base font 'medium' does not exist for font small
2008-04-28 20:48:18.888 Specified base font 'medium' does not exist for font medium
2008-04-28 20:48:18.888 Specified base font 'medium' does not exist for font large
2008-04-28 20:48:18.890 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 20:48:18.958 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 20:48:19.148 Registering Internal as a media playback plugin.
2008-04-28 20:48:19.481 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 20:48:19.834 Failed to run 'cdrecord --scanbus'
2008-04-28 20:48:19.840 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 20:48:19.846 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 20:48:19.926 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 20:48:23.492 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 20:48:23.494 Using protocol version 40
2008-04-28 20:48:27.891 Deleting UPnP client...
2008-04-28 20:48:27.892 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
Starting mythfrontend.real..
2008-04-28 20:52:23.545 New DB connection, total: 2
2008-04-28 20:52:23.545 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:52:23.550 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:52:23.550 Enabled verbose msgs:  important general
2008-04-28 20:52:23.689 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:52:23.689 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:52:23.920 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:52:23.920 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:52:24.275 Total desktop dim: 640x480, with 1 screen[s].
2008-04-28 20:52:24.276 Using screen 0, 640x480 at 0,0
2008-04-28 20:52:24.279 Switching to square mode (Mythbuntu)
2008-04-28 20:52:24.450 Using the Qt painter
2008-04-28 20:52:24.454 lirc init success using configuration file: /home/thoraxe/.mythtv/lircrc
2008-04-28 20:52:24.454 JoystickMenuClient Error: Joystick disabled - Failed to read /home/thoraxe/.mythtv/joystickmenurc
2008-04-28 20:52:25.766 Specified base font 'medium' does not exist for font clock
2008-04-28 20:52:25.772 Specified base font 'medium' does not exist for font small
2008-04-28 20:52:25.772 Specified base font 'medium' does not exist for font medium
2008-04-28 20:52:25.772 Specified base font 'medium' does not exist for font large
2008-04-28 20:52:25.774 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 20:52:25.841 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-28 20:52:25.917 Registering Internal as a media playback plugin.
2008-04-28 20:52:26.134 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-28 20:52:26.185 Failed to run 'cdrecord --scanbus'
2008-04-28 20:52:26.191 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-04-28 20:52:26.197 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-04-28 20:52:26.259 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-28 20:52:46.573 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-28 20:52:46.575 Using protocol version 40
2008-04-28 20:52:46.587 TV: Attempting to change from None to WatchingLiveTV
2008-04-28 20:52:46.588 Using protocol version 40
2008-04-28 20:52:48.642 DPMS Deactivated 
2008-04-28 20:52:48.664 New DB connection, total: 3
2008-04-28 20:52:48.665 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:52:49.460 AFD: Opened codec 0x8352ce0, id(MPEG2VIDEO) type(Video)
2008-04-28 20:52:49.461 AFD: codec MP2 has 2 channels
2008-04-28 20:52:49.461 AFD: Opened codec 0x838e8b0, id(MP2) type(Audio)
2008-04-28 20:52:49.548 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-28 20:52:49.549 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-04-28 20:52:49.614 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-04-28 20:52:49.735 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-04-28 20:52:49.736 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-04-28 20:52:49.736 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x83961b8) visual(0x8399728) 
                        XJ_depth(24) WxH(640x480) bpl(1920)
2008-04-28 20:52:49.736 VideoOutputXv Error: Failed to create X buffers.
2008-04-28 20:52:50.048 Couldn't load deinterlace filter 
2008-04-28 20:52:50.059 OSD Theme Dimensions W: 640 H: 480
2008-04-28 20:52:51.088 TV: Changing from None to WatchingLiveTV
2008-04-28 20:52:51.146 Realtime priority would require SUID as root.
2008-04-28 20:52:51.160 Video timing method: USleep with busy wait
2008-04-28 20:52:53.513 WriteAudio: buffer underrun
2008-04-28 20:52:54.111 WriteAudio: buffer underrun
2008-04-28 20:52:54.813 WriteAudio: buffer underrun
2008-04-28 20:52:55.388 WriteAudio: buffer underrun
2008-04-28 20:52:56.029 WriteAudio: buffer underrun
2008-04-28 20:52:57.773 New DB connection, total: 4
2008-04-28 20:52:57.774 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:01.525 WriteAudio: buffer underrun
2008-04-28 20:53:02.100 WriteAudio: buffer underrun
2008-04-28 20:53:02.685 WriteAudio: buffer underrun
2008-04-28 20:53:03.389 WriteAudio: buffer underrun
2008-04-28 20:53:03.983 WriteAudio: buffer underrun
2008-04-28 20:53:04.688 WriteAudio: buffer underrun
2008-04-28 20:53:05.327 WriteAudio: buffer underrun
2008-04-28 20:53:05.984 WriteAudio: buffer underrun
2008-04-28 20:53:06.556 WriteAudio: buffer underrun
2008-04-28 20:53:07.196 WriteAudio: buffer underrun
2008-04-28 20:53:08.017 WriteAudio: buffer underrun
2008-04-28 20:53:08.650 WriteAudio: buffer underrun
2008-04-28 20:53:09.471 WriteAudio: buffer underrun
2008-04-28 20:53:10.099 WriteAudio: buffer underrun
2008-04-28 20:53:10.790 WriteAudio: buffer underrun
2008-04-28 20:53:11.540 WriteAudio: buffer underrun
2008-04-28 20:53:17.384 WriteAudio: buffer underrun
2008-04-28 20:53:17.959 WriteAudio: buffer underrun
2008-04-28 20:53:20.810 WriteAudio: buffer underrun
2008-04-28 20:53:23.925 WriteAudio: buffer underrun
2008-04-28 20:53:24.501 WriteAudio: buffer underrun
2008-04-28 20:53:25.140 WriteAudio: buffer underrun
2008-04-28 20:53:25.783 WriteAudio: buffer underrun
2008-04-28 20:53:26.370 WriteAudio: buffer underrun
2008-04-28 20:53:27.085 WriteAudio: buffer underrun
2008-04-28 20:53:27.667 WriteAudio: buffer underrun
2008-04-28 20:53:28.321 WriteAudio: buffer underrun
2008-04-28 20:53:29.078 WriteAudio: buffer underrun
2008-04-28 20:53:29.771 WriteAudio: buffer underrun
2008-04-28 20:53:30.592 WriteAudio: buffer underrun
2008-04-28 20:53:31.174 WriteAudio: buffer underrun
2008-04-28 20:53:31.866 WriteAudio: buffer underrun
2008-04-28 20:53:32.497 WriteAudio: buffer underrun
2008-04-28 20:53:33.192 WriteAudio: buffer underrun
2008-04-28 20:53:33.924 TV: Attempting to change from WatchingLiveTV to None
2008-04-28 20:53:33.951 WriteAudio: buffer underrun
2008-04-28 20:53:34.292 TV: Changing from WatchingLiveTV to None
2008-04-28 20:53:34.348 DPMS Reactivated.
```

backend.log
```
thoraxe@festivemyth:/var/log/mythtv$ cat mythbackend.log 
2008-04-28 17:32:58.174 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 17:32:58.408 Empty LocalHostName.
2008-04-28 17:32:58.410 Using localhost value of festivemyth
2008-04-28 17:32:58.512 New DB connection, total: 1
2008-04-28 17:32:58.521 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:32:58.524 Closing DB connection named 'DBManager0'
2008-04-28 17:32:58.526 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:32:58.568 New DB connection, total: 2
2008-04-28 17:32:58.717 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:32:58.739 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 17:33:03.458 New DB connection, total: 3
2008-04-28 17:33:03.469 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:33:03.510 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 17:33:03.511 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 17:33:03.556 New DB scheduler connection
2008-04-28 17:33:03.561 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:33:03.625 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 17:33:03.626 Main::Registering HttpStatus Extension
2008-04-28 17:33:03.627 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 17:33:03.628 Enabled verbose msgs:  important general
2008-04-28 17:33:03.678 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 17:33:06.594 Reschedule requested for id -1.
2008-04-28 17:33:06.654 Scheduled 0 items in 0.1 = 0.01 match + 0.05 place
2008-04-28 17:33:06.664 Seem to be woken up by USER
2008-04-28 17:34:23.597 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 17:35:09.925 MainServer::HandleAnnounce Monitor
2008-04-28 17:35:09.929 adding: festivemyth as a client (events: 0)
2008-04-28 17:35:09.931 MainServer::HandleAnnounce Monitor
2008-04-28 17:35:09.932 adding: festivemyth as a client (events: 1)
2008-04-28 17:49:23.650 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 17:54:44.415 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 17:54:44.628 Empty LocalHostName.
2008-04-28 17:54:44.700 Using localhost value of festivemyth
2008-04-28 17:54:44.862 New DB connection, total: 1
2008-04-28 17:54:44.894 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:54:44.919 Closing DB connection named 'DBManager0'
2008-04-28 17:54:44.920 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:54:45.034 New DB connection, total: 2
2008-04-28 17:54:45.036 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:54:45.064 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 17:54:50.229 New DB connection, total: 3
2008-04-28 17:54:50.304 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:54:50.457 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 17:54:50.538 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 17:54:50.836 New DB scheduler connection
2008-04-28 17:54:50.979 Connected to database 'mythconverg' at host: localhost
2008-04-28 17:54:51.095 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 17:54:51.105 Main::Registering HttpStatus Extension
2008-04-28 17:54:51.106 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 17:54:51.107 Enabled verbose msgs:  important general
2008-04-28 17:54:51.149 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 17:54:54.048 Reschedule requested for id -1.
2008-04-28 17:54:54.107 Scheduled 0 items in 0.1 = 0.01 match + 0.05 place
2008-04-28 17:54:54.116 Seem to be woken up by USER
2008-04-28 17:55:19.031 MainServer::HandleAnnounce Monitor
2008-04-28 17:55:19.034 adding: festivemyth as a client (events: 0)
2008-04-28 17:55:19.036 MainServer::HandleAnnounce Monitor
2008-04-28 17:55:19.037 adding: festivemyth as a client (events: 1)
2008-04-28 17:56:11.050 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 18:11:11.104 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 18:17:26.537 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 18:17:26.783 Empty LocalHostName.
2008-04-28 18:17:26.804 Using localhost value of festivemyth
2008-04-28 18:17:26.892 New DB connection, total: 1
2008-04-28 18:17:26.917 Connected to database 'mythconverg' at host: localhost
2008-04-28 18:17:26.919 Closing DB connection named 'DBManager0'
2008-04-28 18:17:26.921 Connected to database 'mythconverg' at host: localhost
2008-04-28 18:17:26.956 New DB connection, total: 2
2008-04-28 18:17:27.088 Connected to database 'mythconverg' at host: localhost
2008-04-28 18:17:27.119 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 18:17:32.181 New DB connection, total: 3
2008-04-28 18:17:32.279 Connected to database 'mythconverg' at host: localhost
2008-04-28 18:17:32.412 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 18:17:32.444 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 18:17:32.517 New DB scheduler connection
2008-04-28 18:17:32.712 Connected to database 'mythconverg' at host: localhost
2008-04-28 18:17:32.936 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 18:17:33.040 Main::Registering HttpStatus Extension
2008-04-28 18:17:33.145 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 18:17:33.196 Enabled verbose msgs:  important general
2008-04-28 18:17:33.320 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 18:17:35.871 Reschedule requested for id -1.
2008-04-28 18:17:35.938 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-04-28 18:17:35.947 Seem to be woken up by USER
2008-04-28 18:18:00.654 MainServer::HandleAnnounce Monitor
2008-04-28 18:18:00.657 adding: festivemyth as a client (events: 0)
2008-04-28 18:18:00.659 MainServer::HandleAnnounce Monitor
2008-04-28 18:18:00.660 adding: festivemyth as a client (events: 1)
2008-04-28 18:18:52.872 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 18:33:52.922 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 18:48:52.956 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 19:03:52.995 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 19:18:53.032 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 19:33:53.068 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 19:48:53.100 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:03:53.136 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:10:28.667 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:10:28.897 Empty LocalHostName.
2008-04-28 20:10:28.977 Using localhost value of festivemyth
2008-04-28 20:10:29.073 New DB connection, total: 1
2008-04-28 20:10:29.099 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:10:29.102 Closing DB connection named 'DBManager0'
2008-04-28 20:10:29.104 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:10:29.137 New DB connection, total: 2
2008-04-28 20:10:29.167 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:10:29.333 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 20:10:34.647 New DB connection, total: 3
2008-04-28 20:10:34.716 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:10:34.792 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:10:34.867 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:10:35.221 New DB scheduler connection
2008-04-28 20:10:35.384 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:10:35.530 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 20:10:35.532 Main::Registering HttpStatus Extension
2008-04-28 20:10:35.533 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:10:35.534 Enabled verbose msgs:  important general
2008-04-28 20:10:35.600 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:10:38.458 Reschedule requested for id -1.
2008-04-28 20:10:38.526 Scheduled 0 items in 0.1 = 0.01 match + 0.05 place
2008-04-28 20:10:38.535 Seem to be woken up by USER
2008-04-28 20:11:01.081 MainServer::HandleAnnounce Monitor
2008-04-28 20:11:01.083 adding: festivemyth as a client (events: 0)
2008-04-28 20:11:01.085 MainServer::HandleAnnounce Monitor
2008-04-28 20:11:01.087 adding: festivemyth as a client (events: 1)
2008-04-28 20:11:55.463 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:26:55.513 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:38:19.617 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:38:19.872 Empty LocalHostName.
2008-04-28 20:38:19.901 Using localhost value of festivemyth
2008-04-28 20:38:19.990 New DB connection, total: 1
2008-04-28 20:38:19.999 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:38:20.001 Closing DB connection named 'DBManager0'
2008-04-28 20:38:20.003 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:38:20.070 New DB connection, total: 2
2008-04-28 20:38:20.201 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:38:20.224 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 20:38:25.404 New DB connection, total: 3
2008-04-28 20:38:25.452 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:38:25.551 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:38:25.583 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:38:25.723 New DB scheduler connection
2008-04-28 20:38:25.941 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:38:26.099 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 20:38:26.234 Main::Registering HttpStatus Extension
2008-04-28 20:38:26.313 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:38:26.463 Enabled verbose msgs:  important general
2008-04-28 20:38:26.534 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:38:29.051 Reschedule requested for id -1.
2008-04-28 20:38:29.119 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-04-28 20:38:29.129 Seem to be woken up by USER
2008-04-28 20:38:51.155 MainServer::HandleAnnounce Monitor
2008-04-28 20:38:51.159 adding: festivemyth as a client (events: 0)
2008-04-28 20:38:51.161 MainServer::HandleAnnounce Monitor
2008-04-28 20:38:51.162 adding: festivemyth as a client (events: 1)
2008-04-28 20:39:46.054 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:43:37.329 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:43:37.567 Empty LocalHostName.
2008-04-28 20:43:37.621 Using localhost value of festivemyth
2008-04-28 20:43:37.759 New DB connection, total: 1
2008-04-28 20:43:37.785 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:43:37.787 Closing DB connection named 'DBManager0'
2008-04-28 20:43:37.789 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:43:37.807 New DB connection, total: 2
2008-04-28 20:43:37.837 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:43:38.002 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 20:43:43.185 New DB connection, total: 3
2008-04-28 20:43:43.217 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:43:43.404 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:43:43.533 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:43:43.758 New DB scheduler connection
2008-04-28 20:43:43.916 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:43:44.184 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 20:43:44.243 Main::Registering HttpStatus Extension
2008-04-28 20:43:44.245 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:43:44.245 Enabled verbose msgs:  important general
2008-04-28 20:43:44.313 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:43:47.054 Reschedule requested for id -1.
2008-04-28 20:43:47.123 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-04-28 20:43:47.132 Seem to be woken up by USER
2008-04-28 20:44:13.103 MainServer::HandleAnnounce Monitor
2008-04-28 20:44:13.105 adding: festivemyth as a client (events: 0)
2008-04-28 20:44:13.107 MainServer::HandleAnnounce Monitor
2008-04-28 20:44:13.108 adding: festivemyth as a client (events: 1)
2008-04-28 20:45:04.057 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:47:24.613 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:47:24.809 Empty LocalHostName.
2008-04-28 20:47:24.879 Using localhost value of festivemyth
2008-04-28 20:47:25.010 New DB connection, total: 1
2008-04-28 20:47:25.042 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:47:25.045 Closing DB connection named 'DBManager0'
2008-04-28 20:47:25.046 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:47:25.073 New DB connection, total: 2
2008-04-28 20:47:25.214 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:47:25.236 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 20:47:30.303 New DB connection, total: 3
2008-04-28 20:47:30.350 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:47:30.606 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:47:30.850 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:47:31.108 New DB scheduler connection
2008-04-28 20:47:31.318 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:47:31.401 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 20:47:31.403 Main::Registering HttpStatus Extension
2008-04-28 20:47:31.404 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:47:31.405 Enabled verbose msgs:  important general
2008-04-28 20:47:31.462 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:47:34.345 Reschedule requested for id -1.
2008-04-28 20:47:34.413 Scheduled 0 items in 0.1 = 0.01 match + 0.06 place
2008-04-28 20:47:34.421 Seem to be woken up by USER
2008-04-28 20:48:23.495 MainServer::HandleAnnounce Monitor
2008-04-28 20:48:23.497 adding: festivemyth as a client (events: 0)
2008-04-28 20:48:23.500 MainServer::HandleAnnounce Monitor
2008-04-28 20:48:23.501 adding: festivemyth as a client (events: 1)
2008-04-28 20:48:51.347 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:52:46.576 MainServer::HandleAnnounce Monitor
2008-04-28 20:52:46.578 adding: festivemyth as a client (events: 0)
2008-04-28 20:52:46.580 MainServer::HandleAnnounce Monitor
2008-04-28 20:52:46.581 adding: festivemyth as a client (events: 1)
2008-04-28 20:52:46.589 MainServer::HandleAnnounce Playback
2008-04-28 20:52:46.596 adding: festivemyth as a client (events: 0)
2008-04-28 20:52:46.600 TVRec(1): Changing from None to WatchingLiveTV
2008-04-28 20:52:46.608 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:52:46.610 ChannelBase(1): IsTunable(Tuner 1,Please add) Failed to find channel in DB on input '1' 
2008-04-28 20:52:46.611 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:52:46.612 TVRec(1): HW Tuner: 1->1
2008-04-28 20:52:46.626 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:52:46.627 TVRec(1) Error: Failed to set channel to Please add.
2008-04-28 20:52:46.713 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Mon Apr 28 20:52:46 2008) endts(Mon Apr 28 20:52:46 2008)
             recstartts(Mon Apr 28 20:52:46 2008) recendts(Mon Apr 28 20:52:46 2008)
             title()
2008-04-28 20:52:46.717 New DB connection, total: 4
2008-04-28 20:52:46.722 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:52:47.844 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
2008-04-28 20:52:47.857 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-04-28 20:52:56.210 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:52:56.214 ChannelBase(1): IsTunable(Composite 1,Please add) Failed to find channel in DB on input '2' 
2008-04-28 20:52:56.215 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:52:56.216 TVRec(1): HW Tuner: 1->1
2008-04-28 20:52:56.447 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:52:56.449 TVRec(1) Error: Failed to set channel to Please add.
2008-04-28 20:52:56.465 Finished recording : channel 4294967295
2008-04-28 20:52:56.475 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Mon Apr 28 20:52:56 2008) endts(Mon Apr 28 20:52:56 2008)
             recstartts(Mon Apr 28 20:52:56 2008) recendts(Mon Apr 28 20:52:56 2008)
             title()
2008-04-28 20:52:57.551 Finished recording : channel 4294967295
2008-04-28 20:52:57.641 TVRec(1): RingBufferChanged()
2008-04-28 20:52:57.656 Finished recording : channel 4294967295
2008-04-28 20:52:57.731 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-04-28 20:52:58.010 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:52:58.020 Empty LocalHostName.
2008-04-28 20:52:58.021 Using localhost value of festivemyth
2008-04-28 20:52:58.045 New DB connection, total: 1
2008-04-28 20:52:58.056 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:52:58.059 Closing DB connection named 'DBManager0'
2008-04-28 20:52:58.062 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:52:58.066 New DB connection, total: 2
2008-04-28 20:52:58.068 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:52:58.076 Current Schema Version: 1214
2008-04-28 20:53:00.621 AFD: Opened codec 0x829ea30, id(MPEG2VIDEO) type(Video)
2008-04-28 20:53:00.630 AFD: codec MP2 has 2 channels
2008-04-28 20:53:00.631 AFD: Opened codec 0x829eeb0, id(MP2) type(Audio)
2008-04-28 20:53:00.796 Preview: Grabbed preview '/var/lib/mythtv/recordings/4294967295_20080428205246.mpg' 720x480@64s
2008-04-28 20:53:11.703 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:53:11.705 ChannelBase(1): IsTunable(Tuner 1,Please add) Failed to find channel in DB on input '1' 
2008-04-28 20:53:11.706 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:53:11.706 TVRec(1): HW Tuner: 1->1
2008-04-28 20:53:12.006 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:53:12.008 TVRec(1) Error: Failed to set channel to Please add.
2008-04-28 20:53:12.057 Finished recording : channel 4294967295
2008-04-28 20:53:12.067 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Mon Apr 28 20:53:12 2008) endts(Mon Apr 28 20:53:12 2008)
             recstartts(Mon Apr 28 20:53:12 2008) recendts(Mon Apr 28 20:53:12 2008)
             title()
2008-04-28 20:53:13.144 Finished recording : channel 4294967295
2008-04-28 20:53:13.273 TVRec(1): RingBufferChanged()
2008-04-28 20:53:13.289 Finished recording : channel 4294967295
2008-04-28 20:53:13.351 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-04-28 20:53:13.612 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:53:13.622 Empty LocalHostName.
2008-04-28 20:53:13.623 Using localhost value of festivemyth
2008-04-28 20:53:13.633 New DB connection, total: 1
2008-04-28 20:53:13.653 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:13.655 Closing DB connection named 'DBManager0'
2008-04-28 20:53:13.658 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:13.662 New DB connection, total: 2
2008-04-28 20:53:13.665 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:13.673 Current Schema Version: 1214
2008-04-28 20:53:16.205 AFD: Opened codec 0x829e9b0, id(MPEG2VIDEO) type(Video)
2008-04-28 20:53:16.210 AFD: codec MP2 has 2 channels
2008-04-28 20:53:16.212 AFD: Opened codec 0x829ee20, id(MP2) type(Audio)
2008-04-28 20:53:16.376 Preview: Grabbed preview '/var/lib/mythtv/recordings/4294967295_20080428205256.mpg' 720x480@64s
2008-04-28 20:53:18.472 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:53:18.476 ChannelBase(1): IsTunable(Composite 1,Please add) Failed to find channel in DB on input '2' 
2008-04-28 20:53:18.477 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:53:18.478 TVRec(1): HW Tuner: 1->1
2008-04-28 20:53:18.753 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:53:18.755 TVRec(1) Error: Failed to set channel to Please add.
2008-04-28 20:53:18.807 Finished recording : channel 4294967295
2008-04-28 20:53:18.815 TVRec(1) Error: GetProgramRingBufferForLiveTV()
			ProgramInfo is invalid.
ProgramInfo: channame() startts(Mon Apr 28 20:53:18 2008) endts(Mon Apr 28 20:53:18 2008)
             recstartts(Mon Apr 28 20:53:18 2008) recendts(Mon Apr 28 20:53:18 2008)
             title()
2008-04-28 20:53:19.893 Finished recording : channel 4294967295
2008-04-28 20:53:20.055 TVRec(1): RingBufferChanged()
2008-04-28 20:53:20.070 Finished recording : channel 4294967295
2008-04-28 20:53:20.131 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-04-28 20:53:20.373 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:53:20.378 Empty LocalHostName.
2008-04-28 20:53:20.379 Using localhost value of festivemyth
2008-04-28 20:53:20.392 New DB connection, total: 1
2008-04-28 20:53:20.411 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:20.414 Closing DB connection named 'DBManager0'
2008-04-28 20:53:20.417 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:20.421 New DB connection, total: 2
2008-04-28 20:53:20.423 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:53:20.430 Current Schema Version: 1214
2008-04-28 20:53:22.988 AFD: Opened codec 0x829e9b0, id(MPEG2VIDEO) type(Video)
2008-04-28 20:53:22.991 AFD: codec MP2 has 2 channels
2008-04-28 20:53:22.992 AFD: Opened codec 0x829ee20, id(MP2) type(Audio)
2008-04-28 20:53:23.157 Preview: Grabbed preview '/var/lib/mythtv/recordings/4294967295_20080428205312.mpg' 720x480@64s
2008-04-28 20:53:33.950 TVRec(1): Changing from WatchingLiveTV to None
2008-04-28 20:53:34.241 Finished recording : channel 4294967295
2008-04-28 20:54:51.460 Expiring 4 MBytes for 4294967295 @ Mon Apr 28 20:52:46 2008 => 
2008-04-28 20:54:51.463 Expiring 8 MBytes for 4294967295 @ Mon Apr 28 20:52:56 2008 => 
2008-04-28 20:54:51.467 Expiring 2 MBytes for 4294967295 @ Mon Apr 28 20:53:12 2008 => 
2008-04-28 20:56:51.474 Expiring 8 MBytes for 4294967295 @ Mon Apr 28 20:53:18 2008 => 
2008-04-28 20:59:00.238 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-28 20:59:00.277 Empty LocalHostName.
2008-04-28 20:59:00.278 Using localhost value of festivemyth
2008-04-28 20:59:00.289 New DB connection, total: 1
2008-04-28 20:59:00.305 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:59:00.307 Closing DB connection named 'DBManager0'
2008-04-28 20:59:00.309 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:59:00.312 New DB connection, total: 2
2008-04-28 20:59:00.314 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:59:00.329 Current Schema Version: 1214
Starting up as the master server.
2008-04-28 20:59:00.363 New DB connection, total: 3
2008-04-28 20:59:00.364 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:59:00.375 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:59:00.376 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
2008-04-28 20:59:00.509 New DB scheduler connection
2008-04-28 20:59:00.511 Connected to database 'mythconverg' at host: localhost
2008-04-28 20:59:00.541 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-04-28 20:59:00.542 Main::Registering HttpStatus Extension
2008-04-28 20:59:00.542 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-04-28 20:59:00.543 Enabled verbose msgs:  important general
2008-04-28 20:59:00.547 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-28 20:59:02.711 MainServer::HandleAnnounce Monitor
2008-04-28 20:59:02.714 adding: festivemyth as a client (events: 0)
2008-04-28 20:59:02.716 MainServer::HandleAnnounce Monitor
2008-04-28 20:59:02.717 adding: festivemyth as a client (events: 1)
2008-04-28 20:59:03.518 Reschedule requested for id -1.
2008-04-28 20:59:03.554 Scheduled 0 items in 0.0 = 0.01 match + 0.03 place
2008-04-28 20:59:03.566 Seem to be woken up by USER
2008-04-28 21:00:20.523 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

```

---

### Post by majoridiot on 2008-04-29
you have a TON of problems with your setup...

the things that jump out to address first are the errors about theme and fonts, as this will
certainly mess up your display:


> **thoraxe said:**
> frontend.log
```
2008-04-28 20:52:23.689 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:52:23.689 The theme (glass-wide) is missing a themeinfo.xml file
2008-04-28 20:52:23.920 Unable to parse themeinfo.xml for glass-wide
2008-04-28 20:52:23.920 The theme (glass-wide) is missing a themeinfo.xml file

2008-04-28 20:52:25.772 Specified base font 'medium' does not exist for font small
2008-04-28 20:52:25.772 Specified base font 'medium' does not exist for font medium
2008-04-28 20:52:25.772 Specified base font 'medium' does not exist for font large
2008-04-28 20:52:25.774 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-04-28 20:52:25.841 Loading from: /usr/share/mythtv/themes/default/base.xml
```


you also have audio issues:

> **thoraxe said:**
> ```
2008-04-28 20:52:49.460 AFD: Opened codec 0x8352ce0, id(MPEG2VIDEO) type(Video)
2008-04-28 20:52:49.461 AFD: codec MP2 has 2 channels
2008-04-28 20:52:49.461 AFD: Opened codec 0x838e8b0, id(MP2) type(Audio)
2008-04-28 20:52:49.548 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-28 20:52:49.549 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-04-28 20:52:49.614 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
...

2008-04-28 20:53:01.525 WriteAudio: buffer underrun
2008-04-28 20:53:02.100 WriteAudio: buffer underrun
2008-04-28 20:53:02.685 WriteAudio: buffer underrun
2008-04-28 20:53:03.389 WriteAudio: buffer underrun
2008-04-28 20:53:03.983 WriteAudio: buffer underrun
2008-04-28 20:53:04.688 WriteAudio: buffer underrun
2008-04-28 20:53:05.327 WriteAudio: buffer underrun
2008-04-28 20:53:05.984 WriteAudio: buffer underrun
2008-04-28 20:53:06.556 WriteAudio: buffer underrun
2008-04-28 20:53:07.196 WriteAudio: buffer underrun... etc.
```

and then there's this as well:
> **thoraxe said:**
> ```
2008-04-28 20:52:49.735 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-04-28 20:52:49.736 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-04-28 20:52:49.736 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x83961b8) visual(0x8399728) 
                        XJ_depth(24) WxH(640x480) bpl(1920)
2008-04-28 20:52:49.736 VideoOutputXv Error: Failed to create X buffers.
2008-04-28 20:52:50.048 Couldn't load deinterlace filter 
2008-04-28 20:52:50.059 OSD Theme Dimensions W: 640 H: 480
2008-04-28 20:52:51.088 TV: Changing from None to WatchingLiveTV
2008-04-28 20:52:51.146 Realtime priority would require SUID as root.
2008-04-28 20:52:51.160 Video timing method: USleep with busy wait
[/code

and it looks like your tuner is not properly configured, since this is all over your backend logs:

> **thoraxe said:**
> [code]2008-04-28 20:59:00.375 GetChannelData() failed because it could not
			find channel number 'Please add' in DB for source '1'.
2008-04-28 20:59:00.376 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
			and we failed to find any suitible channels on any input.
```

i would:

check for and apply the latest mythbuntu updates

try watching livetv again and then check your logs to see if the same errors exist.  if so:

fix the theme issues

fix your sound issues

check the settings for the ati restricted video driver

delete the current tuner and then reconfigure it in mythtv-setup steps 2, 3 (if necessary) and 4.

run mythfilldatabase after setting up the tuner and see how much further along you are by looking
for errors in your logs.

---

