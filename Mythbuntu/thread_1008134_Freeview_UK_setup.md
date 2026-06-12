---
title: "Freeview UK setup"
date: 2008-12-11
forum: Mythbuntu
---

### Post by My Name on 2008-12-11
Hi fellas and ladies,
I am currently setting up mythbuntu for TV, music, and movies etc. I'm just asking if there is a guide for setting these things up for the UK.
I have managed to set up the music, images and movies and it looks good so far. I have purchased a microsoft mce remote and Freecom DVT-T usb stick but I won't have them for a few days.
I guess i need to know how to set up the TV listings and such for the UK. I would also like to use the information section for movie listings. I have set up the weather section but only for 3 day forcast as London only seems to exist in the USA for anything more than 3 days.
I think I will have a fairly standard setup apart from the location.
Do any of the UK uses have any tips or how-to to take a look at?

thanks in advance

---

### Post by SiHa on 2008-12-11
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
has a pretty good guide to setup. 

I found the simplest thing is to use the EIT guide data, the grabber setup was a bit finicky.

The supplied movie listings grabber won't work in the UK.

There's a different one here:
[http://www.gossamer-threads.com/lists/mythtv/users/316916](http://www.gossamer-threads.com/lists/mythtv/users/316916)

But I've never got it to work in the UK. There was a problem where it returned malformed .xml which caused Myth to crash. I think that bug has been fixed in Myth now, but I don't know if it works now.

---

### Post by My Name on 2008-12-11
Cheers old bean, I'll have a tinker tonight.
Any chance of getting a UK how-to in the stickies?

---

### Post by SiHa on 2008-12-11
Sounds like a good idea - would need someone cleverer than me though!
Seriously - it's about six months since I tinkered, I can't remember half of the fiddly bits.
To be fair - there's nothing special about the UK setup that makes it any harder than anywhere else, the important bit is to make sure you correctly identify the tuner as a DVB Capture card, (so that it looks for digital, rather than analoue signals) and set the frequency table to Europe-West.

---

### Post by My Name on 2008-12-11
Thanks for the links. I'll keep this updated in case anyone else needs the same info.

---

### Post by My Name on 2008-12-16
OK, so I followed the instructions in the link above and all seemed to be going well. I did a full scan and have a list of channels. The problem is, i should be able to then go to watch TV and... well watch TV but I have no schedule. The channels are listed but I can't watch anything. After a while it will say that it can't connect to the backend. I have it set up as a combined front and back... i think.
Are there any steps I have missing from that how-to?
Maybe my usb thing can't do EIT listings.
I'll have a go with the XML listings tonight.

---

### Post by SiHa on 2008-12-16
Don't think it's a listings problem, it's that your frontend can't see the backend.

In the backend setup:
Have you got the IP address correct? If it's a standalone machine, you can either leave it as 127.0.0.0 (localost) or change it to the actual IP of the machine.
Did you set a PIN? I think the default is just blank, but you need to either use a PIN (and set that up in the frontend), or set it to '0000'. This section is counter-intuitive, you have to specify '0000' to say you don't want a PIN.
Check the mysql password, it should have been set automatically at setup, but it may have been changed accidentally. You can check what is should be, it's stored in **/etc/mythtv/mysql.txt**

Have a look in **/var/log/mythtv/mythfrontend.log** to see what error you're getting.

---

### Post by My Name on 2008-12-16
Nice one SiHa... I'll check on it tonight.
I have been digging through a few how-tos and things are starting to become a little clearer.

If I can get this going I'll buy you a pint next time you're in London :p

---

### Post by My Name on 2008-12-16
well i've corrected the ip to reflect the computer's ip and i no longer have the problem with no connection to backend.
i still get no guide and can't watch anything.

I'm going to have a crack at the XML guide

---

### Post by My Name on 2008-12-16
well i can't seem to get the xml guide to work but I didn't really try hard.
I figured i would try the radio, but i get nothing from that either.

should it be possible to get a successful scan but get no picture?

---

### Post by My Name on 2008-12-16
well looking at the channels list in mythweb, the freqid columns are empty. I would think that the frequency information has been collected during the channel scan but has not populated the list for the frontend.
Any ideas where the channel frequencies will be stored?

---

### Post by SiHa on 2008-12-17
FWIW, mine has no frequency info either - I think that's for analogue.

Did you run Mythfilldatabase after doing the backend setup? Scratch that - if you can get the channel list in mythweb you must have

What does your frontend log say (after the line 'Attempting to switch from 'None' to 'LiveTV')

---

### Post by My Name on 2008-12-17
OK i'll take a look tonight.
I'll also do a screen grab of my mythweb page to see if there is anything missing

---

### Post by My Name on 2008-12-17
ok here is my log file
```
==> /var/log/mythtv/mtd.log <==
mtd started at Wed Dec 17 21:16:13 2008
mtd is running on a host called iain-desktop
21:16:13: Waiting for connections/jobs
21:16:13: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2008-12-17 21:40:21.261 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-12-17 21:40:21.265 Enabled verbose msgs:  important general
2008-12-17 21:40:21.272 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-17 21:40:24.172 MainServer::HandleAnnounce Monitor
2008-12-17 21:40:24.178 adding: iain-desktop as a client (events: 0)
2008-12-17 21:40:24.179 MainServer::HandleAnnounce Monitor
2008-12-17 21:40:24.181 adding: iain-desktop as a client (events: 1)
2008-12-17 21:40:24.224 Reschedule requested for id -1.
2008-12-17 21:40:24.251 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-12-17 21:40:24.258 Seem to be woken up by USER
2008-12-17 21:40:38.143 MainServer::HandleAnnounce Monitor
2008-12-17 21:40:38.146 adding: iain-desktop as a client (events: 0)
2008-12-17 21:40:38.147 MainServer::HandleAnnounce Monitor
2008-12-17 21:40:38.148 adding: iain-desktop as a client (events: 1)
2008-12-17 21:40:38.160 MainServer::HandleAnnounce Playback
2008-12-17 21:40:38.161 adding: iain-desktop as a client (events: 0)
2008-12-17 21:40:38.166 TVRec(1): Changing from None to WatchingLiveTV
2008-12-17 21:40:38.174 TVRec(1): HW Tuner: 1->1
2008-12-17 21:40:39.249 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-12-17 21:41:05.490 TVRec(1): PauseRecorder() called with no recorder
2008-12-17 21:41:05.500 TVRec(1): HW Tuner: 1->1
2008-12-17 21:41:06.723 Finished recording Unknown: channel 1005
2008-12-17 21:41:06.774 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-12-17 21:41:06.906 Using runtime prefix = /usr
2008-12-17 21:41:06.910 Empty LocalHostName.
2008-12-17 21:41:06.911 Using localhost value of iain-desktop
2008-12-17 21:41:06.920 New DB connection, total: 1
2008-12-17 21:41:06.926 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:41:06.928 Closing DB connection named 'DBManager0'
2008-12-17 21:41:06.930 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:41:06.934 New DB connection, total: 2
2008-12-17 21:41:06.938 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:41:06.944 Current Schema Version: 1214
2008-12-17 21:41:06.961 Preview Error: Previewer file '/var/lib/mythtv/recordings/1005_20081217214038.mpg' is not valid.
2008-12-17 21:41:06.963 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1005_20081217214038.mpg'
2008-12-17 21:41:06.973 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1005_20081217214038.mpg.png) exists: 0 readable: 0 size: 0
2008-12-17 21:41:15.899 TVRec(1): Changing from WatchingLiveTV to None
2008-12-17 21:41:15.939 Finished recording Unknown: channel 5164
2008-12-17 21:41:41.195 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-17 21:42:41.214 Expiring 0 MBytes for 5164 @ Wed Dec 17 21:41:05 2008 => Unknown
2008-12-17 21:46:46.063 Using runtime prefix = /usr
2008-12-17 21:46:46.066 Empty LocalHostName.
2008-12-17 21:46:46.068 Using localhost value of iain-desktop
2008-12-17 21:46:46.078 New DB connection, total: 1
2008-12-17 21:46:46.088 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:46:46.091 Closing DB connection named 'DBManager0'
2008-12-17 21:46:46.093 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:46:46.096 New DB connection, total: 2
2008-12-17 21:46:46.097 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:46:46.111 Current Schema Version: 1214
Starting up as the master server.
2008-12-17 21:46:46.137 New DB connection, total: 3
2008-12-17 21:46:46.142 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:46:46.302 New DB scheduler connection
2008-12-17 21:46:46.303 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:46:47.377 Main::Registering HttpStatus Extension
2008-12-17 21:46:47.380 mythbackend version: 0.21.20080304-1 www.mythtv.org
2008-12-17 21:46:47.381 Enabled verbose msgs:  important general
2008-12-17 21:46:47.384 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-12-17 21:46:49.309 Reschedule requested for id -1.
2008-12-17 21:46:49.336 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-12-17 21:46:49.343 Seem to be woken up by USER
2008-12-17 21:46:55.367 MainServer::HandleAnnounce Monitor
2008-12-17 21:46:55.371 adding: iain-desktop as a client (events: 0)
2008-12-17 21:46:55.372 MainServer::HandleAnnounce Monitor
2008-12-17 21:46:55.373 adding: iain-desktop as a client (events: 1)
2008-12-17 21:46:55.378 Reschedule requested for id -1.
2008-12-17 21:46:55.413 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-12-17 21:46:56.351 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-12-17 21:46:56.361 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-12-17 21:47:07.568 MainServer::HandleAnnounce Monitor
2008-12-17 21:47:07.569 adding: iain-desktop as a client (events: 0)
2008-12-17 21:47:07.571 MainServer::HandleAnnounce Monitor
2008-12-17 21:47:07.573 adding: iain-desktop as a client (events: 1)
2008-12-17 21:47:07.585 MainServer::HandleAnnounce Playback
2008-12-17 21:47:07.587 adding: iain-desktop as a client (events: 0)
2008-12-17 21:47:07.590 TVRec(1): Changing from None to WatchingLiveTV
2008-12-17 21:47:07.597 TVRec(1): HW Tuner: 1->1
2008-12-17 21:47:08.718 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-12-17 21:47:33.039 TVRec(1): PauseRecorder() called with no recorder
2008-12-17 21:47:33.047 TVRec(1): HW Tuner: 1->1
2008-12-17 21:47:34.929 Finished recording Unknown: channel 1005
2008-12-17 21:47:34.961 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-12-17 21:47:35.120 Using runtime prefix = /usr
2008-12-17 21:47:35.127 Empty LocalHostName.
2008-12-17 21:47:35.127 Using localhost value of iain-desktop
2008-12-17 21:47:35.138 New DB connection, total: 1
2008-12-17 21:47:35.145 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:35.149 Closing DB connection named 'DBManager0'
2008-12-17 21:47:35.151 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:35.154 New DB connection, total: 2
2008-12-17 21:47:35.159 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:35.164 Current Schema Version: 1214
2008-12-17 21:47:35.178 Preview Error: Previewer file '/var/lib/mythtv/recordings/1005_20081217214707.mpg' is not valid.
2008-12-17 21:47:35.180 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1005_20081217214707.mpg'
2008-12-17 21:47:35.191 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1005_20081217214707.mpg.png) exists: 0 readable: 0 size: 0
2008-12-17 21:47:37.687 TVRec(1): Changing from WatchingLiveTV to None
2008-12-17 21:47:37.721 Finished recording Unknown: channel 5164

==> /var/log/mythtv/mythfrontend.log <==
Destroying SipFsm object 
2008-12-17 21:28:04.066 Deleting UPnP client...
Starting mythfrontend.real..
2008-12-17 21:40:33.613 New DB connection, total: 2
2008-12-17 21:40:33.613 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:40:33.616 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-17 21:40:33.616 Enabled verbose msgs:  important general
2008-12-17 21:40:34.084 No theme dir: /home/iain/.mythtv/themes/Mythbuntu-8.04
2008-12-17 21:40:34.086 Primary screen 0.
2008-12-17 21:40:34.086 Using screen 0, 1280x1024 at 0,0
2008-12-17 21:40:34.087 No theme dir: /home/iain/.mythtv/themes/Mythbuntu-8.04
2008-12-17 21:40:34.088 Switching to square mode (Mythbuntu-8.04)
2008-12-17 21:40:34.106 Using the Qt painter
2008-12-17 21:40:34.106 JoystickMenuClient Error: Joystick disabled - Failed to read /home/iain/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-17 21:40:34.107 lirc_init failed for mythtv, see preceding messages
2008-12-17 21:40:35.011 Specified base font 'medium' does not exist for font clock
2008-12-17 21:40:35.011 Specified base font 'medium' does not exist for font small
2008-12-17 21:40:35.012 Specified base font 'medium' does not exist for font medium
2008-12-17 21:40:35.012 Specified base font 'medium' does not exist for font large
2008-12-17 21:40:35.013 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-12-17 21:40:35.133 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-17 21:40:35.181 Registering Internal as a media playback plugin.
2008-12-17 21:40:35.327 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-12-17 21:40:35.370 Failed to run 'cdrecord --scanbus'
2008-12-17 21:40:35.380 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-12-17 21:40:35.384 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-12-17 21:40:35.425 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.2:5060 NAT address 192.168.0.2
SIP: Cannot register; proxy, username or password not set
2008-12-17 21:40:35.551 No theme dir: /home/iain/.mythtv/themes/Mythbuntu-8.04
2008-12-17 21:40:38.142 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-17 21:40:38.143 Using protocol version 40
2008-12-17 21:40:38.158 TV: Attempting to change from None to WatchingLiveTV
2008-12-17 21:40:38.159 Using protocol version 40
2008-12-17 21:40:39.264 DPMS Deactivated 
2008-12-17 21:40:39.272 New DB connection, total: 3
2008-12-17 21:40:39.272 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:40:39.291 NVP: Disabling Audio, params(-1,2,44100)
2008-12-17 21:40:39.330 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-17 21:40:39.394 OSD Theme Dimensions W: 640 H: 480
2008-12-17 21:40:39.770 TV: Changing from None to WatchingLiveTV
2008-12-17 21:40:39.776 Realtime priority would require SUID as root.
2008-12-17 21:40:39.877 Video timing method: USleep with busy wait
2008-12-17 21:41:15.897 TV: Attempting to change from WatchingLiveTV to None
2008-12-17 21:41:15.969 TV: Changing from WatchingLiveTV to None
2008-12-17 21:41:15.997 DPMS Reactivated.
Destroying SipFsm object 
2008-12-17 21:41:18.994 Deleting UPnP client...
Starting mythfrontend.real..
2008-12-17 21:47:03.156 New DB connection, total: 2
2008-12-17 21:47:03.157 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:03.159 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-12-17 21:47:03.160 Enabled verbose msgs:  important general
2008-12-17 21:47:03.631 No theme dir: /home/iain/.mythtv/themes/Mythbuntu-8.04
2008-12-17 21:47:03.632 Primary screen 0.
2008-12-17 21:47:03.633 Using screen 0, 1280x1024 at 0,0
2008-12-17 21:47:03.634 No theme dir: /home/iain/.mythtv/themes/Mythbuntu-8.04
2008-12-17 21:47:03.634 Switching to square mode (Mythbuntu-8.04)
2008-12-17 21:47:03.653 Using the Qt painter
2008-12-17 21:47:03.653 JoystickMenuClient Error: Joystick disabled - Failed to read /home/iain/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-12-17 21:47:03.653 lirc_init failed for mythtv, see preceding messages
2008-12-17 21:47:04.531 Specified base font 'medium' does not exist for font clock
2008-12-17 21:47:04.531 Specified base font 'medium' does not exist for font small
2008-12-17 21:47:04.532 Specified base font 'medium' does not exist for font medium
2008-12-17 21:47:04.532 Specified base font 'medium' does not exist for font large
2008-12-17 21:47:04.533 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-12-17 21:47:04.657 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-12-17 21:47:04.709 Registering Internal as a media playback plugin.
2008-12-17 21:47:04.853 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-12-17 21:47:04.896 Failed to run 'cdrecord --scanbus'
2008-12-17 21:47:04.901 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-12-17 21:47:04.906 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-12-17 21:47:04.947 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.2:5060 NAT address 192.168.0.2
SIP: Cannot register; proxy, username or password not set
2008-12-17 21:47:05.078 No theme dir: /home/iain/.mythtv/themes/Mythbuntu-8.04
2008-12-17 21:47:07.565 Connecting to backend server: 192.168.0.2:6543 (try 1 of 5)
2008-12-17 21:47:07.567 Using protocol version 40
2008-12-17 21:47:07.583 TV: Attempting to change from None to WatchingLiveTV
2008-12-17 21:47:07.584 Using protocol version 40
2008-12-17 21:47:08.739 New DB connection, total: 3
2008-12-17 21:47:08.739 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:08.758 NVP: Disabling Audio, params(-1,2,44100)
2008-12-17 21:47:08.789 DPMS Deactivated 
2008-12-17 21:47:08.797 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-12-17 21:47:08.863 OSD Theme Dimensions W: 640 H: 480
2008-12-17 21:47:09.246 TV: Changing from None to WatchingLiveTV
2008-12-17 21:47:09.253 Realtime priority would require SUID as root.
2008-12-17 21:47:09.352 Video timing method: USleep with busy wait
2008-12-17 21:47:34.958 New DB connection, total: 4
2008-12-17 21:47:34.959 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:37.686 TV: Attempting to change from WatchingLiveTV to None
2008-12-17 21:47:37.765 TV: Changing from WatchingLiveTV to None
2008-12-17 21:47:37.788 DPMS Reactivated.
Destroying SipFsm object 
2008-12-17 21:47:40.516 Deleting UPnP client...

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Dec 17 21:16:07 iain-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_11_11_84_da_96, iface: eth0): not well known
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Dec 17 21:16:07 iain-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 17 21:16:07 iain-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPlugin-Ifupdown: (155009256) ... get_connections.
Dec 17 21:16:07 iain-desktop nm-system-settings:    SCPlugin-Ifupdown: (155009256) ... get_connections (managed=false): return empty list.
Dec 17 21:16:07 iain-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Dec 17 21:16:08 iain-desktop gdm[5466]: WARNING: Didn't understand `' (expected true or false) 
Dec 17 21:16:09 iain-desktop acpid: client connected from 5473[0:0] 
Dec 17 21:16:10 iain-desktop kernel: [   42.657893] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Dec 17 21:16:10 iain-desktop kernel: [   42.657915] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Dec 17 21:16:10 iain-desktop kernel: [   42.657959] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Dec 17 21:16:10 iain-desktop acpid: client connected from 5473[0:0] 
Dec 17 21:16:10 iain-desktop /usr/sbin/cron[5541]: (CRON) INFO (pidfile fd = 3)
Dec 17 21:16:10 iain-desktop /usr/sbin/cron[5542]: (CRON) STARTUP (fork ok)
Dec 17 21:16:10 iain-desktop /usr/sbin/cron[5542]: (CRON) INFO (Running @reboot jobs)
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): bringing up device. 
Dec 17 21:16:11 iain-desktop kernel: [   44.322224] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 17 21:16:11 iain-desktop kernel: [   44.325123] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): preparing device. 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Dec 17 21:16:11 iain-desktop kernel: [   44.330735] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 3) 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 2 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Dec 17 21:16:11 iain-desktop nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_11_11_84_da_96
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  dhclient started with pid 5603 
Dec 17 21:16:11 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 21:16:11 iain-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 17 21:16:11 iain-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 17 21:16:11 iain-desktop dhclient: All rights reserved.
Dec 17 21:16:11 iain-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 17 21:16:11 iain-desktop dhclient: 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Dec 17 21:16:12 iain-desktop kernel: [   45.057912] NET: Registered protocol family 17
Dec 17 21:16:12 iain-desktop dhclient: Listening on LPF/eth0/00:11:11:84:da:96
Dec 17 21:16:12 iain-desktop dhclient: Sending on   LPF/eth0/00:11:11:84:da:96
Dec 17 21:16:12 iain-desktop dhclient: Sending on   Socket/fallback
Dec 17 21:16:12 iain-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 17 21:16:12 iain-desktop dhclient: DHCPOFFER of 192.168.0.2 from 192.168.0.1
Dec 17 21:16:12 iain-desktop dhclient: DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
Dec 17 21:16:12 iain-desktop dhclient: DHCPACK of 192.168.0.2 from 192.168.0.1
Dec 17 21:16:12 iain-desktop dhclient: bound to 192.168.0.2 -- renewal in 121565 seconds.
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>    address 192.168.0.2 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>    gateway 192.168.0.1 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>    nameserver '192.168.0.1' 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 17 21:16:12 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 17 21:16:12 iain-desktop avahi-daemon[4615]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.
Dec 17 21:16:12 iain-desktop avahi-daemon[4615]: New relevant interface eth0.IPv4 for mDNS.
Dec 17 21:16:12 iain-desktop avahi-daemon[4615]: Registering new address record for 192.168.0.2 on eth0.IPv4.
Dec 17 21:16:12 iain-desktop avahi-daemon[4615]: Registering new address record for fe80::211:11ff:fe84:da96 on eth0.*.
Dec 17 21:16:13 iain-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Dec 17 21:16:13 iain-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Dec 17 21:16:13 iain-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec 17 21:16:13 iain-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 17 21:16:13 iain-desktop ntpd[5137]: ntpd exiting on signal 15
Dec 17 21:16:13 iain-desktop ntpdate[5818]: adjust time server 91.189.94.4 offset 0.067517 sec
Dec 17 21:16:13 iain-desktop ntpd[5858]: ntpd 4.2.4p4@1.1520-o Wed Aug 20 17:03:52 UTC 2008 (1)
Dec 17 21:16:13 iain-desktop ntpd[5859]: precision = 1.000 usec
Dec 17 21:16:13 iain-desktop ntpd[5859]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 17 21:16:13 iain-desktop ntpd[5859]: Listening on interface #1 lo, 127.0.0.1#123 Enabled
Dec 17 21:16:13 iain-desktop ntpd[5859]: Listening on interface #2 eth0, 192.168.0.2#123 Enabled
Dec 17 21:16:13 iain-desktop ntpd[5859]: kernel time sync status 0040
Dec 17 21:16:13 iain-desktop ntpd[5859]: frequency initialized 0.060 PPM from /var/lib/ntp/ntp.drift
Dec 17 21:16:14 iain-desktop ntpd[5859]: getaddrinfo: "::1" invalid host address, ignored
Dec 17 21:16:21 iain-desktop kernel: [   54.856022] eth0: no IPv6 routers present
Dec 17 21:17:01 iain-desktop /USR/SBIN/CRON[5954]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 17 21:20:28 iain-desktop ntpd[5859]: synchronized to 91.189.94.4, stratum 2
Dec 17 21:20:28 iain-desktop ntpd[5859]: kernel time sync status change 0001
Dec 17 21:27:43 iain-desktop kernel: [  736.648130] mythbackend[6350]: segfault at 15 ip 0806c642 sp bfa631a0 error 4 in mythbackend[8048000+118000]
Dec 17 21:39:01 iain-desktop /USR/SBIN/CRON[6811]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

==> /var/log/Xorg.0.log <==
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device IR-receiver inside an USB DVB receiver
(**) IR-receiver inside an USB DVB receiver: always reports core events
(**) IR-receiver inside an USB DVB receiver: Device: "/dev/input/event7"
(II) IR-receiver inside an USB DVB receiver: Found keys
(II) IR-receiver inside an USB DVB receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "IR-receiver inside an USB DVB receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) IR-receiver inside an USB DVB receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) IR-receiver inside an USB DVB receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) IR-receiver inside an USB DVB receiver: xkb_layout: "gb"
(II) config/hal: Adding input device Digital TV Receiver Digital TV Receiver
(**) Digital TV Receiver Digital TV Receiver: always reports core events
(**) Digital TV Receiver Digital TV Receiver: Device: "/dev/input/event2"
(II) Digital TV Receiver Digital TV Receiver: Found keys
(II) Digital TV Receiver Digital TV Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Digital TV Receiver Digital TV Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Digital TV Receiver Digital TV Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Digital TV Receiver Digital TV Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) Digital TV Receiver Digital TV Receiver: xkb_layout: "gb"
(II) config/hal: Adding input device Logitech USB Trackball
(**) Logitech USB Trackball: always reports core events
(**) Logitech USB Trackball: Device: "/dev/input/event3"
(II) Logitech USB Trackball: Found x and y relative axes
(II) Logitech USB Trackball: Found 5 mouse buttons
(II) Logitech USB Trackball: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Trackball" (type: MOUSE)
(**) Logitech USB Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech USB Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

==> /home/iain/.xsession-errors <==
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-AuOmco5622/agent.5622
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (nm-applet:5888): WARNING **: No connections defined

** (update-notifier:5899): WARNING **: already running?

2008-12-17 21:16:20.239 Using runtime prefix = /usr
2008-12-17 21:16:20.850 XScreenSaver support enabled
2008-12-17 21:16:20.859 DPMS is active.
2008-12-17 21:16:20.861 Empty LocalHostName.
2008-12-17 21:16:20.861 Using localhost value of iain-desktop
2008-12-17 21:16:20.887 New DB connection, total: 1
2008-12-17 21:16:20.908 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:16:20.911 Closing DB connection named 'DBManager0'
2008-12-17 21:16:20.936 Primary screen 0.
2008-12-17 21:16:20.937 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:16:20.938 Using screen 0, 1280x1024 at 0,0
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2008-12-17 21:27:28.712 Using runtime prefix = /usr
2008-12-17 21:27:29.240 XScreenSaver support enabled
2008-12-17 21:27:29.241 DPMS is active.
2008-12-17 21:27:29.241 Empty LocalHostName.
2008-12-17 21:27:29.241 Using localhost value of iain-desktop
2008-12-17 21:27:29.250 New DB connection, total: 1
2008-12-17 21:27:29.255 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:27:29.256 Closing DB connection named 'DBManager0'
2008-12-17 21:27:29.258 Primary screen 0.
2008-12-17 21:27:29.259 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:27:29.260 Using screen 0, 1280x1024 at 0,0
tail: error reading `/proc/driver/nvidia/agp': Is a directory
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory

Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 1%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 22%

Reading package lists... 52%

Reading package lists... 85%

Reading package lists... 85%

Reading package lists... 86%

Reading package lists... 86%

Reading package lists... 88%

Reading package lists... 88%

Reading package lists... 89%

Reading package lists... 89%

Reading package lists... 92%

Reading package lists... 94%

Reading package lists... 94%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 95%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... 96%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 38%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

OK

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done


Reading package lists... 0%

Reading package lists... 0%

Reading package lists... 9%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 0%

Reading state information... Done

 * Stopping MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2008-12-17 21:40:33.057 Using runtime prefix = /usr
2008-12-17 21:40:33.584 XScreenSaver support enabled
2008-12-17 21:40:33.584 DPMS is active.
2008-12-17 21:40:33.585 Empty LocalHostName.
2008-12-17 21:40:33.585 Using localhost value of iain-desktop
2008-12-17 21:40:33.594 New DB connection, total: 1
2008-12-17 21:40:33.598 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:40:33.600 Closing DB connection named 'DBManager0'
2008-12-17 21:40:33.602 Primary screen 0.
2008-12-17 21:40:33.602 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:40:33.604 Using screen 0, 1280x1024 at 0,0
tail: error reading `/proc/driver/nvidia/agp': Is a directory
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
 * Stopping MythTV server: mythbackend 
   ...done.
 * Restarting MythTV server: mythbackend 
No /usr/bin/mythbackend found running; none killed.
   ...done.
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead
2008-12-17 21:47:02.596 Using runtime prefix = /usr
2008-12-17 21:47:03.127 XScreenSaver support enabled
2008-12-17 21:47:03.127 DPMS is active.
2008-12-17 21:47:03.128 Empty LocalHostName.
2008-12-17 21:47:03.128 Using localhost value of iain-desktop
2008-12-17 21:47:03.137 New DB connection, total: 1
2008-12-17 21:47:03.141 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:03.143 Closing DB connection named 'DBManager0'
2008-12-17 21:47:03.145 Primary screen 0.
2008-12-17 21:47:03.146 Connected to database 'mythconverg' at host: localhost
2008-12-17 21:47:03.147 Using screen 0, 1280x1024 at 0,0

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             9.2G  2.2G  6.6G  25% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  332K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.9M  502M   1% /dev
tmpfs                 505M     0  505M   0% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb5             100G  219M   94G   1% /home
/dev/sda1             147G  188M  140G   1% /home/iain/Movies

==> uname -a <==
Linux iain-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

==> lsusb <==
Bus 005 Device 002: ID 14aa:0226 AVerMedia (again) or C&E 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
GCC version:  gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce FX 5500
IRQ:   		 16
Video BIOS: 	 04.34.20.69.04
Card Type: 	 AGP
DMA Size: 	 32 bits
DMA Mask: 	 0xffffffff
Bus Location: 	 01.00.0

==> lshw <==
computer
    description: Computer
    product: Springdale-G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=4C87FE5E-23DF-11D9-AAAF-000C6E8BBFE7
  *-core
       description: Motherboard
       product: D865GLC
       vendor: Intel Corporation
       physical id: 0
       version: AAC28906-409
       serial: [REMOVED]
       slot: VIDEO
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: BF86510A.86A.0063.P18.0406220349 (06/22/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: J2E1
          size: 3066MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 39
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 0
             serial: [REMOVED]
             slot: J6G1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 1
             serial: [REMOVED]
             slot: J6G2
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR Synchronous 333 MHz (3.0 ns) [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 2
             serial: [REMOVED]
             slot: J6H1
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM DDR Synchronous 333 MHz (3.0 ns) [empty]
             product: PartNum4
             vendor: Manufacturer4
             physical id: 3
             serial: [REMOVED]
             slot: J6H2
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 2.1
                bus info: pci@0000:02:02.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32 module=emu10k1_gp
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=[REMOVED] latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: SAMSUNG SP1614N
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TM10
                serial: [REMOVED]
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1060faf6
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /home/iain/Movies
                   version: 1.0
                   serial: [REMOVED]
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-16 19:54:46 filesystem=ext3 modified=2008-12-17 21:15:52 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered mounted=2008-12-17 21:15:52 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3120026A
                vendor: Seagate
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 3.06
                serial: [REMOVED]
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000877f5
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: [REMOVED]
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-17 20:39:23 filesystem=ext3 modified=2008-12-17 21:15:08 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-12-17 20:48:53 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 102GiB
                   capacity: 102GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /home
                      capacity: 100GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 1906MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD writer
                product: DVD-RW  DVR-107D
                vendor: PIONEER
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.10
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio dvd
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
can you make head or tail of it?

---

### Post by ianhaycox on 2008-12-18
Just to verify that your hardware works and to eliminate any Myth problems try this,

Stop mythbackend

```

$ sudo /etc/init.d/mythtv-backend stop

```

Create a channels.conf in ~/.mplayer

```

BBC 1 London:10773:h:0:22000:5000:5001:6301
Five:10773:h:0:22000:5400:5401:6335

```

Run 

```

$ mplayer dvb://"BBC 1 London"

```

and you should get Live TV and sound for BBC1

---

### Post by SiHa on 2008-12-18
The only thing that jumps out is in the backend log, is complains about the filename being invalid when trying to generate a preview.

Is /var/lib/mythtv/recordings writeable? LiveTV is buffered to the HDD, so if it can't write to that directory, that would cause this problem

Also, your syslog shows a segfault. Don't know what causes this (or what it really is to be honest). But I do know it's not good.

Whatever, I Second ianhaycox suggestion to make sure your card is OK outside of Myth.

---

### Post by My Name on 2008-12-18
Okydoke
thanks fellas i'll have a butchers tonight.
I did manage to get the guide working though.
Not sure how, but with a bit of fiddling around ip addresses and the like.
It also seems to lose the connection to the backend after a while of complaining that it can't lock to a station.

---

### Post by My Name on 2008-12-18
this is what i'm getting in the terminal
```
iain@iain-desktop:~$ mplayer dvb://"BBC 1 London"
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://BBC 1 London.
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://BBC 1 London.


Exiting... (End of file)

```
I'm assuming the .conf file was co contain the > BBC 1 London:10773:h:0:22000:5000:5001:6301
Five:10773:h:0:22000:5400:5401:6335

---

### Post by SiHa on 2008-12-18
If you can't get the mplayer way to work, have a look [[COLOR="Blue"]_here_[/COLOR]](http://www.mythtv.org/wiki/index.php/Dvbscan) and [[COLOR="Blue"]_here_[/COLOR]](http://www.mythtv.org/wiki/index.php/Tzap) for guides on Tzap and DVBscan (just 'scan' in ubuntu).
Also [[COLOR="Blue"]_here_[/COLOR]](http://www.linuxtv.org/wiki/index.php/Scan) for a guide on w-scan, which is what I used, I think, to test my card outside of MythTV. 

Also have a look at [[COLOR="Blue"]_http://parker1.co.uk/mythtv_ubuntu.php_[/COLOR]](http://parker1.co.uk/mythtv_ubuntu.php) for some good MythTV tips.

---

### Post by My Name on 2008-12-18
OMG!!!!!!!!!!!!!!!!!!
what the hell does that mean
```
iain@iain-desktop:~$ scan -c
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.

```

---

### Post by ianhaycox on 2008-12-18
Was the config file in the ~/.mplayer directory. Note the . (dot) ?

I just deleted my channels.conf file and got the same error.

If you look at the man page for mplayer you can specify an alternate filename for the channels file.

---

### Post by My Name on 2008-12-18
> **ianhaycox said:**
> Was the config file in the ~/.mplayer directory. Note the . (dot) ?

I just deleted my channels.conf file and got the same error.

If you look at the man page for mplayer you can specify an alternate filename for the channels file.

yup.
where can I find that option?

---

### Post by ianhaycox on 2008-12-18
Just re-read your first reply, and you've got a DVB-T card. I gave you a config file for a DVB-S card.

You'll need to find a channels.conf file for the UK and the appropriate transmitter depending on where you live.

Try a quick search on google for channels.conf UK or have a look in 

/usr/share/doc/dvb-utils/examples/scan/dvb-t/

for an initial scan file.

---

### Post by My Name on 2008-12-18
ok I've got a file for crystal palace, just not sure what to do with it.
it is saying that the config file is empty, and looking at the file named "config" rather than "channels.conf" is empty.
Am I missing something obvious.


I feel like such a noob:confused:

---

### Post by ianhaycox on 2008-12-18
The Crystal Palace file you have, is provided as the initial scan input file to the (dvb)scan utility which then produces a channels.conf file with all the necessary frequencies, PIDs etc.

Have a look at [http://linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://linuxtv.org/wiki/index.php/Testing_your_DVB_device)

I know it's really confusing. It took ages to to get my head around it all and get my card working. Unfortunately I've had to push out of my brain what I learnt to make way for new stuff :-)

Keep plugging away, it's fab when it finally works !

---

### Post by My Name on 2008-12-19
ahahahahahahahah. I have Dave playing through mplayer outside myth.
Thanks ianhaycox for the links.
So now I know the usb device is working as it should.
Now how do I transfer this success to myth?

---

### Post by ianhaycox on 2008-12-19
Within the Myth backend setup program there is an option to import your working channels.conf file into Myth.

Run, mythtv-setup and choose the appropriate options to setup the correct TV card etc. and eventually you should get to an option to perform a channel scan, choose the option to import your channels.conf file.

There is no harm in repeating the backend setup several times until you get it to work. I don't know that much about setting up a DVB-T card as I've only got a DVB-S card so maybe someone else might help a bit more here.

At least you know the TV Card works.

Fingers crossed.

---

### Post by My Name on 2008-12-19
ok i'm using dvb scan to create a channels.conf file. unfortunatly it is only picking up 10 channels. If i scan with myth i can get them all but I don't get to watch any of them. 
I can import the channels.conf file into myth and the TV works great, but only for those few channels.
Why can myth find them but dvbscan can't?

---

### Post by My Name on 2008-12-20
OK things are starting to clear up.
I made my own initial scn file using the info in the links you sent me.
That gives me a full list of channels.
The channels I can watch however are still the few I can get with the normal dvbscan
I have come to the conclusion that i need a signal booster.
I guess both my set top boxs have built in boosters so they don't have a problem displaying the channels.
Looks like I'll be buying a booster over chrimbo
I'll post back in the new year when I get back to London

---

### Post by SteveGodfrey on 2008-12-20
I'm in the UK using a DVB-T card (Nova-t & Nova-TD-USB). The only way I could check the signal was using Kaffeine, none of the other methods worked for me. They certainly worked in previous versions of Ubuntu - with these cards infact. So I'm not sure what's going on there.

---

### Post by drifting on 2008-12-21
If you have some channels, and you get round to adding your booster, try a scan of existing transports, worked for me when the older myth scanner used to crash with DVB-T

Paul.

---

### Post by My Name on 2009-01-12
OK chaps I'm back!

I received my booster today and it has made absolutely no difference:(
I found this thread which seems interesting but I have no idea what they are talking about.
[http://ubuntuforums.org/showthread.php?t=752321&highlight=Freecom](http://ubuntuforums.org/showthread.php?t=752321&highlight=Freecom)
I can view Dave and sky 3... oh and E4+1 but nothing else.
Any ideas?

found this too. but still not sure what it means
[http://www.mailinglistarchive.com/mythtv-users@mythtv.org/msg32621.html](http://www.mailinglistarchive.com/mythtv-users@mythtv.org/msg32621.html)

---

### Post by My Name on 2009-01-15
Well if anyone is interested I have got the tv working perfectly.
What I did was to boot into XP, which I have kicking around for just this kind of thing. I installed the freecom usb DVB-t stick and installed software that would alow me to view live tv, I think it was progDVB. I had a look at the frequency setting in the channel info after a full scan.
All I had to do was put these frequencies into mythtv via the channel editor. It was a simple case of rounding up to the nearest three digits. So it would end up looking something like 564000000.
hey presto, full normal telly!!!:guitar:

---

