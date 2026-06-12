---
title: "HDMI Audio stops working upon exiting and re-entering Front-end"
date: 2009-11-23
forum: Mythbuntu
---

### Post by larsolav on 2009-11-23
Hi all,
I am running a fresh install of 9.10 on an EVGA board with integrated GeForce 9300 GPU using HDMI for audio and video.
Added "defaults.pcm.device 3" to /etc/asound.conf and changed MythTV sound to Alsa:default. Audio works great at least when playing recordings.

However, whenever I exit the front-end and then re-enter front-end there is no sound! I try logging out and in, but still no sound. The only thing that will bring back the audio is a reboot.

Frontend log says this upon playing a recording after exiting and re-enteringthe front-end:

> 2009-11-23 19:28:09.273 TV: Attempting to change from None to Watching WatchingRecording
2009-11-23 19:28:09.370 MythContext: Connecting to backend server: 192.168.1.71:6543 (try 1 of 1)
2009-11-23 19:28:09.371 Using protocol version 50
2009-11-23 19:28:09.484 TV: StartPlayer(0, Watching WatchingRecording, main) -- begin
2009-11-23 19:28:09.633 AFD: Opened codec 0x3740420, id(MPEG2VIDEO) type(Video)
2009-11-23 19:28:09.633 AFD: codec AC3 has 6 channels
2009-11-23 19:28:09.634 AFD: Opened codec 0x3ae7740, id(AC3) type(Audio)
2009-11-23 19:28:09.634 AFD: codec AC3 has 2 channels
2009-11-23 19:28:09.634 AFD: Opened codec 0x3ae7d80, id(AC3) type(Audio)
2009-11-23 19:28:09.635 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-23 19:28:09.635 Opening ALSA audio device 'default'.
2009-11-23 19:28:10.183 mixer unable to find control Master 1
2009-11-23 19:28:10.187 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-23 19:28:10.187 Opening ALSA audio device 'default'.
2009-11-23 19:28:10.189 mixer unable to find control Master 1
2009-11-23 19:28:10.473 NVP(0): Forcing decode extra audio option on (Video method requires it).
2009-11-23 19:28:10.474 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-11-23 19:28:10.475 OSD Theme Dimensions W: 1280 H: 720
2009-11-23 19:28:10.734 New DB connection, total: 3
2009-11-23 19:28:10.733 TV: StartPlayer(0, Watching WatchingRecording, main) -- end ok
2009-11-23 19:28:10.734 Connected to database 'mythconverg' at host: localhost
2009-11-23 19:28:10.735 Realtime priority would require SUID as root.
2009-11-23 19:28:10.737 TV: Changing from None to Watching WatchingRecording
2009-11-23 19:28:10.796 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-23 19:28:10.810 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-11-23 19:28:10.830 Video timing method: USleep with busy wait
2009-11-23 19:28:16.617 TV: Attempting to change from Watching WatchingRecording to None
2009-11-23 19:28:16.623 TV: Changing from Watching WatchingRecording to None


I googled "mixer unable to find control Master 1" but did not find any answers.
Anyone who can shed some light on my mystery? Thanks!

---

### Post by larsolav on 2009-11-25
Okay,
To further troubleshoot I deleted mythfrontend.log, rebooted, played a recording (audio works), exited frontend, re-entered frontend, played same recording (no audio).

Here is the frontend log with the audio working:

> Starting mythfrontend.real..
2009-11-25 21:43:05.451 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-25 21:43:05.452 Using runtime prefix = /usr
2009-11-25 21:43:05.452 Using configuration directory = /home/husebo/.mythtv
2009-11-25 21:43:06.324 Empty LocalHostName.
2009-11-25 21:43:06.324 Using localhost value of mythbox
2009-11-25 21:43:06.328 New DB connection, total: 1
2009-11-25 21:43:06.332 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:43:06.332 Closing DB connection named 'DBManager0'
2009-11-25 21:43:06.364 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-25 21:43:06.367 DPMS is active.
2009-11-25 21:43:06.493 Primary screen: 0.
2009-11-25 21:43:06.493 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:43:06.494 Using screen 0, 1920x1080 at 0,0
2009-11-25 21:43:06.598 MythUI Image Cache size set to 20971520 bytes
2009-11-25 21:43:06.599 Enabled verbose msgs:  important general
2009-11-25 21:43:06.726 Primary screen: 0.
2009-11-25 21:43:06.727 Using screen 0, 1920x1080 at 0,0
2009-11-25 21:43:06.872 Using theme base resolution of 1280x720
2009-11-25 21:43:06.886 LIRC: Successfully initialized '/dev/lircd' using '/home/husebo/.mythtv/lircrc' config
2009-11-25 21:43:06.886 JoystickMenuThread Error: Joystick disabled - Failed to read /home/husebo/.mythtv/joystickmenurc
2009-11-25 21:43:07.483 Using the Qt painter
2009-11-25 21:43:08.031 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-25 21:43:08.043 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-25 21:43:08.100 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-25 21:43:08.101 Unable to load window 'backgroundwindow' from base
2009-11-25 21:43:08.104 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-25 21:43:09.704 Desktop video mode: 1920x1080 60.0024 Hz
2009-11-25 21:43:09.919 Registering Internal as a media playback plugin.
2009-11-25 21:43:10.332 Registering WebBrowser as a media playback plugin.
2009-11-25 21:43:10.777 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-25 21:43:10.779 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-25 21:43:10.782 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-25 21:43:10.785 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-25 21:43:11.508 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-25 21:43:11.528 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-25 21:43:11.601 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-25 21:43:11.664 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-25 21:43:11.777 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-25 21:43:11.778 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-25 21:43:12.868 MythContext: Connecting to backend server: 192.168.1.71:6543 (try 1 of 1)
2009-11-25 21:43:12.869 Using protocol version 50
2009-11-25 21:43:24.311 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-11-25 21:43:25.407 New DB connection, total: 2
2009-11-25 21:43:25.408 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:43:25.443 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-25 21:43:37.027 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-11-25 21:43:37.126 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-11-25 21:43:37.372 AFD: Opened codec 0x7f4d106429c0, id(MPEG2VIDEO) type(Video)
2009-11-25 21:43:37.372 AFD: codec AC3 has 6 channels
2009-11-25 21:43:37.373 AFD: Opened codec 0x7f4d10669dd0, id(AC3) type(Audio)
2009-11-25 21:43:37.373 AFD: codec AC3 has 1 channels
2009-11-25 21:43:37.373 AFD: Opened codec 0x7f4d1066a200, id(AC3) type(Audio)
2009-11-25 21:43:37.375 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-25 21:43:37.376 Opening ALSA audio device 'default'.
2009-11-25 21:43:37.407 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-11-25 21:43:37.816 Mixer unable to find control PCM
2009-11-25 21:43:37.816 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.821 Mixer unable to find control PCM
2009-11-25 21:43:37.825 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-25 21:43:37.825 Opening ALSA audio device 'default'.
2009-11-25 21:43:37.827 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:37.833 Mixer unable to find control PCM
2009-11-25 21:43:38.756 NVP(0): Forcing decode extra audio option on (Video method requires it).
2009-11-25 21:43:38.756 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-11-25 21:43:38.758 OSD Theme Dimensions W: 1280 H: 720
2009-11-25 21:43:39.370 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2009-11-25 21:43:39.371 TV: Changing from None to Watching WatchingPreRecorded
2009-11-25 21:43:39.372 Realtime priority would require SUID as root.
2009-11-25 21:43:39.396 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-25 21:43:39.457 Video timing method: USleep with busy wait
2009-11-25 21:43:47.843 TV: Attempting to change from Watching WatchingPreRecorded to None
2009-11-25 21:43:47.888 TV: Changing from Watching WatchingPreRecorded to None
2009-11-25 21:43:47.889 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-25 21:44:13.434 Deleting UPnP client...

Half a minute later upon stopping playing the recording I exit frontend. There is only one line entered for that in the log:
> 2009-11-25 21:44:13.434 Deleting UPnP client...
I then open re-enter frontend and try the same recording:
> Starting mythfrontend.real..
2009-11-25 21:45:55.433 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org](www.mythtv.org)
2009-11-25 21:45:55.433 Using runtime prefix = /usr
2009-11-25 21:45:55.433 Using configuration directory = /home/husebo/.mythtv
2009-11-25 21:45:56.287 Empty LocalHostName.
2009-11-25 21:45:56.287 Using localhost value of mythbox
2009-11-25 21:45:56.293 New DB connection, total: 1
2009-11-25 21:45:56.295 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:45:56.295 Closing DB connection named 'DBManager0'
2009-11-25 21:45:56.301 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-25 21:45:56.302 DPMS is active.
2009-11-25 21:45:56.303 Primary screen: 0.
2009-11-25 21:45:56.305 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:45:56.306 Using screen 0, 1920x1080 at 0,0
2009-11-25 21:45:56.311 MythUI Image Cache size set to 20971520 bytes
2009-11-25 21:45:56.312 Enabled verbose msgs:  important general
2009-11-25 21:45:56.315 Primary screen: 0.
2009-11-25 21:45:56.315 Using screen 0, 1920x1080 at 0,0
2009-11-25 21:45:56.316 Using theme base resolution of 1280x720
2009-11-25 21:45:56.318 LIRC: Successfully initialized '/dev/lircd' using '/home/husebo/.mythtv/lircrc' config
2009-11-25 21:45:56.319 JoystickMenuThread Error: Joystick disabled - Failed to read /home/husebo/.mythtv/joystickmenurc
2009-11-25 21:45:56.430 Using the Qt painter
2009-11-25 21:45:56.479 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-25 21:45:56.483 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-25 21:45:56.488 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-25 21:45:56.488 Unable to load window 'backgroundwindow' from base
2009-11-25 21:45:56.493 New DB connection, total: 2
2009-11-25 21:45:56.493 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:45:56.495 New DB connection, total: 3
2009-11-25 21:45:56.495 Connected to database 'mythconverg' at host: localhost
2009-11-25 21:45:56.500 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-25 21:45:56.644 Desktop video mode: 1920x1080 60.0024 Hz
2009-11-25 21:45:56.731 Registering Internal as a media playback plugin.
2009-11-25 21:45:56.746 Registering WebBrowser as a media playback plugin.
2009-11-25 21:45:56.777 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-25 21:45:56.778 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-25 21:45:56.781 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-25 21:45:56.783 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-25 21:45:56.798 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-25 21:45:56.818 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-25 21:45:56.829 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-25 21:45:56.857 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-25 21:45:56.905 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2009-11-25 21:45:56.906 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-25 21:45:57.481 MythContext: Connecting to backend server: 192.168.1.71:6543 (try 1 of 1)
2009-11-25 21:45:57.482 Using protocol version 50
2009-11-25 21:46:01.627 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2009-11-25 21:46:02.400 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-25 21:46:07.330 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-11-25 21:46:07.401 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-11-25 21:46:07.582 AFD: Opened codec 0x53eede0, id(MPEG2VIDEO) type(Video)
2009-11-25 21:46:07.582 AFD: codec AC3 has 6 channels
2009-11-25 21:46:07.582 AFD: Opened codec 0x54b8db0, id(AC3) type(Audio)
2009-11-25 21:46:07.582 AFD: codec AC3 has 1 channels
2009-11-25 21:46:07.582 AFD: Opened codec 0x50f1610, id(AC3) type(Audio)
2009-11-25 21:46:07.583 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-25 21:46:07.583 Opening ALSA audio device 'default'.
2009-11-25 21:46:07.966 mixer unable to find control Master 1
2009-11-25 21:46:07.984 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-25 21:46:07.984 Opening ALSA audio device 'default'.
2009-11-25 21:46:07.989 mixer unable to find control Master 1
2009-11-25 21:46:08.177 NVP(0): Forcing decode extra audio option on (Video method requires it).
2009-11-25 21:46:08.177 FilterManager: Failed to load filter 'colorspace', no such filter exists
2009-11-25 21:46:08.178 OSD Theme Dimensions W: 1280 H: 720
2009-11-25 21:46:08.402 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2009-11-25 21:46:08.403 Realtime priority would require SUID as root.
2009-11-25 21:46:08.403 TV: Changing from None to Watching WatchingPreRecorded
2009-11-25 21:46:08.447 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-25 21:46:08.470 Video timing method: USleep with busy wait
2009-11-25 21:46:17.492 TV: Attempting to change from Watching WatchingPreRecorded to None
2009-11-25 21:46:17.510 TV: Changing from Watching WatchingPreRecorded to None
2009-11-25 21:46:17.510 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-25 21:46:22.840 AudioPulseUtil: Resume Success

Any one see anything in the logs on why the audio does not work after I re-enter the frontend? I flummoxed 
Thanks in advance! Happy Turkey-day!

---

### Post by SiHa on 2009-11-26
Just a wild stab in the dark, and by no means a fix, but perhaps a kludge.

The first (successful) time, it's complainig about PCM, but sound still works. The second time, it's Master 1. Is Master 1 muted in alsamixer?

Why it's picking a different channel God only knows...

---

### Post by larsolav on 2009-11-30
Thanks Simon,
"Master" is unmuted in alsamixer... Still a mystery to me what is going on. I guess it is not a huge problem, only when the Front-end crashes once in a while I'll have to reboot instead of just starting up the front-end again. I guess my up-time statistics will suffer!:D

---

### Post by SiHa on 2009-11-30
> **larsolav said:**
> I guess my up-time statistics will suffer!:D



The longest I had my old frontend up was about a month. It just got suspended every night, rather than turned off.

---

### Post by nunrgguy on 2009-12-05
I have a similar issue with one of my f/es. For some reason the mixer on the pulse audio side keeps defaulting to mute on the master on reboot.

---

### Post by larsolav on 2009-12-05
Well, kinda fixed it this morning.
I commented out "defaults.pcm.device 3" to /etc/asound.conf by putting "#" in front of the sentence, changed MythTV sound to Alsa:HDMI, and rebooted.
After reboot I can now exit and enter the frontend again without loosing the sound in Mythtv! I haven't tried Mythmusic or any other players to see if I get sound, but I guess the default sound is no longer over HDMI...

---

### Post by dmfrey on 2009-12-07
try running
```

ps -ef | grep mythfrontend.real

```

See if you have more than one session active. The one not showing session id is the current one, the others need to be removed.  

I used to have this problem in 9.04.  I haven't seen it 9.10.  Multiple sessions would get started and it caused audio not to play (among other issues).

If this is so, you have to delete the extra sessions in something like ~/.gnome/sessions.  I am drawing a blank on the exact location but you should be able match session id's from the ps output files in the directory.  When these sessions have been delete restart gdm.

I hope this helps.

---

### Post by larsolav on 2009-12-08
> **dmfrey said:**
> try running
```

ps -ef | grep mythfrontend.real

```

See if you have more than one session active. The one not showing session id is the current one, the others need to be removed.  

I used to have this problem in 9.04.  I haven't seen it 9.10.  Multiple sessions would get started and it caused audio not to play (among other issues).

If this is so, you have to delete the extra sessions in something like ~/.gnome/sessions.  I am drawing a blank on the exact location but you should be able match session id's from the ps output files in the directory.  When these sessions have been delete restart gdm.

I hope this helps.

Thanks dmfrey!
Here is the output of that command:
> husebo@mythbox:~$ ps -ef | grep mythfrontend.real
husebo    2102  2070  0 07:37 pts/0    00:00:00 grep --color=auto mythfrontend.real
husebo    2416     1  9 Dec05 ?        07:19:21 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log

Does that mean I have two instances of the frontend running? And how do I prevent it? I don't have a ~/.gnome/sessions on my system. I have ~/.gnome2/ and ~/.gnome2_private/, both without any "sessions" in them....

---

### Post by dmfrey on 2009-12-08
larsolav,

You look to be ok, the first process is just your grep process, the other is the actual mythfrontend process.

This doesn't appear to be your issue.

It sounded familiar to mine, but that was with 9.04.  Now that I am on 9.10 I haven't seen that issue.

---

### Post by larsolav on 2009-12-09
> **dmfrey said:**
> larsolav,

You look to be ok, the first process is just your grep process, the other is the actual mythfrontend process.

This doesn't appear to be your issue.

It sounded familiar to mine, but that was with 9.04.  Now that I am on 9.10 I haven't seen that issue.

Thanks!
So much about Linux I need to learn...

---

