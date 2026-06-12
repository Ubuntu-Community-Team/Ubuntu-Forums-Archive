---
title: "Need help diagnosing spontaneous frontend slowdown"
date: 2010-03-01
forum: Mythbuntu
---

### Post by nwillis on 2010-03-01
Hi all;

I'm bangin my head against the wall here.  Mythbuntu 9.10; separate frontend connecting to a remote backend.  Up until yesterday, it worked perfectly.  Now, when I launch the gui, it takes forever -- it displays the BG image for around 30s before loading the menus.  When I enter "watch recordings" it shows %|SUBTITLE|% stuff for about 5-6seconds before it loads the program list from the backend.  It does load them, including preview images.  But when I try to play one, it hangs on the "Please Wait...." message for about a minute, then goes black, then dumps me back into the recordings page again.

*ALL* of the recordings play perfectly on the windowed frontend running on the backend itself (which is also a regular desktop machine).  And like I said, this just started today, without warning.  I can't see anything in the backed logs; I haven't changed config or anything else on the newly-problematic frontend -- what could it be?

Thanks,
n

---

### Post by SiHa on 2010-03-02
Frontend log from the suspect machine might be a good starting point...

---

### Post by nwillis on 2010-03-02
Blank, unfortunately.  Even when started with --service.  There are old mythfrontend.log files from a previous dist-upgrade; something obviously borked back then.  Which would be interesting to diagnose as well, but is probably a separate issue.

I *can*, however, cut-n-paste console output from starting mythfrontend from an xterm....

```
mythfrontend
2010-03-02 11:41:42.167 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-03-02 11:41:42.187 AudioPulseUtil: Suspend Success
2010-03-02 11:41:42.187 Using runtime prefix = /usr
2010-03-02 11:41:42.187 Using configuration directory = /home/nate/.mythtv2
2010-03-02 11:41:42.947 Using localhost value of videobox_secondary
2010-03-02 11:41:42.957 New DB connection, total: 1
2010-03-02 11:41:42.965 Connected to database 'mythconverg' at host: 192.168.1.101
2010-03-02 11:41:42.966 Closing DB connection named 'DBManager0'
2010-03-02 11:41:42.996 ScreenSaverX11Private: Gnome screen saver support enabled
2010-03-02 11:41:42.998 DPMS is active.
2010-03-02 11:41:43.000 Primary screen: 0.
2010-03-02 11:41:43.026 Connected to database 'mythconverg' at host: 192.168.1.101
2010-03-02 11:41:43.034 Using screen 0, 1280x720 at 0,0
2010-03-02 11:41:43.727 MythUI Image Cache size set to 20971520 bytes
2010-03-02 11:41:43.728 Enabled verbose msgs:  important general
2010-03-02 11:41:44.168 Primary screen: 0.
2010-03-02 11:41:44.190 Using screen 0, 1280x720 at 0,0
2010-03-02 11:41:44.191 Using theme base resolution of 1280x720
2010-03-02 11:41:45.732 LIRC: Successfully initialized '/dev/lircd' using '/home/nate/.lircrc' config
2010-03-02 11:41:45.732 JoystickMenuThread Error: Joystick disabled - Failed to read /home/nate/.mythtv2/joystickmenurc
2010-03-02 11:41:51.107 Using the Qt painter
2010-03-02 11:41:51.146 Removing stale cache dir: /home/nate/.mythtv2/themecache/MythCenter-wide.1360.768
2010-03-02 11:41:51.181 Removing stale cache dir: /home/nate/.mythtv2/themecache/MythCenter-wide.1360.768/keyboard
2010-03-02 11:41:51.233 Removing stale cache dir: /home/nate/.mythtv2/themecache/MythCenter-wide.1360.768/title
2010-03-02 11:41:51.243 Removing stale cache dir: /home/nate/.mythtv2/themecache/MythCenter-wide.1360.768/ui
2010-03-02 11:41:51.250 Removing stale cache dir: /home/nate/.mythtv2/themecache/MythCenter-wide.1360.768/watermark
2010-03-02 11:41:51.301 Loaded base theme from /usr/share/mythtv/themes/MythCenter-wide/base.xml
2010-03-02 11:41:51.519 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-03-02 11:41:51.532 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-03-02 11:41:51.541 DataDirectProcessor::FixProgramIDs() -- begin
2010-03-02 11:41:51.559 New DB connection, total: 2
2010-03-02 11:41:51.564 Connected to database 'mythconverg' at host: 192.168.1.101
2010-03-02 11:41:51.570 New DB DataDirect connection
2010-03-02 11:41:51.571 Connected to database 'mythconverg' at host: 192.168.1.101
2010-03-02 11:41:51.865 New DB connection, total: 3
2010-03-02 11:41:51.866 Connected to database 'mythconverg' at host: 192.168.1.101
2010-03-02 11:41:52.189 DataDirectProcessor::FixProgramIDs() -- end
2010-03-02 11:41:52.888 Current MythTV Schema Version (DBSchemaVer): 1244
2010-03-02 11:42:07.620 Desktop video mode: 1280x720 60.0024 Hz
2010-03-02 11:42:17.144 Updating keybinding description...
2010-03-02 11:42:19.790 Updating keybinding description...
2010-03-02 11:42:20.240 Updating keybinding description...
2010-03-02 11:42:27.780 Registering Internal as a media playback plugin.
2010-03-02 11:42:34.670 MMUnix::AddDevice() Error: failed to stat /dev/bdi,
            eno: No such file or directory (2)
2010-03-02 11:42:34.680 MMUnix::AddDevice() Error: failed to stat /dev/power,
            eno: No such file or directory (2)
2010-03-02 11:42:34.689 MMUnix::AddDevice() Error: failed to stat /dev/trace,
            eno: No such file or directory (2)
2010-03-02 11:42:34.700 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-03-02 11:42:34.977 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-03-02 11:42:37.631 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-03-02 11:42:39.211 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-02 11:42:48.540 Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/menu-ui.xml
2010-03-02 11:42:48.742 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-03-02 11:42:48.744 Found mainmenu.xml for theme 'MythCenter-wide'
2010-03-02 11:42:50.353 MythContext: Connecting to backend server: 192.168.1.101:6543 (try 1 of 1)
2010-03-02 11:42:50.354 Using protocol version 50
2010-03-02 11:46:38.202 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-03-02 11:46:40.397 Loading window theme from /usr/share/mythtv/themes/MythCenter-wide/recordings-ui.xml
2010-03-02 11:46:40.397 Loading window theme from /usr/share/mythtv/themes/default-wide/recordings-ui.xml
2010-03-02 11:48:20.668 TV: Attempting to change from None to Watching WatchingPreRecorded
2010-03-02 11:48:21.199 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2010-03-02 11:48:24.051 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 1.0 seconds for data to become available...
2010-03-02 11:48:25.822 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 1.0 seconds for data to become available...
2010-03-02 11:48:26.823 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 2.0 seconds for data to become available...
2010-03-02 11:48:34.107 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 2.0 seconds for data to become available...
2010-03-02 11:48:35.272 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 1.0 seconds for data to become available...
2010-03-02 11:48:40.379 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 2.0 seconds for data to become available...
2010-03-02 11:48:45.040 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 1.0 seconds for data to become available...
2010-03-02 11:48:51.962 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 1.0 seconds for data to become available...
2010-03-02 11:48:56.671 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 2.0 seconds for data to become available...
2010-03-02 11:48:58.672 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 4.0 seconds for data to become available...
2010-03-02 11:49:02.674 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Waited 8.0 seconds for data to become available...
2010-03-02 11:49:04.727 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2010-03-02 11:49:05.731 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Taking too long to be allowed to read..
2010-03-02 11:49:06.731 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Taking too long to be allowed to read..
2010-03-02 11:49:07.732 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Taking too long to be allowed to read..
2010-03-02 11:49:08.732 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Taking too long to be allowed to read..
2010-03-02 11:49:09.732 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg): Taking too long to be allowed to read..
2010-03-02 11:49:09.732 restarting readhead thread..
2010-03-02 11:49:14.793 RingBuf(myth://192.168.1.101:6543/3091_20100301185800.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
Terminated

```

As you can see, it is taking a full minute between launching and actually loading the UI xml file, which is new behavior.  Then when hitting play it's getting a string of ringbuf problems.  Also new as of yesterday.  What does it mean?

Thanks,
N

---

### Post by azmyth on 2010-03-02
Looks like a permission issue to me. If it can't read, it's either permission or can't find the file.

---

### Post by nwillis on 2010-03-03
If you mean *filesystem* permissions, that can't be it, since I can open and play the files externally.  Plus I think mythfrontend would report a different error from its POV, too -- in the past I have had the occasional failed recording, which appears in the program list but results in a "the file could not be located" pop-up message when you try to play it.

Thanks,
N

---

