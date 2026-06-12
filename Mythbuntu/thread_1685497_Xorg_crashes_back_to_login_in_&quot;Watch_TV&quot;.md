---
title: "Xorg crashes back to login in &quot;Watch TV&quot;"
date: 2011-02-10
forum: Mythbuntu
---

### Post by wh7qq on 2011-02-10
I'm trying to get mythbuntu going on a new system:  zotac gf8200-c-e mobo with onboard Nvidia 8200.  I am also trying to get "twinview" going so that I can view on my Sony KDL32x400 Bravia.  I've configured the mythtv backend and my signal source is good (HDHomeRun), did the mythtv database thing, all pretty much the same as my other setup which works, but when I try to "Watch TV", mythtv crashes me back to the login screen.  Also can't get nvidia-xconfig to recognize the tv monitor in xorg.conf...no sign of the tv there, except for the"twinview" option.

---

### Post by nickrout on 2011-02-10
when it crashes, what do the frontend and xorg logs say?

Why do you need twinview? Plug it into the TV and only the TV. Try that.

---

### Post by wh7qq on 2011-02-10
Thanks for the input.

> **nickrout said:**
> when it crashes, what do the frontend and xorg logs say?

Why do you need twinview? Plug it into the TV and only the TV. Try that.

See logs below.

As for twinview, it isn't convenient to use the TV as the primary monitor as it is 30' away from the desktop that houses the mythtv system.  I did try just using the TV with mixed success...got it working as a monitor once but the mythtv crash problem had me back at working in the nvidia xserver settings screen and I'm frankly lost.

Is there a way to reset mythtv back to defaults?



Frontend Log

```
Starting mythfrontend.real..
2011-02-10 17:49:59.370 mythfrontend version: branches/release-0-23-fixes [26437] www.mythtv.org
2011-02-10 17:49:59.371 Using runtime prefix = /usr
2011-02-10 17:49:59.371 Using configuration directory = /home/paul/.mythtv
2011-02-10 17:50:00.222 Empty LocalHostName.
2011-02-10 17:50:00.222 Using localhost value of paul-zotac
2011-02-10 17:50:00.247 New DB connection, total: 1
2011-02-10 17:50:00.253 Connected to database 'mythconverg' at host: localhost
2011-02-10 17:50:00.255 Closing DB connection named 'DBManager0'
2011-02-10 17:50:00.282 ScreenSaverX11Private: XScreenSaver support enabled
2011-02-10 17:50:00.284 DPMS is disabled.
2011-02-10 17:50:00.286 Primary screen: 0.
2011-02-10 17:50:00.287 Connected to database 'mythconverg' at host: localhost
2011-02-10 17:50:00.289 Using screen 0, 1280x1024 at 0,0
2011-02-10 17:50:00.311 Desktop video mode: 1280x1024 60.0204 Hz
2011-02-10 17:50:00.339 MythUI Image Cache size set to 20971520 bytes
2011-02-10 17:50:00.376 Enabled verbose msgs:  important general
2011-02-10 17:50:00.385 Primary screen: 0.
2011-02-10 17:50:00.386 Using screen 0, 1280x1024 at 0,0
2011-02-10 17:50:00.387 Using theme base resolution of 1280x720
2011-02-10 17:50:00.394 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-02-10 17:50:00.395 JoystickMenuThread Error: Joystick disabled - Failed to read /home/paul/.mythtv/joystickmenurc
2011-02-10 17:50:00.446 Using Frameless Window
2011-02-10 17:50:00.911 Using the Qt painter
2011-02-10 17:50:01.004 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2011-02-10 17:50:01.012 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2011-02-10 17:50:01.022 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2011-02-10 17:50:01.022 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2011-02-10 17:50:01.028 Current MythTV Schema Version (DBSchemaVer): 1254
2011-02-10 17:50:01.380 Registering Internal as a media playback plugin.
2011-02-10 17:50:01.409 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-10 17:50:01.409 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-10 17:50:01.409 MediaMonitorUnix::AddDevice() - empty device path.
2011-02-10 17:50:01.410 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-02-10 17:50:01.410 Cannot load language en_us for module mythgallery
2011-02-10 17:50:01.416 Cannot load language en_us for module mythmovies
2011-02-10 17:50:01.460 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-02-10 17:50:01.496 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-02-10 17:50:01.501 Cannot load language en_us for module mythmusic
2011-02-10 17:50:01.514 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-02-10 17:50:01.536 Cannot load language en_us for module mythvideo
2011-02-10 17:50:01.546 Cannot load language en_us for module mythweather
2011-02-10 17:50:01.548 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-10 17:50:01.608 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2011-02-10 17:50:01.610 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-10 17:50:02.485 MythContext: Connecting to backend server: 169.254.34.131:6543 (try 1 of 1)
2011-02-10 17:50:02.486 Using protocol version 23056
2011-02-10 17:50:10.335 TV: Attempting to change from None to WatchingLiveTV
2011-02-10 17:50:10.335 MythContext: Connecting to backend server: 169.254.34.131:6543 (try 1 of 1)
2011-02-10 17:50:10.336 Using protocol version 23056
2011-02-10 17:50:10.367 Spawning LiveTV Recorder -- begin
2011-02-10 17:50:10.448 Spawning LiveTV Recorder -- end
2011-02-10 17:50:10.451 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.454 We have a playbackURL(/var/lib/mythtv/livetv/2051_20110210175010.mpg) & cardtype(DUMMY)
2011-02-10 17:50:10.454 We have a RingBuffer
2011-02-10 17:50:10.643 NVP(0): Disabling Audio, params(-1,2,44100)
2011-02-10 17:50:10.676 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-02-10 17:50:10.696 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.754 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.777 OSD Theme Dimensions W: 1280 H: 720
2011-02-10 17:50:10.814 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.873 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.935 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.995 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.054 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.056 New DB connection, total: 2
2011-02-10 17:50:11.056 Connected to database 'mythconverg' at host: localhost
2011-02-10 17:50:11.056 TV: Changing from None to WatchingLiveTV
2011-02-10 17:50:11.057 TV: State is LiveTV & mctx == ctx
2011-02-10 17:50:11.057 New DB connection, total: 3
2011-02-10 17:50:11.057 Connected to database 'mythconverg' at host: localhost
2011-02-10 17:50:11.057 Realtime priority would require SUID as root.
2011-02-10 17:50:11.059 TV: UpdateOSDInput done
2011-02-10 17:50:11.059 TV: UpdateLCD done
2011-02-10 17:50:11.059 TV: ITVRestart done
2011-02-10 17:50:11.062 Video timing method: USleep with busy wait
2011-02-10 17:50:11.733 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
ICE default IO error handler doing an exit(), pid = 2974, errno = 11
<unknown>: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
```

Backend Log

```
2011-02-10 17:50:02.486 MainServer::ANN Monitor
2011-02-10 17:50:02.487 adding: paul-zotac as a client (events: 0)
2011-02-10 17:50:02.502 MainServer::ANN Monitor
2011-02-10 17:50:02.540 adding: paul-zotac as a client (events: 1)
2011-02-10 17:50:10.337 MainServer::ANN Playback
2011-02-10 17:50:10.337 adding: paul-zotac as a client (events: 0)
2011-02-10 17:50:10.369 TVRec(1): Changing from None to WatchingLiveTV
2011-02-10 17:50:10.382 TVRec(1): HW Tuner: 1->1
2011-02-10 17:50:10.449 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-02-10 17:50:10.489 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.505 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.752 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.809 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.870 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.930 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:10.990 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.050 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.107 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.437 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.442 Finished recording Unknown: channel 2051
2011-02-10 17:50:11.486 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.492 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.534 Finished recording Unknown: channel 2051
2011-02-10 17:50:11.574 ProgramInfo(2051_20110210175010.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2011-02-10 17:50:11.606 ProgramInfo(2051_20110210175010.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2011-02-10 17:50:11.617 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:11.651 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2011-02-10 17:50:11.671 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.699 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:11.712 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:11.788 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:11.792 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:50:16.322 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:16.330 TVRec(1): Changing from WatchingLiveTV to None
2011-02-10 17:50:16.339 ProgramInfo(2051_20110210175011.mpg): Recording designated 1080i/p because width was 1920
2011-02-10 17:50:16.401 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:16.402 Finished recording Unknown: channel 2051
2011-02-10 17:50:16.413 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:16.449 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175011.mpg'
2011-02-10 17:50:52.927 Expiring 5 MBytes for 2051 @ Thu Feb 10 17:32:32 2011 => Unknown
2011-02-10 17:50:52.931 ProgramInfo(): Updated pathname '':'' -> '2051_20110210173232.mpg'
2011-02-10 17:50:52.990 ProgramInfo(): Updated pathname '':'' -> '2051_20110210173232.mpg'
2011-02-10 17:50:55.942 ProgramInfo(): Updated pathname '':'' -> '2051_20110210173232.mpg'
2011-02-10 17:52:52.935 Expiring 0 MBytes for 2051 @ Thu Feb 10 17:50:10 2011 => Unknown
2011-02-10 17:52:52.939 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:52:53.042 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:52:55.992 ProgramInfo(): Updated pathname '':'' -> '2051_20110210175010.mpg'
2011-02-10 17:56:52.948 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

---

### Post by wh7qq on 2011-02-11
More info:  The problem is associated with the proprietary nvidia drivers.  If I install mythbuntu with no proprietary drivers it is happy and the TV works just like a normal monitor in tandem with the desktop monitor.  When I  load the nvidia driver (nvidia-current), The TV is initially disabled and comes back after being enabled as a separate x-screen with nothing going on and no cursor, just the mouse logo. When I try to run mythtv "Watch TV" it crashes the desktop back to the login screen.

---

### Post by nickrout on 2011-02-12
What playback profile are you using? If it involves xvmc it will fail in this fashion.

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

---

### Post by superm1 on 2011-02-14
Additionally run a current build from autobuilds - they force xvmc disabled which would prevent this if it's root caused by XvMC.

---

### Post by wh7qq on 2011-02-15
> **nickrout said:**
> What playback profile are you using? If it involves xvmc it will fail in this fashion.

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

That was the issue...Thank you for that!  Mythtv has so much configurabililty that for someone new to it, it is easy to get lost in all the menus...hard to tell what is important and what isn't.

I still cant seem to get audio out of the hdmi port on the mobo...hard to tell if that is a myth issue or something to do with alsa.

---

### Post by nickrout on 2011-02-15
With an 8200 video card you probably should use a vdpau playback profile.

If you are using 0.24 you can possibly get hdmi audio working by chosing Settings|General, about page three is the audio setup. the button at the top of the page scans for audio devices, the list below it then becomes scrollable (left and right arrow) to choose from the detected devices. You should hopefully find something like alsa:hdmi

---

### Post by Saquili on 2011-02-17
Quote:
I still cant seem to get audio out of the hdmi port on the mobo...hard to tell if that is a myth issue or something to do with alsa.



Yes you need to unmute on alsamixer don't forget to hit F6 and go to your HDMI and unmute that. Also type:
aplay -l
you will get something like this:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

In my case card 1 device 3 is hdmi then go to mythfrontend 
Utilities/Setup-->Setup-->General
Goto the 4th page Audio System and change your audio output device to
ALSA:plughw:1,3 where 1 is the card and 3 is the device from aplay -l

---

### Post by nickrout on 2011-02-17
> **Saquili said:**
> Quote:
I still cant seem to get audio out of the hdmi port on the mobo...hard to tell if that is a myth issue or something to do with alsa.



Yes you need to unmute on alsamixer don't forget to hit F6 and go to your HDMI and unmute that. Also type:
aplay -l
you will get something like this:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

In my case card 1 device 3 is hdmi then go to mythfrontend 
Utilities/Setup-->Setup-->General
Goto the 4th page Audio System and change your audio output device to
ALSA:plughw:1,3 where 1 is the card and 3 is the device from aplay -l

As I said you need to scan for devices first. Everyone should be using 0.24-fixes now.

---

### Post by Saquili on 2011-02-17
> **nickrout said:**
> As I said you need to scan for devices first. Everyone should be using 0.24-fixes now.

Nickrout is right .24 does make this and a some of other problems go away not to mention cool new features like auto restarting the frontend if it crashes and populating the video metadata to name a few:D. The autobuilds are a piece of cake.  If for some reason you don't want to upgrade the suggestion above will help you.;)

---

