---
title: "Who is willing to walk a newbie through it?"
date: 2010-02-24
forum: Mythbuntu
---

### Post by Looking2learn on 2010-02-24
Hello, first post.

 I had a windows machine with the hauppauge 150. Without going into details windows got corrupted and I couldn't retrieve it. So I decided to go with Mythbuntu, as I found a basic setup tutorial, and I figured why not?

 So I have Mythbuntu set up as per the video - but I have no TV. My videos, music and such is on an external HD which I would like to have access to as well. 

 So my question to this fine forum, is there anyone out there willing to walk and admitted newbie through this? 

The setup see's the card, the channel scan seems to have seen the channels, but when I select "watch TV" the screen goes blank, then back to the main option screen. 

 Any help would be greatly appreciated.

---

### Post by azmyth on 2010-02-24
It's kind of hard to walk someone through it since there could be a multitude of issues causing your problem. The best way to troubleshot problems is with the log files. They'll be in your /var/log/mythtv folder. Just start your liveTV and then from a shell prompt do a tail /var/log/mythtv/mythfrontend.log and tail /var/log/mythtv/mythbackend.log. If there's an error it will tell you in the log. You can then post here or search here and google.

Just from what I know I suspect you don't have the proper drivers installed. If you're using a nvidia card, Ubuntu doesn't come installed with the drivers you need. What kind of card do you use?

---

### Post by Looking2learn on 2010-02-24
Thank you very much for your reply. Indeed I am using an Nvidia card. I will get the logs and post it here. Thanks for any and all help.

---

### Post by Looking2learn on 2010-02-24
WOW, seems like a lot of errors. Anyway, any help would be appreciated.

Frontend

2010-02-23 17:25:51.627 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2010-02-23 17:25:52.026 No theme dir: /home/kevin/.mythtv/themes/Titivillus
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/agp': Is a directory
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
2010-02-24 15:45:29.366 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2010-02-24 15:45:29.369 Using protocol version 40
2010-02-24 15:45:31.606 Deleting UPnP client...


Backend
2010-02-24 14:26:44.768 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 14:41:44.831 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 14:56:44.895 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:11:44.963 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:26:45.026 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:41:45.088 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:45:29.370 MainServer::HandleAnnounce Monitor
2010-02-24 15:45:29.374 adding: kevin-desktop as a client (events: 0)
2010-02-24 15:45:29.377 MainServer::HandleAnnounce Monitor
2010-02-24 15:45:29.379 adding: kevin-desktop as a client (events: 1)


Thanks for any and all help...

---

### Post by tgm4883 on 2010-02-24
use mythbuntu-log-grabber to get the logs, then post the link here

---

### Post by Looking2learn on 2010-02-24
@TGM, 

 Thanks for the reply. Sorry about the length...

==> /var/log/mythtv/mtd.log <==
mtd started at Tue Feb 23 17:25:28 2010
mtd is running on a host called kevin-desktop
17:25:28: Waiting for connections/jobs
17:25:28: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2010-02-24 07:26:01.457 Grabbing data for Wed Feb 24 2010 offset 13
2010-02-24 07:26:01.459 From Tue Mar 9 05:00:00 2010 to Wed Mar 10 05:00:00 2010 (UTC)
2010-02-24 07:26:01.460 Grabbing listing data
--2010-02-24 07:26:01--  [http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService](http://webservices.schedulesdirect.tmsdatadirect.com/schedulesdirect/tvlistings/xtvdService)
Resolving webservices.schedulesdirect.tmsdatadirect.com... 144.142.232.53
Connecting to webservices.schedulesdirect.tmsdatadirect.com|144.142.232.53|:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/xml]
Saving to: `STDOUT'

     0K .......... .......... .......... .......... .......... 6.31K
    50K .......... .......... .......... .......... .......... 28.6K
   100K .......... .......... .......... ...                   22.4K=11s

2010-02-24 07:26:13 (11.9 KB/s) - `-' saved [136641]

2010-02-24 07:26:13.439 DataDirect: Your subscription expires on 12/13/10 07:05:24
2010-02-24 07:26:27.804 Grab complete.  Actual data from Tue Mar 9 05:00:00 2010 to Wed Mar 10 05:00:00 2010 (UTC)
2010-02-24 07:26:27.825 Main temp tables populated.
2010-02-24 07:26:28.102 Clearing data for source.
2010-02-24 07:26:28.114 Clearing from Tue Mar 9 00:00:00 2010 to Wed Mar 10 00:00:00 2010 (localtime)
2010-02-24 07:26:28.583 Data for source cleared.
2010-02-24 07:26:28.585 Updating programs.
2010-02-24 07:26:30.920 Program table update complete.
2010-02-24 07:26:31.368 Data fetching complete.
2010-02-24 07:26:31.369 Adjusting program database end times.
2010-02-24 07:26:33.353     0 replacements made
2010-02-24 07:26:33.354 Marking generic episodes.
2010-02-24 07:26:33.920     Found 2578
2010-02-24 07:26:33.922 Marking repeats.
2010-02-24 07:26:34.652     Found 4864
2010-02-24 07:26:34.654 Unmarking new episode rebroadcast repeats.
2010-02-24 07:26:35.093     Found 0
2010-02-24 07:26:35.964 Marking episode first showings.
2010-02-24 07:26:42.985 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 07:26:54.258     Found 11511
2010-02-24 07:26:54.263 Marking episode last showings.
2010-02-24 07:27:12.861     Found 11511
2010-02-24 07:27:12.994 Grabbing next suggested grabbing time
2010-02-24 07:27:13.638 DataDirect: BlockedTime is: 2010-02-24T07:27:13
2010-02-24 07:27:13.644 DataDirect: NextSuggestedTime is: 2010-02-25T11:54:47
2010-02-24 07:27:13.657 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2010-02-24 07:27:13.670 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2010-02-24 07:27:13.765 Using protocol version 40
2010-02-24 07:27:13.767 MainServer::HandleAnnounce Monitor
2010-02-24 07:27:13.770 adding: kevin-desktop as a client (events: 0)
2010-02-24 07:27:13.773 MainServer::HandleAnnounce Monitor
2010-02-24 07:27:13.774 adding: kevin-desktop as a client (events: 1)
2010-02-24 07:27:13.804 mythfilldatabase run complete.
2010-02-24 07:27:13.806 DataDirect: Deleting temporary files
2010-02-24 07:27:13.848 Reschedule requested for id -1.
2010-02-24 07:27:14.300 Scheduled 0 items in 0.5 = 0.13 match + 0.33 place
2010-02-24 07:41:43.060 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 07:56:43.136 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 08:11:43.198 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 08:26:43.260 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 08:41:43.321 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 08:56:43.384 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 09:11:43.451 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 09:26:43.513 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 09:41:43.579 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 09:56:43.643 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 10:11:43.709 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 10:26:43.771 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 10:41:43.836 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 10:56:43.895 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 11:11:43.956 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 11:26:44.018 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 11:41:44.083 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 11:56:44.143 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 12:11:44.208 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 12:26:44.266 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 12:41:44.330 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 12:56:44.394 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 13:11:44.459 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 13:26:44.518 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 13:41:44.582 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 13:56:44.644 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 14:11:44.708 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 14:26:44.768 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 14:41:44.831 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 14:56:44.895 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:11:44.963 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:26:45.026 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:41:45.088 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 15:45:29.370 MainServer::HandleAnnounce Monitor
2010-02-24 15:45:29.374 adding: kevin-desktop as a client (events: 0)
2010-02-24 15:45:29.377 MainServer::HandleAnnounce Monitor
2010-02-24 15:45:29.379 adding: kevin-desktop as a client (events: 1)
2010-02-24 15:56:45.149 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 16:11:45.224 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 16:26:45.283 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-24 16:41:45.345 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2010-02-23 16:48:49.536 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 16:49:09.539 New DB connection, total: 3
2010-02-23 16:49:09.558 Connected to database 'mythconverg' at host: localhost
2010-02-23 16:49:09.618 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2010-02-23 16:49:17.439 XMLParse::LoadTheme using /usr/share/mythtv/themes/Titivillus/music-ui.xml
2010-02-23 16:50:32.140 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2010-02-23 16:50:32.163 Using protocol version 40
2010-02-23 16:50:32.227 Received a remote 'Clear Cache' request
2010-02-23 16:50:56.592 Received a remote 'Clear Cache' request
2010-02-23 16:51:03.289 Received a remote 'Clear Cache' request
2010-02-23 16:51:18.199 MythMusic hasn't found any tracks! That's ok with me if it's ok with you.
2010-02-23 16:51:24.403 XMLParse::LoadTheme using /usr/share/mythtv/themes/Titivillus/video-ui.xml
2010-02-23 16:51:25.236 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2010-02-23 16:51:25.238 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2010-02-23 16:51:32.405 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 16:53:29.922 TV: Attempting to change from None to WatchingLiveTV
2010-02-23 16:53:29.925 Using protocol version 40
2010-02-23 16:53:32.624 GetEntryAt(-1) failed.
2010-02-23 16:53:32.658 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-02-23 16:53:32.659 TV Error: LiveTV not successfully started
2010-02-23 16:53:32.659 TV Error: LiveTV not successfully started
2010-02-23 16:53:32.691 TV: Deleting TV Chain in destructor
2010-02-23 16:53:32.727 DPMS Deactivated 
2010-02-23 16:53:32.729 DPMS Reactivated.
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/agp': Is a directory
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
2010-02-23 16:54:11.732 Deleting UPnP client...
Starting mythfrontend.real..
2010-02-23 17:20:45.382 New DB connection, total: 2
2010-02-23 17:20:45.383 Connected to database 'mythconverg' at host: localhost
2010-02-23 17:20:45.408 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2010-02-23 17:20:45.408 Enabled verbose msgs:  important general
2010-02-23 17:20:47.105 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 17:20:47.110 Primary screen 0.
2010-02-23 17:20:47.111 Using screen 0, 1440x900 at 0,0
2010-02-23 17:20:47.112 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 17:20:47.114 Switching to square mode (Titivillus)
2010-02-23 17:20:47.226 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2010-02-23 17:20:47.227 lirc_init failed for mythtv, see preceding messages
2010-02-23 17:20:47.228 JoystickMenuClient Error: Joystick disabled - Failed to read /home/kevin/.mythtv/joystickmenurc
2010-02-23 17:20:48.863 Loading from: /usr/share/mythtv/themes/Titivillus/base.xml
2010-02-23 17:20:49.147 Loading from: /usr/share/mythtv/themes/default/base.xml
2010-02-23 17:20:49.399 Registering Internal as a media playback plugin.
2010-02-23 17:20:49.915 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-02-23 17:20:50.368 Failed to run 'cdrecord --scanbus'
2010-02-23 17:20:50.376 Failed to run 'cdrecord --scanbus -dev=ATA'
2010-02-23 17:20:50.384 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2010-02-23 17:20:50.478 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2010-02-23 17:20:50.785 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 17:20:56.944 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2010-02-23 17:20:56.984 Using protocol version 40
2010-02-23 17:20:57.007 TV: Attempting to change from None to WatchingLiveTV
2010-02-23 17:20:57.009 Using protocol version 40
2010-02-23 17:20:58.918 GetEntryAt(-1) failed.
2010-02-23 17:20:58.920 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-02-23 17:20:58.921 TV Error: LiveTV not successfully started
2010-02-23 17:20:58.921 TV Error: LiveTV not successfully started
2010-02-23 17:20:58.932 TV: Deleting TV Chain in destructor
2010-02-23 17:20:58.936 DPMS Deactivated 
2010-02-23 17:20:58.938 DPMS Reactivated.
2010-02-23 17:21:16.553 Received a remote 'Clear Cache' request
2010-02-23 17:21:30.541 XMLParse::LoadTheme using /usr/share/mythtv/themes/Titivillus/video-ui.xml
2010-02-23 17:21:37.091 Deleting UPnP client...
Starting mythfrontend.real..
2010-02-23 17:25:38.222 New DB connection, total: 2
2010-02-23 17:25:38.265 Connected to database 'mythconverg' at host: localhost
2010-02-23 17:25:38.272 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2010-02-23 17:25:38.273 Enabled verbose msgs:  important general
2010-02-23 17:25:44.588 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 17:25:44.605 Primary screen 0.
2010-02-23 17:25:44.606 Using screen 0, 1440x900 at 0,0
2010-02-23 17:25:44.607 No theme dir: /home/kevin/.mythtv/themes/Titivillus
2010-02-23 17:25:44.609 Switching to square mode (Titivillus)
2010-02-23 17:25:44.771 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2010-02-23 17:25:44.772 lirc_init failed for mythtv, see preceding messages
2010-02-23 17:25:44.796 JoystickMenuClient Error: Joystick disabled - Failed to read /home/kevin/.mythtv/joystickmenurc
2010-02-23 17:25:48.969 Loading from: /usr/share/mythtv/themes/Titivillus/base.xml
2010-02-23 17:25:49.740 Loading from: /usr/share/mythtv/themes/default/base.xml
2010-02-23 17:25:50.165 Registering Internal as a media playback plugin.
2010-02-23 17:25:50.749 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-02-23 17:25:51.498 Failed to run 'cdrecord --scanbus'
2010-02-23 17:25:51.504 Failed to run 'cdrecord --scanbus -dev=ATA'
2010-02-23 17:25:51.515 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2010-02-23 17:25:51.627 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2010-02-23 17:25:52.026 No theme dir: /home/kevin/.mythtv/themes/Titivillus
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/agp': Is a directory
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
2010-02-24 15:45:29.366 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2010-02-24 15:45:29.369 Using protocol version 40
2010-02-24 15:45:31.606 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Feb 24 07:30:01 kevin-desktop /USR/SBIN/CRON[1264]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 07:39:01 kevin-desktop /USR/SBIN/CRON[1504]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 07:40:01 kevin-desktop /USR/SBIN/CRON[1687]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 07:50:01 kevin-desktop /USR/SBIN/CRON[1930]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 08:00:01 kevin-desktop /USR/SBIN/CRON[2176]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 08:00:01 kevin-desktop /USR/SBIN/CRON[2188]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 08:09:01 kevin-desktop /USR/SBIN/CRON[2506]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 08:10:01 kevin-desktop /USR/SBIN/CRON[2693]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 08:17:01 kevin-desktop /USR/SBIN/CRON[3002]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 08:20:01 kevin-desktop /USR/SBIN/CRON[3204]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 08:26:03 kevin-desktop ntpd[3688]: kernel time sync status change 4001
Feb 24 08:30:01 kevin-desktop /USR/SBIN/CRON[3448]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 08:39:01 kevin-desktop /USR/SBIN/CRON[3717]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 08:40:01 kevin-desktop /USR/SBIN/CRON[3908]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 08:43:08 kevin-desktop ntpd[3688]: kernel time sync status change 0001
Feb 24 08:50:01 kevin-desktop /USR/SBIN/CRON[4145]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 09:00:01 kevin-desktop /USR/SBIN/CRON[4384]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 09:00:01 kevin-desktop /USR/SBIN/CRON[4396]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 09:09:01 kevin-desktop /USR/SBIN/CRON[4755]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 09:10:01 kevin-desktop /USR/SBIN/CRON[4938]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 09:17:01 kevin-desktop /USR/SBIN/CRON[5175]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 09:20:02 kevin-desktop /USR/SBIN/CRON[5354]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 09:30:01 kevin-desktop /USR/SBIN/CRON[5591]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 09:39:01 kevin-desktop /USR/SBIN/CRON[5828]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 09:40:01 kevin-desktop /USR/SBIN/CRON[6011]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 09:50:01 kevin-desktop /USR/SBIN/CRON[6248]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:00:01 kevin-desktop /USR/SBIN/CRON[6492]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:00:01 kevin-desktop /USR/SBIN/CRON[6495]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 10:09:01 kevin-desktop /USR/SBIN/CRON[6858]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 10:10:01 kevin-desktop /USR/SBIN/CRON[7041]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:17:01 kevin-desktop /USR/SBIN/CRON[7278]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 10:20:01 kevin-desktop /USR/SBIN/CRON[7457]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:30:01 kevin-desktop /USR/SBIN/CRON[7694]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:39:01 kevin-desktop /USR/SBIN/CRON[7931]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 10:40:01 kevin-desktop /USR/SBIN/CRON[8114]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:50:01 kevin-desktop /USR/SBIN/CRON[8351]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 10:59:37 kevin-desktop ntpd[3688]: kernel time sync status change 4001
Feb 24 11:00:01 kevin-desktop /USR/SBIN/CRON[8590]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 11:00:01 kevin-desktop /USR/SBIN/CRON[8602]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 11:09:01 kevin-desktop /USR/SBIN/CRON[8903]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 11:10:01 kevin-desktop /USR/SBIN/CRON[9086]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 11:16:43 kevin-desktop ntpd[3688]: kernel time sync status change 0001
Feb 24 11:17:01 kevin-desktop /USR/SBIN/CRON[9323]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 11:20:02 kevin-desktop /USR/SBIN/CRON[9502]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 11:30:02 kevin-desktop /USR/SBIN/CRON[9739]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 11:39:01 kevin-desktop /USR/SBIN/CRON[9976]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 11:40:01 kevin-desktop /USR/SBIN/CRON[10159]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 11:50:01 kevin-desktop /USR/SBIN/CRON[10396]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 12:00:02 kevin-desktop /USR/SBIN/CRON[10635]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 12:00:02 kevin-desktop /USR/SBIN/CRON[10648]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 12:09:01 kevin-desktop /USR/SBIN/CRON[10948]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 12:10:01 kevin-desktop /USR/SBIN/CRON[11131]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 12:17:01 kevin-desktop /USR/SBIN/CRON[11368]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 12:20:01 kevin-desktop /USR/SBIN/CRON[11547]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 12:30:01 kevin-desktop /USR/SBIN/CRON[11784]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 12:39:01 kevin-desktop /USR/SBIN/CRON[12021]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 12:40:01 kevin-desktop /USR/SBIN/CRON[12204]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 12:50:01 kevin-desktop /USR/SBIN/CRON[12441]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 13:00:01 kevin-desktop /USR/SBIN/CRON[12680]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 13:00:01 kevin-desktop /USR/SBIN/CRON[12692]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 13:09:01 kevin-desktop /USR/SBIN/CRON[12993]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 13:10:01 kevin-desktop /USR/SBIN/CRON[13176]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 13:17:01 kevin-desktop /USR/SBIN/CRON[13413]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 13:20:01 kevin-desktop /USR/SBIN/CRON[13592]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 13:30:01 kevin-desktop /USR/SBIN/CRON[13829]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 13:39:01 kevin-desktop /USR/SBIN/CRON[14066]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 13:40:01 kevin-desktop /USR/SBIN/CRON[14249]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 13:50:01 kevin-desktop /USR/SBIN/CRON[14486]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 14:00:01 kevin-desktop /USR/SBIN/CRON[14725]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 14:00:01 kevin-desktop /USR/SBIN/CRON[14737]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 14:09:01 kevin-desktop /USR/SBIN/CRON[15038]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 14:10:01 kevin-desktop /USR/SBIN/CRON[15221]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 14:17:01 kevin-desktop /USR/SBIN/CRON[15458]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 14:20:01 kevin-desktop /USR/SBIN/CRON[15637]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 14:30:01 kevin-desktop /USR/SBIN/CRON[15874]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 14:39:01 kevin-desktop /USR/SBIN/CRON[16111]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 14:40:01 kevin-desktop /USR/SBIN/CRON[16294]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 14:50:01 kevin-desktop /USR/SBIN/CRON[16531]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 15:00:01 kevin-desktop /USR/SBIN/CRON[16770]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 15:00:01 kevin-desktop /USR/SBIN/CRON[16783]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 15:09:01 kevin-desktop /USR/SBIN/CRON[17083]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 15:10:01 kevin-desktop /USR/SBIN/CRON[17266]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 15:17:01 kevin-desktop /USR/SBIN/CRON[17503]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 15:20:01 kevin-desktop /USR/SBIN/CRON[17682]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 15:30:01 kevin-desktop /USR/SBIN/CRON[17919]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 15:33:09 kevin-desktop ntpd[3688]: kernel time sync status change 4001
Feb 24 15:39:01 kevin-desktop /USR/SBIN/CRON[18156]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 15:40:01 kevin-desktop /USR/SBIN/CRON[18374]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 15:50:01 kevin-desktop /USR/SBIN/CRON[18693]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 16:00:01 kevin-desktop /USR/SBIN/CRON[18974]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Feb 24 16:00:01 kevin-desktop /USR/SBIN/CRON[18977]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 16:09:01 kevin-desktop /USR/SBIN/CRON[19358]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 16:10:01 kevin-desktop /USR/SBIN/CRON[19543]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 16:17:01 kevin-desktop /USR/SBIN/CRON[19788]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 24 16:20:01 kevin-desktop /USR/SBIN/CRON[19970]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 16:30:01 kevin-desktop /USR/SBIN/CRON[20217]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 16:39:01 kevin-desktop /USR/SBIN/CRON[20465]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb 24 16:40:01 kevin-desktop /USR/SBIN/CRON[20650]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Feb 24 16:41:28 kevin-desktop ntpd[3688]: kernel time sync status change 0001
Feb 24 16:50:01 kevin-desktop /USR/SBIN/CRON[20897]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

==> /var/log/Xorg.0.log <==
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.61
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GT at PCI:1:0:0:
(--) NVIDIA(0):     LG L192WS (CRT-1)
(--) NVIDIA(0): LG L192WS (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device ImExPS/2 Logitech Wheel Mouse
(**) ImExPS/2 Logitech Wheel Mouse: always reports core events
(**) ImExPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Logitech Wheel Mouse: Found 5 mouse buttons
(II) ImExPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImExPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImExPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0

==> /home/kevin/.xsession-errors <==
/etc/gdm/Xsession: Beginning session setup...

2010-02-23 17:25:28.026 Using runtime prefix = /usr
2010-02-23 17:25:28.037 Empty LocalHostName.
2010-02-23 17:25:28.038 Using localhost value of kevin-desktop
2010-02-23 17:25:28.115 New DB connection, total: 1
/usr/bin/startxfce4: X server already running on display :0
2010-02-23 17:25:28.123 Connected to database 'mythconverg' at host: localhost
2010-02-23 17:25:28.128 Closing DB connection named 'DBManager0'
2010-02-23 17:25:28.129 Connected to database 'mythconverg' at host: localhost
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)

(xfce4-panel:3657): xfce4-panel-WARNING **: xfce4-panel is not running
xfdesktop[3656]: starting up
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:3715): WARNING **: already running?

2010-02-23 17:25:37.075 Using runtime prefix = /usr
2010-02-23 17:25:37.784 XScreenSaver support enabled
2010-02-23 17:25:37.786 DPMS is active.
2010-02-23 17:25:37.788 Empty LocalHostName.
2010-02-23 17:25:37.788 Using localhost value of kevin-desktop
2010-02-23 17:25:37.908 New DB connection, total: 1
2010-02-23 17:25:37.974 Connected to database 'mythconverg' at host: localhost
2010-02-23 17:25:37.978 Closing DB connection named 'DBManager0'
2010-02-23 17:25:38.029 Primary screen 0.
2010-02-23 17:25:38.031 Connected to database 'mythconverg' at host: localhost
2010-02-23 17:25:38.035 Using screen 0, 1440x900 at 0,0
** (nm-applet:3711): DEBUG: applet_common_device_state_changed
** (update-notifier:3659): DEBUG: /usr/lib/update-notifier/apt-check returned 3 (security: 0)
** (update-notifier:3659): DEBUG: crashreport_check

Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
** (update-notifier:3659): DEBUG: /usr/lib/update-notifier/apt-check returned 3 (security: 0)
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
/usr/lib/thunar/thunar-vfs-pixbuf-thumbnailer-1: Unrecognized image file format.
thunar-vfs-font-thumbnailer-1: Could not open the input file: broken file
thunar-vfs-font-thumbnailer-1: Could not open the input file: invalid argument

** (xfwm4:3564): WARNING **: Last user time set back to 80880667 (was 81350479)

** (xfwm4:3564): WARNING **: Last user time set back to 81357449 (was 81361975)
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".

==> lsb_release -a <==
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.1G  8.5G  20% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  352K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  164K  249M   1% /dev
tmpfs                 249M     0  249M   0% /dev/shm
lrm                   249M  2.2M  247M   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sda6              81G  234M   81G   1% /var/lib

==> uname -a <==
Linux kevin-desktop 2.6.28-18-generic #59-Ubuntu SMP Thu Jan 28 01:23:03 UTC 2010 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GT (rev a2)
02:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
02:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

==> lsusb <==
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/agp <==

==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

==> /proc/driver/nvidia/warnings <==
Model:          GeForce 7300 GT
IRQ:            16
Video BIOS:      05.73.22.51.61
Card Type:      AGP
DMA Size:      32 bits
DMA Mask:      0xffffffff
Bus Location:      01.00.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.1.2
          size: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: GeForce 7300 GT
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: RTL8139 Ethernet
                vendor: D-Link System Inc
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=[REMOVED] latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-multimedia
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: c
                bus info: pci@0000:02:0c.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by azmyth on 2010-02-25
Open up synaptic and do a search for nvidia. Do you see any of the nvidia with numbers installed which should be nvidia-195?

---

### Post by Looking2learn on 2010-02-25
Thanks for the reply. 

 Nope, it appears that nivdia-180 is installed. No sign of 195 though. Although I am using 9.04, does that make a difference? 

Thanks for any and all help.

---

### Post by azmyth on 2010-02-25
No, you should be okay with what you have in the way of version and nvidia drivers.

Xlib: extension "XFree86-Misc" missing on display ":0.0".

Don't know if this is your problem but here's the packages that could be needed.

libxxf86misc-dev
**libxxf86misc1**
libxxf86misc1-dbg
x11proto-xf86misc-dev

The one in bold I have on my system.

What do you have for the playback profile
Utilities/Setup -> Setup -> TV Settings -> Playback -> 3rd screen in will tell you

---

### Post by Looking2learn on 2010-02-25
Azmyth, thanks again for all your help. 

When I go to setup->setup->tvsettings->playback, the third screen in shows;

current video playback profile: cpu+ 

if rez <= 720 576 & 0 0 -> FFMPEG & Xvideo             edit delete        1
if rez <= 1280 720 & > 720 576 -> XvMC                     edit delete       2
if rez <= 1280 720 & > 720 576 -> libmpeg2 .......         edit delete       3
if rez > 0 0 -> XvMC                                                      edit delete      4
if rez > 0 0 -> libmpeg2 & Xvideo                                   edit delete     5


Hope that makes sense to you. 

Thanks for your thoughts.

---

### Post by azmyth on 2010-02-25
What I would do is keep it simple and create a "add new" and then add an entry with say rez > 0,0 and set this to standard since standard is just ffmpeg then try watching liveTV again.

---

### Post by Looking2learn on 2010-02-26
Hi azmyth, thanks for all your help. I tried to do what you said, but it still doesn't work. That page now reads:

Current video playback Profile CPU +

if rez <= 720 576 & > 0 0 -> FFMpeg & Xvideo
if rez <= 1280 720 & > 720 576 -> XvMC
if rez <= 1280 720 & > 720 576 -> Libmpeg2....
if rez > 0 0 -> FFnpeg & Xvideo


 Should I delete those other entries? Could it be a conflict?  As always, thanks for any and all help.

Kevin

---

### Post by azmyth on 2010-02-26
No, top right says Add New and Delete. Click on the add new and give it a name like testme or something. This will create a new profile. Then click on add new entry and create a match criteria with rez > 0,0 and select as standard which is just ffmpeg then try livetv again.

---

### Post by Looking2learn on 2010-02-26
Opps, sorry.

 Ok, so I added a new profile, so the screen now looks like:

Current Video Playback Profile : Testme

if rez > 0 0 -> ffmpeg & Xvideo   edit delete 1


I work my way through the next few screens just pressing next, until I finish. Then I go back to the main page, select Watch Tv, the screen goes blank, then comes back up with the main page. 

Sorry for being a newbie on this, but I am taking notes so hopefully I can help others later. Thanks for all your help. 

Kevin

---

### Post by azmyth on 2010-02-26
Hmm, feels like your missing something nvidia on the x-side. Open synaptic and do a search of "nvidia". Please list which packages you have installed. Also, do you see a nvidia-glx package installed?

---

### Post by Looking2learn on 2010-02-26
The nvidia search shows the following installed stuff that is installed is:

nvidia-180-llibdvpau
nvidia-settings
nvidia-180-kernal-source
nvidia-common
nvidia-71-modaliases
nvidia-173-modaliases
nvidia-180-modaliases
nvidia-96-modaliases
nvidia-glx-180
xserver-xorg-video-nv
smartdimmer
jockey-gtk
jockey-common

Thanks...

---

### Post by azmyth on 2010-02-26
hmm, that all looks good too. I don't know what else to think of. Maybe someone else can chime in.

---

### Post by Looking2learn on 2010-02-27
Hey there Azmyth, thanks for all your help. I have one last question before I give up on this. I was thinking that if everything seems to be in order, I would redo the entire backend set up, thinking I may have clicked or unclicked an important box or something (I know I am grasping, but when the alternative is MS??). So I go through the backend set up and right at the end of it, it says that:

' var/lib/mythtv/livetv//.test ' is not writeable

and

' var/libs/mythtv/data/ ' doesn't exist? 

Tell me this helps me somehow? 

Thanks again for your time.

Ohh, and when it reported these issues, it asked me if I wanted to fix them. When I said yes to fix them, the screen went back to the main set up page. If I tried to exit, it would tell me about the issues and if I would like them fixed, when I clicked yes, it went back to the main screen, when I tried to exit, it told me about these issues and asked me if I would like them fixed. So to exit out of the program I had to say not to fix them...

---

### Post by Looking2learn on 2010-02-27
WOOHOO! Got TV, doesn't look as good as it should(As I remember), but it is up. I can change the channels, have sound. The remote seems to work as well. 

AZMYTH, many thanks you for your help thus far, and hopefully help tweeking the system. 

Now, what I would like to do is;

 1 improve the picture quality, if possible using other settings.
 2 set up my external drives so I can access the movies, music and such.
 3 set up the plugins so I can see the weather, youtube, and such (if possible)
 4 Anything you think makes mythbuntu a great system.

Thanks again for your help thusfar, and hopefully into the future.

---

### Post by azmyth on 2010-02-27
Glad to hear you got it working. What did you do you may help someone else out? Was it a permission issue? Usually myth will give you an error if a directory can't be written to.

1. What kind of tv tuner card are you using? In the recording profiles from the mythFE utilities/setup, you can change bit rates to try to improve quality. Also, svideo output seems to improve quality. You'll only get so much quality though. I'm using a PVR150 and I've been happy with the quality. Also, have a ATI TV Wonder quality isn't so good.

2. Probably a samba or NFS share would do the trick. I haven't done it myself for myth though. I've done it for other things and NFS isn't to difficult to setup. Samba I found harder.

3. Mythweather through the information settings is where you change which screens and location. Youtube, you'll need the svn since it has the youtube plugins.

4. Kind of up to you on what you like.

---

### Post by Looking2learn on 2010-02-28
Hey azmyth, thanks for the reply....

 Indeed it was a permissions thing. Once I added the directory and changed its permission to read and write, the rest just fell into place. I tried those other profiles and they all worked as well. So the entire thing was just my newbie-ish and not remembering the warnings the first time(I have been doing this piecemeal for a while now)

 I am using the hagppauge(sp?) 150 for the card. After looking at it more I think I can live with the quality for right now. Also, seeing as I am using a LCD TFT display it may just be that, that is giving me the troubles and once I hook it into my TV things should work out well. If not, I'll be back picking your brain..

I have my external drives all set up, so that I can at least watch movies and listen to music. I think I have that part under control, although I am finding the music difficult to organize in a sane manner. It seems as if to myth it is just one giant listing so if I want to listen to song # 250, I have to "skip" 250 times to get to the song. Surely there must be a better way? 

 Could you please show me how and what the svn is, and how to configure it for youtube? 

as for other stuff, is there something like a bittorrent client, or online radio? SkyFM or whatnot?

as always, thanks for all your help.

Kevin

---

