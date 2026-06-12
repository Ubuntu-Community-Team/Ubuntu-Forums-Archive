---
title: "will mythbuntu play iso files?"
date: 2010-11-20
forum: Mythbuntu
---

### Post by blkbx on 2010-11-20
The title says it all really. I could play iso files when I had front and backend on one box but since splitting them I've not been able to do so. Can myth play iso files in a front backend configuration if so could someone tell me how.
thanks lots

---

### Post by tgm4883 on 2010-11-20
Yes, providing you either A) Don't use storage groups if you aren't on 0.24 or later or B) You are on 0.24 or later

---

### Post by blkbx on 2010-11-22
I'm using storage groups with lucid lynx and no go with iso files. The iso files aren't encrypted or anything and the permissions are ok. Can't think of anything else that I  can do.

---

### Post by tgm4883 on 2010-11-22
> **blkbx said:**
> I'm using storage groups with lucid lynx and no go with iso files. The iso files aren't encrypted or anything and the permissions are ok. Can't think of anything else that I  can do.

That didn't really answer my question. I guess if you didn't answer that though that you are likely on the version that shipped with lucid, which is 0.23. That version doesn't support iso files is storage groups, that was added in 0.24. You can install 0.24 from the mythtv-updates repository provided by the mythbuntu team located at [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by blkbx on 2010-11-25
Hi
I'm sorry I thought lucid could work with iso files. It did in a previoud install though that was having both front and backend on the one machine. I've done what you suggested, followed the url to repo page etc and installed everything. Now though the frontend won't load but just gives up a page telling me that
"This version of mythtv requires an updated database. (schema is 10 versions behind)

Please run mythtv-setup or mythtvbackend to update your db.

Database host 192...
Database name : mythconverge"

I've updates the backend the same way that I did the front but still getting the same error. I can't seem to find any help online with google or the mythbuntu forum. Have you any ideas as to what I shpuld do.

---

### Post by williammanda on 2010-11-25
I have ubuntu 10.4 and mythtv .24 and I can't play ISO files. Any ideas?

Here is my mythfrontend log:

> Starting mythfrontend.real..
2010-11-25 11:30:54.232 mythfrontend version: trunk [26882] [www.mythtv.org](www.mythtv.org)
2010-11-25 11:30:54.233 Using runtime prefix = /usr
2010-11-25 11:30:54.233 Using configuration directory = /home/william/.mythtv
2010-11-25 11:30:54.244 ThreadPool:HTTP: Initial 1, Max 5, Timeout 60000
2010-11-25 11:30:55.160 Empty LocalHostName.
2010-11-25 11:30:55.160 Using localhost value of C2Q
2010-11-25 11:30:55.160 Testing network connectivity to '192.168.1.100'
2010-11-25 11:30:55.160 Launching: ping -t 3 -c 1  192.168.1.100  >/dev/null 2>&1
2010-11-25 11:30:55.161 PID 22521: launched
2010-11-25 11:30:55.162 Starting reaper thread
2010-11-25 11:30:55.262 PID 22521: exited: status=0, result=0
2010-11-25 11:30:55.267 New DB connection, total: 1
2010-11-25 11:30:55.479 Connected to database 'mythconverg' at host: 192.168.1.100
2010-11-25 11:30:55.479 Closing DB connection named 'DBManager0'
2010-11-25 11:30:55.480 Connected to database 'mythconverg' at host: 192.168.1.100
2010-11-25 11:30:55.481 Current locale en_US
2010-11-25 11:30:55.481 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-11-25 11:30:55.497 Launching: xscreensaver-command -version >&- 2>&-
2010-11-25 11:30:55.498 PID 22525: launched
2010-11-25 11:30:55.563 PID 22525: exited: status=32512, result=127
2010-11-25 11:30:55.563 Launching: gnome-screensaver-command --help >&- 2>&-
2010-11-25 11:30:55.564 PID 22526: launched
2010-11-25 11:30:55.663 PID 22526: exited: status=0, result=0
2010-11-25 11:30:55.663 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-25 11:30:55.664 DPMS is active.
2010-11-25 11:30:55.725 Desktop video mode: 1440x900 59.887 Hz
2010-11-25 11:30:55.747 Enabled verbose msgs:  important general
2010-11-25 11:30:55.802 Loading en_us translation for module mythfrontend
2010-11-25 11:30:55.846 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2010-11-25 11:30:55.846 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2010-11-25 11:30:55.901 Using Frameless Window
2010-11-25 11:30:55.902 Using Full Screen Window
2010-11-25 11:30:56.103 Using the OpenGL painter
2010-11-25 11:30:56.477 OpenGL: OpenGL vendor  : NVIDIA Corporation
2010-11-25 11:30:56.477 OpenGL: OpenGL renderer: GeForce 9600 GT/PCI/SSE2
2010-11-25 11:30:56.477 OpenGL: OpenGL version : 3.2.0 NVIDIA 195.36.24
2010-11-25 11:30:56.478 OpenGL: Max texture size: 8192 x 8192
2010-11-25 11:30:56.478 OpenGL: Max texture units: 4
2010-11-25 11:30:56.478 OpenGL: Direct rendering: Yes
2010-11-25 11:30:56.478 OpenGL: Initialised MythRenderOpenGL
2010-11-25 11:30:57.163 Current MythTV Schema Version (DBSchemaVer): 1264
2010-11-25 11:30:57.202 New DB connection, total: 2
2010-11-25 11:30:57.203 Connected to database 'mythconverg' at host: 192.168.1.100
2010-11-25 11:30:58.451 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-11-25 11:30:58.451 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-11-25 11:30:58.512 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-11-25 11:30:58.512 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-11-25 11:30:58.649 Launching: ps -ae | grep pulseaudio > /dev/null
2010-11-25 11:30:58.651 PID 22547: launched
2010-11-25 11:30:58.765 PID 22547: exited: status=0, result=0
2010-11-25 11:30:58.954 Pulse: PulseAudio suspend OK
2010-11-25 11:30:59.028 Launching: ps -ae | grep pulseaudio > /dev/null
2010-11-25 11:30:59.030 PID 22550: launched
2010-11-25 11:30:59.066 PID 22550: exited: status=0, result=0
2010-11-25 11:30:59.126 Pulse: PulseAudio resume OK
2010-11-25 11:30:59.279 Registering Internal as a media playback plugin.
2010-11-25 11:30:59.439 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-25 11:30:59.439 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-25 11:30:59.439 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-25 11:30:59.441 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-11-25 11:30:59.447 Loading en_us translation for module mythgallery
2010-11-25 11:30:59.725 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-25 11:30:59.755 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-25 11:30:59.764 Loading en_us translation for module mythmusic
2010-11-25 11:30:59.848 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-11-25 11:30:59.879 Loading en_us translation for module mythvideo
2010-11-25 11:30:59.915 Loading en_us translation for module mythweather
2010-11-25 11:30:59.916 NetworkControl: Listening for remote connections on port 6546
2010-11-25 11:31:00.156 Found mainmenu.xml for theme 'Mythbuntu'
2010-11-25 11:31:00.593 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2010-11-25 11:31:00.593 Using protocol version 63
2010-11-25 11:31:06.131 buildFileList directory = myth://Videos@C2Q/var/lib/mythtv/videos/
2010-11-25 11:31:06.144 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@C2Q/var/lib/mythtv/videos/)
2010-11-25 11:31:06.223 Adding :  : JILLIAN_MICHAELS_BUILD_MUSCLE.ISO : 4c671e1303bdbc19
2010-11-25 11:31:06.331 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M JILLIAN MICHAELS BUILD MUSCLE
2010-11-25 11:31:06.843 No results found for JILLIAN MICHAELS BUILD MUSCLE 0 0
2010-11-25 11:31:15.705 TV: Attempting to change from None to WatchingDVD
2010-11-25 11:31:15.886 AudioPlayer: Disabling Audio, params(0,2,44100)
2010-11-25 11:31:15.886 Launching: ps -ae | grep pulseaudio > /dev/null
2010-11-25 11:31:15.895 PID 22581: launched
2010-11-25 11:31:15.976 PID 22581: exited: status=0, result=0
2010-11-25 11:31:16.036 Pulse: PulseAudio suspend OK
2010-11-25 11:31:16.064 AudioOutput Error: Aborting Audio Reconfigure. Invalid audio parameters ch 2 fmt 0 @ 44100Hz
2010-11-25 11:31:16.064 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch 2 fmt 0 @ 44100Hz
2010-11-25 11:31:16.064 playCtx, Error: Aborting Audio Reconfigure. Invalid audio parameters ch 2 fmt 0 @ 44100Hz
2010-11-25 11:31:16.227 AFD: codec Unknown Codec ID has 2 channels
2010-11-25 11:31:16.228 AFD: Opened codec 0x7f03c4110b70, id(Unknown Codec ID) type(Audio)
2010-11-25 11:31:16.228 Launching: ps -ae | grep pulseaudio > /dev/null
2010-11-25 11:31:16.236 PID 22585: launched
2010-11-25 11:31:16.276 PID 22585: exited: status=0, result=0
2010-11-25 11:31:16.337 Pulse: PulseAudio resume OK
2010-11-25 11:31:16.337 Launching: ps -ae | grep pulseaudio > /dev/null
2010-11-25 11:31:16.346 PID 22588: launched
2010-11-25 11:31:16.376 PID 22588: exited: status=0, result=0
2010-11-25 11:31:16.437 Pulse: PulseAudio suspend OK
2010-11-25 11:31:16.459 AO: Opening audio device 'surround51' ch 6(2) sr 48000 sf signed 32 bit reenc 0
2010-11-25 11:31:16.460 Opening ALSA audio device 'surround51'.
2010-11-25 11:31:16.985 AudioPlayer: Enabling Audio
2010-11-25 11:31:17.084 Clearing OpenGL painter cache.
2010-11-25 11:31:17.271 VDPAU: Created 2 output surfaces.
2010-11-25 11:31:17.271 VDPAU: Version 1
2010-11-25 11:31:17.271 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 19:52:55 PDT 2010
2010-11-25 11:31:17.271 VDPAU: Created VDPAU render device 1440x900
2010-11-25 11:31:17.334 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.334 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.335 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.335 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error
2010-11-25 11:31:17.336 [mp1 @ 0x7f03ecae65c0]Header missing
2010-11-25 11:31:17.336 AFD Error: Unknown audio decoding error

---

### Post by blkbx on 2010-11-26
Are you using separate machines for front and backend? I broke my ability to play ISO files when I started to use a front and backend setup. Also if you are using storage groups and can't play any ISO files then your in the same hole as me. If you come up with a fix please let me know.
I do have a question for you. When I upgraded my lucid lynx frontend. I started to get a dbschema error even though I upgraded the backend aswell.

---

### Post by nickrout on 2010-11-26
stop talking about lucid or maverick. The version of ubuntu you are using is irrelevant. The version of mythtv is what is important.

---

### Post by blkbx on 2010-11-26
But refering to lucid or maverick we are talking about a specific mythtv version except where an upgrade has been done. Which is usually part of the reason for posting.
How are you guys in Christchurch now. Better I hope.
tomas

---

### Post by iitywygms on 2010-11-26
libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-26 17:13:26.831 Failed to open DVD device at myth://Videos@192.168.2.4$
2010-11-26 17:13:26.926 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215O
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-26 17:13:27.030 Failed to open DVD device at myth://Videos@192.168.2.4$

Obviously not working for me.
Running 10.04 with .24 mythtv latest mythbuntu daily.
The iso is not encrypted.

---

### Post by nickrout on 2010-11-27
> **blkbx said:**
> But refering to lucid or maverick we are talking about a specific mythtv version except where an upgrade has been done. Which is usually part of the reason for posting.
How are you guys in Christchurch now. Better I hope.
tomas

yeah but so many people use the mythbuntu repos that it becomes a bit meaningless..

OK, but had another aftershock reminder this morning. makes you jump!

Thanks for asking.

---

### Post by blkbx on 2010-11-27
I think that when I'm told that release .24 is said to play ISO files and it obviously doesn't. That maybe the powers that be, should take an interest.
In upgrading to .24 I've hosed my mysql db and am looking for help on that. I know that mythtv is for tinkering and am prepered to work through the problems that it throws at me. So I can learn as I go and I am, but sometimes wish the angle of learning wasn't always so steep.

---

### Post by tgm4883 on 2010-11-27
> **iitywygms said:**
> libdvdnav: Using dvdnav version svnR1215
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-26 17:13:26.831 Failed to open DVD device at myth://Videos@192.168.2.4$
2010-11-26 17:13:26.926 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215O
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-26 17:13:27.030 Failed to open DVD device at myth://Videos@192.168.2.4$

Obviously not working for me.
Running 10.04 with .24 mythtv latest mythbuntu daily.
The iso is not encrypted.

What log is that? Can you give a ls -l of that directory?



> **blkbx said:**
> I think that when I'm told that release .24 is said to play ISO files and it obviously doesn't. That maybe the powers that be, should take an interest.
In upgrading to .24 I've hosed my mysql db and am looking for help on that. I know that mythtv is for tinkering and am prepered to work through the problems that it throws at me. So I can learn as I go and I am, but sometimes wish the angle of learning wasn't always so steep.

I don't know if I said this in this thread yet, but please don't make blanket statements like that. Especially when they are easily proven wrong. Just because something doesn't work for you doesn't mean it doesn't work for everyone. ISO's work fine here. I just played a home movie ISO on my separate backend/frontend setup and posted the logs below for you.

```
2010-11-27 08:37:00.044 TV: Attempting to change from WatchingDVD to None
2010-11-27 08:37:00.118 VDPAU Painter: Clearing VDPAU painter cache.
2010-11-27 08:37:00.120 MythPainter: 2 images not yet de-allocated.
2010-11-27 08:37:00.183 TV: Changing from WatchingDVD to None

ii  mythtv-frontend                       1:0.24.0+fixes27280-0ubuntu0+mythbunt A personal video recorder application (client)

ii  mythtv-backend                        1:0.24.0+fixes27315-0ubuntu0+mythbunt A personal video recorder application (server)

```

Try an ISO, then check your backend and frontend logs (or post them)

---

### Post by nickrout on 2010-11-27
the fact is that reading the release motes for 0.24 reveals that iso support over storage groups is nor UNencrypted isos only.

---

### Post by blkbx on 2010-11-28
Yes I've read those notes, but there are posters who haven't been able to play their files even though their not encrypted.

---

### Post by iitywygms on 2010-11-28
> **tgm4883 said:**
> What log is that? Can you give a ls -l of that directory?

latest log from /var/log/mythtv/mythfrontend.log

2010-11-28 18:15:31.492 Connected to database 'mythconverg' at host: 192.168.2.4
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-28 18:15:36.347 Failed to open DVD device at /mythbackend/videos/iso/AVCHD-v1_3.iso
2010-11-28 18:15:36.488 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-28 18:15:36.490 Failed to open DVD device at /mythbackend/videos/iso/AVCHD-v1_3.iso

ls -l

kevin@mythbigscreen:/var/log/mythtv$ ls -l
total 3264
-rw-r--r-- 1 mythtv mythtv     354 2010-04-10 18:17 jamu.log
-rw-r--r-- 1 kevin  mythtv     165 2010-11-12 17:07 mtd.log
-rw-rw-r-- 1 kevin  mythtv 3327287 2010-11-28 18:15 mythfrontend.log
-rw-rw-r-- 1 kevin  mythtv       0 2010-01-05 20:41 mythwelcome.log

---

### Post by nickrout on 2010-11-28
> **iitywygms said:**
> latest log from /var/log/mythtv/mythfrontend.log

2010-11-28 18:15:31.492 Connected to database 'mythconverg' at host: 192.168.2.4
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-28 18:15:36.347 Failed to open DVD device at /mythbackend/videos/iso/AVCHD-v1_3.iso
2010-11-28 18:15:36.488 TV: Attempting to change from None to WatchingDVD
libdvdnav: Using dvdnav version svnR1215
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
2010-11-28 18:15:36.490 Failed to open DVD device at /mythbackend/videos/iso/AVCHD-v1_3.iso


with a filename like that (avchd*) I suspect that's not a DVD you are trying to play but some sort of bluray or bd disk.

[http://www.gossamer-threads.com/lists/mythtv/users/460318#460318](http://www.gossamer-threads.com/lists/mythtv/users/460318#460318)

---

### Post by iitywygms on 2010-11-28
> **nickrout said:**
> with a filename like that (avchd*) I suspect that's not a DVD you are trying to play but some sort of bluray or bd disk.

[http://www.gossamer-threads.com/lists/mythtv/users/460318#460318](http://www.gossamer-threads.com/lists/mythtv/users/460318#460318)

DOH! Um yeah, you are right.](*,)](*,)](*,)](*,)

---

