---
title: "Mythtv Frontend on Aspire Revo R1600 fails"
date: 2010-04-19
forum: Mythbuntu
---

### Post by pettitda on 2010-04-19
I'm having some issues getting Mythbuntu running on an Aspire Revo R1600.  I've done several searches on the web and haven't came up with any ideas that work.  I've uninstalled and reinstalled several times, upgraded the RAM to 2 GB, and tried multiple settings.  VDPAU just doesn't want to work, I can't get sound out the HDMI port, or some other problem pops up.  The current state of affairs is that when I tried to play a pre-recorded video, a screen comes up saying "Playback starting..." and it stalls there.  Here's a logfile from where I'm at now:  

2010-04-19 16:03:53.671 mythfrontend version: branches/release-0-22-fixes [22594] [www.mythtv.org]("http://www.mythtv.org")
2010-04-19 16:03:53.672 Using runtime prefix = /usr
2010-04-19 16:03:53.672 Using configuration directory = /home/david/.mythtv
2010-04-19 16:03:54.665 Empty LocalHostName.
2010-04-19 16:03:54.665 Using localhost value of mythfront
2010-04-19 16:03:54.666 Testing network connectivity to '192.168.1.3'
2010-04-19 16:03:54.690 New DB connection, total: 1
2010-04-19 16:04:03.130 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-19 16:04:03.132 Closing DB connection named 'DBManager0'
2010-04-19 16:04:03.177 ScreenSaverX11Private: Gnome screen saver support enabled
2010-04-19 16:04:03.179 DPMS is active.
2010-04-19 16:04:03.207 Primary screen: 0.
2010-04-19 16:04:08.284 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-19 16:04:08.287 Using screen 0, 1280x720 at 0,0
2010-04-19 16:04:08.360 MythUI Image Cache size set to 20971520 bytes
2010-04-19 16:04:08.361 Enabled verbose msgs:  important general
2010-04-19 16:04:08.392 Primary screen: 0.
2010-04-19 16:04:08.393 Using screen 0, 1280x720 at 0,0
2010-04-19 16:04:08.449 Using theme base resolution of 1280x720
2010-04-19 16:04:08.474 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No such file or directory (2)
2010-04-19 16:04:08.474 JoystickMenuThread Error: Joystick disabled - Failed to read /home/david/.mythtv/joystickmenurc
2010-04-19 16:04:08.572 Using the Qt painter
2010-04-19 16:04:08.816 Loaded base theme from /usr/share/mythtv/themes/Terra/base.xml
2010-04-19 16:04:08.893 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-04-19 16:04:08.991 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-04-19 16:04:09.049 New DB connection, total: 2
2010-04-19 16:04:09.050 New DB connection, total: 3
2010-04-19 16:04:09.055 Current MythTV Schema Version (DBSchemaVer): 1244
2010-04-19 16:04:11.751 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
2010-04-19 16:04:11.752 Desktop video mode: 0x0 0 Hz
2010-04-19 16:04:12.273 Registering Internal as a media playback plugin.
2010-04-19 16:04:12.477 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-04-19 16:04:12.965 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-04-19 16:04:13.079 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-04-19 16:04:13.171 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-04-19 16:04:13.336 Loading window theme from /usr/share/mythtv/themes/Terra/menu-ui.xml
2010-04-19 16:04:13.578 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-04-19 16:04:13.583 Found mainmenu.xml for theme 'Terra'
2010-04-19 16:04:14.122 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-19 16:04:19.200 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-19 16:04:19.240 MythContext: Connecting to backend server: 192.168.1.3:6543 (try 1 of 1)
2010-04-19 16:04:19.242 Using protocol version 50
2010-04-19 16:04:19.329 Warning! Time difference between the master backend and this system is 55 seconds.
2010-04-19 16:04:22.363 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-04-19 16:04:23.878 Loading window theme from /usr/share/mythtv/themes/Terra/recordings-ui.xml
2010-04-19 16:04:24.523 MythContext: Connecting to backend server: 192.168.1.3:6543 (try 1 of 1)
2010-04-19 16:04:24.524 Using protocol version 50
2010-04-19 16:04:29.381 TV: Attempting to change from None to Watching WatchingPreRecorded
2010-04-19 16:04:29.517 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2010-04-19 16:04:30.389 AFD: Opened codec 0x8caadc0, id(MPEG2VIDEO) type(Video)
2010-04-19 16:04:30.389 AFD: codec MP2 has 2 channels
2010-04-19 16:04:30.389 AFD: Opened codec 0x8cab170, id(MP2) type(Audio)
2010-04-19 16:04:30.409 Opening audio device 'hdmi'. ch 2(2) sr 48000
2010-04-19 16:04:30.409 Opening ALSA audio device 'hdmi'.
2010-04-19 16:04:30.551 Mixer unable to find control Master 1
2010-04-19 16:04:30.551 mixer unable to find control Master 1
2010-04-19 16:04:30.560 Mixer unable to find control PCM
2010-04-19 16:04:30.560 Mixer unable to find control PCM
2010-04-19 16:04:30.561 Mixer unable to find control Master 1
2010-04-19 16:04:30.561 mixer unable to find control Master 1
2010-04-19 16:04:30.798 MythXGetRefreshRate(): X11 ModeLine query returned zeroes
Xlib:  extension "NV-GLX" missing on display ":0.0".
2010-04-19 16:04:30.835 VidOutVDPAU Error: Failed to initialise VDPAU
2010-04-19 16:04:30.843 VideoOutput, Error: Not compiled with any useable video output method.
2010-04-19 16:04:30.843 NVP(0), Error: Couldn't create VideoOutput instance. Exiting..
2010-04-19 16:04:30.850 Unable to initialize video.
2010-04-19 16:04:50.797 playCtx, Error: StartDecoderThread() Failed to startdecoder
2010-04-19 16:04:50.797 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end error
2010-04-19 16:04:50.828 ScreenSaverX11Private: DPMS Deactivated 1
Starting mythfrontend.real..

Any thoughts on what may be going on???

---

### Post by scub31 on 2010-04-22
got the 1600 as well and just installed mythbuntu 9.10.

hit EXACT same problem and fumbled around until I stumbled onto it.

go to system > hardware drivers and download the "nvidia accelerated graphics driver (version 185) [recommended]" and then reboot.

problem was solved for me.

now I have yet to sort no sound over hdmi.

but getting closer.

---

### Post by Lepy on 2010-04-22
scub31 is correct, proprietary nvidia drivers are required in order to use VDPAU.

I have no experience with audio over HDMI, but if you are hooking it directly into a tv (no receiver/amp), have you tried this: [http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI](http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI)

---

### Post by scub31 on 2010-04-22
heh, I sorted the audio problem.

this one is a myth front end configuration setting.

down in the audio setting screens replace:

alsa:default

with:

alsa:hdmi

instant fix.

this is going better than expected given I've never used a front end before.

(been playing with the .21 backend with HDHomeRun and using PS3 to play it -- works but a bit clunky -- so bit bullet and bought this revo and loaded up full frontend / backend with 9.10)

---

### Post by pettitda on 2010-04-22
Okay, when I download the proprietary drivers, I have even bigger problems.  As soon as I reboot, the HDMI display (LCD flat screen) becomes intermittent.  I can't see the screen long enough to try changing settings.  My flat screen is a 32" 720p Insignia model.

---

### Post by scub31 on 2010-04-22
if you hit control-F2 do you get a new Ubuntu desktop?

Otherwise use putty from your PC and ssh into the thing.

whats in the logs now?

---

### Post by JMcFly on 2010-04-22
Did you try using an RGB cable from the Revo to the LCD?

---

### Post by pettitda on 2010-04-23
The intermittent display begins as soon as the X server starts up.  The problem appears to be unrelated to Myth.  I'm guessing the autoprobe settings that the nvidia driver picked for the LCD TV are incorrect.  This weekend I will try logging in remotely and changing the display settings using the nvidia control panel.

---

### Post by LowSky on 2010-04-23
> **pettitda said:**
> The intermittent display begins as soon as the X server starts up.  The problem appears to be unrelated to Myth.  I'm guessing the autoprobe settings that the nvidia driver picked for the LCD TV are incorrect.  This weekend I will try logging in remotely and changing the display settings using the nvidia control panel.

you could boot into recovery mode in grub and repair xorg

---

### Post by pettitda on 2010-04-24
Okay, I was able to fix the intermittent display by adding the line 

Option "UseEDID" "False" 

to xorg.conf.  However, now I can't get a resolution greater than 640x480.

---

### Post by pettitda on 2010-04-24
Here's the EDID information:


    # EDID version 1 revision 3
Section "Monitor"
    # Block type: 2:0 3:fc
    Identifier "LCD-TV****"
    VendorName "SHI"
    ModelName "LCD-TV****"
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
    HorizSync 30-91
    VertRefresh 55-75
    # Max dot clock (video bandwidth) 220 MHz
    # DPMS capabilities: Active off:no  Suspend:no  Standby:no

    Mode     "1280x720"    # vfreq 60.000Hz, hfreq 45.000kHz
        DotClock    74.250000
        HTimings    1280 1390 1430 1650
        VTimings    720 725 730 750
        Flags    "+HSync" "+VSync"
    EndMode
    Mode     "1360x768"    # vfreq 59.960Hz, hfreq 47.368kHz
        DotClock    72.000000
        HTimings    1360 1408 1440 1520
        VTimings    768 770 775 790
        Flags    "-HSync" "+VSync"
    EndMode
    # Block type: 2:0 3:fc
    # Block type: 2:0 3:fd
EndSection


I tried creating modelines from this information and adding them to the xorg.conf file, but for some reason they are invalidated.

---

### Post by pettitda on 2010-04-24
Okay, now the display seems to be working.  I added the option "ExactModeTimingsDVI" "True" to xorg.conf.  I also used CVT to create a modeline.  

However, the audio still doesn't work.  I tried the ALSA:hdmi setting mentioned earlier and no dice.  Here's the myth log file:

2010-04-24 17:42:11.927 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-24 17:42:11.930 Using screen 0, 1368x768 at 0,0
2010-04-24 17:42:11.962 MythUI Image Cache size set to 20971520 bytes
2010-04-24 17:42:11.963 Enabled verbose msgs:  important general
2010-04-24 17:42:11.979 Primary screen: 0.
2010-04-24 17:42:11.981 Using screen 0, 1368x768 at 0,0
2010-04-24 17:42:11.983 Using theme base resolution of 1280x720
2010-04-24 17:42:12.005 LIRC, Error: Failed to connect to Unix socket '/var/run/lirc/lircd'
            eno: No such file or directory (2)
2010-04-24 17:42:12.005 JoystickMenuThread Error: Joystick disabled - Failed to read /home/david/.mythtv/joystickmenurc
2010-04-24 17:42:12.092 Using the Qt painter
2010-04-24 17:42:12.278 Loaded base theme from /usr/share/mythtv/themes/Terra/base.xml
2010-04-24 17:42:12.345 Loaded base theme from /usr/share/mythtv/themes/default-wide/base.xml
2010-04-24 17:42:12.414 Loaded base theme from /usr/share/mythtv/themes/default/base.xml
2010-04-24 17:42:12.447 New DB connection, total: 2
2010-04-24 17:42:12.455 Current MythTV Schema Version (DBSchemaVer): 1244
2010-04-24 17:42:12.503 New DB connection, total: 3
2010-04-24 17:42:13.497 Desktop video mode: 1368x768 59.8552 Hz
2010-04-24 17:42:13.985 Registering Internal as a media playback plugin.
2010-04-24 17:42:13.987 No plugins directory /usr/lib/mythtv/plugins
2010-04-24 17:42:14.007 Loading window theme from /usr/share/mythtv/themes/Terra/menu-ui.xml
2010-04-24 17:42:14.207 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-04-24 17:42:14.213 Found mainmenu.xml for theme 'Terra'
2010-04-24 17:42:17.522 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-24 17:42:22.595 Connected to database 'mythconverg' at host: 192.168.1.3
2010-04-24 17:42:22.723 MythContext: Connecting to backend server: 192.168.1.3:6543 (try 1 of 1)
2010-04-24 17:42:22.724 Using protocol version 50
2010-04-24 17:42:22.734 Warning! Time difference between the master backend and this system is 64 seconds.
2010-04-24 17:42:26.420 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-04-24 17:42:27.704 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//main_settings.xml
2010-04-24 17:42:41.903 Received a remote 'Clear Cache' request
2010-04-24 17:42:46.605 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//library.xml
2010-04-24 17:42:47.499 Loading window theme from /usr/share/mythtv/themes/Terra/recordings-ui.xml
2010-04-24 17:42:49.730 TV: Attempting to change from None to Watching WatchingPreRecorded
2010-04-24 17:42:49.819 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2010-04-24 17:42:50.508 AFD: Opened codec 0x92b4720, id(MPEG2VIDEO) type(Video)
2010-04-24 17:42:50.508 AFD: codec MP2 has 2 channels
2010-04-24 17:42:50.508 AFD: Opened codec 0x91e2dd0, id(MP2) type(Audio)
2010-04-24 17:42:50.514 Opening audio device 'hdmi'. ch 2(2) sr 48000
2010-04-24 17:42:50.514 Opening ALSA audio device 'hdmi'.
2010-04-24 17:42:50.598 Mixer unable to find control Master 1
2010-04-24 17:42:50.598 mixer unable to find control Master 1
2010-04-24 17:42:50.609 Mixer unable to find control Master 1
2010-04-24 17:42:50.609 mixer unable to find control Master 1
2010-04-24 17:42:51.041 NVP(0): Forcing decode extra audio option on (Video method requires it).
2010-04-24 17:42:51.042 FilterManager: Failed to load filter 'colorspace', no such filter exists
2010-04-24 17:42:51.046 OSD Theme Dimensions W: 1280 H: 720
2010-04-24 17:42:51.855 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2010-04-24 17:42:51.859 Realtime priority would require SUID as root.
2010-04-24 17:42:51.863 TV: Changing from None to Watching WatchingPreRecorded
2010-04-24 17:42:51.876 Video timing method: USleep with busy wait
2010-04-24 17:42:51.896 ScreenSaverX11Private: DPMS Deactivated 1
2010-04-24 17:42:56.457 TV: Attempting to change from Watching WatchingPreRecorded to None
2010-04-24 17:42:56.506 TV: Changing from Watching WatchingPreRecorded to None
2010-04-24 17:42:56.507 ScreenSaverX11Private: DPMS Reactivated 1
2010-04-24 17:43:01.130 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

---

### Post by Lepy on 2010-04-26
I only use nvidia on linux, but some of their cards/drives have given me the most problems while using ubuntu. I also had edid problems with one monitor/graphics combo. I think, I solved my problem hooking it up to another computer and acquiring the edid info through the nvidia control panel.

Sounds like your xorg options are good. It looks like you can acquire your edid too, so try using "nvidia-settings" to do so. Adding these options to the screen settings heading fixed the low res boot problem:

```
    Option         "UseEdidDpi" "FALSE"
    Option         "CustomEDID" "DFP-0:/home/psy/FPD2185W.bin" #path to .bin acquired from nvidia x server settings
    Option         "ExactModeTimingsDVI" "TRUE"
```

If the above does not work, continue by editing your modelines with gtf:

[http://ubuntuforums.org/showpost.php?p=8833886&postcount=5](http://ubuntuforums.org/showpost.php?p=8833886&postcount=5)

Apparently, any driver version above 185 breaks hdmi audio. Other good stuff:
[http://forum.xbmc.org/showthread.php?t=67819](http://forum.xbmc.org/showthread.php?t=67819)

---

