---
title: "DPMS is disabled but my screen starts to go black every 10 minutes."
date: 2009-11-01
forum: Mythbuntu
---

### Post by williammanda on 2009-11-01
My question is what the title states...DPMS is disabled but my screen starts to go black every 10 minutes while viewing recordings or videos. My frontend log say:

```
Starting mythfrontend.real..
2009-11-01 22:02:13.933 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-01 22:02:13.933 Using runtime prefix = /usr
2009-11-01 22:02:13.934 Using configuration directory = /home/william/.mythtv
2009-11-01 22:02:14.348 Empty LocalHostName.
2009-11-01 22:02:14.348 Using localhost value of C2Q
2009-11-01 22:02:14.348 Testing network connectivity to '192.168.1.100'
2009-11-01 22:02:14.356 New DB connection, total: 1
2009-11-01 22:02:14.359 Connected to database 'mythconverg' at host: 192.168.1.100
2009-11-01 22:02:14.360 Closing DB connection named 'DBManager0'
2009-11-01 22:02:14.368 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-01 22:02:14.369 **DPMS is disabled.**
2009-11-01 22:02:14.371 Primary screen: 0.
2009-11-01 22:02:14.371 Connected to database 'mythconverg' at host: 192.168.1.100
2009-11-01 22:02:14.372 Using screen 0, 1366x768 at 0,0
2009-11-01 22:02:14.386 MythUI Image Cache size set to 20971520 bytes
2009-11-01 22:02:14.386 Enabled verbose msgs:  important general
2009-11-01 22:02:14.391 Primary screen: 0.
2009-11-01 22:02:14.391 Using screen 0, 1366x768 at 0,0
2009-11-01 22:02:14.392 Using theme base resolution of 1280x720
2009-11-01 22:02:14.396 LIRC: Successfully initialized '/dev/lircd' using '/home/william/.mythtv/lircrc' config
2009-11-01 22:02:14.396 JoystickMenuThread Error: Joystick disabled - Failed to read /home/william/.mythtv/joystickmenurc
2009-11-01 22:02:14.481 Using the Qt painter
2009-11-01 22:02:14.546 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-01 22:02:14.550 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-01 22:02:14.555 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-01 22:02:14.555 Unable to load window 'backgroundwindow' from base
2009-11-01 22:02:14.559 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-01 22:02:14.569 New DB connection, total: 2
2009-11-01 22:02:14.569 New DB connection, total: 3
2009-11-01 22:02:14.569 Connected to database 'mythconverg' at host: 192.168.1.100
2009-11-01 22:02:14.571 Connected to database 'mythconverg' at host: 192.168.1.100
2009-11-01 22:02:14.876 Desktop video mode: 1366x768 59.9592 Hz
2009-11-01 22:02:15.014 Registering Internal as a media playback plugin.
2009-11-01 22:02:15.041 MMUnix::AddDevice() Error: failed to stat /dev/bdi, 
			eno: No such file or directory (2)
2009-11-01 22:02:15.044 MMUnix::AddDevice() Error: failed to stat /dev/power, 
			eno: No such file or directory (2)
2009-11-01 22:02:15.048 MMUnix::AddDevice() Error: failed to stat /dev/trace, 
			eno: No such file or directory (2)
2009-11-01 22:02:15.054 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-01 22:02:15.082 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-01 22:02:15.111 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-01 22:02:15.124 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-01 22:02:15.161 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-01 22:02:15.187 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2009-11-01 22:02:15.190 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-01 22:02:15.472 MythContext: Connecting to backend server: 192.168.1.100:6543 (try 1 of 1)
2009-11-01 22:02:15.472 Using protocol version 50
```

I have ubuntu 9.10 and installed mythbuntu control center. Any ideas?
Thanks

---

### Post by Mister.Vash on 2009-11-01
Have you checked the screensaver and the idle settings?

Also, take a look at the power management settings in the bios and double check the video section.  It might have a blank screen feature set there.

---

### Post by williammanda on 2009-11-02
> **Mister.Vash said:**
> Have you checked the screensaver and the idle settings?

The screen saver is enabled. I have tried several different time settings.

> **Mister.Vash said:**
> Also, take a look at the power management settings in the bios and double check the video section.  It might have a blank screen feature set there.

The power management in the bios is off and I don't have integrated video.

This has worked fine for the last few versions and it is happening on two different computers.

---

### Post by williammanda on 2009-11-05
I just found out that there is a known bug for the problem I'm having...it's a bug in gnome-screensaver ...it's not properly responding to --poke.

---

### Post by ZedThou on 2009-11-05
I was just having this problem as well even after disabling apm in the bios, making gnome-screensaver unexecutable and disabling DPMS in the X config. What does 'xset q' say? If it looks something like this

```

Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600

```then you also need to run 'xset s noblank'

That fixed it for me anyway.

---

