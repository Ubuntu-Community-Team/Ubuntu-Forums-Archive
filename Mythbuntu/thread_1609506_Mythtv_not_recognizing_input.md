---
title: "Mythtv not recognizing input?"
date: 2010-10-30
forum: Mythbuntu
---

### Post by chee on 2010-10-30
First,  here is my setup:
Dell Inspiron 6400
Haupauge HVR-950Q USB tuner card
Ubuntu 10.10

SO I tried setting up Mythtv when I first installed Ubuntu about a week ago but had no luck,  I tried tweaking some things and messed it up even further to the point where I couldn't even login to the mysql database.  So I reinstalled Mythtv and all Mysql packages and I can now get into both frontend and backend again.  Nice.  

My problem is that when I set up my tuner card I go into the backend and go to Capture Cards,  it recognizes my HVR-950Q as it it lists it in the "Probed info",  I use the "Analog V4L capture card" setting as I am looking to use it with my basic cable.  Everything else I leave as is.

I then go to input connections and I have this:
[V4L: /dev/video0](television) -> (none)
[V4L: /dev/video0](composite) -> (none)
[V4L: /dve/video0](s-video) -> (none)

so I am guessing that I have something set up wrong as I can use my tuner card with both TvTime and Kaffeine fine.

I realize this might be pretty basic and I apologize ahead of time.  Please be patient as I really do want to learn while fixing this problem.

Thank you

---

### Post by tgm4883 on 2010-10-30
You need to set it up in that screen. In mythtv-setup you go through all of the steps. Take a look at [http://www.mythbuntu.org/wiki/installation-guide](http://www.mythbuntu.org/wiki/installation-guide)

---

### Post by chee on 2010-10-30
so I set up a video source called Analog,  then went into the input section and selected that for the [V4L: /dev/video0] (television),  which then allowed me to scan for channels (sweeet).  So I scanned and got the same list as in TvTime (sounds good). 

So this is progress.......  but much more complicated then I thought it would be.  I know people are probably rolling their eyes thinking "God,  what a noob,  he wants it to be plug and play!",  but to be honest I think I could probably figure it out if not for all the foreign terms,  and the problem with that is that those terms are not easily translated in the context that I am looking for.

I appreciate the link but I really didn't get anything from it.
Sorry for the basic/general question but again I just don't know where to start sometimes and get frustrated.

Hopefully I pull through haha!

---

### Post by chee on 2010-10-30
Alrighty,   so now I can schedule recordings (though I haven't checked to see if it will actually record anything),  but I still cannot watch tv.   I press enter on watch TV and it says please wait and then goes back to the same screen.  

To be honest I don't really care about watching TV with Mythtv as I can use Kaffeine and TvTime,  I just want to record TV shows here and there.

I do honestly appreciate any help given.  Thank you

---

### Post by LowSky on 2010-10-30
with some tuners if you use the tuner with another program, while mythtv is running (and technicallly the backend is always running). then mythtv will think the tuner is busy and it will not work unless you restsrt the backend or reboot

i know from experience that myth can be frustrating. i turned my back it the first time i tried it. if you need help ask. and if you nt understand a term, ask! we are here to help.

---

### Post by chee on 2010-10-30
Thanks for the tip,   I will try rebooting and not using the other programs,  see where I get,  at least I have made progress!

---

### Post by nickrout on 2010-10-30
> **chee said:**
> Thanks for the tip,   I will try rebooting and not using the other programs,  see where I get,  at least I have made progress!

try looking at your log  files, /var/log/mythtv/mythfrontend.log for a start

---

### Post by tgm4883 on 2010-10-30
Recording happens in the backend, look at /var/log/mythtv/mythbackend.log

If you can't watch live tv on it, likely you cannot record either. Those are really the same thing.

---

### Post by chee on 2010-11-01
So I found both those files but am unsure of what I am looking for (sorry guys). I maybe try both the frontend and backend and then post the latest entry in the log?

---

### Post by tgm4883 on 2010-11-01
Post the last 100 lines of the logs after trying it.

---

### Post by chee on 2010-11-01
sorry if this is too much but I am honestly lost here,  I am a windows dummie so setup has always been automatic or nothing :(
Here is the backend log (pretty long so again sorry)

(there were a bunch of lines that were the same as this first one but with small time differences,  so I thought I could shorten it up by getting rid of those)
2010-11-01 09:05:58.540 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 09:07:14.704 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 09:22:15.306 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 09:37:15.836 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 09:52:16.365 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 10:07:16.921 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 10:22:17.165 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 10:37:17.576 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 10:52:17.819 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 10:57:18.931 MainServer::ANN Monitor
2010-11-01 10:57:19.127 adding: wes-MM061 as a client (events: 0)
2010-11-01 10:57:19.183 MainServer::ANN Monitor
2010-11-01 10:57:19.227 adding: wes-MM061 as a client (events: 1)
2010-11-01 11:27:17.661 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-01 11:27:17.761 Using runtime prefix = /usr
2010-11-01 11:27:17.817 Using configuration directory = /home/mythtv/.mythtv
2010-11-01 11:27:17.906 Empty LocalHostName.
2010-11-01 11:27:17.972 Using localhost value of wes-MM061
2010-11-01 11:27:18.063 New DB connection, total: 1
2010-11-01 11:27:18.114 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:27:18.162 Closing DB connection named 'DBManager0'
2010-11-01 11:27:18.207 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:27:18.267 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-01 11:27:18.321 MythBackend: Starting up as the master server.
2010-11-01 11:27:18.430 New DB connection, total: 2
2010-11-01 11:27:18.474 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:27:18.591 New DB connection, total: 3
2010-11-01 11:27:18.652 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:27:28.580 Channel(/dev/video0) Error: GetCurrentChannelNum(438): Failed to find Channel
2010-11-01 11:27:28.704 Channel(/dev/video0)::TuneTo(438): Error, failed to find channel.
2010-11-01 11:27:36.715 New DB scheduler connection
2010-11-01 11:27:36.822 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:27:37.003 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-11-01 11:27:37.054 Main::Registering HttpStatus Extension
2010-11-01 11:27:37.126 Enabled verbose msgs:  important general
2010-11-01 11:27:37.192 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 11:27:39.978 Reschedule requested for id -1.
2010-11-01 11:27:40.272 Scheduled 0 items in 0.3 = 0.11 match + 0.18 place
2010-11-01 11:27:40.339 Seem to be woken up by USER
2010-11-01 11:28:56.889 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-01 11:42:18.973 MainServer::ANN Monitor
2010-11-01 11:42:19.800 adding: wes-MM061 as a client (events: 0)
2010-11-01 11:42:20.124 MainServer::ANN Monitor
2010-11-01 11:42:20.189 adding: wes-MM061 as a client (events: 1)
2010-11-01 11:42:22.115 MainServer::ANN Playback
2010-11-01 11:42:22.174 adding: wes-MM061 as a client (events: 0)
2010-11-01 11:42:22.232 TVRec(1): Changing from None to WatchingLiveTV
2010-11-01 11:42:22.324 TVRec(1): HW Tuner: 1->1
2010-11-01 11:42:23.896 Channel(/dev/video0) Error: GetCurrentChannelNum(438): Failed to find Channel
2010-11-01 11:42:23.951 Channel(/dev/video0)::TuneTo(438): Error, failed to find channel.
2010-11-01 11:42:24.007 TVRec(1) Error: Failed to set channel to 438. Reverting to kState_None
2010-11-01 11:42:24.063 TVRec(1): Changing from WatchingLiveTV to None
2010-11-01 11:43:57.010 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by chee on 2010-11-01
Here is the front end log:
Starting mythfrontend.real..
2010-11-01 10:57:09.900 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-01 10:57:09.933 Using runtime prefix = /usr
2010-11-01 10:57:09.933 Using configuration directory = /home/wes/.mythtv
2010-11-01 10:57:10.424 Empty LocalHostName.
2010-11-01 10:57:10.424 Using localhost value of wes-MM061
2010-11-01 10:57:10.618 New DB connection, total: 1
2010-11-01 10:57:11.212 Connected to database 'mythconverg' at host: localhost
2010-11-01 10:57:11.344 Closing DB connection named 'DBManager0'
2010-11-01 10:57:11.431 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-01 10:57:11.433 DPMS is active.
2010-11-01 10:57:11.456 Primary screen: 0.
2010-11-01 10:57:11.457 Connected to database 'mythconverg' at host: localhost
2010-11-01 10:57:11.707 Using screen 0, 1280x800 at 0,0
2010-11-01 10:57:11.849 Desktop video mode: 1280x800 60.0024 Hz
2010-11-01 10:57:12.650 MythUI Image Cache size set to 20971520 bytes
2010-11-01 10:57:13.009 AudioPulseUtil: Suspend Success
2010-11-01 10:57:13.010 Enabled verbose msgs:  important general
2010-11-01 10:57:13.115 Primary screen: 0.
2010-11-01 10:57:13.116 Using screen 0, 1280x800 at 0,0
2010-11-01 10:57:13.133 Using theme base resolution of 1280x720
2010-11-01 10:57:13.161 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-11-01 10:57:13.162 JoystickMenuThread Error: Joystick disabled - Failed to read /home/wes/.mythtv/joystickmenurc
2010-11-01 10:57:13.586 Using Frameless Window
2010-11-01 10:57:13.587 Using Full Screen Window
2010-11-01 10:57:14.352 Using the Qt painter
2010-11-01 10:57:14.968 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-11-01 10:57:15.108 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-11-01 10:57:15.166 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-11-01 10:57:15.166 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-01 10:57:15.345 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-01 10:57:17.501 Registering Internal as a media playback plugin.
2010-11-01 10:57:17.560 No plugins directory /usr/lib/mythtv/plugins
2010-11-01 10:57:17.597 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-01 10:57:17.598 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-01 10:57:17.598 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-01 10:57:17.602 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-11-01 10:57:17.719 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-01 10:57:17.721 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-01 10:57:18.659 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-01 10:57:18.931 Using protocol version 23056
2010-11-01 10:57:28.712 AudioPulseUtil: Resume Success
2010-11-01 10:57:28.713 Deleting UPnP client...
Starting mythfrontend.real..
2010-11-01 11:42:15.288 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-01 11:42:15.288 Using runtime prefix = /usr
2010-11-01 11:42:15.288 Using configuration directory = /home/wes/.mythtv
2010-11-01 11:42:15.856 Empty LocalHostName.
2010-11-01 11:42:15.856 Using localhost value of wes-MM061
2010-11-01 11:42:15.869 New DB connection, total: 1
2010-11-01 11:42:15.878 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:42:15.879 Closing DB connection named 'DBManager0'
2010-11-01 11:42:15.900 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-01 11:42:15.902 DPMS is active.
2010-11-01 11:42:15.905 Primary screen: 0.
2010-11-01 11:42:15.906 Connected to database 'mythconverg' at host: localhost
2010-11-01 11:42:15.909 Using screen 0, 1280x800 at 0,0
2010-11-01 11:42:15.949 Desktop video mode: 1280x800 60.0024 Hz
2010-11-01 11:42:16.740 MythUI Image Cache size set to 20971520 bytes
2010-11-01 11:42:16.786 AudioPulseUtil: Suspend Success
2010-11-01 11:42:16.786 Enabled verbose msgs:  important general
2010-11-01 11:42:16.798 Primary screen: 0.
2010-11-01 11:42:16.799 Using screen 0, 1280x800 at 0,0
2010-11-01 11:42:16.800 Using theme base resolution of 1280x720
2010-11-01 11:42:16.807 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-11-01 11:42:16.807 JoystickMenuThread Error: Joystick disabled - Failed to read /home/wes/.mythtv/joystickmenurc
2010-11-01 11:42:16.846 Using Frameless Window
2010-11-01 11:42:16.846 Using Full Screen Window
2010-11-01 11:42:17.080 Using the Qt painter
2010-11-01 11:42:17.231 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-11-01 11:42:17.243 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-11-01 11:42:17.253 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-11-01 11:42:17.253 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-01 11:42:17.261 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-01 11:42:17.875 Registering Internal as a media playback plugin.
2010-11-01 11:42:17.876 No plugins directory /usr/lib/mythtv/plugins
2010-11-01 11:42:17.888 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-01 11:42:17.888 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-01 11:42:17.889 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-01 11:42:17.891 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-11-01 11:42:17.972 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-01 11:42:17.979 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-01 11:42:18.807 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-01 11:42:18.973 Using protocol version 23056
2010-11-01 11:42:22.113 TV: Attempting to change from None to WatchingLiveTV
2010-11-01 11:42:22.113 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-01 11:42:22.114 Using protocol version 23056
2010-11-01 11:42:22.230 Spawning LiveTV Recorder -- begin
2010-11-01 11:42:24.140 Spawning LiveTV Recorder -- end
2010-11-01 11:42:24.141 GetEntryAt(-1) failed.
2010-11-01 11:42:24.183 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2010-11-01 11:42:24.183 TV Error: HandleStateChange(): LiveTV not successfully started
2010-11-01 11:42:24.183 We have a RingBuffer
2010-11-01 11:42:24.245 TV Error: LiveTV not successfully started
2010-11-01 11:42:24.313 ScreenSaverX11Private: DPMS Deactivated 1
2010-11-01 11:42:24.315 ScreenSaverX11Private: DPMS Reactivated 1
2010-11-01 11:42:33.585 AudioPulseUtil: Resume Success
2010-11-01 11:42:33.585 Deleting UPnP client...

---

### Post by chee on 2010-11-01
I appreciate any help with this BTW.  I am not looking for someone to just say "this isn't set right,  go to this screen and change that, done."  though again any help would be great.  I am more looking for somebody to say "this is your problem,  here's how I know that and here is how you fix it",  so that is the future I might be able to apply some things learned to other instances.

 Thank you again.

---

### Post by tgm4883 on 2010-11-01
Looks like you have it set to a bad channel (438), judging by the log messages below.

```
2010-11-01 11:42:23.896 Channel(/dev/video0) Error: GetCurrentChannelNum(438): Failed to find Channel
2010-11-01 11:42:23.951 Channel(/dev/video0)::TuneTo(438): Error, failed to find channel.
2010-11-01 11:42:24.007 TVRec(1) Error: Failed to set channel to 438. Reverting to kState_None
```

You need to go into mythtv-setup, under step 4 (I think it's the 4th one, where 2 is specifying the tuner, 3 is specifying the channel data, and 4 is connecting the tuner to the channel data) there is an option to set the starting channel, you need to verify you have it on a valid channel.

---

### Post by chee on 2010-11-02
Damn!  I know I set that up at one point but I have done so many uninstall reinstalls that I must have forgot that last time.  Thanks for looking over all those lines,  I know it's a pain.

I am trying it right now,  not sure if I should cross my fingers or uncross them  haha!

---

### Post by chee on 2010-11-02
OK   this could be another one of my problems.   I click "yes" to run myfilldatabase after I exit Mythtv Backend and it seems to be going well but gets stuck at this point 
[img]http://img545.imageshack.us/img545/6436/screenshotda.png[/img]
it just blinks this same thing over and over,  at one point it did change and then went back to the same thing again,  but it had been running for ever and hour when I finally closed it.

---

### Post by chee on 2010-11-03
Well I am going to try reinstalling Mythtv and MySql and start from scratch to see where I can get.  Hopefully that makes a difference :)

---

### Post by chee on 2010-11-08
Update
I now have it scanning for channels,  it seems like the WatchTv will work but I can't get a picture,  I get a program description (which I don't care about haha),  but no picture so far,  so I deleted my video sources and set them up again and scanned for channels again.   Still no picture though,  I will post the past log from both the frontend and backend.

Thank you all.

---

### Post by chee on 2010-11-08
here is the log from the my last try,  it actually kicked me out to my log in screen for some reason.

2010-11-08 12:41:34.075 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-08 12:41:34.076 Using runtime prefix = /usr
2010-11-08 12:41:34.076 Using configuration directory = /home/wes/.mythtv
2010-11-08 12:41:34.620 Empty LocalHostName.
2010-11-08 12:41:34.620 Using localhost value of wes-MM061
2010-11-08 12:41:34.633 New DB connection, total: 1
2010-11-08 12:41:34.641 Connected to database 'mythconverg' at host: localhost
2010-11-08 12:41:34.668 Closing DB connection named 'DBManager0'
2010-11-08 12:41:34.688 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-08 12:41:34.690 DPMS is active.
2010-11-08 12:41:34.694 Primary screen: 0.
2010-11-08 12:41:34.695 Connected to database 'mythconverg' at host: localhost
2010-11-08 12:41:34.697 Using screen 0, 1280x800 at 0,0
2010-11-08 12:41:34.790 Desktop video mode: 1280x800 60.0024 Hz
2010-11-08 12:41:35.569 MythUI Image Cache size set to 20971520 bytes
2010-11-08 12:41:35.607 AudioPulseUtil: Suspend Success
2010-11-08 12:41:35.608 Enabled verbose msgs:  important general
2010-11-08 12:41:35.615 Primary screen: 0.
2010-11-08 12:41:35.616 Using screen 0, 1280x800 at 0,0
2010-11-08 12:41:35.617 Using theme base resolution of 1280x720
2010-11-08 12:41:35.622 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-11-08 12:41:35.622 JoystickMenuThread Error: Joystick disabled - Failed to read /home/wes/.mythtv/joystickmenurc
2010-11-08 12:41:35.664 Using Frameless Window
2010-11-08 12:41:35.665 Using Full Screen Window
2010-11-08 12:41:35.907 Using the Qt painter
2010-11-08 12:41:36.037 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-11-08 12:41:36.048 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-11-08 12:41:36.058 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-11-08 12:41:36.059 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-08 12:41:36.065 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-08 12:41:37.897 Registering Internal as a media playback plugin.
2010-11-08 12:41:37.928 No plugins directory /usr/lib/mythtv/plugins
2010-11-08 12:41:37.939 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-08 12:41:37.940 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-08 12:41:37.940 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-08 12:41:37.945 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-11-08 12:41:38.046 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-08 12:41:38.049 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-08 12:41:38.914 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-08 12:41:38.967 Using protocol version 23056
2010-11-08 12:41:40.885 TV: Attempting to change from None to WatchingLiveTV
2010-11-08 12:41:40.885 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-08 12:41:40.888 Using protocol version 23056
2010-11-08 12:41:41.013 Spawning LiveTV Recorder -- begin
2010-11-08 12:41:41.620 Spawning LiveTV Recorder -- end
2010-11-08 12:41:41.626 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:41.733 We have a playbackURL(/var/lib/mythtv/livetv/2041_20101108124141.mpg) & cardtype(DUMMY)
2010-11-08 12:41:41.734 We have a RingBuffer
2010-11-08 12:41:42.188 NVP(0): Disabling Audio, params(-1,2,44100)
2010-11-08 12:41:42.242 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.296 New DB connection, total: 2
2010-11-08 12:41:42.297 Connected to database 'mythconverg' at host: localhost
2010-11-08 12:41:42.300 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.356 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.413 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.439 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2010-11-08 12:41:42.490 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.546 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.603 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.658 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.706 OSD Theme Dimensions W: 1280 H: 720
2010-11-08 12:41:42.719 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.776 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.832 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.888 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:42.945 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.005 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.060 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.116 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.172 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.229 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.284 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.339 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.395 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.452 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.509 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.566 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.640 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.697 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.773 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.830 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:43.947 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:44.003 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:44.058 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:44.127 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:44.184 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124141.mpg'
2010-11-08 12:41:44.209 Realtime priority would require SUID as root.
2010-11-08 12:41:44.211 TV: Changing from None to WatchingLiveTV
2010-11-08 12:41:44.212 TV: State is LiveTV & mctx == ctx
2010-11-08 12:41:44.214 TV: UpdateOSDInput done
2010-11-08 12:41:44.214 TV: UpdateLCD done
2010-11-08 12:41:44.214 TV: ITVRestart done
2010-11-08 12:41:44.220 Video timing method: USleep with busy wait
2010-11-08 12:41:44.241 ScreenSaverX11Private: DPMS Deactivated 1
2010-11-08 12:41:46.442 ProgramInfo(): Updated pathname '':'' -> '2041_20101108124145.mpg'
2010-11-08 12:41:47.481 RingBuf(/var/lib/mythtv/livetv/2041_20101108124145.mpg): Waited 1.0 seconds for data to become available...
2010-11-08 12:41:47.481 Checking to see if there's a new livetv program to switch to..
2010-11-08 12:41:48.483 RingBuf(/var/lib/mythtv/livetv/2041_20101108124145.mpg): Waited 2.0 seconds for data to become available...
2010-11-08 12:41:48.483 Checking to see if there's a new livetv program to switch to..
2010-11-08 12:41:50.485 RingBuf(/var/lib/mythtv/livetv/2041_20101108124145.mpg): Waited 4.0 seconds for data to become available...
2010-11-08 12:41:50.486 Checking to see if there's a new livetv program to switch to..
2010-11-08 12:41:54.490 RingBuf(/var/lib/mythtv/livetv/2041_20101108124145.mpg): Waited 8.0 seconds for data to become available...
2010-11-08 12:41:54.490 Checking to see if there's a new livetv program to switch to..
2010-11-08 12:41:56.845 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:57.846 RingBuf(/var/lib/mythtv/livetv/2041_20101108124145.mpg): Waited 1.0 seconds for data to become available...
2010-11-08 12:41:57.846 Checking to see if there's a new livetv program to switch to..
2010-11-08 12:41:57.906 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:57.907 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:57.908 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:58.029 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:58.030 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:58.031 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:58.091 [mpeg2video @ 0x26d0120]mpeg_decode_postinit() failure
2010-11-08 12:41:58.242 [mpeg2video @ 0x26d0120]ac-tex damaged at 102 36
2010-11-08 12:41:58.250 [mpeg2video @ 0x26d0120]Warning MVs not available
ICE default IO error handler doing an exit(), pid = 15937, errno = 11
<unknown>: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

---

### Post by chee on 2010-11-15
alrighty,   latest update has me getting into LiveTv,  but no picture or sound and I get a message saying that I should have gotten a lock on the signal by now.  I can scan for channels, etc.  but haven't had a Live picture yet.  here is my frontend log from the session:

2010-11-15 17:34:09.934 Received a remote 'Clear Cache' request
2010-11-15 17:34:16.408 Loading menu theme from /usr/share/mythtv/themes/classic//tvmenu.xml
2010-11-15 17:34:18.891 TV: Attempting to change from None to WatchingLiveTV
2010-11-15 17:34:18.897 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-15 17:34:18.898 Using protocol version 23056
2010-11-15 17:34:19.012 Spawning LiveTV Recorder -- begin
2010-11-15 17:34:19.495 Spawning LiveTV Recorder -- end
2010-11-15 17:34:19.500 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:19.549 We have a playbackURL(/var/lib/mythtv/livetv/2623_20101115173419.mpg) & cardtype(DUMMY)
2010-11-15 17:34:19.550 We have a RingBuffer
2010-11-15 17:34:20.051 NVP(0): Disabling Audio, params(-1,2,44100)
2010-11-15 17:34:20.104 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.160 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.169 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2010-11-15 17:34:20.216 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.272 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.329 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.364 OSD Theme Dimensions W: 1280 H: 720
2010-11-15 17:34:20.385 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.443 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.498 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.553 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.611 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.667 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.723 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.862 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.918 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:20.972 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:21.028 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:21.084 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:21.139 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:21.194 ProgramInfo(): Updated pathname '':'' -> '2623_20101115173419.mpg'
2010-11-15 17:34:21.205 New DB connection, total: 3
2010-11-15 17:34:21.209 Connected to database 'mythconverg' at host: localhost
2010-11-15 17:34:21.211 Realtime priority would require SUID as root.
2010-11-15 17:34:21.211 Video timing method: USleep with busy wait
2010-11-15 17:34:21.229 TV: Changing from None to WatchingLiveTV
2010-11-15 17:34:21.229 TV: State is LiveTV & mctx == ctx
2010-11-15 17:34:21.231 TV: UpdateOSDInput done
2010-11-15 17:34:21.231 TV: UpdateLCD done
2010-11-15 17:34:21.231 TV: ITVRestart done
2010-11-15 17:34:21.256 ScreenSaverX11Private: DPMS Deactivated 1
2010-11-15 17:35:03.128 TV: Attempting to change from WatchingLiveTV to None
2010-11-15 17:35:03.430 TV: Changing from WatchingLiveTV to None
2010-11-15 17:35:03.432 ScreenSaverX11Private: DPMS Reactivated 1
2010-11-15 17:35:06.962 AudioPulseUtil: Resume Success
2010-11-15 17:35:06.963 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

---

### Post by tgm4883 on 2010-11-15
Again, the frontend does absolutly zero tuning of channels. Backend logs are what is needed.

---

### Post by chee on 2010-11-16
OK  I just reinstalled Ubuntu 10.10,  got myself back to where I was before,  I click on Watch TV,   seems like it will work but I get a message saying that I should have locked on the signal by now.  Here is my backend log.........

2010-11-16 17:22:04.137 mythbackend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2010-11-16 17:22:04.205 Using runtime prefix = /usr
2010-11-16 17:22:04.260 Using configuration directory = /home/mythtv/.mythtv
2010-11-16 17:22:04.317 Empty LocalHostName.
2010-11-16 17:22:04.372 Using localhost value of Wes-MM061
2010-11-16 17:22:04.442 New DB connection, total: 1
2010-11-16 17:22:04.514 Connected to database 'mythconverg' at host: localhost
2010-11-16 17:22:04.573 Closing DB connection named 'DBManager0'
2010-11-16 17:22:04.629 Connected to database 'mythconverg' at host: localhost
2010-11-16 17:22:04.690 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-16 17:22:04.754 MythBackend: Starting up as the master server.
2010-11-16 17:22:04.824 New DB connection, total: 2
2010-11-16 17:22:04.886 Connected to database 'mythconverg' at host: localhost
2010-11-16 17:22:12.187 New DB connection, total: 3
2010-11-16 17:22:12.305 Connected to database 'mythconverg' at host: localhost
2010-11-16 17:22:22.079 New DB scheduler connection
2010-11-16 17:22:22.140 Connected to database 'mythconverg' at host: localhost
2010-11-16 17:22:22.222 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-11-16 17:22:22.284 Main::Registering HttpStatus Extension
2010-11-16 17:22:22.340 Enabled verbose msgs:  important general
2010-11-16 17:22:22.415 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-16 17:22:25.207 Reschedule requested for id -1.
2010-11-16 17:22:25.351 Scheduled 0 items in 0.1 = 0.07 match + 0.08 place
2010-11-16 17:22:25.412 Seem to be woken up by USER
2010-11-16 17:22:57.389 MainServer::ANN Monitor
2010-11-16 17:22:57.482 adding: Wes-MM061 as a client (events: 0)
2010-11-16 17:22:57.583 MainServer::ANN Monitor
2010-11-16 17:22:57.682 adding: Wes-MM061 as a client (events: 1)
2010-11-16 17:23:00.138 MainServer::ANN Playback
2010-11-16 17:23:00.234 adding: Wes-MM061 as a client (events: 0)
2010-11-16 17:23:00.293 TVRec(1): Changing from None to WatchingLiveTV
2010-11-16 17:23:00.353 TVRec(1): HW Tuner: 1->1
2010-11-16 17:23:00.630 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-16 17:23:00.719 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:00.884 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.184 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.329 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.420 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.618 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.720 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.775 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.831 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.902 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:01.970 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.081 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.162 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.218 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.275 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.366 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.435 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.490 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.575 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.727 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.838 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.883 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.940 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:02.996 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.052 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.244 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.333 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.401 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.479 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.534 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.590 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.646 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.691 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.746 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.802 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:03.858 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:42.212 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-16 17:23:45.761 TVRec(1): PauseRecorder() called with no recorder
2010-11-16 17:23:45.830 TVRec(1): HW Tuner: 1->1
2010-11-16 17:23:52.884 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:52.962 MainServer::ANN Playback
2010-11-16 17:23:53.027 adding: Wes-MM061 as a client (events: 0)
2010-11-16 17:23:54.190 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:54.261 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:54.318 Finished recording Unknown: channel 1041
2010-11-16 17:23:54.408 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:23:54.476 TVRec(1): Changing from WatchingLiveTV to None
2010-11-16 17:23:54.476 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-16 17:23:54.548 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:23:54.597 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:23:54.652 Finished recording Unknown: channel 1381
2010-11-16 17:23:54.728 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:23:54.815 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffb62048b0)
2010-11-16 17:23:54.837 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:23:54.888 MythSocket(ffffffffb62048b0:-1): writeStringList: Error, socket went unconnected.
			We wrote 0 of 10 bytes with 1 errors
2010-11-16 17:23:54.944 MainServer::ANN Playback
2010-11-16 17:23:55.054 adding: Wes-MM061 as a client (events: 0)
2010-11-16 17:23:55.114 TVRec(1): Changing from None to WatchingLiveTV
2010-11-16 17:23:55.173 TVRec(1): HW Tuner: 1->1
2010-11-16 17:23:55.261 ProgramInfo(1381_20101116172354.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2010-11-16 17:23:55.323 ProgramInfo(1381_20101116172354.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2010-11-16 17:24:03.466 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-11-16 17:24:03.470 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:24:03.583 TVRec(1): Changing from WatchingLiveTV to None
2010-11-16 17:24:03.674 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:24:03.741 Finished recording Unknown: channel 1041
2010-11-16 17:24:03.808 MainServer, Warning: Unknown socket closing MythSocket(0xffffffffb620d678)
2010-11-16 17:24:03.812 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:24:03.874 MythSocket(ffffffffb620d678:-1): writeStringList: Error, socket went unconnected.
			We wrote 0 of 10 bytes with 1 errors
2010-11-16 17:24:03.931 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:24:04.043 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:24:04.099 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:24:04.154 MainServer::ANN Playback
2010-11-16 17:24:04.157 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:24:04.198 adding: Wes-MM061 as a client (events: 0)
2010-11-16 17:24:04.442 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:26:42.336 Expiring 0 MBytes for 1041 @ Tue Nov 16 17:23:00 2010 => Unknown
2010-11-16 17:26:42.392 Expiring 0 MBytes for 1381 @ Tue Nov 16 17:23:54 2010 => Unknown
2010-11-16 17:26:42.394 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:26:42.448 Expiring 0 MBytes for 1041 @ Tue Nov 16 17:23:55 2010 => Unknown
2010-11-16 17:26:42.510 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:26:42.624 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:26:42.686 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:26:42.744 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:26:42.809 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:26:45.512 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172300.mpg'
2010-11-16 17:26:49.612 ProgramInfo(): Updated pathname '':'' -> '1381_20101116172354.mpg'
2010-11-16 17:26:53.673 ProgramInfo(): Updated pathname '':'' -> '1041_20101116172355.mpg'
2010-11-16 17:37:42.595 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-11-16 17:52:42.726 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by chee on 2010-11-19
OK,   so I tried "Mythtv sucessfully finds DVB-T channels, but you cannot watch them" from here [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162)

so I type:
mysql -u mythtv -p
then I have the mysql prompt so I type:
select * from dtv_multiplex;
error 1046: no database selected

This is not in the tutorial.  Not sure what I am supposed to do here.

---

### Post by tgm4883 on 2010-11-19
You need to select the database

---

### Post by chee on 2010-11-19
That is exactly what I am asking how to do........

a friend suggested "use mythtv;"  but I got this error:

ERROR 1044 (42000): Access denied for user 'mythtv'@'localhost' to database 'mythtv'

---

### Post by tgm4883 on 2010-11-19
> **chee said:**
> That is exactly what I am asking how to do........

a friend suggested "use mythtv;"  but I got this error:

ERROR 1044 (42000): Access denied for user 'mythtv'@'localhost' to database 'mythtv'

by default, the database name is mythconverg

---

### Post by chee on 2010-11-19
OMG!   Thank you!   I know this stuff is not hard and should be common sense a lot of the time but when you really don't understand databases, etc.  (for me anyways) it can be a bit intimidating and frustrating.  Thank you again and I apologize if any of my posts have been overly frustrating.

Now to see if I can figure the rest out.  :p

---

### Post by thatguruguy on 2010-11-19
I notice that you are now trying to get your digital tuner working.  Have you had any success setting up your analog tuner?  I'm asking this because I'm considering writing a step-by-step how-to, based upon my experience in getting the analog part of the Hauppauge 950Q set up.

---

### Post by chee on 2010-11-19
Actually I am trying to get both working so any tips you have would be amazing.  I can get it to work with TvTime (analog) and Kaffeine (Digital) but still haven't had luck with Mythtv.  It will scan for channels just like the other 2 but I can't watch Live TV.  

Now if I can only find DVB-T transmission data for my region (or the equivalent) I might be able to get somewhere.

---

### Post by thatguruguy on 2010-11-19
> **chee said:**
> Actually I am trying to get both working so any tips you have would be amazing.  I can get it to work with TvTime (analog) and Kaffeine (Digital) but still haven't had luck with Mythtv.  It will scan for channels just like the other 2 but I can't watch Live TV.  

Now if I can only find DVB-T transmission data for my region (or the equivalent) I might be able to get somewhere.

I'll try to get something posted later on tonight.

---

### Post by chee on 2010-11-19
Just an FYI,  I set up Mythweb and it is a lot easier to edit channel info on that.   But I am still searching for a list of freg IDs for North American OTA channels.

---

### Post by nickrout on 2010-11-20
> **chee said:**
> Just an FYI,  I set up Mythweb and it is a lot easier to edit channel info on that.   But I am still searching for a list of freg IDs for North American OTA channels.

I believe schedules direct does all that once you have a lineup?

---

### Post by chee on 2010-11-20
> **nickrout said:**
> I believe schedules direct does all that once you have a lineup?
  Can you elaborate?  What is schedules direct?  Keep in mind I am in Canada so if it is a free US channel listing it might not work so well,  though I do get quite a few US OTA channels as I am only 45mins from the border.

Thanks

---

### Post by thatguruguy on 2010-11-20
> **chee said:**
> Can you elaborate?  What is schedules direct?  Keep in mind I am in Canada so if it is a free US channel listing it might not work so well,  though I do get quite a few US OTA channels as I am only 45mins from the border.

Thanks

[Schedules Direct]("http://www.schedulesdirect.org/")

---

### Post by chee on 2010-11-20
That what I thought,  it's a pay service right?  I am only using mythtv to record from some old VHS home movies and the occasional tv show from my basic cable,  I don't think I really need a pay service like that.  If I am wrong please tell me.

---

### Post by nickrout on 2010-11-20
> **chee said:**
> That what I thought,  it's a pay service right?  I am only using mythtv to record from some old VHS home movies and the occasional tv show from my basic cable,  I don't think I really need a pay service like that.  If I am wrong please tell me.

either you want to record TV, in which case you should use SD, or you don't want to in which case you don't need it. It's only $20 a year or something isn't it?

---

### Post by thatguruguy on 2010-11-20
It is only $20 a year, and it makes using mythtv a LOT easier.  Highly recommended.

---

### Post by chee on 2010-11-21
OK,  the problem here is that I don't give a crap about scheduling recording,  I just want to be able to set Mythtv to record for an hour at 10pm,  or something like that.  I don't even have internet access at home so updating the schedules would be a problem. 

Pretty much I want a VCR function on my laptop,  no frills.  I can't be the only one that wants to use Mythtv without SD.

---

### Post by nickrout on 2010-11-21
> I can't be the only one that wants to use Mythtv without SD

In north america, probably yes!

I don't know how else you will set up your lineup. In other places you scan for channels and then name them properly etc. 

Believe me when i say myth is so much better with proper scheduling. Otherwise you could just read ```
man at
``` and use something far simpler to do your recording.

I don't know what else to advise, in the meantime > I don't give a crap  isn't that appropriate here. We are volunteers trying to help, not shop assistants who have sold you a lemon.

---

### Post by tgm4883 on 2010-11-21
dumb vcr? You must want

```
cat /dev/video0 > video.mpg
```

---

### Post by chee on 2010-11-22
> **nickrout said:**
> I don't know what else to advise, in the meantime  isn't that appropriate here. We are volunteers trying to help, not shop assistants who have sold you a lemon.

You honestly took that the wrong way?  That was meant as frustration towards Mythtv,  not towards anyone who has helped me here.  Plus I that in the context it was pretty mild.  

I am truly sorry if I offended anyone,  I do appreciate all the help,  seriously I do.  If I had thought that anyone would have found that to be anything but a sign of frustration I would not have posted it.

---

### Post by nickrout on 2010-11-22
> **chee said:**
> You honestly took that the wrong way?  That was meant as frustration towards Mythtv,  not towards anyone who has helped me here.  Plus I that in the context it was pretty mild.  

I am truly sorry if I offended anyone,  I do appreciate all the help,  seriously I do.  If I had thought that anyone would have found that to be anything but a sign of frustration I would not have posted it.

Why not use SD's 7 day free trial to get your lineup and then do your own scheduling once it has expired?

Actually I just remembered you don't have internet, can you beg steal or borrow a connection for a short time?

---

### Post by chee on 2010-11-23
Well I do have internet service here at work ( I own a retail store),  so that still might be an option,  I guess I could scan for channels at home and then update everything here.

BTW I wish I could talk the neighbors into giving me their Wifi password,  they are the most social bunch.  Although I could offer to fix their computer for free.  I would rarely use the internet anyways.....hmmmmmm.

As and aside,  I found a really nice program called Me-TV that was crazy easy to set up and works great,  seemed to set up the shedules itself,  lets you schedule recordings just like a PVR.  My only problem with it is that it only does digital,  my cable is still analog as is anything coming out of my VCR.

---

### Post by chee on 2010-11-27
You know.......  everything just isn't comin up Milhouse on this one.    I have tried everything.   I can scan for channels,  it finds all the regulars (though analog scanning isn't so good,  but neither is my reception here for those 3 channels) but I simply can't get a signal lock or even a signal for that matter.  I would say it is my TvTuner (HVR-950Q, the 72001 model) but it works fine in Windows (though Wintv is mediocre software really).  I updated the firmware to dvb-fe-1.6.114.fw,  and in the dmesg it says the upload is complete.

Now for some reason I can't get Me-TV working in 10.04,  and Kaffeine isn't working great (though TVTime is fine).  So any help on this one would be great (I know I have said this before :p).

Other then that I give up,  I will be messing around with a TvTime analog recording script I read about for the time being,  I am all out of idea and full of frustration.:frown:

Thanks to all that have helped so far!

---

### Post by chee on 2010-12-02
So I have given up on Mythtv.  If this was a dedicated media center tower that was going to stay beside my TV then I would try much harder (and probably have had better luck) but considering it is a fairly old laptop with a USB tuner,  I give up.

I have come up with alternatives though if anyone is interested (and to close out this thread).   I am using Me-TV for digital viewing and recording (make sure you get the newest version as I believe the version in the Ubuntu repos is older,  as it didn't work for me).   

For analog,  I went much simpler,  I found a script that was posted on these forums and edited it to work for me.
[link]http://ubuntuforums.org/showthread.php?t=338029[/link]
The way I got it to run (keep in mind I reverted back to 10.04) is to add ":adevice=/dev/dsp1" after "amode=0" near the bottom of the script.  It works like a charm for what I need it for.  I would imagine that you could change the video source if need be also.

Thanks to all who helped and I apologize for giving up.

---

### Post by thatguruguy on 2010-12-02
That's too bad, especially since I finally posted the [how-to I had promised you]("http://ubuntuforums.org/showthread.php?t=1634328").

Good luck with your set-up.

---

### Post by thatguruguy on 2010-12-30
> **kevinride said:**
> all I had to do was add mkv to the file types and it worked for me. did you add  or  You can also try setting it so mythvideo displays files it doesn't scan .


That's just swell. However, his issue had absolutely nothing to do with mythvideo.

---

