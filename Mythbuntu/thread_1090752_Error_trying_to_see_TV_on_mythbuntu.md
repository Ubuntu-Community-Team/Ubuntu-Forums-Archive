---
title: "Error trying to see TV on mythbuntu"
date: 2009-03-08
forum: Mythbuntu
---

### Post by the_vinz on 2009-03-08
Hello, 

First of all, srroy for my english that isn't the best.
I'm frensh and I have a problem using TV on mythbuntu.

My computer is a athlonXP 2100 , the video card is a ATI Radeon 9500 and the TV card is a WinTV nova-t Digital Terrestrial.

After installing mythbuntu, i tryed to use xine to test my TV card => ok I've got a picture and the sound

I have do the action to install tv card under 
in Capture card setup => Card type DVB DTV Capture Card (v3.x)
in video source => I'have added TNT taht as the configuration bellow:
    France (xmltv)
so the system have added the channels in the channel editor.

But when I try to use the front end, to use watch TV, the screen goes blank for 1 sec and return to the menu.

What's the problem? to I have something wrong ?
What test can I do to give you infos for you to help me ?

Here a part of my lspci:

00:0a.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0a.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0a.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
 
One other info:
My radeon 7500 I have to exits (VGA + DVI) the two are connecter to my LCD TV Screen but I use only the DVI input (the VGA is to have my BIOS info in case of emergency!)


What's the problem? to I have something wrong ?
What test can I do to give you infos for you to help me ?

Second error, when i try to see a avi file (divx), I can see it in xine but when i try to see it in mythbuntu, the screen is blank and I have no sound (but no error!)


In advance, thank you !

---

### Post by scary_jeff on 2009-03-08
Hi

Have you looked in /var/log/mythtv/mythfrontend.log ? There should be an error in that file when you try and watch TV. Also, you set up the xml listing grabber, but did you actually do a channel scan? You have to do this in the 'inputs' section of the backend configuration.

---

### Post by the_vinz on 2009-03-09
Hello

I do not find any error in my log file:
Here is the content of if:

```
2009-03-08 23:35:19.430 New DB connection, total: 2
2009-03-08 23:35:19.431 Connected to database 'mythconverg' at host: localhost
2009-03-08 23:35:19.435 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-08 23:35:19.436 Enabled verbose msgs:  important general
2009-03-08 23:35:23.911 Writing settings file /home/vince/.mythtv/mysql.txt
2009-03-08 23:35:23.912 Closing DB connection named 'DBManager1'
2009-03-08 23:35:23.912 Closing DB connection named 'DBManager0'
2009-03-08 23:35:23.913 Connected to database 'mythconverg' at host: localhost
2009-03-08 23:35:23.949 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-08 23:35:23.952 Total desktop dim: 1280x1024, over 1 screen[s].
2009-03-08 23:35:23.953 Primary screen 0.
2009-03-08 23:35:23.962 Using screen 0, 1280x1024 at 0,0
2009-03-08 23:35:23.963 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-08 23:35:23.964 Switching to square mode (Mythbuntu-8.04)
2009-03-08 23:35:24.175 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-08 23:35:24.176 lirc_init failed for mythtv, see preceding messages
2009-03-08 23:35:24.177 JoystickMenuClient Error: Joystick disabled - Failed to                                                                                                                                read /home/vince/.mythtv/joystickmenurc
2009-03-08 23:36:51.147 Specified base font 'medium' does not exist for font clo                                                                                                                               ck
2009-03-08 23:36:51.147 Specified base font 'medium' does not exist for font sma                                                                                                                               ll
2009-03-08 23:36:51.147 Specified base font 'medium' does not exist for font med                                                                                                                               ium
2009-03-08 23:36:51.147 Specified base font 'medium' does not exist for font lar                                                                                                                               ge
2009-03-08 23:36:51.159 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/ba                                                                                                                               se.xml
2009-03-08 23:36:51.455 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-08 23:36:51.750 Registering Internal as a media playback plugin.
2009-03-08 23:36:51.847 Upgrading to MythArchive schema version 1001
2009-03-08 23:36:51.877 Connected to database 'mythconverg' at host: localhost
2009-03-08 23:36:51.996 Inserting MythFlix initial database information.
2009-03-08 23:36:51.996 Upgrading to MythFlix schema version 1000
2009-03-08 23:36:52.035 Upgrading to MythFlix schema version 1001
2009-03-08 23:36:52.338 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-08 23:36:52.405 Setting Up MythMovies Database Tables
2009-03-08 23:36:52.504 MythMovies Database Setup Complete
2009-03-08 23:36:52.984 Upgrading to MythMusic schema version 1007
2009-03-08 23:36:53.040 Upgrading to MythMusic schema version 1008
2009-03-08 23:36:53.234 Upgrading to MythMusic schema version 1009
2009-03-08 23:36:53.276 Upgrading to MythMusic schema version 1010
2009-03-08 23:36:53.311 Updating music_albumart image types
2009-03-08 23:36:53.316 Upgrading to MythMusic schema version 1011
2009-03-08 23:36:53.318 Upgrading to MythMusic schema version 1012
2009-03-08 23:36:53.346 Upgrading to MythMusic schema version 1013
2009-03-08 23:36:53.487 Failed to run 'cdrecord --scanbus'
2009-03-08 23:36:53.493 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-08 23:36:53.500 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-08 23:36:53.611 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.144:5060 NAT address 192.168.0.144
SIP: Cannot register; proxy, username or password not set
2009-03-08 23:36:54.198 Inserting MythWeather initial database information.
2009-03-08 23:36:54.198 Upgrading to MythWeather schema version 1000
2009-03-08 23:36:54.599 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-08 23:37:00.723 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5                                                                                                                               )
2009-03-08 23:37:00.796 Using protocol version 40
Destroying SipFsm object
2009-03-08 23:37:03.411 Deleting UPnP client...
Starting mythfrontend.real..
2009-03-08 23:42:31.899 New DB connection, total: 2
2009-03-08 23:42:31.900 Connected to database 'mythconverg' at host: localhost
2009-03-08 23:42:31.903 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-03-08 23:42:31.903 Enabled verbose msgs:  important general
2009-03-08 23:42:35.742 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-08 23:42:35.744 Total desktop dim: 1280x1024, over 1 screen[s].
2009-03-08 23:42:35.745 Primary screen 0.
2009-03-08 23:42:35.746 Using screen 0, 1280x1024 at 0,0
2009-03-08 23:42:35.749 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-08 23:42:35.750 Switching to square mode (Mythbuntu-8.04)
2009-03-08 23:42:35.984 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-08 23:42:35.984 lirc_init failed for mythtv, see preceding messages
2009-03-08 23:42:36.007 JoystickMenuClient Error: Joystick disabled - Failed to                                                                                                                                read /home/vince/.mythtv/joystickmenurc
2009-03-08 23:42:39.709 Specified base font 'medium' does not exist for font clo                                                                                                                               ck
2009-03-08 23:42:39.709 Specified base font 'medium' does not exist for font sma                                                                                                                               ll
2009-03-08 23:42:39.709 Specified base font 'medium' does not exist for font med                                                                                                                               ium
2009-03-08 23:42:39.709 Specified base font 'medium' does not exist for font lar                                                                                                                               ge
2009-03-08 23:42:39.711 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/ba                                                                                                                               se.xml
2009-03-08 23:42:39.958 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-08 23:42:40.139 Registering Internal as a media playback plugin.
2009-03-08 23:42:40.457 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-08 23:42:40.949 Failed to run 'cdrecord --scanbus'
2009-03-08 23:42:40.954 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-08 23:42:40.959 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-08 23:42:41.039 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.144:5060 NAT address 192.168.0.144
SIP: Cannot register; proxy, username or password not set
2009-03-08 23:42:41.535 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-08 23:45:54.967 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5                                                                                                                               )
2009-03-08 23:45:54.980 Using protocol version 40
Destroying SipFsm object
2009-03-08 23:45:57.247 Deleting UPnP client...

```

But I've seen that I have a new error.
I cannot watch a video file: The screen stay black/bleu 

Where can I search  the error ?

---

### Post by the_vinz on 2009-03-09
Ok, i have make the association channels DVB card
That's ok.

But the error persist:
I can ear sound of TV and of the videos but the screen stay bleu ! I cannot have any picture...
I don't know where to search, can someone help me ?

Here is the last part of my /var/log/mythtv/mythfrontend.log

```
2009-03-09 19:51:11.551 JoystickMenuClient Error: Joystick disabled - Failed to read /home/vince/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-09 19:51:11.567 lirc_init failed for mythtv, see preceding messages
2009-03-09 19:51:14.012 Specified base font 'medium' does not exist for font clock
2009-03-09 19:51:14.013 Specified base font 'medium' does not exist for font small
2009-03-09 19:51:14.013 Specified base font 'medium' does not exist for font medium
2009-03-09 19:51:14.013 Specified base font 'medium' does not exist for font large
2009-03-09 19:51:14.015 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-03-09 19:51:14.240 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-09 19:51:14.299 Registering Internal as a media playback plugin.
2009-03-09 19:51:14.536 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-09 19:51:14.709 Failed to run 'cdrecord --scanbus'
2009-03-09 19:51:14.715 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-09 19:51:14.722 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-09 19:51:14.779 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.144:5060 NAT address 192.168.0.144
SIP: Cannot register; proxy, username or password not set
2009-03-09 19:51:15.018 No theme dir: /home/vince/.mythtv/themes/Mythbuntu-8.04
2009-03-09 19:51:18.995 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-09 19:51:18.997 Using protocol version 40
2009-03-09 19:51:19.036 TV: Attempting to change from None to WatchingLiveTV
2009-03-09 19:51:19.038 Using protocol version 40
2009-03-09 19:51:20.250 New DB connection, total: 3
2009-03-09 19:51:20.251 DPMS Deactivated 
2009-03-09 19:51:20.252 New DB connection, total: 4
2009-03-09 19:51:20.253 Connected to database 'mythconverg' at host: localhost
2009-03-09 19:51:20.250 Connected to database 'mythconverg' at host: localhost
2009-03-09 19:51:20.286 NVP: Disabling Audio, params(-1,2,44100)
2009-03-09 19:51:20.384 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2009-03-09 19:51:20.552 OSD Theme Dimensions W: 640 H: 480
2009-03-09 19:51:22.199 TV: Changing from None to WatchingLiveTV
2009-03-09 19:51:22.220 Realtime priority would require SUID as root.
2009-03-09 19:51:25.216 Video timing method: USleep with busy wait
2009-03-09 19:51:25.518 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'
2009-03-09 19:51:25.818 AFD: Opened codec 0x9e02e40, id(MPEG2VIDEO) type(Video)
2009-03-09 19:51:25.819 AFD: codec MP3 has 2 channels
2009-03-09 19:51:25.819 AFD: Opened codec 0x9e002b0, id(MP3) type(Audio)
2009-03-09 19:51:25.819 AFD: codec MP3 has 2 channels
2009-03-09 19:51:25.819 AFD: Opened codec 0x9e01cb0, id(MP3) type(Audio)
2009-03-09 19:51:25.819 AFD: codec AC3 has 5 channels
2009-03-09 19:51:25.835 AFD: Opened codec 0x9e02020, id(AC3) type(Audio)
2009-03-09 19:51:25.835 AFD: codec MP3 has 2 channels
2009-03-09 19:51:25.835 AFD: Opened codec 0x9e023a0, id(MP3) type(Audio)
2009-03-09 19:51:25.835 AFD: Opened codec 0x9e73810, id(DVB_SUBTITLE) type(Subtitle)
2009-03-09 19:51:25.835 AFD: Opened codec 0x9e73d00, id(DVB_SUBTITLE) type(Subtitle)
2009-03-09 19:51:25.925 Opening audio device 'default'. ch 2(2) sr 48000
2009-03-09 19:51:25.926 Opening ALSA audio device 'default'.
2009-03-09 19:51:25.971 NVP: Enabling Audio
2009-03-09 19:51:32.806 NVP: prebuffering pause
2009-03-09 19:51:36.819 NVP: Prebuffer wait timed out 10 times.
2009-03-09 19:51:38.420 NVP: Prebuffer wait timed out 10 times.
2009-03-09 19:51:38.779 AFD: Opened codec 0xa3a768c0, id(MPEG2VIDEO) type(Video)
2009-03-09 19:51:38.780 AFD: codec MP3 has 2 channels
2009-03-09 19:51:38.780 AFD: Opened codec 0xa3a76c40, id(MP3) type(Audio)
2009-03-09 19:51:38.780 AFD: Opened codec 0xa3a77230, id(DVB_SUBTITLE) type(Subtitle)
2009-03-09 19:52:35.471 TV: Attempting to change from WatchingLiveTV to None
2009-03-09 19:52:35.986 TV: Changing from WatchingLiveTV to None
2009-03-09 19:52:36.092 DPMS Reactivated.
Destroying SipFsm object 
2009-03-09 19:52:43.541 Deleting UPnP client...

```

---

