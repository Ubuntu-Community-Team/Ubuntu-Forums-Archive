---
title: "mythtv - no tv in frontend"
date: 2008-09-24
forum: Mythbuntu
---

### Post by karl242 on 2008-09-24
Hello there,

I have set up my old computer with mythbuntu and I try to watch tv. On Kaffeine everything works fine - and in "mythtv backend setup" there are also channels found. But when I try to watch tv in mythtv frontend, the screen turns black for about a second and after that the main screen returns again.
My DVB-S-Card is a Technisat Skystar 2 (rev 2.3)

In /var/log/mythtv I got some error messages in the log files

here is the log for mythbackend.log
```
2008-09-24 20:59:05.914 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-09-24 20:59:26.889 MainServer::HandleAnnounce Monitor
2008-09-24 20:59:26.892 adding: myth-desktop as a client (events: 0)
2008-09-24 20:59:26.894 MainServer::HandleAnnounce Monitor
2008-09-24 20:59:26.895 adding: myth-desktop as a client (events: 1)
2008-09-24 20:59:26.900 MainServer::HandleAnnounce Playback
2008-09-24 20:59:26.902 adding: myth-desktop as a client (events: 0)
2008-09-24 20:59:27.100 TVRec(1): Changing from None to WatchingLiveTV
2008-09-24 20:59:27.114 TVRec(1): HW Tuner: 1->1
2008-09-24 20:59:28.507 TFW, Error: Opening file '/home/myth/tv/2793_20080924205927.mpg'.
			eno: Permission denied (13)
2008-09-24 20:59:28.511 TVRec(1) Error: RingBuffer '/home/myth/tv/2793_20080924205927.mpg' not open...
2008-09-24 20:59:28.512 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-09-24 20:59:28.513 TVRec(1) Error: Failed to create RingBuffer 1
2008-09-24 20:59:28.513 TVRec(1): Changing from WatchingLiveTV to None
2008-09-24 20:59:28.658 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-09-24 21:00:29.506 PID 0x1ff status: Unknown
2008-09-24 21:00:31.358 PID 0x203 status: Encrypted
2008-09-24 21:00:33.292 PID 0x200 status: Encrypted
2008-09-24 21:00:33.300 PID 0x201 status: Encrypted
2008-09-24 21:00:34.659 PID 0x1ff status: Encrypted

```

and mythfrontend.log
```
Starting mythfrontend.real..
2008-09-24 20:59:18.957 New DB connection, total: 2
2008-09-24 20:59:18.958 Connected to database 'mythconverg' at host: localhost
2008-09-24 20:59:18.963 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-09-24 20:59:18.963 Enabled verbose msgs:  important general
2008-09-24 20:59:19.124 Unable to parse themeinfo.xml for glass-wide
2008-09-24 20:59:19.124 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-24 20:59:19.381 Unable to parse themeinfo.xml for glass-wide
2008-09-24 20:59:19.381 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-24 20:59:20.799 Primary screen 0.
2008-09-24 20:59:20.800 Using screen 0, 1024x768 at 0,0
2008-09-24 20:59:20.804 Switching to square mode (Mythbuntu-8.04)
2008-09-24 20:59:20.837 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-09-24 20:59:20.838 lirc_init failed for mythtv, see preceding messages
2008-09-24 20:59:20.838 JoystickMenuClient Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font clock
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font small
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font medium
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font large
2008-09-24 20:59:22.988 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-09-24 20:59:23.128 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-09-24 20:59:23.216 Registering Internal as a media playback plugin.
2008-09-24 20:59:23.303 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-09-24 20:59:23.364 Failed to run 'cdrecord --scanbus'
2008-09-24 20:59:23.370 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-09-24 20:59:23.375 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-09-24 20:59:23.448 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-09-24 20:59:23.673 NetworkControl: Listening for remote connections on port 6546
2008-09-24 20:59:26.887 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-09-24 20:59:26.888 Using protocol version 40
2008-09-24 20:59:26.899 TV: Attempting to change from None to WatchingLiveTV
2008-09-24 20:59:26.900 Using protocol version 40
2008-09-24 20:59:28.656 GetEntryAt(-1) failed.
2008-09-24 20:59:28.658 EntryToProgram(0@Do Jan 1 01:00:00 1970) failed to get pginfo
2008-09-24 20:59:28.659 TV Error: LiveTV not successfully started
2008-09-24 20:59:28.659 TV Error: LiveTV not successfully started
2008-09-24 20:59:28.755 TV: Deleting TV Chain in destructor
2008-09-24 20:59:28.775 DPMS Deactivated 
2008-09-24 20:59:28.776 DPMS Reactivated.
2008-09-24 20:59:30.792 Deleting UPnP client...

```

So it seems the error is in the permissions - as mythbackend.log says ... but how do I avoid this? I am not so firm with linux.

I hope someone can help me ...

One thing left - perhaps it is important ... I can even see the channels in the frontend when I try to schedule a recording.

thanks,
karl

---

### Post by tgm4883 on 2008-09-24
> **karl242 said:**
> Hello there,

I have set up my old computer with mythbuntu and I try to watch tv. On Kaffeine everything works fine - and in "mythtv backend setup" there are also channels found. But when I try to watch tv in mythtv frontend, the screen turns black for about a second and after that the main screen returns again.
My DVB-S-Card is a Technisat Skystar 2 (rev 2.3)

In /var/log/mythtv I got some error messages in the log files

here is the log for mythbackend.log
```
2008-09-24 20:59:05.914 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-09-24 20:59:26.889 MainServer::HandleAnnounce Monitor
2008-09-24 20:59:26.892 adding: myth-desktop as a client (events: 0)
2008-09-24 20:59:26.894 MainServer::HandleAnnounce Monitor
2008-09-24 20:59:26.895 adding: myth-desktop as a client (events: 1)
2008-09-24 20:59:26.900 MainServer::HandleAnnounce Playback
2008-09-24 20:59:26.902 adding: myth-desktop as a client (events: 0)
2008-09-24 20:59:27.100 TVRec(1): Changing from None to WatchingLiveTV
2008-09-24 20:59:27.114 TVRec(1): HW Tuner: 1->1
2008-09-24 20:59:28.507 TFW, Error: Opening file '/home/myth/tv/2793_20080924205927.mpg'.
			eno: Permission denied (13)
2008-09-24 20:59:28.511 TVRec(1) Error: RingBuffer '/home/myth/tv/2793_20080924205927.mpg' not open...
2008-09-24 20:59:28.512 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-09-24 20:59:28.513 TVRec(1) Error: Failed to create RingBuffer 1
2008-09-24 20:59:28.513 TVRec(1): Changing from WatchingLiveTV to None
2008-09-24 20:59:28.658 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-09-24 21:00:29.506 PID 0x1ff status: Unknown
2008-09-24 21:00:31.358 PID 0x203 status: Encrypted
2008-09-24 21:00:33.292 PID 0x200 status: Encrypted
2008-09-24 21:00:33.300 PID 0x201 status: Encrypted
2008-09-24 21:00:34.659 PID 0x1ff status: Encrypted

```

and mythfrontend.log
```
Starting mythfrontend.real..
2008-09-24 20:59:18.957 New DB connection, total: 2
2008-09-24 20:59:18.958 Connected to database 'mythconverg' at host: localhost
2008-09-24 20:59:18.963 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-09-24 20:59:18.963 Enabled verbose msgs:  important general
2008-09-24 20:59:19.124 Unable to parse themeinfo.xml for glass-wide
2008-09-24 20:59:19.124 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-24 20:59:19.381 Unable to parse themeinfo.xml for glass-wide
2008-09-24 20:59:19.381 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-24 20:59:20.799 Primary screen 0.
2008-09-24 20:59:20.800 Using screen 0, 1024x768 at 0,0
2008-09-24 20:59:20.804 Switching to square mode (Mythbuntu-8.04)
2008-09-24 20:59:20.837 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-09-24 20:59:20.838 lirc_init failed for mythtv, see preceding messages
2008-09-24 20:59:20.838 JoystickMenuClient Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font clock
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font small
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font medium
2008-09-24 20:59:22.983 Specified base font 'medium' does not exist for font large
2008-09-24 20:59:22.988 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-09-24 20:59:23.128 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-09-24 20:59:23.216 Registering Internal as a media playback plugin.
2008-09-24 20:59:23.303 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-09-24 20:59:23.364 Failed to run 'cdrecord --scanbus'
2008-09-24 20:59:23.370 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-09-24 20:59:23.375 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-09-24 20:59:23.448 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-09-24 20:59:23.673 NetworkControl: Listening for remote connections on port 6546
2008-09-24 20:59:26.887 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-09-24 20:59:26.888 Using protocol version 40
2008-09-24 20:59:26.899 TV: Attempting to change from None to WatchingLiveTV
2008-09-24 20:59:26.900 Using protocol version 40
2008-09-24 20:59:28.656 GetEntryAt(-1) failed.
2008-09-24 20:59:28.658 EntryToProgram(0@Do Jan 1 01:00:00 1970) failed to get pginfo
2008-09-24 20:59:28.659 TV Error: LiveTV not successfully started
2008-09-24 20:59:28.659 TV Error: LiveTV not successfully started
2008-09-24 20:59:28.755 TV: Deleting TV Chain in destructor
2008-09-24 20:59:28.775 DPMS Deactivated 
2008-09-24 20:59:28.776 DPMS Reactivated.
2008-09-24 20:59:30.792 Deleting UPnP client...

```

So it seems the error is in the permissions - as mythbackend.log says ... but how do I avoid this? I am not so firm with linux.

I hope someone can help me ...

One thing left - perhaps it is important ... I can even see the channels in the frontend when I try to schedule a recording.

thanks,
karl

Move your recording directory (storage directory) out of the home directory

---

### Post by karl242 on 2008-09-24
that's it! thank you!

---

