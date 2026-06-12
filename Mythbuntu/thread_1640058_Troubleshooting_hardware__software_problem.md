---
title: "Troubleshooting hardware / software problem"
date: 2010-12-07
forum: Mythbuntu
---

### Post by williammanda on 2010-12-07
I'm having an issue where when playing a recording or video in mythtv, the video and audio disappear and the computer is non-responsive. I'm trying to troubleshoot this issue but I'm not as versed in linux. I'm not sure what logs to look at and or any diagnostic software to use. Any ideas?

---

### Post by LowSky on 2010-12-07
search the file system for the /var/log/mythtv/mythfrontend.log file it will tell us what is going on during playback

if you could also tell us what kind of video you are playing when the incendent last occured.

also could you list your hardware.

---

### Post by williammanda on 2010-12-07
Setup:
Processor: Intel Core 2 Quad CPU Q9300 @ 2.50GHz (Total Cores: 4), Motherboard: Intel DX38BT, Chipset: Intel 82X38/X48 + ICH9R, Memory: 3958MB, Disk: 1000GB Hitachi HDS72101 + 500GB Seagate ST3500630AS, Graphics: GeForce 8400 GS 512MB (567/333MHz)

I want to make it clear that I don't think this is a mythtv problem. It can occur while using mythtv. It also occurred while using rhythmbox but the audio still worked.

The media played was varying between HD recordings and DVD videos. The durations before the error - 1 to 10 minutes.

Here's the frontend log:

```
Starting mythfrontend.real..
2010-12-07 07:50:43.295 mythfrontend version: branches/release-0-24-fixes [27419] www.mythtv.org
2010-12-07 07:50:43.295 Using runtime prefix = /usr
2010-12-07 07:50:43.295 Using configuration directory = /home/william/.mythtv
2010-12-07 07:50:43.307 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-12-07 07:50:44.054 Empty LocalHostName.
2010-12-07 07:50:44.054 Using localhost value of C2Q
2010-12-07 07:50:44.055 Testing network connectivity to '192.168.1.100'
2010-12-07 07:50:44.167 New DB connection, total: 1
2010-12-07 07:50:44.279 Connected to database 'mythconverg' at host: 192.168.1.100
2010-12-07 07:50:44.283 Closing DB connection named 'DBManager0'
2010-12-07 07:50:44.284 Connected to database 'mythconverg' at host: 192.168.1.100
2010-12-07 07:50:44.285 Current locale EN_US
2010-12-07 07:50:44.285 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-12-07 07:50:44.456 ScreenSaverX11Private: Gnome screen saver support enabled
2010-12-07 07:50:44.457 DPMS is active.
2010-12-07 07:50:44.492 Desktop video mode: 1440x900 59.887 Hz
2010-12-07 07:50:44.509 Enabled verbose msgs:  important general
2010-12-07 07:50:44.534 Loading en_us translation for module mythfrontend
2010-12-07 07:50:44.566 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2010-12-07 07:50:44.566 JoystickMenuThread: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2010-12-07 07:50:44.621 Using Frameless Window
2010-12-07 07:50:44.621 Using Full Screen Window
2010-12-07 07:50:44.892 Using the Qt painter
2010-12-07 07:50:45.498 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-07 07:50:45.522 New DB connection, total: 2
2010-12-07 07:50:45.523 Connected to database 'mythconverg' at host: 192.168.1.100
2010-12-07 07:50:46.636 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-12-07 07:50:46.636 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-12-07 07:50:46.689 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-12-07 07:50:46.689 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-12-07 07:50:47.021 Pulse: PulseAudio suspend OK
2010-12-07 07:50:47.218 Pulse: PulseAudio resume OK
2010-12-07 07:50:47.352 Registering Internal as a media playback plugin.
2010-12-07 07:50:47.399 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-07 07:50:47.399 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-07 07:50:47.400 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-07 07:50:47.400 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-07 07:50:47.405 Loading en_us translation for module mythgallery
2010-12-07 07:50:47.695 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-07 07:50:47.728 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-07 07:50:47.736 Loading en_us translation for module mythmusic
2010-12-07 07:50:47.819 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-12-07 07:50:47.895 Loading en_us translation for module mythvideo
2010-12-07 07:50:47.925 Loading en_us translation for module mythweather
2010-12-07 07:50:47.926 NetworkControl: Listening for remote connections on port 6546
2010-12-07 07:50:48.169 Found mainmenu.xml for theme 'Mythbuntu'
2010-12-07 07:50:48.250 MythCoreContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2010-12-07 07:50:48.252 Using protocol version 63
2010-12-07 07:50:57.784 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
2010-12-07 07:51:05.247 TV: Attempting to change from None to WatchingPreRecorded
2010-12-07 07:51:05.426 Pulse: PulseAudio suspend OK
2010-12-07 07:51:05.596 AFD: Opened codec 0x7fb78d548110, id(MPEG2VIDEO) type(Video)
2010-12-07 07:51:05.596 AFD: codec AC3 has 2 channels
2010-12-07 07:51:05.596 AFD: Opened codec 0x7fb78d9cc040, id(AC3) type(Audio)
2010-12-07 07:51:05.726 Pulse: PulseAudio resume OK
2010-12-07 07:51:05.826 Pulse: PulseAudio suspend OK
2010-12-07 07:51:05.848 AO: Opening audio device 'surround51:CARD=Intel,DEV=0' ch 6(2) sr 48000 sf signed 32 bit reenc 0
2010-12-07 07:51:06.044 AudioPlayer: Enabling Audio
2010-12-07 07:51:06.550 VDPAU: Created 2 output surfaces.
2010-12-07 07:51:06.550 VDPAU: Version 1
2010-12-07 07:51:06.550 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.26  Mon Nov 29 01:12:52 PST 2010
2010-12-07 07:51:06.550 VDPAU: Created VDPAU render device 1440x900
2010-12-07 07:51:06.620 Player(0): Forcing decode extra audio option on (Video method requires it).
2010-12-07 07:51:06.672 Player(0): Video timing method: USleep with busy wait
2010-12-07 07:51:06.672 TV: Changing from None to WatchingPreRecorded
2010-12-07 07:51:06.698 ScreenSaverX11Private: DPMS Deactivated 1
2010-12-07 07:51:06.707 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-12-07 07:51:18.584 AFD: Audio stream changed
2010-12-07 07:51:18.614 AO: Opening audio device 'surround51:CARD=Intel,DEV=0' ch 6(6) sr 48000 sf signed 16 bit reenc 0
2010-12-07 08:05:28.481 Player(0): Timed out waiting for free video buffers.
2010-12-07 08:05:49.567 Player(0): Timed out waiting for free video buffers.
```

---

### Post by williammanda on 2010-12-08
A bit of history:
I originally had a Nvidia 9600GT on this system and swapped it for the 8400GS due to overscan issues on the other system. Also I had played around with compiz and loaded files to get the 3D effect.

After review:
I never had this non-responsive problem with the 9600GT. It only occurred with the 8400GS.

I decided to remove the compiz via the software center. I removed any compiz that was installed. I tested a video and the problem is gone. Since I removed all the compiz, will this present any new problem? Do I need to get back to the original state of compiz installation and if so how?

---

### Post by SlugSlug on 2010-12-08
compiz is the cause of many problems like this -- if you can live without wobbly windows then leave it alone :)

---

### Post by thatguruguy on 2010-12-08
You can always set up a script to disable compiz when mythtv starts, and re-enable it when mythtv ends.

If you're using a computer which is both a frontend and a backend, and the frontend runs all the time, compiz is of limited value.

---

