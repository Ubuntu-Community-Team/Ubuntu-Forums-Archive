---
title: "VDPAU fails when playing back a recording and OpenGL is the Paint Engine"
date: 2009-11-14
forum: Mythbuntu
---

### Post by terp4life2001 on 2009-11-14
I suspect that this issue may not be a bug, but instead an incompatibility.

If I have to choose between the two- VDPAU (for playback) trumps OpenGL (as a paint menu), since this is running on an ION.
The problem is that the mythtv menus are not smooth using the Qt paint engine. Is there anything else I can do to help the menu aesthetics if I can't use OpenGL?

Thanks,

//Rob

Here is my log for reference.

Script started on Sat 14 Nov 2009 02:24:29 PM PST
]0;rwlove@lefteye: ~rwlove@lefteye:~$ exitsu -ls -l /usr/local/bin/runmyth
[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[Csu -[Kexit[Kmythfrontend -v "important,general"
2009-11-14 14:24:48.280 mythfrontend version: branches/release-0-22-fixes [22783] [www.mythtv.org](www.mythtv.org)
2009-11-14 14:24:48.324 AudioPulseUtil: Suspend Success
2009-11-14 14:24:48.325 Using runtime prefix = /usr
2009-11-14 14:24:48.325 Using configuration directory = /home/rwlove/.mythtv
2009-11-14 14:24:49.184 Empty LocalHostName.
2009-11-14 14:24:49.184 Using localhost value of lefteye
2009-11-14 14:24:49.185 Testing network connectivity to 'thecore'
2009-11-14 14:24:49.214 New DB connection, total: 1
2009-11-14 14:24:49.221 Connected to database 'mythconverg' at host: thecore
2009-11-14 14:24:49.223 Closing DB connection named 'DBManager0'
2009-11-14 14:24:49.259 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-14 14:24:49.261 DPMS is disabled.
2009-11-14 14:24:49.265 Primary screen: 0.
2009-11-14 14:24:49.267 Connected to database 'mythconverg' at host: thecore
2009-11-14 14:24:49.270 Using screen 0, 1920x1080 at 0,0
2009-11-14 14:24:49.294 MythUI Image Cache size set to 20971520 bytes
2009-11-14 14:24:49.296 Enabled verbose msgs: important general
2009-11-14 14:24:49.313 Primary screen: 0.
2009-11-14 14:24:49.314 Using screen 0, 1920x1080 at 0,0
2009-11-14 14:24:49.316 Using theme base resolution of 1280x720
2009-11-14 14:24:49.331 LIRC: Successfully initialized '/dev/lircd' using '/home/rwlove/.mythtv/lircrc' config
2009-11-14 14:24:49.331 JoystickMenuThread Error: Joystick disabled - Failed to read /home/rwlove/.mythtv/joystickmenurc
2009-11-14 14:24:49.860 Using the OpenGL painter
2009-11-14 14:24:50.183 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-14 14:24:50.195 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-14 14:24:50.225 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-14 14:24:50.226 Unable to load window 'backgroundwindow' from base
2009-11-14 14:24:50.234 New DB connection, total: 2
2009-11-14 14:24:50.236 New DB connection, total: 3
2009-11-14 14:24:50.238 Connected to database 'mythconverg' at host: thecore
2009-11-14 14:24:50.238 Connected to database 'mythconverg' at host: thecore
2009-11-14 14:24:50.256 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-14 14:24:50.717 Desktop video mode: 1920x1080 60.0024 Hz
2009-11-14 14:24:50.991 Key Up is bound to multiple actions in context TV Playback.
2009-11-14 14:24:50.992 Key Down is bound to multiple actions in context TV Playback.
2009-11-14 14:24:51.107 Registering Internal as a media playback plugin.
2009-11-14 14:24:51.217 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-14 14:24:51.299 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-14 14:24:51.376 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-14 14:24:51.413 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-14 14:24:51.518 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-14 14:24:51.637 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2009-11-14 14:24:51.644 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-14 14:24:53.622 Using NV NPOT texture extension
2009-11-14 14:24:53.986 MythContext: Connecting to backend server: 192.168.1.210:6543 (try 1 of 1)
2009-11-14 14:24:53.988 Using protocol version 50
2009-11-14 14:24:55.766 Loading menu theme from /usr/share/mythtv/themes/classic//tvmenu.xml
2009-11-14 14:24:58.106 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-14 14:25:01.123 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-11-14 14:25:01.202 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-11-14 14:25:03.304 RingBuf(myth://192.168.1.210:6543/1476_20091114115900.mpg): Waited 2.0 seconds for data to become available...
2009-11-14 14:25:03.982 AFD: Opened codec 0xbc493d0, id(MPEG2VIDEO) type(Video)
2009-11-14 14:25:03.982 AFD: codec AC3 has 2 channels
2009-11-14 14:25:03.984 AFD: Opened codec 0xbc49bc0, id(AC3) type(Audio)
2009-11-14 14:25:03.989 Opening audio device 'hdmi'. ch 2(2) sr 48000
2009-11-14 14:25:03.989 Opening ALSA audio device 'hdmi'.
2009-11-14 14:25:04.105 mixer unable to find control Master 1
2009-11-14 14:25:04.333 VidOutVDPAU Error: Failed to initialise VDPAU
2009-11-14 14:25:04.365 VideoOutput, Error: Not compiled with any useable video output method.
2009-11-14 14:25:04.365 NVP(0), Error: Couldn't create VideoOutput instance. Exiting..
2009-11-14 14:25:04.365 Unable to initialize video.
^C
]0;rwlove@lefteye: ~rwlove@lefteye:~$ [H[2J]0;rwlove@lefteye: ~rwlove@lefteye:~$ exit
exit

Script done on Sat 14 Nov 2009 02:25:17 PM PST

---

### Post by terp4life2001 on 2009-11-14
I should mention that the OS is Mythbuntu 9.10.

---

### Post by ZedThou on 2009-11-14
I'm using the two together with no issues, using the 190.42 nvidia driver. Have you tried the latest driver?

---

### Post by terp4life2001 on 2009-11-14
> **ZedThou said:**
> I'm using the two together with no issues, using the 190.42 nvidia driver. Have you tried the latest driver?

Yes, I'm using the 190.42 driver. I just re-installed it and it's 32bit OpenGL libraries.

---

### Post by jyavenard on 2009-11-14
> **ZedThou said:**
> I'm using the two together with no issues, using the 190.42 nvidia driver. Have you tried the latest driver?

And if you select Qt for paint menu, are you sure you get VDPAU playback ?
How do you know its using VDPAU? does it say so in the log ?

When VDPAU can't be initialised, it reverts to software decoding, so when you select a VDPAU profile you may not always get it.

With the error shown in your log, are you sure you are using "nvidia" for the graphic drivers in xorg.conf ?

Looks like VDPAU isn't available at all on your system ; so either you aren't using the nvidia drivers for display, or your video card doesn't support vdpau...

---

### Post by terp4life2001 on 2009-11-14
> **jyavenard said:**
> And if you select Qt for paint menu, are you sure you get VDPAU playback ?
How do you know its using VDPAU? does it say so in the log ?

When VDPAU can't be initialised, it reverts to software decoding, so when you select a VDPAU profile you may not always get it.

With the error shown in your log, are you sure you are using "nvidia" for the graphic drivers in xorg.conf ?

Looks like VDPAU isn't available at all on your system ; so either you aren't using the nvidia drivers for display, or your video card doesn't support vdpau...

Yes it does use VDPAU when Qt is the pain engine. I know that because this is an NVIDIA-Ion system. It only has a 1.6Ghz Atom processor on it. Before I had the VDPAU settings correct in mythtv and mplayer I had played back video without VDPAU and it pegs the CPU with the SW decode. So much that you can hardly do much but Ctrl-C the application to stop it and that signal is considerably delayed.

The last few lines of the log I posted say,

2009-11-14 14:25:04.333 VidOutVDPAU Error: Failed to initialise VDPAU
2009-11-14 14:25:04.365 VideoOutput, Error: Not compiled with any useable video output method.
2009-11-14 14:25:04.365 NVP(0), Error: Couldn't create VideoOutput instance. Exiting..
2009-11-14 14:25:04.365 Unable to initialize video.

so I do think that VDPAU is failing when OpenGL is the paint engine. However, it doesn't seem to be falling back to SW decode. 'top' doesn't show anything using much of the CPU. It seems to just fail and mythfrontend just sits there saying, "Please wait..."

---

### Post by jyavenard on 2009-11-14
It could be that you haven't allocated enough memory to the GPU, recommended minimum is 512MB ; you increase that value in the BIOS.

VDPAU and OpenGL aren't related to each other... Only difference is the extra graphic RAM required.

---

### Post by jyavenard on 2009-11-14
And post the entire log of playing a video with -v playback

You're snippet doesn't give much clue as to what's wrong nor if VDPAU libraries are properly loading

---

### Post by terp4life2001 on 2009-11-14
> **jyavenard said:**
> It could be that you haven't allocated enough memory to the GPU, recommended minimum is 512MB ; you increase that value in the BIOS.

VDPAU and OpenGL aren't related to each other... Only difference is the extra graphic RAM required.

My BIOS only has an option for the "iGPU Frame Buffer".

The settings I had been using were-

"iGPU Frame Buffer Detect: Auto"
the next field was unselectable becuaseit was auto, but it said,
"iGPU Frame Buffer Size: 128"
 
The max size it allows after I change the detect value to "Manual" is 256MB. After doing that, if I set the paint engine to Qt, it crushes my CPU. By that I mean that mythfrontend is maxing out my CPU, observed using 'top'. Even ssh'ing into the machine is very slow, the mythfrontend GUI is pretty much unusable.

The resultant log is-

Script started on Sat 14 Nov 2009 05:53:29 PM PST
]0;rwlove@lefteye: ~rwlove@lefteye:~$ 
[4@(reverse-i-search)`':[C-': mythfrontend -v "important,general"[1@v[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C
[6P]0;rwlove@lefteye: ~rwlove@lefteye:~$
]0;rwlove@lefteye: ~rwlove@lefteye:~$ [C[C[C[C[C[C[C[C[C[C[C[C[C
2009-11-14 17:53:33.379 mythfrontend version: branches/release-0-22-fixes [22783] [www.mythtv.org](www.mythtv.org)
2009-11-14 17:53:33.436 AudioPulseUtil: Suspend Success
2009-11-14 17:53:33.437 Using runtime prefix = /usr
2009-11-14 17:53:33.438 Using configuration directory = /home/rwlove/.mythtv
2009-11-14 17:53:34.302 Empty LocalHostName.
2009-11-14 17:53:34.302 Using localhost value of lefteye
2009-11-14 17:53:34.303 Testing network connectivity to 'thecore'
2009-11-14 17:53:34.337 New DB connection, total: 1
2009-11-14 17:53:34.343 Connected to database 'mythconverg' at host: thecore
2009-11-14 17:53:34.344 Closing DB connection named 'DBManager0'
2009-11-14 17:53:34.370 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-14 17:53:34.374 DPMS is active.
2009-11-14 17:53:34.377 Primary screen: 0.
2009-11-14 17:53:34.381 Connected to database 'mythconverg' at host: thecore
2009-11-14 17:53:34.384 Using screen 0, 1920x1080 at 0,0
2009-11-14 17:53:34.416 MythUI Image Cache size set to 20971520 bytes
2009-11-14 17:53:34.418 Enabled verbose msgs: important general
2009-11-14 17:53:34.433 Primary screen: 0.
2009-11-14 17:53:34.435 Using screen 0, 1920x1080 at 0,0
2009-11-14 17:53:34.437 Using theme base resolution of 1280x720
2009-11-14 17:53:34.469 LIRC: Successfully initialized '/dev/lircd' using '/home/rwlove/.mythtv/lircrc' config
2009-11-14 17:53:34.469 JoystickMenuThread Error: Joystick disabled - Failed to read /home/rwlove/.mythtv/joystickmenurc
2009-11-14 17:53:35.059 Using the OpenGL painter
2009-11-14 17:53:39.496 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-14 17:53:39.510 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-14 17:53:39.528 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-14 17:53:39.529 Unable to load window 'backgroundwindow' from base
2009-11-14 17:53:39.561 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-14 17:53:39.992 Desktop video mode: 1920x1080 60.0024 Hz
2009-11-14 17:53:40.247 Key Up is bound to multiple actions in context TV Playback.
2009-11-14 17:53:40.248 Key Down is bound to multiple actions in context TV Playback.
2009-11-14 17:53:40.346 Registering Internal as a media playback plugin.
2009-11-14 17:53:40.453 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-14 17:53:40.522 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-14 17:53:40.605 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-14 17:53:40.640 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-14 17:53:40.749 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-14 17:53:40.881 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2009-11-14 17:53:40.888 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-14 17:53:42.868 Using NV NPOT texture extension
Killed
]0;rwlove@lefteye: ~rwlove@lefteye:~$ exit

---

### Post by terp4life2001 on 2009-11-14
> **jyavenard said:**
> And post the entire log of playing a video with -v playback

You're snippet doesn't give much clue as to what's wrong nor if VDPAU libraries are properly loading

Here it is-

Script started on Sat 14 Nov 2009 05:59:24 PM PST
]0;rwlove@lefteye: ~rwlove@lefteye:~$ 
[4@(reverse-i-search)`':[Cp': cp typescript /mnt/thebrain/shared/[10Pl': mythfrontend -v playback[1@a[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[1@y[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C
[8P]0;rwlove@lefteye: ~rwlove@lefteye:~$
]0;rwlove@lefteye: ~rwlove@lefteye:~$ [C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C
2009-11-14 17:59:33.933 mythfrontend version: branches/release-0-22-fixes [22783] [www.mythtv.org](www.mythtv.org)
2009-11-14 17:59:33.980 AudioPulseUtil: Suspend Success
2009-11-14 17:59:33.982 Using runtime prefix = /usr
2009-11-14 17:59:33.982 Using configuration directory = /home/rwlove/.mythtv
2009-11-14 17:59:34.844 Empty LocalHostName.
2009-11-14 17:59:34.844 Using localhost value of lefteye
2009-11-14 17:59:34.845 Testing network connectivity to 'thecore'
2009-11-14 17:59:34.874 New DB connection, total: 1
2009-11-14 17:59:34.882 Connected to database 'mythconverg' at host: thecore
2009-11-14 17:59:34.884 Closing DB connection named 'DBManager0'
2009-11-14 17:59:34.907 ScreenSaverX11Private: Gnome screen saver support enabled
2009-11-14 17:59:34.910 DPMS is active.
2009-11-14 17:59:34.914 Primary screen: 0.
2009-11-14 17:59:34.916 Connected to database 'mythconverg' at host: thecore
2009-11-14 17:59:34.919 Using screen 0, 1920x1080 at 0,0
2009-11-14 17:59:34.945 MythUI Image Cache size set to 20971520 bytes
2009-11-14 17:59:34.945 user: 1000 effective user: 1000 before privileged thread
2009-11-14 17:59:34.945 user: 1000 effective user: 1000 run_priv_thread
2009-11-14 17:59:34.945 user: 1000 effective user: 1000 after privileged thread
2009-11-14 17:59:34.947 Enabled verbose msgs:  important general playback
2009-11-14 17:59:34.968 Primary screen: 0.
2009-11-14 17:59:34.970 Using screen 0, 1920x1080 at 0,0
2009-11-14 17:59:34.972 Using theme base resolution of 1280x720
2009-11-14 17:59:34.998 LIRC: Successfully initialized '/dev/lircd' using '/home/rwlove/.mythtv/lircrc' config
2009-11-14 17:59:34.999 JoystickMenuThread Error: Joystick disabled - Failed to read /home/rwlove/.mythtv/joystickmenurc
2009-11-14 17:59:35.631 Using the OpenGL painter
2009-11-14 17:59:36.030 Loaded base theme from /usr/share/mythtv/themes/Mythbuntu/base.xml
2009-11-14 17:59:36.046 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2009-11-14 17:59:36.066 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2009-11-14 17:59:36.068 Unable to load window 'backgroundwindow' from base
2009-11-14 17:59:36.094 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-14 17:59:36.538 Desktop video mode: 1920x1080 60.0024 Hz
2009-11-14 17:59:36.584 max_width: 1920 max_height: 1080
2009-11-14 17:59:36.812 Key Up is bound to multiple actions in context TV Playback.
2009-11-14 17:59:36.813 Key Down is bound to multiple actions in context TV Playback.
2009-11-14 17:59:36.917 Registering Internal as a media playback plugin.
2009-11-14 17:59:37.022 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-11-14 17:59:37.090 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2009-11-14 17:59:37.182 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2009-11-14 17:59:37.208 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2009-11-14 17:59:37.315 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2009-11-14 17:59:37.445 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2009-11-14 17:59:37.452 Found mainmenu.xml for theme 'Mythbuntu'
2009-11-14 17:59:39.382 Using NV NPOT texture extension
2009-11-14 17:59:39.727 MythContext: Connecting to backend server: 192.168.1.210:6543 (try 1 of 1)
2009-11-14 17:59:39.729 Using protocol version 50
2009-11-14 18:00:20.492 ScreenSaverX11Private: Calling gnome-screensaver-command --poke
2009-11-14 18:00:24.242 Loading menu theme from /usr/share/mythtv/themes/classic//tvmenu.xml
2009-11-14 18:00:26.304 New DB connection, total: 2
2009-11-14 18:00:26.306 Connected to database 'mythconverg' at host: thecore
2009-11-14 18:00:26.308 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/recordings-ui.xml
2009-11-14 18:00:31.532 TV: StartTV() -- begin
2009-11-14 18:00:31.545 TV: ctor
2009-11-14 18:00:31.640 TV: DrawUnusedRects() -- begin
2009-11-14 18:00:31.640 TV: DrawUnusedRects() -- end
2009-11-14 18:00:31.642 TV: tv->Playback() -- begin
2009-11-14 18:00:31.655 TV: tv->Playback() -- end
2009-11-14 18:00:31.655 TV: StartTV -- process events begin
2009-11-14 18:00:31.739 TV: HandleStateChange(0) -- begin
2009-11-14 18:00:31.739 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-11-14 18:00:31.746 RingBuf(myth://192.168.1.210:6543/1476_20091114115900.mpg): OpenFile(myth://192.168.1.210:6543/1476_20091114115900.mpg, 12)
2009-11-14 18:00:31.770 RingBuf(myth://192.168.1.210:6543/1476_20091114115900.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-11-14 18:00:31.820 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-11-14 18:00:32.569 AFD: Stream #0, has id 0x940 codec id MPEG2VIDEO, type Video, bitrate 2235200 at 0x1f6bea0
2009-11-14 18:00:32.573 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2009-11-14 18:00:32.573 VDP: LoadBestPreferences(2048x2048, 0)
2009-11-14 18:00:32.573 VDP: LoadBestPreferences(2048x2048, 60)
2009-11-14 18:00:32.573 VDP: LoadBestPreferences(528x480, 60)
2009-11-14 18:00:32.576 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2009-11-14 18:00:32.576 VDP: LoadBestPreferences(2048x2048, 0)
2009-11-14 18:00:32.576 VDP: LoadBestPreferences(2048x2048, 60)
2009-11-14 18:00:32.576 VDP: LoadBestPreferences(528x480, 60)
2009-11-14 18:00:32.579 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2009-11-14 18:00:32.579 VDP: LoadBestPreferences(2048x2048, 0)
2009-11-14 18:00:32.579 VDP: LoadBestPreferences(2048x2048, 60)
2009-11-14 18:00:32.579 VDP: LoadBestPreferences(528x480, 60)
2009-11-14 18:00:32.582 Using 1 CPUs for decoding
2009-11-14 18:00:32.582 AFD: InitVideoCodec() 0x19ebcf0 id(MPEG2VIDEO) type (Video).
2009-11-14 18:00:32.582 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2009-11-14 18:00:32.583 AFD: Using vdpau for video decoding
2009-11-14 18:00:32.583 AFD: Looking for decoder for MPEG2VIDEO
2009-11-14 18:00:32.583 AFD: Opened codec 0x19ebcf0, id(MPEG2VIDEO) type(Video)
2009-11-14 18:00:32.583 AFD: Stream #1, has id 0x941 codec id AC3, type Audio, bitrate 128000 at 0x19ec120
2009-11-14 18:00:32.583 AFD: codec AC3 has 2 channels
2009-11-14 18:00:32.583 AFD: Looking for decoder for AC3
2009-11-14 18:00:32.584 AFD: Opened codec 0x1f18360, id(AC3) type(Audio)
2009-11-14 18:00:32.585 RingBuf(myth://192.168.1.210:6543/1476_20091114115900.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-11-14 18:00:32.587 Opening audio device 'hdmi'. ch 2(2) sr 48000
2009-11-14 18:00:32.587 Opening ALSA audio device 'hdmi'.
2009-11-14 18:00:32.870 mixer unable to find control Master 1
2009-11-14 18:00:32.876 Dec: Trying to select track (w/lang)
2009-11-14 18:00:32.876 Dec: Selecting first track
2009-11-14 18:00:32.876 Dec: Selected track #1 in the Unknown language(0)
2009-11-14 18:00:32.877 Dec: Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-11-14 18:00:32.944 Position map filled from DB to: 188112
2009-11-14 18:00:32.945 Dec: SyncPositionMap prerecorded, from DB: 6492 entries
2009-11-14 18:00:32.945 Dec: SyncPositionMap, new totframes: 188112, new length: 6276, posMap size: 6492
2009-11-14 18:00:32.946 AFD: Position map found
2009-11-14 18:00:32.946 AFD: Successfully opened decoder for file: "myth://192.168.1.210:6543/1476_20091114115900.mpg". novideo(0)
2009-11-14 18:00:32.954 VideoOutput: Allowed renderers: vdpau
2009-11-14 18:00:32.954 VideoOutput: Allowed renderers (filt: vdpau): vdpau
2009-11-14 18:00:32.964 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2009-11-14 18:00:32.964 VDP: LoadBestPreferences(2048x2048, 0)
2009-11-14 18:00:32.964 VDP: LoadBestPreferences(2048x2048, 60)
2009-11-14 18:00:32.965 VDP: LoadBestPreferences(528x480, 60)
2009-11-14 18:00:32.965 VideoOutput: Preferred renderer: vdpau
2009-11-14 18:00:32.965 VideoOutput: Trying video renderer: 'vdpau'
2009-11-14 18:00:32.980 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(1) rend(vdpau) osd(vdpau) osdfade(disabled) deint(vdpaubobdeint,vdpauonefield) filt(vdpauskipchroma,colorspace=0)
2009-11-14 18:00:32.981 VDP: LoadBestPreferences(2048x2048, 0)
2009-11-14 18:00:32.981 VDP: LoadBestPreferences(2048x2048, 60)
2009-11-14 18:00:33.026 VideoOutWindow::SetPIPState. pip_state: 0]
2009-11-14 18:00:33.027 Display Rect  left: 0, top: 0, width: 1920, height: 1080, aspect: 1.33333
2009-11-14 18:00:33.027 Video Rect    left: 0, top: 0, width: 528, height: 480, aspect: 1.33333
2009-11-14 18:00:33.027 VDP: LoadBestPreferences(528x480, 60)
2009-11-14 18:00:33.027 Display Rect  left: 0, top: 0, width: 1920, height: 1080, aspect: 1.33333
2009-11-14 18:00:33.027 Video Rect    left: 0, top: 0, width: 528, height: 480, aspect: 1.33333
2009-11-14 18:00:33.027 VDP: SetVideoRenderer(vdpau)
2009-11-14 18:00:33.027 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-11-14 18:00:33.030 VidOutVDPAU: VDPAU Colorkey: 0x20202 (depth 24)
2009-11-14 18:00:33.034 VideoOutput: Pixel dimensions: Screen 1920x1080, window 1920x1080
2009-11-14 18:00:33.034 VideoOutput: Actual display dimensions: 488x274 mm  Aspect: 1.78102
2009-11-14 18:00:33.035 VideoOutput: Estimated window dimensions: 488x274 mm  Aspect: 1.78102
2009-11-14 18:00:33.035 VDPAU: Enabling SkipChromaDeinterlace.
2009-11-14 18:00:33.244 WriteAudio: buffer underrun
2009-11-14 18:00:33.746 WriteAudio: buffer underrun
2009-11-14 18:00:33.762 VDPAU: Version 0
2009-11-14 18:00:33.762 VDPAU: Information NVIDIA VDPAU Driver Shared Library  190.42  Tue Oct 20 21:20:26 PDT 2009
2009-11-14 18:00:33.851 VDPAU Error: Error at util-vdpau.cpp:871 (#23, The system does not have enough resources to complete the requested operation at this time.)
2009-11-14 18:00:33.851 VDPAU Error: Failed to create output surface.
2009-11-14 18:00:33.851 VidOutVDPAU Error: Failed to initialise VDPAU
2009-11-14 18:00:33.851 VidOutVDPAU: DiscardFrames(1)
2009-11-14 18:00:33.851 VideoBuffers::DiscardFrames(1): 
2009-11-14 18:00:33.852 VideoBuffers::DiscardFrames():  -- done()
2009-11-14 18:00:33.852 VideoBuffers::DiscardFrames(1):  -- done
2009-11-14 18:00:33.852 VidOutVDPAU: DiscardFrames() 3:  -- done()
2009-11-14 18:00:33.877 VidOutVDPAU: DiscardFrames(1)
2009-11-14 18:00:33.877 VideoBuffers::DiscardFrames(1): 
2009-11-14 18:00:33.877 VideoBuffers::DiscardFrames():  -- done()
2009-11-14 18:00:33.877 VideoBuffers::DiscardFrames(1):  -- done
2009-11-14 18:00:33.877 VidOutVDPAU: DiscardFrames() 3:  -- done()
2009-11-14 18:00:33.877 VideoOutput, Error: Not compiled with any useable video output method.
2009-11-14 18:00:33.878 NVP(0), Error: Couldn't create VideoOutput instance. Exiting..
2009-11-14 18:00:33.886 Unable to initialize video.
2009-11-14 18:00:52.994 playCtx, Error: StartDecoderThread() Failed to startdecoder
2009-11-14 18:00:52.994 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end error
2009-11-14 18:00:53.079 TV: HandleStateChange(0) -- end
2009-11-14 18:00:53.079 TV: StartTV -- process events end
2009-11-14 18:00:53.079 TV: StartTV -- process events 2 begin
2009-11-14 18:00:53.080 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-14 18:00:53.081 ScreenSaverX11Private: ResetTimer -- begin
2009-11-14 18:00:53.081 ScreenSaverX11Private: StopTimer
2009-11-14 18:00:53.082 ScreenSaverX11Private: StartTimer
2009-11-14 18:00:53.082 ScreenSaverX11Private: ResetTimer -- end
2009-11-14 18:00:53.083 TV: StartTV -- process events 2 end
2009-11-14 18:00:53.113 TV::~TV() -- begin
2009-11-14 18:00:53.164 TV::~TV() -- lock
^C
]0;rwlove@lefteye: ~rwlove@lefteye:~$ exit
exit

Script done on Sat 14 Nov 2009 06:01:05 PM PST

---

### Post by terp4life2001 on 2009-11-14
I think changing that iGPU buffer size actually helped/worked. I think that mythfrontend was only killing the CPU when I had the verbose mode on with the increased iGPU buffer setting.

I'm running it now without verbose mode and the menu transitions do look smoother, but it seems to slow the system down so navigating menu items is a bit jerky. So, I guess it looks nicer but is a bit awkward; it wasn't perfect with Qt either. 

I can playback recordings as well as videos through mythvideo using mplayer as an external player. In both cases it takes a bit longer for the video or recording to start than it did in Qt mode.

With OpenGL now it's taking about 70% of my CPU and memory when I'm using the remote control to navigate quickly through the listed recordings. I guess the Atom CPU (1.6Ghz) just can't keep up with the OpenGL rendering and verbose output.

---

### Post by terp4life2001 on 2009-11-14
These two posts seem to indicate that I need to install more memory-

[http://lifehacker.com/5391308/build-a-silent-standalone-xbmc-media-center-on-the-cheap]("http://lifehacker.com/5391308/build-a-silent-standalone-xbmc-media-center-on-the-cheap")

[http://www.xbmc.org/forum/showthread.php?t=53888]("http://www.xbmc.org/forum/showthread.php?t=53888")

---

### Post by jyavenard on 2009-11-14
> **terp4life2001 said:**
> 
2009-11-14 18:00:33.762 VDPAU: Information NVIDIA VDPAU Driver Shared Library  190.42  Tue Oct 20 21:20:26 PDT 2009
2009-11-14 18:00:33.851 VDPAU Error: Error at util-vdpau.cpp:871 (#23, The system does not have enough resources to complete the requested operation at this time.)
2009-11-14 18:00:33.851 VDPAU Error: Failed to create output surface.



There you have it ...

Not enough RAM allocated to the GPU ...

Bump it to 512MB...

---

