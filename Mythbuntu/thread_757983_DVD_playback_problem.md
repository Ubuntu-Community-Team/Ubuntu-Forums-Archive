---
title: "DVD playback problem"
date: 2008-04-17
forum: Mythbuntu
---

### Post by Adrian Baugh on 2008-04-17
I'm using Mythbuntu 8.04 beta, updates up to date, dual core AMD64, onboard GeForce 7050 using the nvidia-new driver. I'm using ffmpeg as the decoder and all the device names are correct. (My drive is /dev/scd0 symlinked to /dev/dvd).

All video playback is fine (using the internal player) except DVDs created with MythArchive. These almost (but not quite) always immediately crash mythfrontend, leaving me with the xfce desktop. Other DVDs work fine. I've switched to using xine for the time being, but would love to see the internal player fixed as the DVD bookmarking is really useful. Output is attached below...

myth@myth-desktop:~$ mythfrontend
2008-04-13 01:40:55.780 Using runtime prefix = /usr, libdir = /usr/lib
2008-04-13 01:40:55.781 Configuration::Load - Error parsing: /home/myth/.mythtv/config.xml at line: 1 column: 1
2008-04-13 01:40:55.781 Configuration::Load - Error Msg: unexpected end of file
2008-04-13 01:40:56.255 XScreenSaver support enabled
2008-04-13 01:40:56.255 DPMS is disabled.
2008-04-13 01:40:56.256 Empty LocalHostName.
2008-04-13 01:40:56.256 Using localhost value of myth-desktop
2008-04-13 01:40:56.257 Configuration::Load - Error parsing: /home/myth/.mythtv/config.xml at line: 1 column: 1
2008-04-13 01:40:56.257 Configuration::Load - Error Msg: unexpected end of file
2008-04-13 01:40:56.269 New DB connection, total: 1
2008-04-13 01:40:56.273 Connected to database 'mythconverg' at host: localhost
2008-04-13 01:40:56.274 Closing DB connection named 'DBManager0'
2008-04-13 01:40:56.276 Primary screen 0.
2008-04-13 01:40:56.276 Connected to database 'mythconverg' at host: localhost
2008-04-13 01:40:56.278 Using screen 0, 1360x768 at 0,0
2008-04-13 01:40:56.286 New DB connection, total: 2
2008-04-13 01:40:56.286 Connected to database 'mythconverg' at host: localhost
2008-04-13 01:40:56.289 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-04-13 01:40:56.289 Enabled verbose msgs: important general
2008-04-13 01:40:56.652 Primary screen 0.
2008-04-13 01:40:56.652 Using screen 0, 1360x768 at 0,0
2008-04-13 01:40:56.654 Switching to square mode (G.A.N.T)
2008-04-13 01:40:56.673 Using the Qt painter
2008-04-13 01:40:56.679 JoystickMenuClient Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
2008-04-13 01:40:56.690 lirc init success using configuration file: /home/myth/.mythtv/lircrc
2008-04-13 01:40:58.454 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-04-13 01:40:58.550 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-04-13 01:40:58.605 Registering Internal as a media playback plugin.
2008-04-13 01:40:58.670 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-04-13 01:40:58.737 MythMusic adding CD-Writer: 0,0,0 -- ST3160815AS
2008-04-13 01:40:58.738 MythMusic adding CD-Writer: 1,0,0 -- DVD A DH20A1S
2008-04-13 01:40:58.796 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-04-13 01:40:58.877 Starting update of BBC-Current-XML
2008-04-13 01:40:58.885 Starting update of BBC-3day-XML
2008-04-13 01:40:58.893 Starting update of Animated-Map-Download
2008-04-13 01:40:58.911 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-04-13 01:40:58.912 Using protocol version 40
2008-04-13 01:41:00.046 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccu rrentxml.pl -u SI -d /home/myth/.mythtv/MythWeather/BBC-Current-XML L2441 has exited
2008-04-13 01:41:00.046 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbcth reedayxml.pl -u SI -d /home/myth/.mythtv/MythWeather/BBC-3day-XML L2441 has exited
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Pan's Labyrinth
libdvdnav: DVD Serial Number: 47FFA1D400002710
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/myth/.dvdnav/Pan's Labyrinth.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000007ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000dbb
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
2008-04-13 01:41:04.060 Opened DVD device at //dev/scd0
2008-04-13 01:41:04.060 There are 1 titles on the disk
2008-04-13 01:41:04.060 Title 0 has 0 parts.
2008-04-13 01:41:04.104 TV: Attempting to change from None to WatchingPreRecorded
libdvdnav: Using dvdnav version 0.1.10-xine from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: Pan's Labyrinth
libdvdnav: DVD Serial Number: 47FFA1D400002710
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/myth/.dvdnav/Pan's Labyrinth.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000011f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000007ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000dbb
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
2008-04-13 01:41:04.213 Opened DVD device at //dev/scd0
2008-04-13 01:41:04.213 There are 1 titles on the disk
2008-04-13 01:41:04.213 Title 0 has 0 parts.
2008-04-13 01:41:04.259 AFD: Opened codec 0xb58030, id(MPEG2VIDEO) type(Video)
2008-04-13 01:41:04.259 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-13 01:41:04.294 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-04-13 01:41:04.334 OSD Theme Dimensions W: 640 H: 480
2008-04-13 01:41:04.576 TV: Changing from None to WatchingPreRecorded
Segmentation fault (core dumped)
myth@myth-desktop:~$

---

### Post by elaiel on 2008-04-29
I have exact the same problem. And since I tested with Pan's Labyrinth as well, it might be the DVD. Other DVDs run fine.

---

### Post by otterstrom on 2008-05-23
I am having similar problem. I am new to linux and installed Mythbuntu 8.04 yesterday. I have an AMD Athlon 64 processor. (I could not get the amd installation .iso to work so I used the i386 and it worked).

So far Myth seems to be running fine, but I can't get a DVD to play. I have a lite-on dvd burner. I have tried a couple different DVD's. When I put the DVD in it will show up with and icon and a title on the desktop, but it will not play with VLC. Neither will the DVD play on the Myth Frontend. 

Does anyone have any tips I can try to resolve this issue?

Thanks

---

### Post by otterstrom on 2008-05-23
Nevermind, I figured out I had not enabled/installed the proper codecs.

DVD playback is working now.

---

