---
title: "frontend connection issue"
date: 2011-02-09
forum: Mythbuntu
---

### Post by davidstoll on 2011-02-09
I had to reinstall my backend system completely.  The mysql password changed, but the IP's stayed the same (my router assigns static based on mac).  However, my frontend (which didn't get any changes or updates) is not able to connect to the re-installed backend.

I put in the new mysql password in the setup, but I'm not sure what else to do.

The error says no upnp found and can't connect to backend IP "is it running"?

Everything is hard wired, no wireless.  The backend is humming along now just fine.  It is setup as a frontend/backend combo.

Is there a wizard I can initiate?

---

### Post by nhtrader on 2011-02-09
I too had this error and if I recall; I think you need to synchronize a few files. The new password and such didn't propagate to all of the files:

These three contents should match...
sudo pico /etc/mythtv/config.xml
sudo pico /home/mythtv/.mythtv/config.xml
sudo pico /home/your_username/.mythtv/config.xml

These three contents should match...
sudo pico /etc/mythtv/mysql.txt
sudo pico /home/mythtv/.mythtv/mysql.txt
sudo pico /home/your_username/.mythtv/mysql.txt

I think this is what I did.... it's a bit fuzzy.

---

### Post by nickrout on 2011-02-09
> **davidstoll said:**
> I had to reinstall my backend system completely.  The mysql password changed, but the IP's stayed the same (my router assigns static based on mac).  However, my frontend (which didn't get any changes or updates) is not able to connect to the re-installed backend.

I put in the new mysql password in the setup, but I'm not sure what else to do.

The error says no upnp found and can't connect to backend IP "is it running"?

Everything is hard wired, no wireless.  The backend is humming along now just fine.  It is setup as a frontend/backend combo.

Is there a wizard I can initiate?

logs!!!!

---

### Post by davidstoll on 2011-02-09
> **nhtrader said:**
> I too had this error and if I recall; I think you need to synchronize a few files. The new password and such didn't propagate to all of the files:

These three contents should match...
sudo pico /etc/mythtv/config.xml
sudo pico /home/mythtv/.mythtv/config.xml
sudo pico /home/your_username/.mythtv/config.xml

These three contents should match...
sudo pico /etc/mythtv/mysql.txt
sudo pico /home/mythtv/.mythtv/mysql.txt
sudo pico /home/your_username/.mythtv/mysql.txt

I think this is what I did.... it's a bit fuzzy.

One of the files in the first set did not have the correct password, so I fixed that, but I still had the issue.

Also, /home/your_username/.mythtv/config.xml is slightly different then the others.  The password, username, etc matches, but the format of the file is a bit different.  The last set (mysql.txt) all match exactly.

---

### Post by davidstoll on 2011-02-09
> **nickrout said:**
> logs!!!!

About the only thing that seems strange is that it's trying to connect to 127.0.0.1...but this is a frontend, so unless that is the localhost address for the backend's use on the backend itself, I don't think that's right.


```
2011-02-09 21:50:02.720 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2011-02-09 21:50:02.721 Using runtime prefix = /usr
2011-02-09 21:50:02.721 Using configuration directory = /home/david/.mythtv
2011-02-09 21:50:03.466 Empty LocalHostName.
2011-02-09 21:50:03.466 Using localhost value of Aspire-R3610
2011-02-09 21:50:03.502 New DB connection, total: 1
2011-02-09 21:50:03.518 Connected to database 'mythconverg' at host: 192.168.0.11
2011-02-09 21:50:03.520 Closing DB connection named 'DBManager0'
2011-02-09 21:50:03.552 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-09 21:50:03.556 DPMS is disabled.
2011-02-09 21:50:03.560 Primary screen: 0.
2011-02-09 21:50:03.573 Connected to database 'mythconverg' at host: 192.168.0.11
2011-02-09 21:50:03.581 Using screen 0, 1024x768 at 0,0
2011-02-09 21:50:03.681 Desktop video mode: 1024x768 60.006 Hz
2011-02-09 21:50:03.886 MythUI Image Cache size set to 20971520 bytes
2011-02-09 21:50:03.953 Enabled verbose msgs:  important general
2011-02-09 21:50:04.019 Primary screen: 0.
2011-02-09 21:50:04.026 Using screen 0, 1024x768 at 0,0
2011-02-09 21:50:04.028 Using theme base resolution of 1280x720
2011-02-09 21:50:04.132 LIRC: Successfully initialized '/dev/lircd' using '/home/david/.mythtv/lircrc' config
2011-02-09 21:50:04.132 JoystickMenuThread Error: Joystick disabled - Failed to read /home/david/.mythtv/joystickmenurc
2011-02-09 21:50:04.661 Using Frameless Window
2011-02-09 21:50:04.662 Using Full Screen Window
2011-02-09 21:50:05.106 Using the Qt painter
2011-02-09 21:50:05.386 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/metallurgy/base.xml'
2011-02-09 21:50:05.541 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-02-09 21:50:05.604 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-02-09 21:50:05.658 Current MythTV Schema Version (DBSchemaVer): 1254
2011-02-09 21:50:09.207 Registering Internal as a media playback plugin.
2011-02-09 21:50:09.540 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-09 21:50:09.541 Cannot load language en_us for module mythgallery
2011-02-09 21:50:09.559 Cannot load language en_us for module mythmovies
2011-02-09 21:50:09.697 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-09 21:50:10.231 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-09 21:50:10.310 Cannot load language en_us for module mythmusic
2011-02-09 21:50:10.396 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-02-09 21:50:10.774 Cannot load language en_us for module mythvideo
2011-02-09 21:50:10.856 Cannot load language en_us for module mythweather
2011-02-09 21:50:10.879 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/metallurgy/menu-ui.xml
2011-02-09 21:50:11.283 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-02-09 21:50:11.295 Found mainmenu.xml for theme 'metallurgy'
2011-02-09 21:50:11.443 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-09 21:50:11.444 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-02-09 21:50:13.873 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2011-02-09 21:50:14.723 New DB connection, total: 2
2011-02-09 21:50:14.736 Connected to database 'mythconverg' at host: 192.168.0.11
2011-02-09 21:50:14.754 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/metallurgy/recordings-ui.xml
2011-02-09 21:50:14.846 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-09 21:50:14.847 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-02-09 21:50:14.913 PlaybackBox Error: SortedList is Empty
2011-02-09 21:50:14.914 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-09 21:50:14.915 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-02-09 21:50:14.981 PlaybackBox Error: SortedList is Empty
2011-02-09 21:50:17.085 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-09 21:50:17.086 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-02-09 21:50:18.199 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-02-09 21:50:18.199 Connection to master server timed out.
			Either the server is down or the master server settings
			in mythtv-settings does not contain the proper IP address

2011-02-09 21:50:20.651 Deleting UPnP client...
```

---

### Post by nickrout on 2011-02-09
In mythtv-setup on the backend, what is the IP of the backend setup to be? I am willing to bet you have this set to 127.0.0.1. Set it to the external IP of the master backend.

---

### Post by davidstoll on 2011-02-09
> **nickrout said:**
> In mythtv-setup on the backend, what is the IP of the backend setup to be? I am willing to bet you have this set to 127.0.0.1. Set it to the external IP of the master backend.

Yes, thank you.  I set that up one time years ago and totally forgot about it.

Thank you thank you thank you.

:)

---

### Post by nickrout on 2011-02-09
LOL glad it worked.

---

