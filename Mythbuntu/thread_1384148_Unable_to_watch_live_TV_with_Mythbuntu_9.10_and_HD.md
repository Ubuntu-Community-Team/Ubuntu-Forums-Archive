---
title: "Unable to watch live TV with Mythbuntu 9.10 and HD-PVR"
date: 2010-01-18
forum: Mythbuntu
---

### Post by jquintana on 2010-01-18
Hello all.

I followed [this]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") guide for setting up my new HD-PVR. I am able to record tv using the command line (cat /dev/video0 > filename.ts) but unable to see anything through MythTV.

When I lauch MythTV and go to watch tv I get a screen that says Please Wait... for a few seconds and then it goes back to the MythTV menu.

Any help is greatly appreciated!

---

### Post by jquintana on 2010-01-19
...anyone?

Thanks!

---

### Post by jquintana on 2010-01-20
I am willing to pay someone to remote into my system and help me set this up. Send me a PM for more info if you are up for it.

Thanks!

---

### Post by larsolav on 2010-01-20
I don't have cable, so therefore no HD-PVR either.
But have you looked at what the backend log says? It may be able to shed some light as to what may be wrong...

/var/log/mythtv/mythbackend.log

---

### Post by myth1914 on 2010-01-20
Starting with "mythfrontend" at the command line will show what it is going on when you attempt to view.  I don't recall the log for that, but if you could capture and post?

---

### Post by drascus on 2010-01-20
have you tried to e-mail the person who wrote the tutorial or if it's a wiki have you tried to write to someone that contributed to the wiki? they could probably help you. and if you wanted to pay someone you might be able to pay them to fix it for you.

---

### Post by jquintana on 2010-01-21
> **myth1914 said:**
> Starting with "mythfrontend" at the command line will show what it is going on when you attempt to view.  I don't recall the log for that, but if you could capture and post?I tried starting mythtv from the command line and was able to copy the screen output; it can be seen here:

```

[FONT=monospace]
[LIST=1]
[*]2010-01-21 01:38:24.069 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
[*]2010-01-21 01:38:24.083 Using runtime prefix = /usr
[*]2010-01-21 01:38:24.083 Using configuration directory = /home/juan/.mythtv
[*]2010-01-21 01:38:24.937 Empty LocalHostName.
[*]2010-01-21 01:38:24.937 Using localhost value of mythbe
[*]2010-01-21 01:38:24.948 New DB connection, total: 1
[*]2010-01-21 01:38:24.955 Connected to database 'mythconverg' at host: localhost
[*]2010-01-21 01:38:24.956 Closing DB connection named 'DBManager0'
[*]2010-01-21 01:38:24.966 ScreenSaverX11Private: Gnome screen saver support enabled
[*]2010-01-21 01:38:24.969 DPMS is active.
[*]2010-01-21 01:38:24.970 Primary screen: 0.
[*]2010-01-21 01:38:24.971 Connected to database 'mythconverg' at host: localhost
[*]2010-01-21 01:38:24.971 Using screen 0, 1024x768 at 0,0
[*]2010-01-21 01:38:24.978 MythUI Image Cache size set to 20971520 bytes
[*]2010-01-21 01:38:24.978 Enabled verbose msgs:  important general
[*]2010-01-21 01:38:24.981 Primary screen: 0.
[*]2010-01-21 01:38:24.981 Using screen 0, 1024x768 at 0,0
[*]2010-01-21 01:38:24.982 Using theme base resolution of 1280x720
[*]2010-01-21 01:38:24.985 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
[*]                        eno: No such file or directory (2)
[*]2010-01-21 01:38:24.985 JoystickMenuThread Error: Joystick disabled - Failed to read /home/juan/.mythtv/joystickmenurc
[*]2010-01-21 01:38:25.077 Using the Qt painter
[*]2010-01-21 01:38:25.124 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
[*]2010-01-21 01:38:25.141 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
[*]2010-01-21 01:38:25.146 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
[*]2010-01-21 01:38:25.146 Unable to load window 'backgroundwindow' from base
[*]2010-01-21 01:38:25.150 Current MythTV Schema Version (DBSchemaVer): 1244
[*]2010-01-21 01:38:25.150 New DB connection, total: 2
[*]2010-01-21 01:38:25.157 Connected to database 'mythconverg' at host: localhost
[*]2010-01-21 01:38:25.269 Desktop video mode: 1024x768 60.006 Hz
[*]2010-01-21 01:38:25.394 Registering Internal as a media playback plugin.
[*]2010-01-21 01:38:25.440 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
[*]                        eno: No such file or directory (2)
[*]2010-01-21 01:38:25.442 MMUnix::AddDevice() Error: failed to stat /dev/power, 
[*]                        eno: No such file or directory (2)
[*]2010-01-21 01:38:25.445 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
[*]                        eno: No such file or directory (2)
[*]2010-01-21 01:38:25.448 MonitorRegisterExtensions(0x100, gif,jpg,png)
[*]2010-01-21 01:38:25.459 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
[*]2010-01-21 01:38:25.475 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
[*]2010-01-21 01:38:25.481 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
[*]2010-01-21 01:38:25.502 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
[*]2010-01-21 01:38:25.569 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
[*]2010-01-21 01:38:25.570 Found mainmenu.xml for theme 'Mythbuntu'
[*]2010-01-21 01:38:25.853 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
[*]2010-01-21 01:38:25.853 Using protocol version 50
[*]2010-01-21 01:38:28.410 TV: Attempting to change from None to Watching WatchingLiveTV
[*]2010-01-21 01:38:28.411 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
[*]2010-01-21 01:38:28.412 Using protocol version 50
[*]2010-01-21 01:38:28.517 Spawning LiveTV Recorder -- begin
[*]2010-01-21 01:38:28.915 Spawning LiveTV Recorder -- end
[*]2010-01-21 01:38:28.916 GetEntryAt(-1) failed.
[*]2010-01-21 01:38:28.917 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
[*]2010-01-21 01:38:28.917 TV Error: HandleStateChange(): LiveTV not successfully started
[*]2010-01-21 01:38:28.917 We have a RingBuffer
[*]2010-01-21 01:38:28.967 TV Error: LiveTV not successfully started
[*]2010-01-21 01:38:28.991 ScreenSaverX11Private: DPMS Deactivated 1
[*]2010-01-21 01:38:28.992 ScreenSaverX11Private: DPMS Reactivated 1
[*]2010-01-21 01:38:37.164 Deleting UPnP client...
[*]Error in my_thread_global_end(): 1 threads didn't exi
[*]
```
[/LIST]
[/FONT]

I'm not exactly sure what I'm looking for though. 

This is the only thing that really stands out to me:

2010-01-21 01:38:28.917 TV Error: HandleStateChange(): LiveTV not successfully started2010-01-21 01:38:28.917 We have a RingBuffer
2010-01-21 01:38:28.967 TV Error: LiveTV not successfully started2010-01-21 01:38:28.991 ScreenSaverX11Private: DPMS Deactivated 1

---

### Post by jquintana on 2010-01-21
> **larsolav said:**
> I don't have cable, so therefore no HD-PVR either.
But have you looked at what the backend log says? It may be able to shed some light as to what may be wrong...

/var/log/mythtv/mythbackend.logI posted the log but am not sure what I'm looking for...

---

### Post by jquintana on 2010-01-21
> **drascus said:**
> have you tried to e-mail the person who wrote the tutorial or if it's a wiki have you tried to write to someone that contributed to the wiki? they could probably help you. and if you wanted to pay someone you might be able to pay them to fix it for you.I didnt know I could email the contributors of the wiki page. Will do that now.

Thanks!

---

### Post by larsolav on 2010-01-21
> **jquintana said:**
> I posted the log but am not sure what I'm looking for...

Hi there!
Where is the backend log? I see the frontend log above, but maybe there is more info in the backend log.

However, a couple of things to check based on your frontend log above:*

1. Is your start channel for that tuner a valid channel with program info (check the start channel in mythtv-setup and check program info with your program guide)

2. Is your program guide information correct in general? If not, try running:

```
mythfilldatabase --refresh-all
```


* Source: [http://ubuntuforums.org/showthread.php?t=710516](http://ubuntuforums.org/showthread.php?t=710516)
also see [http://www.gossamer-threads.com/lists/mythtv/users/194290](http://www.gossamer-threads.com/lists/mythtv/users/194290) 
Web search "GetEntryAt(-1) failed" and/or "failed to get pginfo" there are some discussions in forums that may be applicable to your situation. However, it looks like you just need to get that start channel thing fixed....

Cheers!

---

### Post by jquintana on 2010-01-22
Problem solved.

I had confused component and composite cables so I had the wrong one set!

I am going to reinstall Mythbuntu from scratch this weekend and make sure I have everything correct so I can document it.

Thanks to all who have helped me get this far!

---

