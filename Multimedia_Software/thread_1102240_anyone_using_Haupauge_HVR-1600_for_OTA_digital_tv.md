---
title: "anyone using Haupauge HVR-1600 for OTA digital tv?"
date: 2009-03-21
forum: Multimedia Software
---

### Post by salmonsm on 2009-03-21
I have been through hell and back trying to get this to work. I can get the mythbuntu desktop on my TV and in Setup I can see the HVR-1600 is picking up stations, but when I choose "watch tv" it flickers for a moment, then nothing.

here are the logs.



thanks for any help.

==> /var/log/mythtv/mtd.log <==
mtd started at Sat Mar 21 11:31:21 2009
mtd is running on a host called thinkcentre
11:31:21: Waiting for connections/jobs
11:31:21: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-03-21 10:54:56.244 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-21 11:09:56.267 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-21 11:24:56.292 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-21 11:29:50.538 MainServer::HandleAnnounce Monitor
2009-03-21 11:29:50.552 adding: thinkcentre as a client (events: 0)
2009-03-21 11:29:50.553 MainServer::HandleAnnounce Monitor
2009-03-21 11:29:50.555 adding: thinkcentre as a client (events: 1)
2009-03-21 11:29:50.587 MainServer::HandleAnnounce Playback
2009-03-21 11:29:50.625 adding: thinkcentre as a client (events: 0)
2009-03-21 11:29:50.661 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:29:50.680 TVRec(4): HW Tuner: 4->4
2009-03-21 11:29:50.691 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:29:50.692 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:29:50.693 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:29:50.695 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:10.556 Using runtime prefix = /usr
2009-03-21 11:31:10.591 Empty LocalHostName.
2009-03-21 11:31:10.595 Using localhost value of thinkcentre
2009-03-21 11:31:10.637 New DB connection, total: 1
2009-03-21 11:31:10.738 Connected to database 'mythconverg' at host: localhost
2009-03-21 11:31:10.793 Closing DB connection named 'DBManager0'
2009-03-21 11:31:10.881 Connected to database 'mythconverg' at host: localhost
2009-03-21 11:31:10.888 New DB connection, total: 2
2009-03-21 11:31:10.890 Connected to database 'mythconverg' at host: localhost
2009-03-21 11:31:10.928 Current Schema Version: 1214
Starting up as the master server.
2009-03-21 11:31:11.228 New DB connection, total: 3
2009-03-21 11:31:11.288 Connected to database 'mythconverg' at host: localhost
2009-03-21 11:31:11.406 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:11.469 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:13.980 New DB scheduler connection
2009-03-21 11:31:13.986 Connected to database 'mythconverg' at host: localhost
2009-03-21 11:31:14.048 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-03-21 11:31:14.068 Main::Registering HttpStatus Extension
2009-03-21 11:31:14.069 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-21 11:31:14.070 Enabled verbose msgs:  important general
2009-03-21 11:31:14.100 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-03-21 11:31:16.996 Reschedule requested for id -1.
2009-03-21 11:31:17.186 Scheduled 0 items in 0.2 = 0.07 match + 0.12 place
2009-03-21 11:31:17.199 Seem to be woken up by USER
2009-03-21 11:31:35.505 MainServer::HandleAnnounce Monitor
2009-03-21 11:31:35.511 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:35.513 MainServer::HandleAnnounce Monitor
2009-03-21 11:31:35.514 adding: thinkcentre as a client (events: 1)
2009-03-21 11:31:35.521 MainServer::HandleAnnounce Playback
2009-03-21 11:31:35.523 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:35.529 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:35.536 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:35.541 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:35.542 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:35.547 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:35.567 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:37.129 MainServer::HandleAnnounce Playback
2009-03-21 11:31:37.132 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:37.141 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:37.147 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:37.155 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:37.157 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:37.159 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:37.163 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:37.647 MainServer::HandleAnnounce Playback
2009-03-21 11:31:37.649 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:37.656 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:37.663 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:37.671 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:37.675 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:37.684 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:37.691 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:38.061 MainServer::HandleAnnounce Playback
2009-03-21 11:31:38.064 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:38.067 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:38.071 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:38.076 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:38.090 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:38.091 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:38.095 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:38.321 MainServer::HandleAnnounce Playback
2009-03-21 11:31:38.324 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:38.332 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:38.339 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:38.344 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:38.345 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:38.357 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:38.359 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:38.521 MainServer::HandleAnnounce Playback
2009-03-21 11:31:38.524 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:38.533 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:38.539 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:38.543 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:38.544 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:38.547 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:38.551 TVRec(4): Changing from WatchingLiveTV to None
2009-03-21 11:31:38.758 MainServer::HandleAnnounce Playback
2009-03-21 11:31:38.759 adding: thinkcentre as a client (events: 0)
2009-03-21 11:31:38.764 TVRec(4): Changing from None to WatchingLiveTV
2009-03-21 11:31:38.771 TVRec(4): HW Tuner: 4->4
2009-03-21 11:31:38.777 DTVMux, Error: Could not find tuning parameters for mplex 32767
2009-03-21 11:31:38.782 DVBChan(4:0) Error: SetChannelByString(6): Failed to initialize multiplex options
2009-03-21 11:31:38.783 TVRec(4) Error: Failed to set channel to 6. Reverting to kState_None
2009-03-21 11:31:38.787 TVRec(4): Changing from WatchingLiveTV to None

==> /var/log/mythtv/mythfrontend.log <==
2009-03-21 11:29:50.704 GetEntryAt(-1) failed.
2009-03-21 11:29:50.734 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:29:50.734 TV Error: LiveTV not successfully started
2009-03-21 11:29:50.735 TV Error: LiveTV not successfully started
2009-03-21 11:29:50.831 TV: Deleting TV Chain in destructor
2009-03-21 11:29:50.838 DPMS Deactivated 
2009-03-21 11:29:50.840 DPMS Reactivated.
Destroying SipFsm object 
2009-03-21 11:30:01.408 Deleting UPnP client...
Starting mythfrontend.real..
2009-03-21 11:31:26.582 New DB connection, total: 2
2009-03-21 11:31:26.583 Connected to database 'mythconverg' at host: localhost
2009-03-21 11:31:26.587 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-03-21 11:31:26.587 Enabled verbose msgs:  important general
2009-03-21 11:31:28.650 No theme dir: /home/salmonsm/.mythtv/themes/Retro
2009-03-21 11:31:28.652 Primary screen 0.
2009-03-21 11:31:28.653 Using screen 0, 1024x768 at 0,0
2009-03-21 11:31:28.653 No theme dir: /home/salmonsm/.mythtv/themes/Retro
2009-03-21 11:31:28.654 Switching to square mode (Retro)
2009-03-21 11:31:28.889 Using the Qt painter
2009-03-21 11:31:28.889 JoystickMenuClient Error: Joystick disabled - Failed to read /home/salmonsm/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-03-21 11:31:28.889 lirc_init failed for mythtv, see preceding messages
2009-03-21 11:31:29.963 Loading from: /usr/share/mythtv/themes/Retro/base.xml
2009-03-21 11:31:30.100 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-03-21 11:31:30.242 Registering Internal as a media playback plugin.
2009-03-21 11:31:30.423 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-03-21 11:31:30.713 Failed to run 'cdrecord --scanbus'
2009-03-21 11:31:30.718 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-03-21 11:31:30.723 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-03-21 11:31:30.778 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.105:5060 NAT address 192.168.1.105
SIP: Cannot register; proxy, username or password not set
2009-03-21 11:31:31.058 No theme dir: /home/salmonsm/.mythtv/themes/Retro
2009-03-21 11:31:35.489 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-03-21 11:31:35.490 Using protocol version 40
2009-03-21 11:31:35.519 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:35.521 Using protocol version 40
2009-03-21 11:31:35.572 GetEntryAt(-1) failed.
2009-03-21 11:31:35.595 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:35.595 TV Error: LiveTV not successfully started
2009-03-21 11:31:35.596 TV Error: LiveTV not successfully started
2009-03-21 11:31:35.627 TV: Deleting TV Chain in destructor
2009-03-21 11:31:35.634 DPMS Deactivated 
2009-03-21 11:31:35.636 DPMS Reactivated.
2009-03-21 11:31:37.125 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:37.129 Using protocol version 40
2009-03-21 11:31:37.168 GetEntryAt(-1) failed.
2009-03-21 11:31:37.168 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:37.169 TV Error: LiveTV not successfully started
2009-03-21 11:31:37.169 TV Error: LiveTV not successfully started
2009-03-21 11:31:37.228 TV: Deleting TV Chain in destructor
2009-03-21 11:31:37.237 DPMS Deactivated 
2009-03-21 11:31:37.237 DPMS Reactivated.
2009-03-21 11:31:37.643 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:37.646 Using protocol version 40
2009-03-21 11:31:37.700 GetEntryAt(-1) failed.
2009-03-21 11:31:37.700 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:37.701 TV Error: LiveTV not successfully started
2009-03-21 11:31:37.701 TV Error: LiveTV not successfully started
2009-03-21 11:31:37.746 TV: Deleting TV Chain in destructor
2009-03-21 11:31:37.755 DPMS Deactivated 
2009-03-21 11:31:37.755 DPMS Reactivated.
2009-03-21 11:31:38.059 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:38.061 Using protocol version 40
2009-03-21 11:31:38.100 GetEntryAt(-1) failed.
2009-03-21 11:31:38.100 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:38.101 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.101 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.162 TV: Deleting TV Chain in destructor
2009-03-21 11:31:38.171 DPMS Deactivated 
2009-03-21 11:31:38.171 DPMS Reactivated.
2009-03-21 11:31:38.317 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:38.321 Using protocol version 40
2009-03-21 11:31:38.367 GetEntryAt(-1) failed.
2009-03-21 11:31:38.367 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:38.368 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.368 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.421 TV: Deleting TV Chain in destructor
2009-03-21 11:31:38.430 DPMS Deactivated 
2009-03-21 11:31:38.430 DPMS Reactivated.
2009-03-21 11:31:38.516 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:38.520 Using protocol version 40
2009-03-21 11:31:38.556 GetEntryAt(-1) failed.
2009-03-21 11:31:38.556 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:38.557 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.557 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.620 TV: Deleting TV Chain in destructor
2009-03-21 11:31:38.630 DPMS Deactivated 
2009-03-21 11:31:38.630 DPMS Reactivated.
2009-03-21 11:31:38.754 TV: Attempting to change from None to WatchingLiveTV
2009-03-21 11:31:38.757 Using protocol version 40
2009-03-21 11:31:38.792 GetEntryAt(-1) failed.
2009-03-21 11:31:38.792 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2009-03-21 11:31:38.792 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.793 TV Error: LiveTV not successfully started
2009-03-21 11:31:38.857 TV: Deleting TV Chain in destructor
2009-03-21 11:31:38.869 DPMS Deactivated 
2009-03-21 11:31:38.869 DPMS Reactivated.

---

### Post by steefjeqv on 2009-03-22
Hi,

Try using Kaffeine or MeTV to test your TV card.


Greetings,
Steven

---

### Post by salmonsm on 2009-03-22
> **steefjeqv said:**
> Hi,

Try using Kaffeine or MeTV to test your TV card.


Greetings,
Steven

Thanks for the reply, Steven. I finally managed to install MeTV but it says the card is busy. 

I've tried a simple test- cat/dev/video0 > test.mpg and it does display something, so I think the card works. But I keep getting errors about the program info not loading.  

Supposedly this card works with MythTV but it's not official. 

What should I try?

Thanks.

---

### Post by steefjeqv on 2009-03-23
Hi,

It seems this card needs additional firmware.

Did you already install it ?

You can download it here :

[http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz]("http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz")

Untar it and copy the file to /lib/firmware/yourkernelversion.

If this doesn't help you can try installing the latest v4l drivers :

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Retrieving_the_Latest_V4L-DVB_Source_Code]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Retrieving_the_Latest_V4L-DVB_Source_Code")

Greetings,
Steven

---

### Post by MarioHTPC on 2009-04-29
HI I have the same problem with my HVR-1600  I install Mythbuntu 9.04 the latest version. I upgrade the firmware. The digital parts of the card work well but the analog one doesn 't play a black page for 1 to 10 secondes and the menu came back. I try VLC player  and when i configure this card with VLC the analog  work on VLC but not on mythbuntu. I also try mythDora and its the same problem. Its like the problem is comming from mythtv setup.  
 
I search also for help.
 
Thanks.

---

