---
title: "Hanging Mythfrontend?"
date: 2010-11-29
forum: Mythbuntu
---

### Post by faktor on 2010-11-29
Hi all,

I'm new to mythtv and have suddenly a problem.
After install all was ok.   starded up on a HD-channel after some time and then mythfrontend hanged and i could not do anything so i needed to switch of the computer the "hard way".

after that mythfrontend started to behave strange with haning in about 20 sec up to two minutes, but i cant see any channels at all.

Some part of the log you can se here under. What can i do?
Must i reinstall everything or can i just reset mythfrontend to original settings or do some kind of restore?

EDIT: mythbuntu 10.10

2010-11-29 07:53:35.132 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-11-29 07:53:35.141 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-11-29 07:53:35.149 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-11-29 07:53:35.150 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-29 07:53:35.154 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-29 07:53:35.458 Registering Internal as a media playback plugin.
2010-11-29 07:53:35.481 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.481 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.481 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.482 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.483 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.483 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.484 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.484 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.485 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.486 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.486 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.486 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.487 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.488 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.488 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-29 07:53:35.488 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-11-29 07:53:35.531 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-29 07:53:35.563 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-29 07:53:35.579 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-11-29 07:53:35.611 Starting update of wunderground
2010-11-29 07:53:35.619 Starting update of wunderground
2010-11-29 07:53:35.628 Starting update of wunderground
2010-11-29 07:53:35.639 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-11-29 07:53:35.715 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-11-29 07:53:35.718 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-29 07:53:36.675 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-29 07:53:36.686 Using protocol version 23056
2010-11-29 07:53:37.578 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground.pl -u SI -d /home/peter/.mythtv/MythWeather/wunderground Los Angeles, California' has exited
2010-11-29 07:53:37.612 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground.pl -u SI -d /home/peter/.mythtv/MythWeather/wunderground Stockholm, Sweden' has exited
2010-11-29 07:53:37.645 'nice /usr/share/mythtv/mythweather/scripts/wunderground/wunderground.pl -u SI -d /home/peter/.mythtv/MythWeather/wunderground Izhevsk' has exited
2010-11-29 07:53:45.109 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-11-29 07:53:46.846 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-11-29 07:53:49.241 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//tv_settings.xml
2010-11-29 07:54:01.891 Received a remote 'Clear Cache' request
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2010-11-29 07:54:05.687 Failed to mount /dev/sdc.
2010-11-29 07:54:05.689 Found a handler - 'MythGallery Media Handler 1/2'
2010-11-29 07:54:05.711 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml
2010-11-29 07:54:05.733 MythFontProperties, Error: Failed to load 'baselarge', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml @ 11
			Name: 'title'	Type: 'font'
2010-11-29 07:54:05.736 New DB connection, total: 2
2010-11-29 07:54:05.737 Connected to database 'mythconverg' at host: localhost
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2010-11-29 07:54:35.744 Failed to mount /dev/sdd.
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2010-11-29 07:54:35.931 Failed to mount /dev/sdc.
2010-11-29 07:54:35.940 Found a handler - 'MythGallery Media Handler 1/2'
2010-11-29 07:54:35.945 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml
2010-11-29 07:54:35.948 MythFontProperties, Error: Failed to load 'baselarge', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml @ 11
			Name: 'title'	Type: 'font'
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2010-11-29 07:55:05.785 Failed to mount /dev/sde.
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2010-11-29 07:55:06.143 Failed to mount /dev/sdd.
2010-11-29 07:55:06.333 Received a remote 'Clear Cache' request
2010-11-29 07:55:06.336 Found a handler - 'MythGallery Media Handler 1/2'
2010-11-29 07:55:06.338 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml
2010-11-29 07:55:06.339 MythFontProperties, Error: Failed to load 'baselarge', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml @ 11
			Name: 'title'	Type: 'font'
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
2010-11-29 07:55:35.837 Failed to mount /dev/sdf.
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2010-11-29 07:55:36.497 Failed to mount /dev/sde.
2010-11-29 07:55:36.602 Found a handler - 'MythGallery Media Handler 1/2'
2010-11-29 07:55:36.602 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml
2010-11-29 07:55:36.605 MythFontProperties, Error: Failed to load 'baselarge', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/Mythbuntu/gallery-ui.xml @ 11
			Name: 'title'	Type: 'font'

---

### Post by ian dobson on 2010-11-29
Hi,

I would say there's something wrong with your fstab

mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2010-11-29 07:55:05.785 Failed to mount /dev/sde

Check that all your drives you are trying to mount actually exist.

Regards
Ian Dobson

---

### Post by tobi-wan on 2010-12-28
Hi,

I had *exactly* the same error as you, in the same setup (Mythbuntu 10.10). I found out that the reason was my mobile phone, which I had plugged into the machine and which was registered as two devices, /dev/sde and /dev/sdf. 

I have absolutely no clue why this would randomly crash the MythTV frontend, but there you go: I unplugged the phone and everything works like a charm again.

Hopefully, this helps you and does not put you on to a wrong trail :-)

---

