---
title: "Update .21 Ruins Playback (even after suggested fixes)"
date: 2008-03-22
forum: Mythbuntu
---

### Post by Cackette on 2008-03-22
Everything was working perfectly until I updated to .21 via the Update Manager.  Once it updated, video playback has been broken. For HD recordings, when tried to playback, the video and audio would start, then the video would freeze 1-2 seconds in.  For SD recording playbacks, a rainbow pattern/static would show and audio played.  I browsed the forums and tried removing mythdvd and updating mythvideo, but the problems still occur.  I've tried every playback option, and CPU-- is the only one that makes SD work.  None of the settings make HD work.

> Starting mythfrontend.real..
2008-03-22 12:47:46.605 New DB connection, total: 2
2008-03-22 12:47:46.606 Connected to database 'mythconverg' at host: localhost
2008-03-22 12:47:46.608 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-03-22 12:47:46.608 Enabled verbose msgs:  important general
2008-03-22 12:47:46.691 The theme (Isthmus) is missing a themeinfo.xml file
2008-03-22 12:47:46.785 The theme (Isthmus) is missing a themeinfo.xml file
2008-03-22 12:47:46.957 Could not open settings file /home/htpc/.mythtv/mysql.txt for writing
2008-03-22 12:47:46.964 Total desktop dim: 1920x1080, with 1 screen[s].
2008-03-22 12:47:46.964 Using screen 0, 1920x1080 at 0,0
2008-03-22 12:47:46.966 Switching to wide mode (MythCenter-wide)
2008-03-22 12:47:46.979 Using the Qt painter
2008-03-22 12:47:46.981 lirc init success using configuration file: /home/htpc/.mythtv/lircrc
2008-03-22 12:47:46.981 JoystickMenuClient Error: Joystick disabled - Failed to read /home/htpc/.mythtv/joystickmenurc
2008-03-22 12:47:48.601 Loading from: /usr/share/mythtv/themes/MythCenter-wide/base.xml
2008-03-22 12:47:48.718 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-22 12:47:48.760 Registering Internal as a media playback plugin.
2008-03-22 12:47:48.805 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-03-22 12:47:48.849 Failed to run 'cdrecord --scanbus'
2008-03-22 12:47:48.853 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-03-22 12:47:48.858 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-03-22 12:47:48.887 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-03-22 12:47:48.931 Unable to initialize plugin 'mythstream'.
SIP listening on IP Address 192.168.1.104:5060 NAT address 192.168.1.104
SIP: Cannot register; proxy, username or password not set
2008-03-22 12:47:59.212 XMLParse::LoadTheme using /usr/share/mythtv/themes/MythCenter-wide/ui.xml
2008-03-22 12:47:59.522 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-22 12:47:59.523 Using protocol version 40
2008-03-22 12:48:01.135 TV: Attempting to change from None to WatchingPreRecorded
2008-03-22 12:48:01.149 DPMS Deactivated 
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
2008-03-22 12:48:01.349 AFD: Opened codec 0x870cda0, id(MPEG2VIDEO) type(Video)
2008-03-22 12:48:01.349 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-03-22 12:48:01.350 AFD: Opened codec 0x870d3d0, id(AC3) type(Audio)
2008-03-22 12:48:01.355 Opening audio device 'default'. ch 2(2) sr 48000
2008-03-22 12:48:01.355 Opening ALSA audio device 'default'.
2008-03-22 12:48:01.474 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'opengl,xv-blit,xshm,xlib,' available, using 'opengl' instead.
2008-03-22 12:48:01.815 OSD Theme Dimensions W: 640 H: 480
2008-03-22 12:48:02.162 TV: Changing from None to WatchingPreRecorded
2008-03-22 12:48:02.191 Realtime priority would require SUID as root.
2008-03-22 12:48:02.220 audio stream changed
2008-03-22 12:48:02.222 audio stream changed
2008-03-22 12:48:02.223 audio stream changed
2008-03-22 12:48:02.239 audio stream changed
2008-03-22 12:48:02.255 audio stream changed
2008-03-22 12:48:02.272 audio stream changed
2008-03-22 12:48:02.288 audio stream changed
2008-03-22 12:48:02.298 Video timing method: USleep with busy wait
2008-03-22 12:48:02.305 audio stream changed
2008-03-22 12:48:02.305 audio stream changed
2008-03-22 12:48:02.321 audio stream changed
2008-03-22 12:48:02.336 audio stream changed

---

### Post by grourk on 2008-03-23
I was having the exact same problem yesterday after updating.  Setting the playback profile to CPU++ fixed it for me.  (In Setup -> TV Settings ->Playback page 3).

I haven't had too much time to investigate why this fixed it or what exactly those playback profiles are.  It seems they are new with v0.21.

Hope this helps.

---

### Post by Cackette on 2008-03-23
> **grourk said:**
> I was having the exact same problem yesterday after updating.  Setting the playback profile to CPU++ fixed it for me.  (In Setup -> TV Settings ->Playback page 3).

I haven't had too much time to investigate why this fixed it or what exactly those playback profiles are.  It seems they are new with v0.21.

Hope this helps.
with CPU++ I get only audio on both HD and SD. The only profile I've had luck with is CPU-- where I can get SD to work, but not HD.

---

### Post by p$y on 2008-03-23
try to disable the _bob deinterlace_ in the profile settings.

---

### Post by batman01 on 2008-04-07
I also have this problem.  It looks like the update has killed XVMC support as changing to CPU+ or ++ uses software rendering. Using CPU-- should use hardware XVMC rendering as worked previously. 

The log shows renderer "xvmc-blit not available". It seems to fall back to OpenGL which doesn't work at all on my via board. 

I ran xine from the OS menu and forced it to XVMC video output and could then play a video quite happily with minimal CPU, so the Openchrome drivers are still working, so it looks like MythTVs inteface to the openchrome DRi is broken in some way.

Bummer.

---

### Post by aseriesoftubes on 2008-04-14
I have the same problem with my system (Mythbuntu 8.04 with MythTV .21 and all recommended fixes). XvMC playback was pretty darn good on the same system with 7.10 and .20.2.

I've tried editing /etc/X11/XvMCConfig, but changing the entry to anything but libXvMC.so.1 results in a black screen.

I get adequate playback using the CPU+ profile. This will work for now, but I'm not impressed with the playback quality of HD content (slow pans and movements are jerky). CPU++ is too much for my system (P4 2.6GHz) and causes stuttering on HD playback.

I have not tried disabling Bob in the XvMC profile, but I will do that tonight and report back.

p$y: Do you think the Linear Blend deinterlacer would work, or are you suggesting disabling deinterlacing completely?

---

### Post by aseriesoftubes on 2008-04-15
Well, I've tried disabling Bob in the CPU-- (XvMC) profile, to no avail. The other deint option (One Field, I believe) shows the same problems. If I turn deinterlacing off, playback does not stutter, but the quality is not acceptable to me.

I ended up creating a new profile that uses libmpeg2 for everything, and it works reasonably well, which is strange, because my CPU is a Pentium 4. I've only been able to make it work with the "lower-powered" deinterlacing methods (ie, not Greedy or Yadif), of which Bob seems to work best. Unfortunately, this configuration does not work very well when watching live HDTV (but live SDTV is fine).

---

### Post by callagga on 2008-05-01
I'm new to mythtv and just installed mythbuntu and upgraded to the latest version.  I'm getting the following in the logs, and live tv is a little jerky (similar symptoms to what others describe)

```
2008-05-01 19:20:35.901 VideoOutputXv **Error: XvMC output requested, but is not supported by display.**
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2008-05-01 19:20:35.909 VideoOutputXv: **Desired video renderer 'xvmc-blit' not available.**
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-05-01 19:20:35.914 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-05-01 19:20:35.957 Video timing method: USleep with busy wait

```

What's the best way forward me me?  (i.e. I've used mythbuntu ISO)

BTW - My version info:

```
greg@mythtv:/var/log/mythtv$  mythbackend --version
Please include all output in bug reports.
MythTV Version   : 16838
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_arts using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_xvmc_vld using_glx_proc_addr_arb using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 using_live

```

Also the log from the same time for the BACKEND is:
```
2008-05-01 19:20:30.494 MainServer::HandleAnnounce Playback
2008-05-01 19:20:30.497 adding: mythtv as a client (events: 0)
2008-05-01 19:20:30.499 TVRec(1): Changing from None to WatchingLiveTV
2008-05-01 19:20:30.508 TVRec(1): HW Tuner: 1->1
2008-05-01 19:20:30.515 DVBChan(1:0) Warning: Unsupported constellation parameter.
2008-05-01 19:20:31.661 DVBSM(0), Warning: Can not measure Bit Error Rate
                        eno: Operation not supported (95)
2008-05-01 19:20:31.664 DVBSM(0), Warning: Can not count Uncorrected Blocks
                        eno: Operation not supported (95)
2008-05-01 19:20:31.676 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-01 19:20:33.574 Finished recording Unknown: channel 2001
2008-05-01 19:20:34.652 Finished recording Unknown: channel 2001
2008-05-01 19:20:34.690 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-01 19:20:41.197 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-01 19:20:43.331 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(211)
2008-05-01 19:20:45.703 Empty LocalHostName.
2008-05-01 19:20:45.707 TFW, Error: Write() -- IOBOUND end
2008-05-01 19:20:46.434 Using localhost value of mythtv
2008-05-01 19:20:47.864 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(9147)
2008-05-01 19:20:50.600 New DB connection, total: 1
2008-05-01 19:20:51.444 TFW, Error: Write() -- IOBOUND end
2008-05-01 19:20:51.955 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(2379)
2008-05-01 19:20:52.458 Connected to database 'mythconverg' at host: localhost
2008-05-01 19:20:54.262 TFW, Error: Write() -- IOBOUND end
2008-05-01 19:20:54.601 Closing DB connection named 'DBManager0'
2008-05-01 19:20:54.831 Connected to database 'mythconverg' at host: localhost
2008-05-01 19:20:55.592 New DB connection, total: 2
2008-05-01 19:20:56.000 Connected to database 'mythconverg' at host: localhost
2008-05-01 19:20:56.402 Current Schema Version: 1214
2008-05-01 19:20:56.851 Preview Error: Previewer file '/var/lib/mythtv/recordings/2001_20080501192030.mpg' is not valid.
2008-05-01 19:20:56.928 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2001_20080501192030.mpg'
2008-05-01 19:20:57.704 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/2001_20080501192030.mpg.png) exists: 0 readable: 0 size: 0

```

---

### Post by aseriesoftubes on 2008-05-01
Can you post the output of:
cat /etc/X11/xorg.conf 
cat /etc/X11/XvMCConfig

I just recently got XvMC working by tweaking these files. Your frontend output makes it sound like XvMC isn't properly set up in one (or both) of the places listed above.

---

### Post by callagga on 2008-05-02
thanks - here is the data you asked for:

```
greg@mythtv:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection
greg@mythtv:~$

```

```
greg@mythtv:~$ cat /etc/X11/XvMCConfig
libXvMC.so.1
greg@mythtv:~$

```

thanks - any advice appreciated

---

### Post by aseriesoftubes on 2008-05-02
Hmm, I haven't used an Intel chipset for this purpose, so I'm not too familiar with the procedure. From what I gather, though, it looks like you need to change the line in /etc/X11/XvMCConfig to say:
```
libI810XvMC.so
```

You might also try adding the following at the end of your xorg.conf, but it may not do anything:
```
Section "Extensions"
     Option "Composite" "Disabled"
EndSection
```

I'm sorry I couldn't be more helpful. Perhaps somebody else on this board might know more about using XvMC with Intel drivers (it might even be worth starting a new thread).

---

### Post by gavinjc on 2008-05-06
I had the same problem so I went through the XvMC setup guide at:

[http://www.mythtv.org/wiki/index.php/XvMC](http://www.mythtv.org/wiki/index.php/XvMC)

everything seemed OK except for the xorg.conf so I added this to my xorg.conf and XvMC is now working again.

```
Section "Device"
    Identifier "Videocard0"
    Driver "nvidia"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"
    Option "NVAGP" "1"
EndSection

Section "Extensions"
    Option "Composite" "Disabled"
EndSection
```

Cheers Gavin C.

---

### Post by callagga on 2008-05-07
I swapped to the SLIM playback profile and it doesn't seem too bad.  Is "XvMC" better to use if I can get it working?

---

