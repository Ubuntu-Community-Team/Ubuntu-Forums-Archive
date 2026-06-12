---
title: "HDHomerun mythbuntu &quot;error was encountered while displaying video&quot;"
date: 2009-05-20
forum: Mythbuntu
---

### Post by scottac on 2009-05-20
So I am trying to set up my first myth frontend/backend system. I have gone through the setup process and I am getting frustrated with this error.

I have scanned for channels and the tuner has detected a number of QAM-256 channels. I select a channel to start on and then run mythfilldatabase. I open mythfrontend and It stalls for a few seconds and the a message pops up "error was encountered while displaying video". 

As far as troubleshooting this issue I have no clue where to start. I am using the nvidia 180.xx drivers for video. could there be something wrong with my xorg.conf (this is just a guess). 

I have also attempted to change the channel which myth frontend starts on to other detected channels and still nothing. 

What else might I be missing?

Thanks.....

---

### Post by Dewey_Oxberger on 2009-05-20
Is there anything more helpful in the log?  Look in:

/var/log/mythtv/

The frontend and backend logs are in there.

Are you 9.04?

---

### Post by scottac on 2009-05-20
Ok I just looked at the logs however I don't really know what any of it means.

I just ran myth frontend again and here is what is showing up in both the fronend and backend logs

mythbackend.log
```
2009-05-20 16:31:01.872 MainServer::HandleAnnounce Monitor
2009-05-20 16:31:01.877 adding: fredo-mythbackmain as a client (events: 0)
2009-05-20 16:31:01.895 MainServer::HandleAnnounce Monitor
2009-05-20 16:31:01.896 adding: fredo-mythbackmain as a client (events: 1)
2009-05-20 16:31:01.899 MainServer::HandleAnnounce Playback
2009-05-20 16:31:01.901 adding: fredo-mythbackmain as a client (events: 0)
2009-05-20 16:31:01.904 TVRec(1): Changing from None to WatchingLiveTV
2009-05-20 16:31:01.915 TVRec(1): HW Tuner: 1->1
2009-05-20 16:31:01.920 HDHRChan(ffffffff/0): device found at address 192.168.1.3
2009-05-20 16:31:03.035 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-20 16:31:04.137 Finished recording Unknown: channel 1721
2009-05-20 16:31:05.164 Finished recording Unknown: channel 1721
2009-05-20 16:31:05.178 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-20 16:31:05.235 Using runtime prefix = /usr
2009-05-20 16:31:05.237 Empty LocalHostName.
2009-05-20 16:31:05.237 Using localhost value of fredo-mythbackmain
2009-05-20 16:31:05.241 New DB connection, total: 1
2009-05-20 16:31:05.246 Connected to database 'mythconverg' at host: localhost
2009-05-20 16:31:05.260 Closing DB connection named 'DBManager0'
2009-05-20 16:31:05.266 Connected to database 'mythconverg' at host: localhost
2009-05-20 16:31:05.272 New DB connection, total: 2
2009-05-20 16:31:05.279 Connected to database 'mythconverg' at host: localhost
2009-05-20 16:31:05.288 Current Schema Version: 1214
2009-05-20 16:31:05.294 Preview Error: Previewer file '/var/lib/mythtv/recordings/1721_20090520163102.mpg' is not valid.
2009-05-20 16:31:05.308 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1721_20090520163102.mpg'
2009-05-20 16:31:05.323 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1721_20090520163102.mpg.png) exists: 0 readable: 0 size: 0
2009-05-20 16:31:11.687 TVRec(1): Changing from WatchingLiveTV to None
2009-05-20 16:31:12.690 Finished recording Unknown: channel 1721
```


mythfrontend.log
```
2009-05-20 16:30:57.819 New DB connection, total: 2
2009-05-20 16:30:57.820 Connected to database 'mythconverg' at host: localhost
2009-05-20 16:30:57.821 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-05-20 16:30:57.821 Enabled verbose msgs:  important general
2009-05-20 16:30:58.096 No theme dir: /home/fredo/.mythtv/themes/Mythbuntu-8.04
2009-05-20 16:30:58.097 Primary screen 0.
2009-05-20 16:30:58.097 Using screen 0, 1680x1050 at 0,0
2009-05-20 16:30:58.097 No theme dir: /home/fredo/.mythtv/themes/Mythbuntu-8.04
2009-05-20 16:30:58.097 Switching to square mode (Mythbuntu-8.04)
2009-05-20 16:30:58.108 Using the Qt painter
2009-05-20 16:30:58.108 JoystickMenuClient Error: Joystick disabled - Failed to read /home/fredo/.mythtv/joystickmenurc
2009-05-20 16:30:58.109 lirc init success using configuration file: /home/fredo/.mythtv/lircrc
2009-05-20 16:30:58.426 Specified base font 'medium' does not exist for font clock
2009-05-20 16:30:58.427 Specified base font 'medium' does not exist for font small
2009-05-20 16:30:58.427 Specified base font 'medium' does not exist for font medium
2009-05-20 16:30:58.427 Specified base font 'medium' does not exist for font large
2009-05-20 16:30:58.427 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-05-20 16:30:58.512 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-05-20 16:30:58.533 Registering Internal as a media playback plugin.
2009-05-20 16:30:58.576 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-05-20 16:30:58.667 MythMusic adding CD-Writer: 4,0,0 -- CD/DVDW SH-S182M
2009-05-20 16:30:58.667 MythMusic adding CD-Writer: 4,1,0 -- CD/DVDW SH-S182M
2009-05-20 16:30:58.698 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-05-20 16:30:58.732 No theme dir: /home/fredo/.mythtv/themes/Mythbuntu-8.04
2009-05-20 16:31:01.872 Connecting to backend server: 192.168.1.20:6543 (try 1 of 5)
2009-05-20 16:31:01.872 Using protocol version 40
2009-05-20 16:31:01.898 TV: Attempting to change from None to WatchingLiveTV
2009-05-20 16:31:01.899 Using protocol version 40
2009-05-20 16:31:03.048 New DB connection, total: 3
2009-05-20 16:31:03.048 Connected to database 'mythconverg' at host: localhost
2009-05-20 16:31:03.057 NVP: Disabling Audio, params(-1,2,44100)
2009-05-20 16:31:03.082 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-05-20 16:31:03.099 DPMS Deactivated 
2009-05-20 16:31:03.123 OSD Theme Dimensions W: 640 H: 480
2009-05-20 16:31:03.351 TV: Changing from None to WatchingLiveTV
2009-05-20 16:31:03.352 Realtime priority would require SUID as root.
2009-05-20 16:31:03.454 Video timing method: USleep with busy wait
2009-05-20 16:31:11.685 RingBuf(/var/lib/mythtv/recordings/1721_20090520163104.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1721_20090520163104.mpg'.
2009-05-20 16:31:11.685 NVP, Error: JumpToProgram's OpenFile failed.
2009-05-20 16:31:11.685 NVP, Error: Unknown error, exiting decoder
2009-05-20 16:31:11.686 TV: Attempting to change from WatchingLiveTV to None
2009-05-20 16:31:13.158 TV: Changing from WatchingLiveTV to None
2009-05-20 16:31:13.245 DPMS Reactivated.
2009-05-20 16:31:16.213 Deleting UPnP client...
```

---

### Post by scottac on 2009-05-21
And yes. I am running 9.04...

---

### Post by scottac on 2009-05-23
Bump.  

Someone please help...

---

### Post by epi 1:10,000 on 2009-05-23
I wish I could help..  Did you follow the directions @

[http://www.mythtv.org/wiki/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/Silicondust_HDHomeRun)



Is this a dedicated frontend/Backend?  If so why do your logs say 

Connecting to backend server: 192.168.1.20:6543 (try 1 of 5)     ???????

Shouldn't it be

Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)

If you have your frontend setup to connect to your backend @ localhost?



Did you test your hardware w/ something like    [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)     to see if all your hardware is functioning properly?  Memtest, hardrive tools, ect.

9.04 32bit or 64bit?

what are your playback settings?

do you have the VDPAU patches?  

Do you get to the point were you can click on watching Live TV or does it crash before then?  If you click on live TV do you get a black screen, a messed up pixilated picture or decent video before it crashes?

How strong is your cable signal? How many times is it split?  Are you using a cable amplifyer and if so what make, moddel, ect?  if you unhook one of hte cables going to the homerun and hook it up to the digital cable ready tv how many channels does it find?  If you tune to the channels on that tv what kind/quality of picture do you get?

---

