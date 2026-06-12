---
title: "unable to watch or record tv"
date: 2011-04-16
forum: Mythbuntu
---

### Post by phillipcc on 2011-04-16
hi forum i am unable to watch live tv or record programs i ran mythfrontend from the terminal so i could get some output and produced this output
:~$ mythfrontend
2011-04-17 06:46:15.207 mythfrontend version: branches/release-0-23-fixes [26437] [www.mythtv.org](www.mythtv.org)
2011-04-17 06:46:15.208 Using runtime prefix = /usr
2011-04-17 06:46:15.208 Using configuration directory = /home/phil/.mythtv
2011-04-17 06:46:15.924 Empty LocalHostName.
2011-04-17 06:46:15.925 Using localhost value of MythTV
2011-04-17 06:46:15.938 New DB connection, total: 1
2011-04-17 06:46:15.943 Connected to database 'mythconverg' at host: localhost
2011-04-17 06:46:15.944 Closing DB connection named 'DBManager0'
2011-04-17 06:46:15.981 ScreenSaverX11Private: XScreenSaver support enabled
2011-04-17 06:46:15.986 DPMS is disabled.
2011-04-17 06:46:15.989 Primary screen: 0.
2011-04-17 06:46:15.990 Connected to database 'mythconverg' at host: localhost
2011-04-17 06:46:15.993 Using screen 0, 1024x768 at 0,0
2011-04-17 06:46:16.022 Desktop video mode: 1024x768 84.9979 Hz
2011-04-17 06:46:16.254 MythUI Image Cache size set to 20971520 bytes
2011-04-17 06:46:16.288 Enabled verbose msgs:  important general
2011-04-17 06:46:16.300 Primary screen: 0.
2011-04-17 06:46:16.301 Using screen 0, 1024x768 at 0,0
2011-04-17 06:46:16.303 Using theme base resolution of 800x600
2011-04-17 06:46:16.316 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2011-04-17 06:46:16.317 JoystickMenuThread Error: Joystick disabled - Failed to read /home/phil/.mythtv/joystickmenurc
2011-04-17 06:46:16.375 Using Frameless Window
2011-04-17 06:46:16.375 Using Full Screen Window
2011-04-17 06:46:16.647 Using the Qt painter
2011-04-17 06:46:17.023 MythFontProperties, Warning: Attempting to define 'small'
			with face 'DejaVu Sans', but it already exists with face 'Arial'
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 989
			Name: 'small'	Type: 'font'
2011-04-17 06:46:17.049 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 995
			Name: 'medium'	Type: 'font'
2011-04-17 06:46:17.074 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1001
			Name: 'large'	Type: 'font'
2011-04-17 06:46:17.099 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
			Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1007
			Name: 'clock'	Type: 'font'
2011-04-17 06:46:17.102 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/MythCenter/base.xml'
2011-04-17 06:46:17.129 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-04-17 06:46:17.142 New DB connection, total: 2
2011-04-17 06:46:17.143 Connected to database 'mythconverg' at host: localhost
2011-04-17 06:46:17.147 Current MythTV Schema Version (DBSchemaVer): 1254
2011-04-17 06:46:18.013 Registering Internal as a media playback plugin.
2011-04-17 06:46:18.068 Cannot load language en_us for module mytharchive
2011-04-17 06:46:18.120 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-17 06:46:18.121 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-17 06:46:18.122 MediaMonitorUnix::AddDevice() - empty device path.
2011-04-17 06:46:18.127 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-04-17 06:46:18.128 Cannot load language en_us for module mythgallery
2011-04-17 06:46:18.158 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-04-17 06:46:18.239 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-04-17 06:46:18.257 Cannot load language en_us for module mythmusic
2011-04-17 06:46:18.271 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-04-17 06:46:18.325 Cannot load language en_us for module mythvideo
2011-04-17 06:46:18.337 Cannot load language en_us for module mythweather
2011-04-17 06:46:18.345 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/MythCenter/menu-ui.xml
2011-04-17 06:46:18.572 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-04-17 06:46:18.579 Found mainmenu.xml for theme 'MythCenter'
2011-04-17 06:46:19.130 MythContext: Connecting to backend server: 192.168.15.100:6543 (try 1 of 1)
2011-04-17 06:46:26.136 MythSocket(9bd56f8:37): readStringList: Error, timed out after 7000 ms.
2011-04-17 06:46:26.137 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2011-04-17 06:46:31.137 MythContext: Connecting to backend server: 192.168.15.100:6543 (try 1 of 1)
2011-04-17 06:46:38.141 MythSocket(9ba4a20:37): readStringList: Error, timed out after 7000 ms.
2011-04-17 06:46:38.142 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
and when i run watch tv this is the output i am getting ok error mythtv is using all available inputs but no active recordings anyone know what might be wrong at all also i have very limited linux skills a friend set this up but he is away any help would be greatly appreciated thanks phill

---

### Post by klc5555 on 2011-04-16
You didn't say whether this particular installation has ever worked. If it did work once, then some particulars around what hardware etc. it has would be appropriate, as well as what happened prior to it ceasing to work. If the installation has never worked, then it's worth asking whether the mythtv backend was ever set up, which will be necessary before livetv or recording functions will work. This can be done from the frontend, via "Setup" in the menu, or from a prompt via "mythtv-setup". In either case, you'll need information from the mythtv manual at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

---

### Post by phillipcc on 2011-04-16
hi sorry wasnt thinking straight i have a gigabyte  k7 serie ga-7va-c motherboard with 1 gig of ram with 2 winfast dtv1000-t tv cards and a leadtek dtv2000ds now the 2 winfast cards were previously installed in a msi motherboard which has seen its day so i got this one its an older motherboard i know its working cause im using the computer its in everything was working fine till the old motherboard died so i changed over by taking the old hard drives out and putting them into this one straight swap no new install which i had hoped to do but none of the cds i burnt wanted to play the game especially in the new burner a blu ray burner and cds dont really like each other so everything was working fine in old computer in new one it just gives me those errors ok i try to watch tv it says the name of the program thats on then it just drops out with a few different messages current message is error opening jump program file  buffer any suggestions or help would be most appreciated thanks
phillip




> **klc5555 said:**
> You didn't say whether this particular installation has ever worked. If it did work once, then some particulars around what hardware etc. it has would be appropriate, as well as what happened prior to it ceasing to work. If the installation has never worked, then it's worth asking whether the mythtv backend was ever set up, which will be necessary before livetv or recording functions will work. This can be done from the frontend, via "Setup" in the menu, or from a prompt via "mythtv-setup". In either case, you'll need information from the mythtv manual at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

---

### Post by klc5555 on 2011-04-17
For a transferred installation to a new motherboard like this there are a few things to check, so far as I remember from the last time I blew up a motherboard.

First, in the newly transferred installation the video/tv storage drives and directories may have been inadvertently mounted as owner/grp "root" They need to be owner/grp "mythtv" and have permissions set appropriately (maybe 775) so that all necessary accounts can access the storage drives properly. The owner/grp permissions status of directories used for storage can be checked from a terminal by: 

ls -l <path to your storage directories, usually under /var/lib/mythtv/recordings, etc.>

Second, on this "new motherboard" installation the odds are near certain that you'll have to go into the mythtv backend setup and set up the "tuner cards" and "input connections" as though this were a brand new installation. If you have changed or renamed any of the storage drives or directories, or if the paths to any of them have been changed in this transferred installation, the "Storage Groups" section of the backend setup will have to be modified to accurately reflect the paths to all the recordings directories.

---

