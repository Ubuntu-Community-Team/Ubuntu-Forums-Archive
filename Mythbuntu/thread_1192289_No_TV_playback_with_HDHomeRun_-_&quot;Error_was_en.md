---
title: "No TV playback with HDHomeRun - &quot;Error was encountered while displaying video&quot;"
date: 2009-06-19
forum: Mythbuntu
---

### Post by gungfujoe on 2009-06-19
I'm using Mythbuntu 9.04 x86 with an HDHomeRun and an ATI Radeon 3450-based video card.  After finally getting Mythbackend to recognize my HDHomeRun (have to restart the backend, since it loads before the system gets an IP address), I restarted the frontend, hit "Watch TV," and got a blank screen, followed a few seconds later by "Error was encountered while displaying video."

Looking at the log file (appended below), it looks as if the backend doesn't have permission to work with the mpg files it needs to create to display a TV feed.  I restarted the backend with "sudo /etc/init.d/mythtv-backend restart", and looking at the process list (ps -A u | grep myth), I see that the backend is indeed running under the "mythtv" user, and not under my own login.  And when I look in /var/lib/mythtv/recordings, I see a handful of 0-byte MPG files owned by mythtv.  Mythtv also owns the directory, which has 775 (drwxrwsr-x) permissions.

What gives?  I was using MythTV 8.10 on here before, and while I had a number of serious problems preventing me from using it (I replaced the motherboard and installed 9.04 from scratch), I never encountered anything like this.

```
Starting up as the master server.
2009-06-19 22:58:34.931 HDHRChan(ffffffff/0): device found at address 192.168.1.11
2009-06-19 22:58:34.936 New DB connection, total: 3
2009-06-19 22:58:34.942 Connected to database 'mythconverg' at host: localhost
2009-06-19 22:58:35.027 New DB scheduler connection
2009-06-19 22:58:35.028 Connected to database 'mythconverg' at host: localhost
2009-06-19 22:58:35.035 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-06-19 22:58:35.036 Main::Registering HttpStatus Extension
2009-06-19 22:58:35.044 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-06-19 22:58:35.050 Enabled verbose msgs:  important general
2009-06-19 22:58:35.059 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-19 22:58:38.031 Reschedule requested for id -1.
2009-06-19 22:58:38.044 Scheduled 0 items in 0.0 = 0.01 match + 0.01 place
2009-06-19 22:58:38.047 Seem to be woken up by USER
2009-06-19 22:58:55.031 Expiring 0 MBytes for 2080 @ Fri Jun 19 20:59:53 2009 => Unknown
2009-06-19 22:58:55.036 Expiring 0 MBytes for 2080 @ Fri Jun 19 20:59:56 2009 => Unknown
2009-06-19 22:58:55.038 Expiring 0 MBytes for 2080 @ Fri Jun 19 21:00:07 2009 => Unknown
2009-06-19 22:58:55.042 Expiring 0 MBytes for 2080 @ Fri Jun 19 21:00:09 2009 => Unknown
2009-06-19 22:58:58.045 Error deleting '/var/lib/mythtv/recordings/2080_20090619205953.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 22:58:58.049 Delete Error '/var/lib/mythtv/recordings/2080_20090619205953.mpg'
			eno: Permission denied (13)
2009-06-19 22:58:58.050 Error deleting file: /var/lib/mythtv/recordings/2080_20090619205953.mpg. Keeping metadata in database.
2009-06-19 22:58:58.054 Error deleting '/var/lib/mythtv/recordings/2080_20090619205956.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 22:58:58.059 Delete Error '/var/lib/mythtv/recordings/2080_20090619205956.mpg'
			eno: Permission denied (13)
2009-06-19 22:58:58.062 Error deleting file: /var/lib/mythtv/recordings/2080_20090619205956.mpg. Keeping metadata in database.
2009-06-19 22:58:58.070 Error deleting '/var/lib/mythtv/recordings/2080_20090619210007.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 22:58:58.075 Delete Error '/var/lib/mythtv/recordings/2080_20090619210007.mpg'
			eno: Permission denied (13)
2009-06-19 22:58:58.079 Error deleting file: /var/lib/mythtv/recordings/2080_20090619210007.mpg. Keeping metadata in database.
2009-06-19 22:58:58.086 Error deleting '/var/lib/mythtv/recordings/2080_20090619210009.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 22:58:58.091 Delete Error '/var/lib/mythtv/recordings/2080_20090619210009.mpg'
			eno: Permission denied (13)
2009-06-19 22:58:58.094 Error deleting file: /var/lib/mythtv/recordings/2080_20090619210009.mpg. Keeping metadata in database.
2009-06-19 22:59:30.225 MainServer::HandleAnnounce Monitor
2009-06-19 22:59:30.227 adding: HTPC as a client (events: 0)
2009-06-19 22:59:30.228 MainServer::HandleAnnounce Monitor
2009-06-19 22:59:30.228 adding: HTPC as a client (events: 1)
2009-06-19 22:59:30.238 MainServer::HandleAnnounce Playback
2009-06-19 22:59:30.267 adding: HTPC as a client (events: 0)
2009-06-19 22:59:30.317 TVRec(1): Changing from None to WatchingLiveTV
2009-06-19 22:59:30.320 TVRec(1): HW Tuner: 1->1
2009-06-19 22:59:31.371 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-19 22:59:32.492 Finished recording Unknown: channel 2080
2009-06-19 22:59:33.514 Finished recording Unknown: channel 2080
2009-06-19 22:59:33.535 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-19 22:59:33.578 Using runtime prefix = /usr
2009-06-19 22:59:33.583 Empty LocalHostName.
2009-06-19 22:59:33.584 Using localhost value of HTPC
2009-06-19 22:59:33.588 New DB connection, total: 1
2009-06-19 22:59:33.592 Connected to database 'mythconverg' at host: localhost
2009-06-19 22:59:33.593 Closing DB connection named 'DBManager0'
2009-06-19 22:59:33.595 Connected to database 'mythconverg' at host: localhost
2009-06-19 22:59:33.601 New DB connection, total: 2
2009-06-19 22:59:33.605 Connected to database 'mythconverg' at host: localhost
2009-06-19 22:59:33.646 Current Schema Version: 1214
2009-06-19 22:59:33.650 Preview Error: Previewer file '/var/lib/mythtv/recordings/2080_20090619225930.mpg' is not valid.
2009-06-19 22:59:33.670 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2080_20090619225930.mpg'
2009-06-19 22:59:33.677 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/2080_20090619225930.mpg.png) exists: 0 readable: 0 size: 0
2009-06-19 22:59:40.048 TVRec(1): Changing from WatchingLiveTV to None
2009-06-19 22:59:41.044 Finished recording Unknown: channel 2080
2009-06-19 22:59:55.044 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-19 23:00:55.053 Expiring 0 MBytes for 2080 @ Fri Jun 19 20:59:53 2009 => Unknown
2009-06-19 23:00:55.054 Expiring 0 MBytes for 2080 @ Fri Jun 19 20:59:56 2009 => Unknown
2009-06-19 23:00:55.057 Expiring 0 MBytes for 2080 @ Fri Jun 19 21:00:07 2009 => Unknown
2009-06-19 23:00:55.059 Expiring 0 MBytes for 2080 @ Fri Jun 19 21:00:09 2009 => Unknown
2009-06-19 23:00:58.060 Error deleting '/var/lib/mythtv/recordings/2080_20090619205953.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 23:00:58.064 Delete Error '/var/lib/mythtv/recordings/2080_20090619205953.mpg'
			eno: Permission denied (13)
2009-06-19 23:00:58.077 Error deleting file: /var/lib/mythtv/recordings/2080_20090619205953.mpg. Keeping metadata in database.
2009-06-19 23:00:58.082 Error deleting '/var/lib/mythtv/recordings/2080_20090619205956.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 23:00:58.086 Delete Error '/var/lib/mythtv/recordings/2080_20090619205956.mpg'
			eno: Permission denied (13)
2009-06-19 23:00:58.095 Error deleting file: /var/lib/mythtv/recordings/2080_20090619205956.mpg. Keeping metadata in database.
2009-06-19 23:00:58.102 Error deleting '/var/lib/mythtv/recordings/2080_20090619210007.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 23:00:58.107 Delete Error '/var/lib/mythtv/recordings/2080_20090619210007.mpg'
			eno: Permission denied (13)
2009-06-19 23:00:58.114 Error deleting file: /var/lib/mythtv/recordings/2080_20090619210007.mpg. Keeping metadata in database.
2009-06-19 23:00:58.126 Error deleting '/var/lib/mythtv/recordings/2080_20090619210009.mpg' could not open 
			eno: Permission denied (13)
2009-06-19 23:00:58.136 Delete Error '/var/lib/mythtv/recordings/2080_20090619210009.mpg'
			eno: Permission denied (13)
2009-06-19 23:00:58.145 Error deleting file: /var/lib/mythtv/recordings/2080_20090619210009.mpg. Keeping metadata in database.
2009-06-19 23:01:10.231 HDHRChan(ffffffff/0): device found at address 192.168.1.11
```

---

### Post by AboveTheLogic on 2009-06-20
can you give us your output for this:

```
ls -la /var/lib/mythtv
```

and maybe this:

```
ls -la /var/lib/mythtv/recordings
```

FYI this is how mine works:
```
~$ ls -la /var/lib/mythtv/
total 8
drwxr-xr-x  4 root   root     36 2009-05-16 15:45 .
drwxr-xr-x 60 root   root   4096 2009-06-19 07:34 ..
drwxrwsr-x  2 mythtv mythtv 4096 2009-06-19 20:07 recordings
drwxrwxr-x  2 mythtv mythtv    6 2008-10-15 22:58 videos

```

---

### Post by gungfujoe on 2009-06-20
I had deleted the zero-byte mpg files last time, so I tried again this morning (same results).  Here are the directory listings you asked for (I've got "ll" aliased to "ls -laF", hence the trailing slashes on directories):

```
~$ ll /var/lib/mythtv/
total 12
drwxr-xr-x  7 root   root     77 2009-04-20 11:21 ./
drwxr-xr-x 58 root   root   4096 2009-06-15 18:31 ../
drwxrwsr-x 60 mythtv mythtv 4096 2009-06-19 20:02 music/
drwxrwxr-x  2 mythtv mythtv    6 2009-04-10 02:16 pictures/
drwxr-xr-x  2 mythtv mythtv    6 2009-04-10 02:16 posters/
drwxrwsr-x  2 mythtv mythtv   66 2009-06-20 08:45 recordings/
drwxrwxr-x  2 mythtv mythtv 4096 2009-06-19 22:49 videos/

~$ ll /var/lib/mythtv/recordings/
total 0
drwxrwsr-x 2 mythtv mythtv 66 2009-06-20 08:45 ./
drwxr-xr-x 7 root   root   77 2009-04-20 11:21 ../
-rw-r--r-- 1 mythtv mythtv  0 2009-06-20 08:45 2080_20090620084503.mpg
-rw-r--r-- 1 mythtv mythtv  0 2009-06-20 08:45 2080_20090620084505.mpg
```

And here's the new backend log

```
Starting up as the master server.
2009-06-20 08:42:49.275 HDHRChan(ffffffff/0): device found at address 192.168.1.11
2009-06-20 08:42:49.277 New DB connection, total: 3
2009-06-20 08:42:49.280 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:42:49.369 New DB scheduler connection
2009-06-20 08:42:49.370 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:42:49.378 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-06-20 08:42:49.380 Main::Registering HttpStatus Extension
2009-06-20 08:42:49.384 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-06-20 08:42:49.388 Enabled verbose msgs:  important general
2009-06-20 08:42:49.392 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-20 08:42:52.373 Reschedule requested for id -1.
2009-06-20 08:42:52.530 Scheduled 0 items in 0.2 = 0.15 match + 0.01 place
2009-06-20 08:42:52.598 Seem to be woken up by USER
2009-06-20 08:44:09.375 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-06-20 08:44:34.557 HDHRChan(ffffffff/0): device found at address 192.168.1.11
2009-06-20 08:45:01.962 MainServer::HandleAnnounce Monitor
2009-06-20 08:45:01.966 adding: HTPC as a client (events: 0)
2009-06-20 08:45:01.972 MainServer::HandleAnnounce Monitor
2009-06-20 08:45:01.973 adding: HTPC as a client (events: 1)
2009-06-20 08:45:01.975 MainServer::HandleAnnounce Playback
2009-06-20 08:45:01.996 adding: HTPC as a client (events: 0)
2009-06-20 08:45:02.053 TVRec(1): Changing from None to WatchingLiveTV
2009-06-20 08:45:02.058 TVRec(1): HW Tuner: 1->1
2009-06-20 08:45:04.135 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-20 08:45:05.237 Finished recording Unknown: channel 2080
2009-06-20 08:45:06.256 Finished recording Unknown: channel 2080
2009-06-20 08:45:06.273 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-20 08:45:06.321 Using runtime prefix = /usr
2009-06-20 08:45:06.325 Empty LocalHostName.
2009-06-20 08:45:06.325 Using localhost value of HTPC
2009-06-20 08:45:06.330 New DB connection, total: 1
2009-06-20 08:45:06.334 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:45:06.335 Closing DB connection named 'DBManager0'
2009-06-20 08:45:06.336 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:45:06.340 New DB connection, total: 2
2009-06-20 08:45:06.344 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:45:06.349 Current Schema Version: 1214
2009-06-20 08:45:06.397 Preview Error: Previewer file '/var/lib/mythtv/recordings/2080_200906200845
03.mpg' is not valid.
2009-06-20 08:45:06.399 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2080_20090
620084503.mpg'
2009-06-20 08:45:06.403 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/2080_20090620084503.mpg.png) exists: 0 
readable: 0 size: 0
2009-06-20 08:45:12.780 TVRec(1): Changing from WatchingLiveTV to None
2009-06-20 08:45:13.782 Finished recording Unknown: channel 2080
2009-06-20 08:46:09.388 Expiring 0 MBytes for 2080 @ Sat Jun 20 08:45:03 2009 => Unknown
2009-06-20 08:46:09.392 Expiring 0 MBytes for 2080 @ Sat Jun 20 08:45:05 2009 => Unknown
2009-06-20 08:46:16.402 New DB connection, total: 4
2009-06-20 08:46:16.409 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:46:43.049 HDHRChan(ffffffff/0): device found at address 192.168.1.11
```

Here;s the frontend log for the same time period:

```
Starting mythfrontend.real..
2009-06-20 08:44:54.655 New DB connection, total: 2
2009-06-20 08:44:54.655 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:44:54.656 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-06-20 08:44:54.656 Enabled verbose msgs:  important general
2009-06-20 08:44:57.566 No theme dir: /home/eharris/.mythtv/themes/ProjectGrayhem-wide
2009-06-20 08:44:57.567 Total desktop dim: 1920x1080, over 1 screen[s].
2009-06-20 08:44:57.567 Primary screen 0.
2009-06-20 08:44:57.567 Using screen 0, 1920x1080 at 0,0
2009-06-20 08:44:57.568 No theme dir: /home/eharris/.mythtv/themes/ProjectGrayhem-wide
2009-06-20 08:44:57.568 Switching to wide mode (ProjectGrayhem-wide)
2009-06-20 08:44:57.660 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-06-20 08:44:57.660 lirc_init failed for mythtv, see preceding messages
2009-06-20 08:44:57.660 JoystickMenuClient Error: Joystick disabled - Failed to read /home/eharris/
.mythtv/joystickmenurc
2009-06-20 08:44:58.587 Specified base font 'medium' does not exist for font clock
2009-06-20 08:44:58.587 Specified base font 'medium' does not exist for font small
2009-06-20 08:44:58.587 Specified base font 'medium' does not exist for font medium
2009-06-20 08:44:58.587 Specified base font 'medium' does not exist for font large
2009-06-20 08:44:58.587 Loading from: /usr/share/mythtv/themes/ProjectGrayhem-wide/base.xml
2009-06-20 08:44:58.648 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-06-20 08:44:58.668 Registering Internal as a media playback plugin.
2009-06-20 08:44:58.717 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-06-20 08:44:58.728 Failed to run 'cdrecord --scanbus'
2009-06-20 08:44:58.731 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-06-20 08:44:58.735 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-06-20 08:44:58.749 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-06-20 08:44:58.773 Starting update of NWS-XML
2009-06-20 08:44:58.777 Starting update of NDFD-6_day
2009-06-20 08:44:58.789 Starting update of NDFD-18_Hour
2009-06-20 08:44:58.795 No theme dir: /home/eharris/.mythtv/themes/ProjectGrayhem-wide
2009-06-20 08:44:59.827 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home
/eharris/.mythtv/MythWeather/NWS-XML KDCA has exited
2009-06-20 08:44:59.827 wind_gust::
2009-06-20 08:44:59.827 nrecoverable error parsing script output 
2009-06-20 08:45:00.797 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home
/eharris/.mythtv/MythWeather/NDFD-18_Hour +38.50,-077.02 has exited
2009-06-20 08:45:00.958 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/e
harris/.mythtv/MythWeather/NDFD-6_day +38.50,-077.02 has exited
2009-06-20 08:45:01.961 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-06-20 08:45:01.962 Using protocol version 40
2009-06-20 08:45:01.975 TV: Attempting to change from None to WatchingLiveTV
2009-06-20 08:45:01.975 Using protocol version 40
2009-06-20 08:45:04.174 New DB connection, total: 3
2009-06-20 08:45:04.174 Connected to database 'mythconverg' at host: localhost
2009-06-20 08:45:04.181 NVP: Disabling Audio, params(-1,2,44100)
2009-06-20 08:45:04.196 DPMS Deactivated 
2009-06-20 08:45:04.257 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2009-06-20 08:45:04.292 OSD Theme Dimensions W: 640 H: 480
2009-06-20 08:45:04.557 TV: Changing from None to WatchingLiveTV
2009-06-20 08:45:04.558 Realtime priority would require SUID as root.
2009-06-20 08:45:04.560 Video timing method: USleep with busy wait
2009-06-20 08:45:12.778 RingBuf(/var/lib/mythtv/recordings/2080_20090620084505.mpg): Invalid file (
fd -1) when opening '/var/lib/mythtv/recordings/2080_20090620084505.mpg'.
2009-06-20 08:45:12.778 NVP, Error: JumpToProgram's OpenFile failed.
2009-06-20 08:45:12.778 NVP, Error: Unknown error, exiting decoder
2009-06-20 08:45:12.779 TV: Attempting to change from WatchingLiveTV to None
2009-06-20 08:45:14.250 TV: Changing from WatchingLiveTV to None
2009-06-20 08:45:14.338 DPMS Reactivated.
2009-06-20 08:45:17.811 Deleting UPnP client...
```

---

### Post by AboveTheLogic on 2009-06-20
hmm, nothing inparticualr stands out to me about your permissions, they do look fine (just as you suggested in your original post)

but also, in your second logs, there are no permission denied errors, so I suppose that makes sense

I can't think of anything else off hand, hopefully someone with more experience than I can chime in...

---

### Post by gungfujoe on 2009-06-25
So nobody has any idea why this error might occur?  I didn't mention it before, but the "Error was encountered while displaying video" message appears within the MythTV theme.  It's not some random error popped onto the screen by some app, the OS, or some driver.  It's an error displayed by MythTV within the display theme.

To say that I'm getting frustrated would be an understatement.  I've had all of this hardware for over 6 months now, and so far, I can't do any more with it than I did with my old Win2K system that was hooked up to my old TV.  That is, I can surf the web and I can play videos that I've downloaded and saved to the hard drive.  No TV, no DVR, nothing. :(

---

### Post by Mister.Vash on 2009-06-27
The line that catches my eye is from the frontend log.
> 2009-06-20 08:45:12.778 RingBuf(/var/lib/mythtv/recordings/2080_20090620084505.mpg): Invalid file (
fd -1) when opening '/var/lib/mythtv/recordings/2080_20090620084505.mpg'.

I did a quick search, didn't really find anything too helpful on that message, found the following thread with the same message but not sure if it's really a solution.
[http://www.mythtvtalk.com/forum/installation-issues/5406-help-ringbuf-invalid-file-fd-1-error.html](http://www.mythtvtalk.com/forum/installation-issues/5406-help-ringbuf-invalid-file-fd-1-error.html)

Have you tried testing the hdhomerun with vlc, or another similar program, just to make sure that everything is working correctly with the  hdhomerun?  Doing so should at least rule that out as an issue - here's a link to a quick way to use them together:
[http://www.silicondust.com/forum/viewtopic.php?t=1924](http://www.silicondust.com/forum/viewtopic.php?t=1924)


If that looks good, then I would recommend that on both the frontend and the backend, you increase the verbosity of the logging, that may help provide additional details about what is going on.  Also, if you can't find any better information about that specific Ringbuf error, I would suggest posting to the mythtv-users list:
[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)

---

### Post by gungfujoe on 2009-06-27
> **Mister.Vash said:**
> I did a quick search, didn't really find anything too helpful on that message, found the following thread with the same message but not sure if it's really a solution.
[http://www.mythtvtalk.com/forum/installation-issues/5406-help-ringbuf-invalid-file-fd-1-error.html](http://www.mythtvtalk.com/forum/installation-issues/5406-help-ringbuf-invalid-file-fd-1-error.html)
No, that's not really a solution.  After not finding a solution, the guy bought a new video card.  In my case, I was using another motherboard with Mythbuntu 8.10, and while I never got it working fully, I DID get live TV to display (with no audio - audio driver issues, along with extreme RAM finickiness were why I found another motherboard.  Audio worked "out of the box" with this motherboard, and it works with the RAM I want to use in it).

So I don't buy the claim that it's the video card.  This same video card worked with live TV just a little while ago, on a different motherboard, on a different Mythbuntu install.

> **Mister.Vash said:**
> Have you tried testing the hdhomerun with vlc, or another similar program, just to make sure that everything is working correctly with the  hdhomerun?
Yes.  I actually can't get the instructions you linked to working, but I do have a Windows PC that I've used to test the HDHomeRun with.  It's wirelessly connected, so I get lots of artifacts in the video, but it plays, both with video and audio.  (I've got a dual-router setup.  The living room has a "client bridge", offering wired connections to the HDHomeRun, HTPC, and Blu-Ray plater, but they connect wirelessly to the computers and cable modem that are on another router in the computer room).

I've posted a request for help on the HDHomeRun forums regarding the VLC Linux instructions you sent, which I can't get to work, but I can verify that the HDHomeRun works from another system.


> **Mister.Vash said:**
> If that looks good, then I would recommend that on both the frontend and the backend, you increase the verbosity of the logging, that may help provide additional details about what is going on.  Also, if you can't find any better information about that specific Ringbuf error, I would suggest posting to the mythtv-users list:
[http://www.mythtv.org/mailman/listinfo/mythtv-users/](http://www.mythtv.org/mailman/listinfo/mythtv-users/)
Thanks.  I hadn't thought about increasing the logging verbosity.  I'll figure out how to do that and post new logs here.  I joined the mythtvtalk.com forums, but I'll also join the user email list.

Thanks for your guidance, I appreciate it.  It's given me some new avenues to pursue, even if it hasn't gotten me to the point of fixing the problem yet.

---

### Post by gungfujoe on 2009-06-27
Er, I figured it out...  I was starting on an invalid channel, and even if I changed to a valid channel before it timed it, it still timed out on the invalid channel, ignoring the fact that I changed channels.

Oops.

Now onto the next problem - I get loud static in place of the audio.  I'll play with that a bit and start a new thread for it, though.

---

