---
title: "New mythbuntu 10.10 install on ATI HD 4250 goed very ugly..."
date: 2011-07-01
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2011-07-01
This is a new Mythbuntu 10.10 64bit install on a custom system running Windows 7 Home Premium, a Windows HTPC.  Because Mythtv Windows cannot display recordings from 0.24 fixes back-end without stuttering, I tried to add a Mythbuntu 10.10 64bit front end.  After fixing all the little connection, mysql and video driver glitches , now I am at an impasse because when the frontend starts, it immediately crashes (139) and attempts a restart.  The only way I found to stop this compulsive behavior was to restart.  The frontend log complained about no audio drivers, even though they exist in the mobos ATI HD 4250.  Xfce's mixer didn't actually appear to be able to do anything. So I used Mythbuntu Control Centre to bring in Ubuntu standard.   Now sound preferences correctly points to RS880 Audio Device as hardware and RS880 S Audio Device [Radeon HD 4200] Digital Stereo (HDMI) as output, but Mythtv frontend still chokes, and triggers the eternal restart...

2011-07-01 19:08:46.869 mythfrontend version: fixes/0.24 [v0.24.1-36-gd06878a] [www.mythtv.org](www.mythtv.org)
2011-07-01 19:08:46.869 Using runtime prefix = /usr
2011-07-01 19:08:46.869 Using configuration directory = /home/ljohnson/.mythtv
2011-07-01 19:08:46.869 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-01 19:08:47.645 Empty LocalHostName.
2011-07-01 19:08:47.645 Using localhost value of KISE-057
2011-07-01 19:08:47.657 New DB connection, total: 1
2011-07-01 19:08:47.672 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:08:47.680 Closing DB connection named 'DBManager0'
2011-07-01 19:08:47.693 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:08:47.707 Current locale en_US
2011-07-01 19:08:47.707 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-01 19:08:48.675 ScreenSaverX11Private: XScreenSaver support enabled
2011-07-01 19:08:48.675 ScreenSaverX11Private: Gnome screen saver support enabled
2011-07-01 19:08:48.677 DPMS is disabled.
2011-07-01 19:08:48.786 Desktop video mode: 1920x1080 60.000 Hz
2011-07-01 19:08:49.106 Enabled verbose msgs:  important general
2011-07-01 19:08:49.148 Loading en_us translation for module mythfrontend
2011-07-01 19:08:49.282 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2011-07-01 19:08:49.282 JoystickMenuThread: Joystick disabled - Failed to read /home/ljohnson/.mythtv/joystickmenurc
2011-07-01 19:08:49.800 Using Frameless Window
2011-07-01 19:08:49.801 Using Full Screen Window
2011-07-01 19:08:50.023 Using the Qt painter
2011-07-01 19:08:50.211 New DB connection, total: 2
2011-07-01 19:08:50.235 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:08:50.247 New DB connection, total: 3
2011-07-01 19:08:50.258 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:08:50.460 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-01 19:08:51.411 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-07-01 19:08:51.412 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-07-01 19:08:51.415 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-07-01 19:08:51.415 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-07-01 19:08:52.145 Pulse: PulseAudio suspend OK
2011-07-01 19:08:52.145 Audio output device is set to a Windows device but Windows support is not compiled in!
2011-07-01 19:08:52.145 No useable audio output driver found.
2011-07-01 19:08:52.145 Don't disable OSS support unless you're not running on Linux.
2011-07-01 19:08:52.339 Pulse: PulseAudio resume OK
Restarting mythfrontend.real...

Driver, driver, where at thou...?

Per bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513069)

from: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Installed the following packages:
linux-backports-modules-alsa-2.6.35-30-generic (2.6.35-30.22)
linux-backports-modules-alsa-maverick-generic (2.6.35.30.38)

Now the log reports...
2011-07-01 19:41:47.747 mythfrontend version: fixes/0.24 [v0.24.1-36-gd06878a] [www.mythtv.org](www.mythtv.org)
2011-07-01 19:41:47.747 Using runtime prefix = /usr
2011-07-01 19:41:47.747 Using configuration directory = /home/ljohnson/.mythtv
2011-07-01 19:41:47.748 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-01 19:41:48.438 Empty LocalHostName.
2011-07-01 19:41:48.438 Using localhost value of KISE-057
2011-07-01 19:41:48.441 New DB connection, total: 1
2011-07-01 19:41:48.466 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:41:48.469 Closing DB connection named 'DBManager0'
2011-07-01 19:41:48.479 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:41:48.504 Current locale en_US
2011-07-01 19:41:48.504 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-01 19:41:49.478 ScreenSaverX11Private: XScreenSaver support enabled
2011-07-01 19:41:49.478 ScreenSaverX11Private: Gnome screen saver support enabled
2011-07-01 19:41:49.479 DPMS is disabled.
2011-07-01 19:41:49.580 Desktop video mode: 1920x1080 60.000 Hz
2011-07-01 19:41:49.925 Enabled verbose msgs:  important general
2011-07-01 19:41:49.983 Loading en_us translation for module mythfrontend
2011-07-01 19:41:50.120 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
			eno: No such file or directory (2)
2011-07-01 19:41:50.120 JoystickMenuThread: Joystick disabled - Failed to read /home/ljohnson/.mythtv/joystickmenurc
2011-07-01 19:41:50.660 Using Frameless Window
2011-07-01 19:41:50.660 Using Full Screen Window
2011-07-01 19:41:50.896 Using the Qt painter
2011-07-01 19:41:51.041 New DB connection, total: 2
2011-07-01 19:41:51.074 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-01 19:41:51.080 New DB connection, total: 3
2011-07-01 19:41:51.096 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:41:51.259 Connected to database 'mythconverg' at host: 192.168.0.55
2011-07-01 19:41:51.985 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-07-01 19:41:51.985 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-07-01 19:41:51.986 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-07-01 19:41:51.986 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-07-01 19:41:52.644 Pulse: PulseAudio suspend OK
2011-07-01 19:41:52.644 Audio output device is set to a Windows device but Windows support is not compiled in!
2011-07-01 19:41:52.644 No useable audio output driver found.
2011-07-01 19:41:52.644 Don't disable OSS support unless you're not running on Linux.
2011-07-01 19:41:52.742 Pulse: PulseAudio resume OK
Restarting mythfrontend.real...

Alsa Mixer: ```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.23 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA ATI HDMI                                   F1:  Help               &#9474;
&#9474; Chip: ATI RS690/780 HDMI                             F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: S/PDIF                                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                     &#9484;&#9472;&#9472;&#9488;                                     &#9474;
&#9474;                                     &#9474;OO&#9474;                                     &#9474;
&#9474;                                     &#9492;&#9472;&#9472;&#9496;                                     &#9474;
&#9474;                                  < S/PDIF >                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```
 
So I ran Alsa Info Script ([http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh))
[http://www.alsa-project.org/db/?f=94caa729bc5e9e7c6eb086a492e368a343a646cc](http://www.alsa-project.org/db/?f=94caa729bc5e9e7c6eb086a492e368a343a646cc)

and no joy yet...Help!!!

---

### Post by ian dobson on 2011-07-02
Hi,

OK so you tried MythTV under windows and it couldn't play videos, you then installed ubuntu/mythbuntu and the frontend crashes all the time. Did you use the same host name for the windows install and the ubuntu install? If so thats your problem. MythTV stores almost all the configuration information in the SQL database, using the host name to know which PC uses which parameter.

Looking in your log files I see **Audio output device is set to a Windows device but Windows support is not compiled in!** which I imagine could cause your problem or there could be other settings which could crash the frontend. 

Backup you mySql database then manually delete all the settings for the frontend and retry, or just rename the frontend to something else and retry.

Note: ATI aren't the best cards for MythTV, I can only speak for Linux but I've never had problems with NVidia cards.

Regards
Ian Dobson

---

### Post by keepitsimpleengr on 2011-07-02
> **ian dobson said:**
> Hi,

&#8943; just rename the frontend to something else and retry.

Note: ATI aren't the best cards for MythTV, I can only speak for Linux but I've never had problems with NVidia cards. &#8943;

Right on!   Worked like a charm!  Point your elbow at the ceiling and pat yourself on the back for me!

Regards nVidia cards &#8943; I prefer also but the mobo came with HD 4250 and if it works….  In any case, this HTPC reside in the bedroom and drives an ancient flat-screen.

· &#8943; Now to fix the hang on video play stop &#8943; ·

---

### Post by ian dobson on 2011-07-02
Hi,

Glad to be of service. Log files are there to tell you whats wrong....

Regards
Ian Dobson

---

