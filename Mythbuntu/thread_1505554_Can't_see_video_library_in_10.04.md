---
title: "Can't see video library in 10.04"
date: 2010-06-09
forum: Mythbuntu
---

### Post by GROwen on 2010-06-09
Hi all, for some crazy reason I can't manage to see any of the video files I've put in the default mythbuntu directory. Is it an issue with the files themselves being in directories?

I've tried finding video manager but haven't had any luck.

The path I follow is;

Utilities/Setup>Setup>Video Settings> then where should I be looking?

Thanks for any help you can give me with this.

---

### Post by larsolav on 2010-06-09
When in the place to view the videos in Myth have you pressed m and scanned for changes, or something like that?

---

### Post by GROwen on 2010-06-09
no, but am definitely going to give that a try when I get home. Thanks for the tip. Do you know of any other way to scan for media?

---

### Post by newlinux on 2010-06-10
video manager is gone in myth .23, as you can scan and manage metadata from mythvideo directly. If scanning doesn't work, take a look at your frontend logs.

---

### Post by GROwen on 2010-06-12
Thanks newlinux, when I read your post I thought "No worries, I'l check the logs and post them here if I need help". Well, I'm not finding things that easy.

I went into Mythbuntu log grabber and selected Frontend log but don't know how to find the log on [http://mythbuntu.pastebin.com](http://mythbuntu.pastebin.com)

So once I've hit Apply what do I do next?

---

### Post by williammanda on 2010-06-12
Please provide more information.
1. Please provide the exact steps you are taking to view the videos. Supply photos if possible.
2. What is you setup? BE/FE combination, remote frontend, etc...
3. Are you using storage groups? If not what are you using if you have more than one computer?

---

### Post by newlinux on 2010-06-12
> **GROwen said:**
> Thanks newlinux, when I read your post I thought "No worries, I'l check the logs and post them here if I need help". Well, I'm not finding things that easy.

I went into Mythbuntu log grabber and selected Frontend log but don't know how to find the log on [http://mythbuntu.pastebin.com](http://mythbuntu.pastebin.com)

So once I've hit Apply what do I do next?

sorry, I don't use the mythbuntu log grabber. I just look at the logs directly in /var/log/mythtv/

---

### Post by tgm4883 on 2010-06-12
> **GROwen said:**
> Thanks newlinux, when I read your post I thought "No worries, I'l check the logs and post them here if I need help". Well, I'm not finding things that easy.

I went into Mythbuntu log grabber and selected Frontend log but don't know how to find the log on [http://mythbuntu.pastebin.com](http://mythbuntu.pastebin.com)

So once I've hit Apply what do I do next?

See [http://mythbuntu.org/node/341](http://mythbuntu.org/node/341)

---

### Post by GROwen on 2010-06-14
to go with the more straight forward method for now (although wlike the prospect of log grabber) here's the log from /var/logs/mythbuntu

> Starting mythfrontend.real..
2010-06-14 19:16:16.293 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-06-14 19:16:16.293 Using runtime prefix = /usr
2010-06-14 19:16:16.293 Using configuration directory = /home/guy/.mythtv
2010-06-14 19:16:16.988 Empty LocalHostName.
2010-06-14 19:16:16.988 Using localhost value of Boxee-lady
2010-06-14 19:16:16.995 New DB connection, total: 1
2010-06-14 19:16:16.999 Connected to database 'mythconverg' at host: localhost
2010-06-14 19:16:16.999 Closing DB connection named 'DBManager0'
2010-06-14 19:16:17.011 ScreenSaverX11Private: XScreenSaver support enabled
2010-06-14 19:16:17.012 DPMS is disabled.
2010-06-14 19:16:17.013 Primary screen: 0.
2010-06-14 19:16:17.014 Connected to database 'mythconverg' at host: localhost
2010-06-14 19:16:17.015 Using screen 0, 1024x768 at 0,0
2010-06-14 19:16:17.026 Desktop video mode: 1024x768 49.9925 Hz
2010-06-14 19:16:17.039 MythUI Image Cache size set to 20971520 bytes
2010-06-14 19:16:17.062 Enabled verbose msgs:  important general
2010-06-14 19:16:17.067 Primary screen: 0.
2010-06-14 19:16:17.068 Using screen 0, 1024x768 at 0,0
2010-06-14 19:16:17.068 Using theme base resolution of 1280x720
2010-06-14 19:16:17.074 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-06-14 19:16:17.074 JoystickMenuThread Error: Joystick disabled - Failed to read /home/guy/.mythtv/joystickmenurc
2010-06-14 19:16:17.117 Using Frameless Window
2010-06-14 19:16:17.117 Using Full Screen Window
2010-06-14 19:16:17.263 Using the Qt painter
2010-06-14 19:16:17.381 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-06-14 19:16:17.394 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-06-14 19:16:17.405 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-06-14 19:16:17.405 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-06-14 19:16:17.410 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-14 19:16:17.827 Registering Internal as a media playback plugin.
2010-06-14 19:16:17.849 Cannot load language en_us for module mytharchive
2010-06-14 19:16:17.875 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-14 19:16:17.876 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-14 19:16:17.876 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-14 19:16:17.877 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-06-14 19:16:17.877 Cannot load language en_us for module mythgallery
2010-06-14 19:16:17.880 Cannot load language en_us for module mythmovies
2010-06-14 19:16:17.898 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-06-14 19:16:17.936 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-06-14 19:16:17.941 Cannot load language en_us for module mythmusic
2010-06-14 19:16:17.948 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-06-14 19:16:17.971 Cannot load language en_us for module mythvideo
2010-06-14 19:16:17.978 Cannot load language en_us for module mythweather
2010-06-14 19:16:17.979 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-06-14 19:16:18.041 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-06-14 19:16:18.044 Found mainmenu.xml for theme 'Mythbuntu'
2010-06-14 19:16:18.401 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-14 19:16:18.408 Using protocol version 56
2010-06-14 19:16:30.007 Deleting UPnP client...

Hope that's helpful im working out what I'm doing wrong.

Thanks

---

### Post by newlinux on 2010-06-14
I didn't see anything in those logs that indicated you tried to scan. We need to see logs from a time when you went into mythvideo and tried to use the scan function. If you did try to scan during this logs, then we probably need to turn up the verbosity (or get my eyes checked as I missed the part where it tries to scan in the log - I thought it would be obvious, but maybe not).

---

### Post by GROwen on 2010-06-15
Sorry about that. I've done the scan by going into media library>video and pressing 'm' then scan for changes

the resulting log is

> Starting mythfrontend.real..
2010-06-15 17:59:56.654 mythfrontend version: branches/release-0-23-fixes [24158] [www.mythtv.org]("http://www.mythtv.org")
2010-06-15 17:59:56.654 Using runtime prefix = /usr
2010-06-15 17:59:56.654 Using configuration directory = /home/guy/.mythtv
2010-06-15 17:59:57.355 Empty LocalHostName.
2010-06-15 17:59:57.355 Using localhost value of Boxee-lady
2010-06-15 17:59:57.362 New DB connection, total: 1
2010-06-15 17:59:57.365 Connected to database 'mythconverg' at host: localhost
2010-06-15 17:59:57.366 Closing DB connection named 'DBManager0'
2010-06-15 17:59:57.378 ScreenSaverX11Private: XScreenSaver support enabled
2010-06-15 17:59:57.379 DPMS is disabled.
2010-06-15 17:59:57.380 Primary screen: 0.
2010-06-15 17:59:57.381 Connected to database 'mythconverg' at host: localhost
2010-06-15 17:59:57.382 Using screen 0, 1024x768 at 0,0
2010-06-15 17:59:57.393 Desktop video mode: 1024x768 49.9925 Hz
2010-06-15 17:59:57.406 MythUI Image Cache size set to 20971520 bytes
2010-06-15 17:59:57.431 Enabled verbose msgs:  important general
2010-06-15 17:59:57.436 Primary screen: 0.
2010-06-15 17:59:57.436 Using screen 0, 1024x768 at 0,0
2010-06-15 17:59:57.437 Using theme base resolution of 1280x720
2010-06-15 17:59:57.442 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-06-15 17:59:57.442 JoystickMenuThread Error: Joystick disabled - Failed to read /home/guy/.mythtv/joystickmenurc
2010-06-15 17:59:57.487 Using Frameless Window
2010-06-15 17:59:57.488 Using Full Screen Window
2010-06-15 17:59:57.632 Using the Qt painter
2010-06-15 17:59:57.748 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-06-15 17:59:57.761 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-06-15 17:59:57.772 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-06-15 17:59:57.772 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-06-15 17:59:57.777 Current MythTV Schema Version (DBSchemaVer): 1254
2010-06-15 17:59:58.214 Registering Internal as a media playback plugin.
2010-06-15 17:59:58.237 Cannot load language en_us for module mytharchive
2010-06-15 17:59:58.263 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-15 17:59:58.264 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-15 17:59:58.264 MediaMonitorUnix::AddDevice() - empty device path.
2010-06-15 17:59:58.265 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-06-15 17:59:58.265 Cannot load language en_us for module mythgallery
2010-06-15 17:59:58.268 Cannot load language en_us for module mythmovies
2010-06-15 17:59:58.286 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-06-15 17:59:58.325 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-06-15 17:59:58.331 Cannot load language en_us for module mythmusic
2010-06-15 17:59:58.338 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-06-15 17:59:58.361 Cannot load language en_us for module mythvideo
2010-06-15 17:59:58.368 Cannot load language en_us for module mythweather
2010-06-15 17:59:58.370 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-06-15 17:59:58.434 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-06-15 17:59:58.437 Found mainmenu.xml for theme 'Mythbuntu'
2010-06-15 17:59:58.790 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-06-15 17:59:58.791 Using protocol version 56
2010-06-15 18:05:52.203 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-06-15 18:05:55.267 New DB connection, total: 2
2010-06-15 18:05:55.267 Connected to database 'mythconverg' at host: localhost
2010-06-15 18:05:55.268 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2010-06-15 18:05:55.338 PlaybackBox Error: SortedList is Empty
2010-06-15 18:05:55.520 PlaybackBox Error: SortedList is Empty
2010-06-15 18:06:01.585 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-06-15 18:06:01.794 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@Boxee-lady/var/lib/mythtv/videos/)
2010-06-15 18:06:10.532 buildFileList directory = myth://Videos@Boxee-lady/var/lib/mythtv/videos/
2010-06-15 18:06:10.532 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@Boxee-lady/var/lib/mythtv/videos/)
2010-06-15 18:06:17.440 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-06-15 18:06:33.877 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-06-15 18:06:33.889 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/default-wide/video-ui.xml
2010-06-15 18:06:55.850 Deleting UPnP client...

having a look through that it doesn't look like it's thrown up any errors but there are definitely files in that directory. There are sub-directories in that folder and some of which have their own sub-directories.

---

### Post by newlinux on 2010-06-15
Has me stumped. What are the permissions that you have on files in that directory? What file types (extensions) do they have? Make sure those extensions aren't set to be ignored in the video settings. Also, Is this a standalone installation (combined frontend/backend)?

---

### Post by tgm4883 on 2010-06-15
Is there a /var/log/mythtv/jamu.log ?

---

### Post by GROwen on 2010-06-16
There is, and it's contents are very informative.

> 2010-06-16 21:17:02.420 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.

The thing I don't understand is where am I suppose to put the media?

---

### Post by tgm4883 on 2010-06-16
> **GROwen said:**
> There is, and it's contents are very informative.



The thing I don't understand is where am I suppose to put the media?

It's important to post the whole log, as that error is benign.

---

### Post by GROwen on 2010-06-17
cool I'll do that later on today, from memory I think it was more of the same repeated from previous logins/attempts.

---

### Post by GROwen on 2010-06-17
ok here it is

> 2010-06-03 22:17:02.148 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 17:17:03.026 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 18:17:02.278 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 19:17:02.964 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 20:17:01.522 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 21:17:02.481 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 22:17:02.667 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-05 23:17:01.910 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-09 22:17:02.256 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-09 23:17:02.583 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-10 19:17:02.276 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-12 17:17:01.781 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-12 20:17:02.674 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-12 21:17:02.227 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-14 19:17:05.688 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-14 20:17:02.158 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-15 18:17:02.259 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-15 19:17:01.662 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-16 21:17:02.420 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.
2010-06-16 22:17:01.847 Python Database Connection: Using connection settings from /home/mythtv/.mythtv/config.xml

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/fanart)
The Front end setting has been ignored.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/coverart)
The Front end setting has been ignored.

! Warning: You have a front end video directory path that is a duplicate of this backend's 'Videos' storage group.
Front end directory (/var/lib/mythtv/videos)
The Front end setting has been ignored.
This Front end video directory will cause duplicate entires in MythVideo.

! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/banners)
The Front end setting has been ignored.

Thanks tgm4883, hope it helps

---

### Post by andree_b on 2010-06-17
The jamu warnings can be ignored ... 
I removed the entries in my frontend settings after i got the same warnings so the warning went away but something didn't work afterwards (cant remember exactly what but i think it was metadatadownload directly in mythtv). Probably one of the things that needed to be fixed for storage groups to leave beta status ;-)

You should probably check file types and permissions as stated by newlinux above.

---

### Post by tgm4883 on 2010-06-17
> **andree_b said:**
> The jamu warnings can be ignored ... 
I removed the entries in my frontend settings after i got the same warnings so the warning went away but something didn't work afterwards (cant remember exactly what but i think it was metadatadownload directly in mythtv). Probably one of the things that needed to be fixed for storage groups to leave beta status ;-)

You should probably check file types and permissions as stated by newlinux above.

That actually works just fine. Maybe you were thinking of ISO's?

---

### Post by GROwen on 2010-06-19
All the directory permissions are set to the default that the Mythbuntu distro gives them.

It is a combined frontend/backend (sorry newlinux, missed that question when looking over your response.)

I've also just stumbled across an error when using iTunes. It plays all the songs I have in var>lib>mythtv>music fine (I've set that directory as my media folder in iTunes so when it starts up it's the default media folder). But when I try and import I get the error

> You don't have write permission for your iTunes media folder or a folder within it

But when I look at the folder permission from the client end it says I have full read & write permissions.

iTunes is being run on a mac (10.4).

I can go into Finder and create a directory and add files to it but does anyone have any idea why iTunes can't do that?

Could this be related to the same thing that's causing mythTV to not see all the videos in var>lib>mythtv>videos?

How can I check file permissions with Thunar? I installed Nautilus because I find it easier to deal with but it seems to have no effect with sharing etc. For example:

var>lib>mythtv>music doesn't show as being shared under Nautilus but it obviously is because I can mount it on the mac and using Nautilus to set share permissions makes no difference how the directory is shared (when I set it as a share through Nautilus it didn't get rid of the error I received when trying to import into iTunes.)

Is the way that Nautilus, Thunar and the mythbuntu distro share all different? I'm beginning to be totally confused...

---

### Post by tgm4883 on 2010-06-19
Forget the errors in jamu.log, I forgot we don't even have the files in the database yet. 

What directory are your videos stored in?


What is the output of 

```
ls -l /var/lib/mythtv/
```

---

### Post by GROwen on 2010-06-19
Here's the output for that command.

> total 52
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 banners
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 coverart
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 db_backups
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 fanart
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 livetv
drwxrwsr-x 214 mythtv mythtv 12288 2010-06-19 18:42 music
drwxrwxr-x   3 mythtv mythtv  4096 2010-06-09 22:58 pictures
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 recordings
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 screenshots
drwxrwsr-x   2 mythtv mythtv  4096 2010-06-20 11:21 trailers
drwxrwsr-x   8 mythtv mythtv  4096 2010-06-20 11:21 videos


another strange behaviour is after trying to use hibernate mythtv no longer starts at startup

---

