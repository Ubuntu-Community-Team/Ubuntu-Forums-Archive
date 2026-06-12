---
title: "RingBuf problem opening Live TV"
date: 2010-01-02
forum: Mythbuntu
---

### Post by tylersontag on 2010-01-02
When i try to start live tv it locks up for the 16 second timeout and doesn't do anything...  Heres my logfile~

```
Starting mythfrontend.real..
2010-01-02 22:20:53.292 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-01-02 22:20:53.297 Using runtime prefix = /usr
2010-01-02 22:20:53.297 Using configuration directory = /home/tag/.mythtv
2010-01-02 22:20:54.066 Empty LocalHostName.
2010-01-02 22:20:54.066 Using localhost value of tagcenter
2010-01-02 22:20:54.279 New DB connection, total: 1
2010-01-02 22:20:54.387 Connected to database 'mythconverg' at host: 127.0.0.1
2010-01-02 22:20:54.398 Closing DB connection named 'DBManager0'
2010-01-02 22:20:54.585 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-02 22:20:54.646 DPMS is active.
2010-01-02 22:20:54.665 Primary screen: 0.
2010-01-02 22:20:54.666 Connected to database 'mythconverg' at host: 127.0.0.1
2010-01-02 22:20:54.668 Using screen 0, 1600x1200 at 0,0
2010-01-02 22:20:54.774 MythUI Image Cache size set to 20971520 bytes
2010-01-02 22:20:54.775 Enabled verbose msgs:  important general
2010-01-02 22:20:54.961 Primary screen: 0.
2010-01-02 22:20:54.962 Using screen 0, 1600x1200 at 0,0
2010-01-02 22:20:55.068 Using theme base resolution of 1280x720
2010-01-02 22:20:55.155 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-01-02 22:20:55.155 JoystickMenuThread Error: Joystick disabled - Failed to read /home/tag/.mythtv/joystickmenurc
2010-01-02 22:20:55.555 Using the Qt painter
2010-01-02 22:20:55.929 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-01-02 22:20:55.991 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-01-02 22:20:56.004 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-02 22:20:56.052 Unable to load window 'backgroundwindow' from base
2010-01-02 22:20:56.188 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-02 22:20:58.201 Desktop video mode: 1600x1200 60.3173 Hz
2010-01-02 22:20:59.479 Registering Internal as a media playback plugin.
2010-01-02 22:20:59.496 No plugins directory /usr/lib/mythtv/plugins
2010-01-02 22:20:59.557 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-02 22:20:59.561 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-02 22:20:59.564 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-02 22:20:59.575 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2010-01-02 22:20:59.578 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2010-01-02 22:20:59.584 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2010-01-02 22:20:59.591 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-01-02 22:20:59.685 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-01-02 22:20:59.700 Found mainmenu.xml for theme 'Mythbuntu'
2010-01-02 22:21:01.505 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-02 22:21:01.516 Using protocol version 50
2010-01-02 22:21:19.664 New DB connection, total: 2
2010-01-02 22:21:19.803 Connected to database 'mythconverg' at host: 127.0.0.1
2010-01-02 22:21:20.778 TV: Attempting to change from None to Watching WatchingLiveTV
2010-01-02 22:21:20.850 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-02 22:21:20.851 Using protocol version 50
2010-01-02 22:21:21.094 Spawning LiveTV Recorder -- begin
2010-01-02 22:21:24.189 Spawning LiveTV Recorder -- end
2010-01-02 22:21:24.235 We have a playbackURL(/var/lib/mythtv/livetv/1005_20100102222122.mpg) & cardtype(HDPVR)
2010-01-02 22:21:30.832 RingBuf(/var/lib/mythtv/livetv/1005_20100102222122.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/livetv/1005_20100102222122.mpg'.
2010-01-02 22:21:30.942 We have a RingBuffer
2010-01-02 22:21:31.243 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- begin
2010-01-02 22:21:32.804 RingBuf(/var/lib/mythtv/livetv/1005_20100102222122.mpg) Error: Invalid file descriptor in 'safe_read()'
...
2010-01-02 22:21:48.978 RingBuf(/var/lib/mythtv/livetv/1005_20100102222122.mpg) Error: Invalid file descriptor in 'safe_read()'
2010-01-02 22:21:48.984 RingBuf(/var/lib/mythtv/livetv/1005_20100102222122.mpg) Error: Waited 16 seconds for data, aborting.
2010-01-02 22:21:49.072 RingBuf(/var/lib/mythtv/livetv/1005_20100102222122.mpg) Warning: Peek() requested 2048 bytes, but only returning 0
2010-01-02 22:21:49.086 NVP::OpenFile(): Error, couldn't read file: /var/lib/mythtv/livetv/1005_20100102222122.mpg
2010-01-02 22:21:50.053 TV: StartPlayer(0, Watching WatchingLiveTV, main) -- end error
2010-01-02 22:21:50.506 TV Error: LiveTV not successfully started
2010-01-02 22:21:54.516 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-02 22:21:57.404 ScreenSaverX11Private: DPMS Reactivated 1
```

Any ideas?

---

