---
title: "VDPAU Choppy video and stuttering audio after upgrade to 10.04"
date: 2010-07-04
forum: Mythbuntu
---

### Post by golbez_88rule on 2010-07-04
I recently upgraded my frontend (Acer Aspire Revo 1600) from mythbuntu 9.10 to 10.04 via synaptic. A week ago I upgraded my backend machine from 9.10 to 10.04 and after sorting through a few issues things are working fine on that machine. Before the upgrade on the frontend, I was able to play HD recordings from the backend's HDPVR smoothly with no stuttering of audio using the **VDPAU slim** playback profile.  I selected the same profile after the upgrade, and now I've notice some slight choppiness of the video and stuttering on the audio.  The binary nvidia driver on the frontend is enabled and it is version **195.36.24**. I am able to play the recordings smoothly on my backend machine (it has an ATI Radeon 5770 and AMD Quad core processor), so I do not believe it is an issue with the video files themselves.  I also tried setting the audio device to NULL thinking it was an audio buffering issue, but the problems still persist. I also tried the other VDPAU playback profiles and they were even worse. Since playback was working fine in 9.10 (myth 0.22), are there any other parts in the upgrade process that could have caused the problems other than possibly the new nvidia binary driver?  

Possible Diagnostic info:

mythfrontend.log:
```

2010-07-05 11:52:05.091 UPnPautoconf() - Found one UPnP backend
2010-07-05 11:52:05.205 Testing network connectivity to '192.168.1.2'
2010-07-05 11:52:05.216 Closing DB connection named 'DBManager0'
2010-07-05 11:52:05.218 Connected to database 'mythconverg' at host: 192.168.1.2
2010-07-05 11:52:05.220 Closing DB connection named 'DBManager0'
2010-07-05 11:52:05.268 ScreenSaverX11Private: XScreenSaver support enabled
2010-07-05 11:52:05.268 ScreenSaverX11Private: Gnome screen saver support enabled
2010-07-05 11:52:05.271 DPMS is disabled.
2010-07-05 11:52:05.275 Primary screen: 0.
2010-07-05 11:52:05.277 Connected to database 'mythconverg' at host: 192.168.1.2
2010-07-05 11:52:05.280 Using screen 0, 1920x1080 at 0,0
2010-07-05 11:52:05.312 Desktop video mode: 1920x1080 60.0024 Hz
2010-07-05 11:52:05.374 MythUI Image Cache size set to 20971520 bytes
2010-07-05 11:52:05.429 AudioPulseUtil: Suspend Success
2010-07-05 11:52:05.430 Enabled verbose msgs:  important general
2010-07-05 11:52:05.444 Primary screen: 0.
2010-07-05 11:52:05.445 Using screen 0, 1920x1080 at 0,0
2010-07-05 11:52:05.447 Using theme base resolution of 1280x720
2010-07-05 11:52:05.468 LIRC: Successfully initialized '/dev/lircd' using '/home/eric/.mythtv/lircrc' config
2010-07-05 11:52:05.469 JoystickMenuThread Error: Joystick disabled - Failed to read /home/eric/.mythtv/joystickmenurc
2010-07-05 11:52:05.552 Using Frameless Window
2010-07-05 11:52:05.553 Using Full Screen Window
2010-07-05 11:52:06.395 Using the Qt painter
2010-07-05 11:52:06.697 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/metallurgy/base.xml'
2010-07-05 11:52:06.907 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-07-05 11:52:07.021 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-07-05 11:52:07.044 Current MythTV Schema Version (DBSchemaVer): 1254
2010-07-05 11:52:07.150 New DB connection, total: 2
2010-07-05 11:52:07.154 Connected to database 'mythconverg' at host: 192.168.1.2
2010-07-05 11:52:08.260 Registering Internal as a media playback plugin.
2010-07-05 11:52:08.320 Cannot load language en_us for module mytharchive
2010-07-05 11:52:08.326 Cannot load language en_us for module mythbrowser
2010-07-05 11:52:08.334 Registering WebBrowser as a media playback plugin.
2010-07-05 11:52:08.334 Cannot load language en_us for module mythbrowser
2010-07-05 11:52:08.401 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-07-05 11:52:08.402 Cannot load language en_us for module mythgallery
2010-07-05 11:52:08.409 Cannot load language en_us for module mythmovies
2010-07-05 11:52:08.456 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-07-05 11:52:08.557 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-07-05 11:52:08.572 Cannot load language en_us for module mythmusic
2010-07-05 11:52:08.585 Cannot load language en_us for module mythnews
2010-07-05 11:52:08.604 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-07-05 11:52:08.671 Cannot load language en_us for module mythvideo
2010-07-05 11:52:08.688 Cannot load language en_us for module mythweather
2010-07-05 11:52:08.693 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/metallurgy/menu-ui.xml
2010-07-05 11:52:09.217 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-07-05 11:52:09.221 Found mainmenu.xml for theme 'metallurgy'
2010-07-05 11:52:09.284 MythContext: Connecting to backend server: 192.168.1.2:6543 (try 1 of 1)
2010-07-05 11:52:09.285 Using protocol version 56
2010-07-05 11:52:11.645 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-07-05 11:52:14.002 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/metallurgy/recordings-ui.xml
2010-07-05 11:52:21.015 TV: Attempting to change from None to WatchingPreRecorded
2010-07-05 11:52:21.834 AFD: Opened codec 0x8ec78c0, id(H264) type(Video)
2010-07-05 11:52:21.835 AFD: codec AC3 has 6 channels
2010-07-05 11:52:21.840 AFD: Opened codec 0x8ecc810, id(AC3) type(Audio)
2010-07-05 11:52:21.885 Opening audio device '/dev/dsp1'. ch 2(6) sr 48000 (reenc 1)
2010-07-05 11:52:21.885 Opening OSS audio device '/dev/dsp1'.
2010-07-05 11:52:21.929 Opening audio device '/dev/dsp1'. ch 2(6) sr 48000 (reenc 1)
2010-07-05 11:52:21.929 Opening OSS audio device '/dev/dsp1'.
2010-07-05 11:52:21.974 Opening audio device '/dev/dsp1'. ch 2(6) sr 48000 (reenc 1)
2010-07-05 11:52:21.974 Opening OSS audio device '/dev/dsp1'.
2010-07-05 11:52:22.105 VDPAU: Created 2 output surfaces.
2010-07-05 11:52:22.106 VDPAU: Version 1
2010-07-05 11:52:22.106 VDPAU: Information NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 10:39:56 PDT 2010
2010-07-05 11:52:22.106 VDPAU: Created VDPAU render device 1920x1080
2010-07-05 11:52:22.689 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-07-05 11:52:22.694 OSD Theme Dimensions W: 1280 H: 720
2010-07-05 11:52:23.050 TV: Changing from None to WatchingPreRecorded
2010-07-05 11:52:23.053 The realtime priority setting is not enabled.
2010-07-05 11:52:23.059 OpenGLVideoSync()
2010-07-05 11:52:23.369 Video timing method: SGI OpenGL
2010-07-05 11:52:23.402 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-07-05 11:52:23.983 NVP(0): prebuffering pause
2010-07-05 11:52:24.083 NVP(0): prebuffering pause
2010-07-05 11:52:24.167 NVP(0): prebuffering pause
2010-07-05 11:52:24.250 NVP(0): prebuffering pause
2010-07-05 11:52:24.323 NVP(0): prebuffering pause

... EDIT: prebuffering pause repeated many more times

2010-07-05 11:54:01.760 NVP(0): prebuffering pause
2010-07-05 11:54:01.837 NVP(0): prebuffering pause
2010-07-05 11:54:01.896 NVP(0): prebuffering pause
2010-07-05 11:54:01.930 TV: Attempting to change from WatchingPreRecorded to None
2010-07-05 11:54:01.936 ~OpenGLVideoSync() -- closing opengl vsync
2010-07-05 11:54:01.966 TV: Changing from WatchingPreRecorded to None
2010-07-05 11:54:11.332 AudioPulseUtil: Resume Success
2010-07-05 11:54:11.347 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

```

Settings for HDPVR on backend PC:
```

eric@mythtvback:/sys/module/hdpvr/parameters$ v4l2-ctl --device=/dev/video0 -l
                     brightness (int)  : min=0 max=255 step=1 default=134 value=134 flags=slider
                       contrast (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                     saturation (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                            hue (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                      sharpness (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                 audio_encoding (menu) : min=3 max=4 default=3 value=3 flags=update
                 video_encoding (menu) : min=2 max=2 default=2 value=2
             video_bitrate_mode (menu) : min=0 max=1 default=1 value=1 flags=update
                  video_bitrate (int)  : min=1000000 max=13500000 step=100000 default=6500000 value=6500000
             video_peak_bitrate (int)  : min=1100000 max=20200000 step=100000 default=9000000 value=9000000 flags=inactive

```

---

### Post by itlarson on 2010-07-05
I'm having the same problems.  Admittedly my motherboard 8300 graphics are difficult to get working at best.  In particular this xorg section:
Section "Extensions"
       Option "Composite" "Disable"
   EndSection
causes a complete meltdown, even though it was one of the things I needed to do in .23 to get vdpau working.  I am wondering if downgrading to the 32 bit version of Mythvbuntu has something to do with it.  I was hoping the 32 bit flashplayer would help hulu playback.

---

### Post by scottcrawford on 2010-07-06
I recently had issues too after some updates. I enabled one of the nvidia repositories and updated my driver to version 256. That fixed it for me.

---

### Post by itlarson on 2010-07-06
Wow, they're up to version 256 already?  I'm just using the 195 version that came with lucid.  I might try that even though I've had issues (probably self inflicted) with nvidia ppa's before.  Vdpau definitly gave me the best picture I have ever gotten.

---

### Post by golbez_88rule on 2010-07-06
> **scottcrawford said:**
> I recently had issues too after some updates. I enabled one of the nvidia repositories and updated my driver to version 256. That fixed it for me.

Scottcrawford, could you share which nvidia repo you enabled?  Also did you uninstall the previous version of the driver before installing the 256 version?

---

### Post by scottcrawford on 2010-07-07
I used the ppa:ubuntu-x-swat/x-updates repository. I've also got nvidia-vdpau and nvidia-vdpau-cutting-edge-multimedia enabled. I think I removed the binary driver first, but I can't remember for sure. I actually did a couple of full re-installs of Ubuntu in my efforts to fix the stuttering problem, trying different repos each time.

---

### Post by itlarson on 2010-07-10
I have gotten VDPAU working with the 256 driver.  Here's what I did.  

First I added the driver repository:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo aptitude update

I then opened synaptic and clicked on "nvidia-current"  and chose "upgrade".  I did the same for "nvidia-settings", and then clicked "apply".  After the install was compleat I did "sudo gdm restart".

Initialy my screen was scrambled, but still readable, so I renamed xorg, ran nvidia-setup, and rebooted.   If I did it again I would rename xorg, and run the nvidia-setup program before restarting x. 

I now had working  graphics, but vdpau still was choppy.  I opened xorg and added the all important 

   Section "Extensions"
       Option "Composite" "Disable"
   EndSection

to the end of the file.  This had been vital with the 185 driver, but caused the graphics to lock up under 195.  I also added 

Option         "TripleBuffer" "True"

to the devices section to allocate more memory to 2D graphics.  I did "sudo gdm restart" and tryed to play a recording.  Sucess!

If anyone else is having trouble, be sure to consult the "troubleshooting" section of [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by golbez_88rule on 2010-07-11
I've solved the issue!  Upgrading the Nvidia driver to the 256 version using the instructions provided by itlarson went through without a hitch and now all of my HD content is playing back smoothly like it was in 0.22. I recommend anyone running a frontend with the Gforce 9400M who upgrades to mythbuntu 10.04 to get the latest Nvidia drivers if they have the same issues as I did.  Thanks again!

---

