---
title: "audio stops working after restarting frontend"
date: 2010-01-10
forum: Mythbuntu
---

### Post by dude08 on 2010-01-10
I'm running Mythbuntu 9.10 with a motherboard integrated ATI HD 4200 using the HDMI output on it for video and audio. It seems to be working just fine when I boot up with the frontend loading up on boot. The weird thing is that If I just close the frontend without doing anything else and then start it back up from the Applications menu, suddenly the sound doesnt work now, despite working in other programs. Anyone have any ideas where I could start with this issue?

---

### Post by ian dobson on 2010-01-10
Hi,

Have a look in your frontend log file (/var/log/mythtv/frontend.log), maybe you'll see some error message.

Regards
Ian Dobson

---

### Post by dude08 on 2010-01-10
After looking through the logs I found some problems coming from the frontend, looking at the backend logs there seems to be no problems there.

As you can see at first its unable to find PCM, then after restarting the frontend its unable to find the Master, I've tried switching between the two and no avail. The second time there are also several stat errors.

> 
==> /var/log/mythtv/mythfrontend.log <==
2010-01-10 13:23:00.215 AFD: Opened codec 0x47d9600, id(WMV3) type(Video)
2010-01-10 13:23:00.377 Opening audio device 'default'. ch 2(2) sr 32000
2010-01-10 13:23:00.377 Opening ALSA audio device 'default'.
2010-01-10 13:23:00.390 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2010-01-10 13:23:00.482 Mixer unable to find control PCM
2010-01-10 13:23:00.482 Mixer unable to find control PCM
2010-01-10 13:23:00.482 Mixer unable to find control PCM
2010-01-10 13:23:00.482 Mixer unable to find control PCM
2010-01-10 13:23:00.483 Mixer unable to find control PCM
2010-01-10 13:23:00.483 Mixer unable to find control PCM
2010-01-10 13:23:00.483 Mixer unable to find control PCM
2010-01-10 13:23:00.483 Mixer unable to find control PCM
2010-01-10 13:23:00.483 Mixer unable to find control PCM
2010-01-10 13:23:00.503 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-01-10 13:23:00.510 OSD Theme Dimensions W: 1280 H: 720
2010-01-10 13:23:00.856 TV: StartPlayer(0, Watching Video, main) -- end ok
2010-01-10 13:23:00.856 TV: Changing from None to Watching Video
2010-01-10 13:23:00.856 New DB connection, total: 3
2010-01-10 13:23:00.857 Connected to database 'mythconverg' at host: localhost
2010-01-10 13:23:00.857 New DB connection, total: 4
2010-01-10 13:23:00.858 Connected to database 'mythconverg' at host: localhost
2010-01-10 13:23:00.858 Video timing method: USleep with busy wait
2010-01-10 13:23:00.858 Realtime priority would require SUID as root.
2010-01-10 13:23:00.886 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-10 13:23:05.172 TV: Attempting to change from Watching Video to None
2010-01-10 13:23:05.197 TV: Changing from Watching Video to None
2010-01-10 13:23:05.198 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-10 13:23:08.851 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
Starting mythfrontend.real..
2010-01-10 13:23:20.984 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2010-01-10 13:23:20.985 Using runtime prefix = /usr
2010-01-10 13:23:20.985 Using configuration directory = /home/sean/.mythtv
2010-01-10 13:23:21.676 Empty LocalHostName.
2010-01-10 13:23:21.677 Using localhost value of liberty
2010-01-10 13:23:21.686 New DB connection, total: 1
2010-01-10 13:23:21.693 Connected to database 'mythconverg' at host: localhost
2010-01-10 13:23:21.693 Closing DB connection named 'DBManager0'
2010-01-10 13:23:21.707 ScreenSaverX11Private: Gnome screen saver support enabled
2010-01-10 13:23:21.709 DPMS is active.
2010-01-10 13:23:21.711 Primary screen: 0.
2010-01-10 13:23:21.711 Connected to database 'mythconverg' at host: localhost
2010-01-10 13:23:21.713 Using screen 0, 1280x720 at 0,0
2010-01-10 13:23:21.727 MythUI Image Cache size set to 20971520 bytes
2010-01-10 13:23:21.728 Enabled verbose msgs:  important general
2010-01-10 13:23:21.730 Primary screen: 0.
2010-01-10 13:23:21.731 Using screen 0, 1280x720 at 0,0
2010-01-10 13:23:21.731 Using theme base resolution of 1280x720
2010-01-10 13:23:21.733 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-01-10 13:23:21.733 JoystickMenuThread Error: Joystick disabled - Failed to read /home/sean/.mythtv/joystickmenurc
2010-01-10 13:23:21.783 Using the Qt painter
2010-01-10 13:23:21.834 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2010-01-10 13:23:21.836 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-01-10 13:23:21.839 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-01-10 13:23:21.840 Unable to load window 'backgroundwindow' from base
2010-01-10 13:23:21.867 Current MythTV Schema Version (DBSchemaVer): 1244
2010-01-10 13:23:21.939 Desktop video mode: 1280x720 60.0024 Hz
2010-01-10 13:23:22.259 Registering Internal as a media playback plugin.
2010-01-10 13:23:22.298 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
            eno: No such file or directory (2)
2010-01-10 13:23:22.302 MMUnix::AddDevice() Error: failed to stat /dev/power, 
            eno: No such file or directory (2)
2010-01-10 13:23:22.307 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
            eno: No such file or directory (2)
2010-01-10 13:23:22.310 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-01-10 13:23:22.342 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-01-10 13:23:22.355 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-01-10 13:23:22.361 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-01-10 13:23:22.377 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-01-10 13:23:22.391 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-01-10 13:23:22.405 Found mainmenu.xml for theme 'Mythbuntu'
2010-01-10 13:23:22.792 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-01-10 13:23:22.792 Using protocol version 50
2010-01-10 13:23:23.964 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-01-10 13:23:24.691 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-01-10 13:23:24.893 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@liberty/var/lib/mythtv/videos/)
2010-01-10 13:23:24.926 New DB connection, total: 2
2010-01-10 13:23:24.926 Connected to database 'mythconverg' at host: localhost
2010-01-10 13:23:27.193 TV: Attempting to change from None to Watching Video
2010-01-10 13:23:27.424 TV: StartPlayer(0, Watching Video, main) -- begin
2010-01-10 13:23:27.456 AFD: codec WMAV2 has 2 channels
2010-01-10 13:23:27.458 AFD: Opened codec 0x7fafe8006390, id(WMAV2) type(Audio)
2010-01-10 13:23:27.460 AFD: Opened codec 0x7fafe800afd0, id(WMV3) type(Video)
2010-01-10 13:23:27.462 Opening audio device 'default'. ch 2(2) sr 32000
2010-01-10 13:23:27.462 Opening ALSA audio device 'default'.
2010-01-10 13:23:27.664 Mixer unable to find control Master
2010-01-10 13:23:27.665 Mixer unable to find control Master
2010-01-10 13:23:27.691 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-01-10 13:23:27.707 OSD Theme Dimensions W: 1280 H: 720
2010-01-10 13:23:27.876 TV: StartPlayer(0, Watching Video, main) -- end ok
2010-01-10 13:23:27.876 TV: Changing from None to Watching Video
2010-01-10 13:23:27.887 Realtime priority would require SUID as root.
2010-01-10 13:23:27.892 Video timing method: USleep with busy wait
2010-01-10 13:23:27.943 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-10 13:23:32.781 TV: Attempting to change from Watching Video to None
2010-01-10 13:23:32.815 TV: Changing from Watching Video to None
2010-01-10 13:23:32.818 ScreenSaverX11Private: DPMS Reactivated 1
2010-01-10 13:23:35.894 AudioPulseUtil: Resume Success
2010-01-10 13:23:35.894 Deleting UPnP client...


---

### Post by larsolav on 2010-01-11
Hi, I had the exact same problem! See my post: [http://ubuntuforums.org/showthread.php?t=1335833](http://ubuntuforums.org/showthread.php?t=1335833)
For me, I think it was my asound.conf file that messed things up for a reason...

Do you have an /etc/asound.conf ? And if so, what does it say?

---

### Post by dude08 on 2010-01-11
Thanks for pointing out that thread, but I don't have an /etc/asound.conf file or any related-looking config file in my home directory. Your post motivated me to put another 90 mins of tinkering around and I've since installed regular Ubuntu 9.10 x86-64 and am having the same problems. I recently tried changing my audio device to "ALSA:hw:1,3" based on the output from the command `aplay -l`:
> 
sean@liberty:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


 Now I'm getting a rate errror:
> 
2010-01-11 17:35:37.776 TV: StartPlayer(0, Watching Video, main) -- begin
2010-01-11 17:35:37.821 AFD: codec WMAV2 has 2 channels
2010-01-11 17:35:37.828 AFD: Opened codec 0x625e900, id(WMAV2) type(Audio)
2010-01-11 17:35:37.835 AFD: Opened codec 0x613d110, id(WMV3) type(Video)
2010-01-11 17:35:37.837 Opening audio device 'hw:1,3'. ch 2(2) sr 32000
2010-01-11 17:35:37.838 Opening ALSA audio device 'hw:1,3'.
2010-01-11 17:35:37.874 AudioOutput Error: Rate doesn't match (requested 32000Hz, got 48000Hz)
2010-01-11 17:35:37.874 AudioOutput Error: Unable to set ALSA parameters
2010-01-11 17:35:37.874 NVP(0): Disabling Audio, reason is: Unable to set ALSA parameters
2010-01-11 17:35:37.903 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'


---

