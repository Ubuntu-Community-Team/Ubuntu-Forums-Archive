---
title: "Frontend crash"
date: 2010-10-10
forum: Mythbuntu
---

### Post by eriktheblu on 2010-10-10
My frontend has recently decided that it will not load fully.

The GUI shows the background image, waits for a minute, then closes.

When run from the terminal I get
```
eriktheblu@eriktheblu-desktop:~$ mythfrontend
2010-10-10 13:33:08.366 mythfrontend version: branches/release-0-23-fixes [24158] www.mythtv.org
2010-10-10 13:33:08.367 Using runtime prefix = /usr
2010-10-10 13:33:08.367 Using configuration directory = /home/eriktheblu/.mythtv
2010-10-10 13:33:09.181 Empty LocalHostName.
2010-10-10 13:33:09.181 Using localhost value of eriktheblu-desktop
2010-10-10 13:33:09.192 New DB connection, total: 1
2010-10-10 13:33:09.199 Connected to database 'mythconverg' at host: localhost
2010-10-10 13:33:09.201 Closing DB connection named 'DBManager0'
2010-10-10 13:33:09.229 ScreenSaverX11Private: XScreenSaver support enabled
2010-10-10 13:33:09.231 DPMS is disabled.
2010-10-10 13:33:09.233 Primary screen: 0.
2010-10-10 13:33:09.235 Connected to database 'mythconverg' at host: localhost
2010-10-10 13:33:09.237 Using screen 0, 1366x768 at 0,0
2010-10-10 13:33:09.267 Desktop video mode: 1366x768 59.8158 Hz
2010-10-10 13:33:09.297 MythUI Image Cache size set to 20971520 bytes
2010-10-10 13:33:09.324 Enabled verbose msgs:  important general
2010-10-10 13:33:09.329 Primary screen: 0.
2010-10-10 13:33:09.329 Using screen 0, 1366x768 at 0,0
2010-10-10 13:33:09.331 Using theme base resolution of 1280x720
2010-10-10 13:33:09.336 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2010-10-10 13:33:09.337 JoystickMenuThread Error: Joystick disabled - Failed to read /home/eriktheblu/.mythtv/joystickmenurc
2010-10-10 13:33:09.367 Using Frameless Window
2010-10-10 13:33:09.367 Using Full Screen Window
2010-10-10 13:33:09.579 Using the Qt painter
2010-10-10 13:33:09.743 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-10-10 13:33:09.766 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-10-10 13:33:09.787 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-10-10 13:33:09.787 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-10-10 13:33:09.805 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-10 13:33:10.233 Registering Internal as a media playback plugin.
2010-10-10 13:33:10.260 Cannot load language en_us for module mytharchive
2010-10-10 13:33:10.289 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.289 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.289 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.296 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.297 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.297 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.298 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.298 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.299 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.300 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.300 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.300 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.301 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.302 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.302 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.303 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.303 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.303 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-10 13:33:10.304 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-10-10 13:33:10.304 Cannot load language en_us for module mythgallery
2010-10-10 13:33:10.307 Cannot load language en_us for module mythmovies
2010-10-10 13:33:10.327 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-10-10 13:33:10.366 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-10-10 13:33:10.372 Cannot load language en_us for module mythmusic
2010-10-10 13:33:10.384 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-10-10 13:33:10.412 Cannot load language en_us for module mythvideo
2010-10-10 13:33:10.418 Cannot load language en_us for module mythweather
2010-10-10 13:33:10.420 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-10-10 13:33:10.514 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-10-10 13:33:10.521 Found mainmenu.xml for theme 'Mythbuntu'
2010-10-10 13:33:11.385 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-10-10 13:33:11.386 Using protocol version 56
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault

```
I recently changed my DVD settings to automatically detect the appropriate codec, and then did a system update. I can't say either of those is responsible, but this started after the reboot.

There is no sdc drive on this system (it was a firewire HDD that has been disconnected). I removed the reference to in in /etc/fstab.

Not sure what QPixmap is about, but to eliminate the obvious I reinstalled everything that came up from searching "pixmap" in synaptic. libXpm4 was the only package; it did not help.

Any ideas?

---

### Post by ian dobson on 2010-10-10
Hi,

Can you try deleteing your theme cache, it's somewhere under /home. Sorry I can't say exactly where it is, my frontend is down at the moment.

ps. It may be worth going over to autobulds (0.23-fixes for mythtv)

Regards
Ian Dobson

---

### Post by eriktheblu on 2010-10-10
I found ~/.mythtv/themecache/Mythbuntu.1366.768 and ~/.mythtv/osdcahce

I removed all the files they contained; no change.

---

### Post by tgm4883 on 2010-10-10
Are you able to launch it with a different theme?

```
mythfrontend -O Theme=Terra
```

---

### Post by eriktheblu on 2010-10-10
Why yes... yes I am.


I suppose if I switch the default theme, or perhaps reinstall all themes that might fix it.

---

### Post by tgm4883 on 2010-10-10
> **eriktheblu said:**
> Why yes... yes I am.


I suppose if I switch the default theme, or perhaps reinstall all themes that might fix it.

No, i've run into that issue before but I thought it was just my system. Can you file a bug here  [http://launchpad.net/mythbuntu](http://launchpad.net/mythbuntu)

---

