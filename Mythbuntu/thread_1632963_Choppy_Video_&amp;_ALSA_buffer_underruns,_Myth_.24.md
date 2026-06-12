---
title: "Choppy Video &amp; ALSA buffer underruns, Myth .24"
date: 2010-11-28
forum: Mythbuntu
---

### Post by Chunk of Earth on 2010-11-28
I just upgraded my Myth box to Maverick and Myth 0.24 and the internal player is having fits trying to play video from either the recording list or MythVideo.
There are two failure modes. In the first mode I get choppy video and rapid audio, like the audio is running fast and the video is jumping ahead to catch up with it. Along with the choppy video I get the following error repeatedly in the mythfrontend.log file```
ALSA, Error: WriteAudio: buffer underrun
```In the second failure mode the frontend just crashes back to the desktop. No error is reported in either the frontend.log or syslog files.
I haven't been able to determine a pattern to the recordings that fail in either mode but each recording always fails in the same way.
I've gone into the frontend setup and rescanned the audio devices as instructed in the Myth 0.24 release notes and made the selections shown in the attached screen shot. (Note also the bogosity of the invisible options caused by the slected theme - the only adult theme available for my 4:3 set)
It's interesting to note that I can select an audio device that does not produce output here and then the frontend will play back flawless video (sans audio) for all recordings.

**Hardware:**
Dell PowerEdge 400SC, Intel(R) Pentium(R) 4 CPU 2.80GHz, 2.5 GB RAM
NV44A [GeForce 6200]
Sound Blaster Live! 5.1 with LiveDrive

**Tests:**
-```
aplay -D hw:CARD=Live,DEV=2 SURROUNDTEST_011212.wav
aplay -D hw:CARD=Live,DEV=2 SURROUNDTEST_DD_640.wav
```Both commands produced flawless audio through the optical output with DTS and AC-3 passthrough, respectively, and all five speakers working.

- Created an .asoundrc file in my home directory pointing the default output to the optical port and tested applications such as VLC using the default audio device. The applications properly directed default output to the optical port. .asoundrc is:```
pcm.!default {
        type hw
        card Live
        device 2
}
```- Played video with VLC using default audio output and VLC produced flawless full-screen video from a HD source with AC-3 passthrough.

**aplay -L Output:**
```
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Live
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Direct sample mixing device
dmix:CARD=Live,DEV=2
    SB Live! 5.1 [SB0060], Multichannel Capture/PT Playback
    Direct sample mixing device
dmix:CARD=Live,DEV=3
    SB Live! 5.1 [SB0060], Multichannel Playback
    Direct sample mixing device
dsnoop:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Direct sample snooping device
dsnoop:CARD=Live,DEV=2
    SB Live! 5.1 [SB0060], Multichannel Capture/PT Playback
    Direct sample snooping device
dsnoop:CARD=Live,DEV=3
    SB Live! 5.1 [SB0060], Multichannel Playback
    Direct sample snooping device
hw:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Direct hardware device without any conversions
hw:CARD=Live,DEV=2
    SB Live! 5.1 [SB0060], Multichannel Capture/PT Playback
    Direct hardware device without any conversions
hw:CARD=Live,DEV=3
    SB Live! 5.1 [SB0060], Multichannel Playback
    Direct hardware device without any conversions
plughw:CARD=Live,DEV=0
    SB Live! 5.1 [SB0060], ADC Capture/Standard PCM Playback
    Hardware device with all software conversions
plughw:CARD=Live,DEV=2
    SB Live! 5.1 [SB0060], Multichannel Capture/PT Playback
    Hardware device with all software conversions
plughw:CARD=Live,DEV=3
    SB Live! 5.1 [SB0060], Multichannel Playback
    Hardware device with all software conversions
```How can I get the internal player to work as well as the other apps?

Edit:
I ran mythfrontend -v audio in both failure modes with the following results:
First mode:```
:~$ mythfrontend -v audio
2010-11-30 18:30:58.265 mythfrontend version: branches/release-0-24-fixes [27352] www.mythtv.org
2010-11-30 18:30:58.266 Using runtime prefix = /usr
2010-11-30 18:30:58.266 Using configuration directory = /home/mythuser/.mythtv
2010-11-30 18:30:58.267 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-11-30 18:30:58.888 Empty LocalHostName.
2010-11-30 18:30:58.888 Using localhost value of atoz
2010-11-30 18:30:58.905 New DB connection, total: 1
2010-11-30 18:30:58.908 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:30:58.921 Closing DB connection named 'DBManager0'
2010-11-30 18:30:58.922 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:30:58.925 Current locale EN_US
2010-11-30 18:30:58.926 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-11-30 18:30:59.141 ScreenSaverX11Private: XScreenSaver support enabled
2010-11-30 18:30:59.141 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-30 18:30:59.143 DPMS is disabled.
2010-11-30 18:30:59.168 Desktop video mode: 800x600 60.317 Hz
2010-11-30 18:30:59.198 Enabled verbose msgs:  important general audio
2010-11-30 18:30:59.207 Loading en_us translation for module mythfrontend
2010-11-30 18:30:59.224 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-11-30 18:30:59.225 JoystickMenuThread: Joystick disabled - Failed to read /home/mythuser/.mythtv/joystickmenurc
2010-11-30 18:30:59.302 Using Frameless Window
2010-11-30 18:30:59.302 Using Full Screen Window
2010-11-30 18:30:59.531 Using the OpenGL painter
2010-11-30 18:30:59.636 OpenGL: OpenGL vendor  : NVIDIA Corporation
2010-11-30 18:30:59.636 OpenGL: OpenGL renderer: GeForce 6200/AGP/SSE2
2010-11-30 18:30:59.636 OpenGL: OpenGL version : 2.1.2 NVIDIA 260.19.06
2010-11-30 18:30:59.636 OpenGL: Max texture size: 4096 x 4096
2010-11-30 18:30:59.636 OpenGL: Max texture units: 4
2010-11-30 18:30:59.636 OpenGL: Direct rendering: Yes
2010-11-30 18:30:59.636 OpenGL: Initialised MythRenderOpenGL
2010-11-30 18:31:00.081 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-30 18:31:00.084 New DB connection, total: 2
2010-11-30 18:31:00.085 New DB connection, total: 3
2010-11-30 18:31:00.085 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:31:00.088 Current MythTV Schema Version (DBSchemaVer): 1264
2010-11-30 18:31:00.093 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:31:00.310 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-11-30 18:31:00.311 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-11-30 18:31:00.311 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/blootube-wide/themeinfo.xml
2010-11-30 18:31:00.311 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/blootube-wide) is missing a themeinfo.xml file.
2010-11-30 18:31:00.314 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-11-30 18:31:00.315 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-11-30 18:31:00.542 Pulse: PulseAudio not running
2010-11-30 18:31:00.554 AO: Sample rate 48000 is supported
2010-11-30 18:31:00.555 AO: 2 channel(s) are supported
2010-11-30 18:31:00.608 AO: AC3 or DTS capable
2010-11-30 18:31:00.608 AO: 6 channel(s) are supported
2010-11-30 18:31:00.612 AO: Killing AudioOutputDSP
2010-11-30 18:31:00.613 Found ALSA:plughw:CARD=Live,DEV=2 (ALSA:plughw:CARD=Live,DEV=2
Device supports up to 5.1 (AC3,DTS,))
2010-11-30 18:31:00.843 Registering Internal as a media playback plugin.
2010-11-30 18:31:00.889 Loading en_us translation for module mytharchive
2010-11-30 18:31:00.898 Registering WebBrowser as a media playback plugin.
2010-11-30 18:31:00.898 Loading en_us translation for module mythbrowser
2010-11-30 18:31:00.956 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-30 18:31:00.956 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-30 18:31:00.957 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-30 18:31:00.958 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-11-30 18:31:00.958 Loading en_us translation for module mythgallery
2010-11-30 18:31:00.973 Loading en_us translation for module mythgame
2010-11-30 18:31:01.001 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-30 18:31:01.087 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-30 18:31:01.098 Loading en_us translation for module mythmusic
2010-11-30 18:31:01.104 Loading en_us translation for module mythnetvision
2010-11-30 18:31:01.112 Loading en_us translation for module mythnews
2010-11-30 18:31:01.125 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-11-30 18:31:01.163 Loading en_us translation for module mythvideo
2010-11-30 18:31:01.177 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/maps/radar/regions/us_rainfall_est_, 1
2010-11-30 18:31:01.178 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/forecast/us_ec_9regwxhi1_large_usen, 1
2010-11-30 18:31:01.178 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/us_ec_9regradar_plus_us, 1
2010-11-30 18:31:01.179 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/atl_oce_sat_720x486/, 1
2010-11-30 18:31:01.180 Starting update of NWS-XML
2010-11-30 18:31:01.193 Starting update of NDFD-6_day
2010-11-30 18:31:01.209 Loading en_us translation for module mythweather
2010-11-30 18:31:01.249 Found mainmenu.xml for theme 'Graphite'
2010-11-30 18:31:01.445 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-30 18:31:01.446 Using protocol version 63
2010-11-30 18:31:02.260 'nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/mythuser/.mythtv/MythWeather/NWS-XML KCRW' has exited
2010-11-30 18:31:06.985 'nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/mythuser/.mythtv/MythWeather/NDFD-6_day +38.22,-081.35' has exited
2010-11-30 18:31:51.732 TV: Attempting to change from None to WatchingPreRecorded
2010-11-30 18:31:52.102 Pulse: PulseAudio not running
2010-11-30 18:31:52.112 AO: Sample rate 48000 is supported
2010-11-30 18:31:52.112 AO: 2 channel(s) are supported
2010-11-30 18:31:52.161 AO: AC3 or DTS capable
2010-11-30 18:31:52.161 AO: 6 channel(s) are supported
2010-11-30 18:31:52.165 AO: Killing AudioOutputDSP
2010-11-30 18:31:52.282 AFD: Opened codec 0xaaec9360, id(MPEG2VIDEO) type(Video)
2010-11-30 18:31:52.282 AFD: codec AC3 has 2 channels
2010-11-30 18:31:52.283 AFD: Opened codec 0xab43d930, id(AC3) type(Audio)
2010-11-30 18:31:52.283 AFD: Audio Track #1 is A/V stream #1 and has 2 channels in the English language(6647399).
2010-11-30 18:31:52.283 AFD: Selected track 1: English AC3 2ch (A/V Stream #1)
2010-11-30 18:31:52.283 AFD: Initializing audio parms from audio track #1
2010-11-30 18:31:52.283 AFD: Audio format changed 
            from id(NONE)     -1Hz -1ch -1bps     to id( AC3)  48000Hz  2ch 16bps    
2010-11-30 18:31:52.283 AO: Killing AudioOutputDSP
2010-11-30 18:31:52.402 Pulse: PulseAudio not running
2010-11-30 18:31:52.409 AO: Sample rate 48000 is supported
2010-11-30 18:31:52.409 AO: 2 channel(s) are supported
2010-11-30 18:31:52.458 AO: AC3 or DTS capable
2010-11-30 18:31:52.458 AO: 6 channel(s) are supported
2010-11-30 18:31:52.458 AO: Killing AudioOutputDSP
2010-11-30 18:31:52.459 AO: Original codec was AC3, signed 16 bit, 48 kHz, 2 channels
2010-11-30 18:31:52.459 AO: enc(0), passthru(0), canAC3(1), canDTS(1), canLPCM(0), configured_channels(2), 2 channels supported(1)
2010-11-30 18:31:52.459 AO: Opening audio device 'plughw:CARD=Live,DEV=2' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2010-11-30 18:31:52.459 ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=200000, period_time=50000)
2010-11-30 18:31:52.460 ALSA: Buffer time = 200000 us
2010-11-30 18:31:52.461 ALSA: Period time = 50000 us
2010-11-30 18:31:52.461 ALSA: Buffer size = 9600 | Period size = 2400
2010-11-30 18:31:52.462 AO: Audio fragment size: 4800
2010-11-30 18:31:52.462 AO: Audio Stretch Factor: 1
2010-11-30 18:31:52.462 AO: Ending Reconfigure()
2010-11-30 18:31:52.462 AudioPlayer: Enabling Audio
2010-11-30 18:31:52.462 AO: Reconfigure(): No change -> exiting
2010-11-30 18:31:52.463 AO: kickoffOutputAudioLoop: pid = 2848
2010-11-30 18:31:52.463 AO: OutputAudioLoop: Play Event
2010-11-30 18:31:58.780 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-11-30 18:31:58.830 OSD: Base theme size: 1280x720
2010-11-30 18:31:58.830 OSD: Scaling factors: 0.55x0.6
2010-11-30 18:31:58.951 OSD: Base theme size: 1280x720
2010-11-30 18:31:58.951 OSD: Scaling factors: 0.55x0.6
2010-11-30 18:31:58.952 OSD: Base theme size: 1280x720
2010-11-30 18:31:58.952 OSD: Scaling factors: 0.55x0.6
2010-11-30 18:31:58.970 Player(0): Video timing method: USleep with busy wait
2010-11-30 18:31:58.971 TV: Changing from None to WatchingPreRecorded
2010-11-30 18:31:58.989 AO: OutputAudioLoop: Play Event
2010-11-30 18:31:59.034 VideoOutput: Created YV12 OSD.
2010-11-30 18:31:59.888 ALSA, Error: WriteAudio: buffer underrun
2010-11-30 18:32:00.290 ALSA, Error: WriteAudio: buffer underrun
2010-11-30 18:32:00.691 ALSA, Error: WriteAudio: buffer underrun
2010-11-30 18:32:03.891 ALSA, Error: WriteAudio: buffer underrun
2010-11-30 18:32:04.892 ALSA, Error: WriteAudio: buffer underrun
2010-11-30 18:32:04.998 TV: Attempting to change from WatchingPreRecorded to None
2010-11-30 18:32:05.018 AO: Killing AudioOutputDSP
2010-11-30 18:32:05.042 AO: OutputAudioLoop: Stop Event
2010-11-30 18:32:05.043 AO: kickoffOutputAudioLoop exiting
2010-11-30 18:32:05.044 TV: Changing from WatchingPreRecorded to None
2010-11-30 18:32:21.350 OpenGL: Deleting OpenGL Resources
2010-11-30 18:32:21.376 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

```Second mode:```
:~$ mythfrontend -v audio
2010-11-30 18:03:41.535 mythfrontend version: branches/release-0-24-fixes [27352] www.mythtv.org
2010-11-30 18:03:41.535 Using runtime prefix = /usr
2010-11-30 18:03:41.535 Using configuration directory = /home/mythuser/.mythtv
2010-11-30 18:03:41.537 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-11-30 18:03:42.042 Empty LocalHostName.
2010-11-30 18:03:42.043 Using localhost value of atoz
2010-11-30 18:03:42.060 New DB connection, total: 1
2010-11-30 18:03:42.063 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:03:42.075 Closing DB connection named 'DBManager0'
2010-11-30 18:03:42.076 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:03:42.079 Current locale EN_US
2010-11-30 18:03:42.080 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-11-30 18:03:42.295 ScreenSaverX11Private: XScreenSaver support enabled
2010-11-30 18:03:42.295 ScreenSaverX11Private: Gnome screen saver support enabled
2010-11-30 18:03:42.296 DPMS is disabled.
2010-11-30 18:03:42.320 Desktop video mode: 800x600 60.317 Hz
2010-11-30 18:03:42.342 Enabled verbose msgs:  important general audio
2010-11-30 18:03:42.347 Loading en_us translation for module mythfrontend
2010-11-30 18:03:42.360 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-11-30 18:03:42.361 JoystickMenuThread: Joystick disabled - Failed to read /home/mythuser/.mythtv/joystickmenurc
2010-11-30 18:03:42.440 Using Frameless Window
2010-11-30 18:03:42.440 Using Full Screen Window
2010-11-30 18:03:42.668 Using the OpenGL painter
2010-11-30 18:03:42.776 OpenGL: OpenGL vendor  : NVIDIA Corporation
2010-11-30 18:03:42.776 OpenGL: OpenGL renderer: GeForce 6200/AGP/SSE2
2010-11-30 18:03:42.777 OpenGL: OpenGL version : 2.1.2 NVIDIA 260.19.06
2010-11-30 18:03:42.777 OpenGL: Max texture size: 4096 x 4096
2010-11-30 18:03:42.777 OpenGL: Max texture units: 4
2010-11-30 18:03:42.777 OpenGL: Direct rendering: Yes
2010-11-30 18:03:42.777 OpenGL: Initialised MythRenderOpenGL
2010-11-30 18:03:43.221 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-11-30 18:03:43.235 Current MythTV Schema Version (DBSchemaVer): 1264
2010-11-30 18:03:43.392 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-11-30 18:03:43.392 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-11-30 18:03:43.393 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/blootube-wide/themeinfo.xml
2010-11-30 18:03:43.393 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/blootube-wide) is missing a themeinfo.xml file.
2010-11-30 18:03:43.398 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-11-30 18:03:43.398 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-11-30 18:03:43.596 Pulse: PulseAudio not running
2010-11-30 18:03:43.609 AO: Sample rate 48000 is supported
2010-11-30 18:03:43.609 AO: 2 channel(s) are supported
2010-11-30 18:03:43.664 AO: AC3 or DTS capable
2010-11-30 18:03:43.665 AO: 6 channel(s) are supported
2010-11-30 18:03:43.668 AO: Killing AudioOutputDSP
2010-11-30 18:03:43.668 Found ALSA:plughw:CARD=Live,DEV=2 (ALSA:plughw:CARD=Live,DEV=2
Device supports up to 5.1 (AC3,DTS,))
2010-11-30 18:03:43.860 Registering Internal as a media playback plugin.
2010-11-30 18:03:43.893 Loading en_us translation for module mytharchive
2010-11-30 18:03:43.900 Registering WebBrowser as a media playback plugin.
2010-11-30 18:03:43.900 Loading en_us translation for module mythbrowser
2010-11-30 18:03:43.947 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-30 18:03:43.948 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-30 18:03:43.948 MediaMonitorUnix::AddDevice() - empty device path.
2010-11-30 18:03:43.949 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-11-30 18:03:43.949 Loading en_us translation for module mythgallery
2010-11-30 18:03:43.963 Loading en_us translation for module mythgame
2010-11-30 18:03:43.990 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-11-30 18:03:44.055 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-11-30 18:03:44.061 Loading en_us translation for module mythmusic
2010-11-30 18:03:44.066 Loading en_us translation for module mythnetvision
2010-11-30 18:03:44.074 Loading en_us translation for module mythnews
2010-11-30 18:03:44.085 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-11-30 18:03:44.111 Loading en_us translation for module mythvideo
2010-11-30 18:03:44.126 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/maps/radar/regions/us_rainfall_est_, 1
2010-11-30 18:03:44.126 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/forecast/us_ec_9regwxhi1_large_usen, 1
2010-11-30 18:03:44.126 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/us_ec_9regradar_plus_us, 1
2010-11-30 18:03:44.127 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/atl_oce_sat_720x486/, 1
2010-11-30 18:03:44.128 Starting update of NWS-XML
2010-11-30 18:03:44.128 NWS-XML recently updated, skipping.
2010-11-30 18:03:44.129 Starting update of NDFD-6_day
2010-11-30 18:03:44.130 NDFD-6_day recently updated, skipping.
2010-11-30 18:03:44.130 Loading en_us translation for module mythweather
2010-11-30 18:03:44.160 Found mainmenu.xml for theme 'Graphite'
2010-11-30 18:03:44.267 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-11-30 18:03:44.268 Using protocol version 63
2010-11-30 18:03:57.580 New DB connection, total: 2
2010-11-30 18:03:57.581 Connected to database 'mythconverg' at host: localhost
2010-11-30 18:04:05.535 TV: Attempting to change from None to WatchingPreRecorded
2010-11-30 18:04:05.849 Pulse: PulseAudio not running
2010-11-30 18:04:05.858 AO: Sample rate 48000 is supported
2010-11-30 18:04:05.858 AO: 2 channel(s) are supported
2010-11-30 18:04:05.911 AO: AC3 or DTS capable
2010-11-30 18:04:05.911 AO: 6 channel(s) are supported
2010-11-30 18:04:05.915 AO: Killing AudioOutputDSP
2010-11-30 18:04:05.982 AFD: Opened codec 0xa66a880, id(MPEG2VIDEO) type(Video)
2010-11-30 18:04:05.982 AFD: codec AC3 has 2 channels
2010-11-30 18:04:05.983 AFD: Opened codec 0xa66ae40, id(AC3) type(Audio)
2010-11-30 18:04:05.983 AFD: Audio Track #1 is A/V stream #1 and has 2 channels in the English language(6647399).
2010-11-30 18:04:05.983 AFD: Selected track 1: English AC3 2ch (A/V Stream #1)
2010-11-30 18:04:05.983 AFD: Initializing audio parms from audio track #1
2010-11-30 18:04:05.983 AFD: Audio format changed 
            from id(NONE)     -1Hz -1ch -1bps     to id( AC3)  48000Hz  2ch 16bps    
2010-11-30 18:04:05.983 AO: Killing AudioOutputDSP
2010-11-30 18:04:06.050 Pulse: PulseAudio not running
2010-11-30 18:04:06.057 AO: Sample rate 48000 is supported
2010-11-30 18:04:06.057 AO: 2 channel(s) are supported
2010-11-30 18:04:06.114 AO: AC3 or DTS capable
2010-11-30 18:04:06.114 AO: 6 channel(s) are supported
2010-11-30 18:04:06.114 AO: Killing AudioOutputDSP
2010-11-30 18:04:06.114 AO: Original codec was AC3, signed 16 bit, 48 kHz, 2 channels
2010-11-30 18:04:06.114 AO: enc(0), passthru(0), canAC3(1), canDTS(1), canLPCM(0), configured_channels(2), 2 channels supported(1)
2010-11-30 18:04:06.114 AO: Opening audio device 'plughw:CARD=Live,DEV=2' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2010-11-30 18:04:06.115 ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=200000, period_time=50000)
2010-11-30 18:04:06.116 ALSA: Buffer time = 200000 us
2010-11-30 18:04:06.116 ALSA: Period time = 50000 us
2010-11-30 18:04:06.116 ALSA: Buffer size = 9600 | Period size = 2400
2010-11-30 18:04:06.116 AO: Audio fragment size: 4800
2010-11-30 18:04:06.116 AO: Audio Stretch Factor: 1
2010-11-30 18:04:06.116 AO: Ending Reconfigure()
2010-11-30 18:04:06.117 AudioPlayer: Enabling Audio
2010-11-30 18:04:06.117 AO: Reconfigure(): No change -> exiting
2010-11-30 18:04:06.117 AO: Using time stretch 1.3
2010-11-30 18:04:06.117 AO: kickoffOutputAudioLoop: pid = 2299
2010-11-30 18:04:06.118 AO: OutputAudioLoop: Play Event
2010-11-30 18:04:10.037 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-11-30 18:04:10.078 OSD: Base theme size: 1280x720
2010-11-30 18:04:10.078 OSD: Scaling factors: 0.4125x0.6
Illegal instruction

```

---

### Post by jyavenard on 2010-11-30
Any particular reason you are forcing the output to 48kHz?
your audio card only supports 48kHz to start with and report as such.

That settings is in the "advanced" option for a reason: there should be no need for you to play with those unless you know exactly what you are doing.

And why use an audio device that obviously wasn't auto-detected by the audio scan.. (the selection you have on your screen capture, isn't what is used in the log, so you obviously have manually played with it beforehand)

Please stick to the default usage, and let myth do its job in detecting what devices are available

---

### Post by thatguruguy on 2010-11-30
> **Chunk of Earth said:**
> 
- Created an .asoundrc file in my home directory pointing the default output to the optical port and tested applications such as VLC using the default audio device. The applications properly directed default output to the optical port. .asoundrc is:```
pcm.!default {
        type hw
        card Live
        device 2
}
```- Played video with VLC using default audio output and VLC produced flawless full-screen video from a HD source with AC-3 passthrough.

Mythtv won't see any settings in the .asoundrc in your home directory, because mythtv doesn't share your home directory with you.

Have you considered allowing pulseaudio to control sound?

You'll have to create file called /etc/asound.conf, set up as follows:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

Then, use ALSA: Pulse as your sound device on your front-end.

---

### Post by Chunk of Earth on 2010-11-30
Do you think I would have made the changes you see if it was working at the default settings? I've been working on this since Saturday and tested dozens of different combinations of settings. It's a little unfair of you to criticize me for trying different settings to get this to work. That's why they're there, right? And the device shown in the screen capture absolutely **was** detected by the audio scan and, yes, I changed it between the time I took the screen shot and the time I made the verbose logs because it wasn't working.
If there is a particular set of parameters for which you'd like to see a log file, I can plug 'em in and post that up for you *tout suite*, though.

---

### Post by Chunk of Earth on 2010-11-30
> **thatguruguy said:**
> Mythtv won't see any settings in the .asoundrc in your home directory, because mythtv doesn't share your home directory with you.Sure it does. The frontend runs in userspace. There are several configuration stores in my home directory including the .mythtv directory. You can see it reading that one in the log files I posted.

> Have you considered allowing pulseaudio to control sound?Yes, I have but I didn't want to deviate from a standard Mythbuntu config any farther than I absolutely have to. ALSA seems to be working so I'm a little reluctant to alter the system audio.

---

### Post by thatguruguy on 2010-11-30
> **Chunk of Earth said:**
> Sure it does. The frontend runs in userspace. There are several configuration stores in my home directory including the .mythtv directory. You can see it reading that one in the log files I posted.

You're right about the frontend.

> Yes, I have but I didn't want to deviate from a standard Mythbuntu config any farther than I absolutely have to. ALSA seems to be working so I'm a little reluctant to alter the system audio.

Actually, I'm pretty sure that using pulseaudio to control audio is intended to become the standard Mythbuntu config.  For example, OSS was removed from the kernel used in mythbuntu 10.10, which means that you can no longer use /dev/dsp as an audio capture device in the backend  (which used to be the standard way of capturing audio on analog cards).  The audio framework was completely redone for myth .24, including much-improved pulseaudio support.

---

### Post by MC_Claus on 2010-12-01
I'm experiencing the same issue as OP, after updating my myth earlier today to 0.24.0+fixes27373.

I am, however, only seeing the issue when playing back HD content (live only actually, haven't tried recorded). This wasn't a problem yesterday/earlier myth 0.24 version. 

I have also tried to set the audio device to NULL, but the problem didn't went away, so I'm not quite sure that this is a pure ALSA/audio issue.

---

### Post by Chunk of Earth on 2010-12-01
> **jyavenard said:**
> Any particular reason you are forcing the output to 48kHz?
your audio card only supports 48kHz to start with and report as such.

That settings is in the "advanced" option for a reason: there should be no need for you to play with those unless you know exactly what you are doing.

And why use an audio device that obviously wasn't auto-detected by the audio scan.. (the selection you have on your screen capture, isn't what is used in the log, so you obviously have manually played with it beforehand)

Please stick to the default usage, and let myth do its job in detecting what devices are available
Ta Daa! [/Me Jumps Through Hoop]
Is this more helpful? A new screen shot with matching verbose audio logs for both failure modes. Exactly the same result.```
:~$ mythfrontend -v audio
2010-12-01 14:37:32.694 mythfrontend version: branches/release-0-24-fixes [27352] www.mythtv.org
2010-12-01 14:37:32.694 Using runtime prefix = /usr
2010-12-01 14:37:32.694 Using configuration directory = /home/mythuser/.mythtv
2010-12-01 14:37:32.708 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-12-01 14:37:33.629 Empty LocalHostName.
2010-12-01 14:37:33.629 Using localhost value of atoz
2010-12-01 14:37:33.645 New DB connection, total: 1
2010-12-01 14:37:33.649 Connected to database 'mythconverg' at host: localhost
2010-12-01 14:37:33.660 Closing DB connection named 'DBManager0'
2010-12-01 14:37:33.661 Connected to database 'mythconverg' at host: localhost
2010-12-01 14:37:33.663 Current locale en_US
2010-12-01 14:37:33.663 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-12-01 14:37:33.882 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-01 14:37:33.882 ScreenSaverX11Private: Gnome screen saver support enabled
2010-12-01 14:37:33.884 DPMS is disabled.
2010-12-01 14:37:33.917 Desktop video mode: 800x600 60.317 Hz
2010-12-01 14:37:34.010 Enabled verbose msgs:  important general audio
2010-12-01 14:37:34.014 Loading en_us translation for module mythfrontend
2010-12-01 14:37:34.068 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-01 14:37:34.068 JoystickMenuThread: Joystick disabled - Failed to read /home/mythuser/.mythtv/joystickmenurc
2010-12-01 14:37:34.159 Using Frameless Window
2010-12-01 14:37:34.159 Using Full Screen Window
2010-12-01 14:37:34.275 Using the Qt painter
2010-12-01 14:37:34.912 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Arial'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1006
            Name: 'small'    Type: 'fontdef'
2010-12-01 14:37:34.930 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1012
            Name: 'medium'    Type: 'fontdef'
2010-12-01 14:37:34.939 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1018
            Name: 'large'    Type: 'fontdef'
2010-12-01 14:37:34.948 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1024
            Name: 'clock'    Type: 'fontdef'
2010-12-01 14:37:34.985 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-01 14:37:34.986 New DB connection, total: 2
2010-12-01 14:37:34.987 Connected to database 'mythconverg' at host: localhost
2010-12-01 14:37:35.671 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-12-01 14:37:35.671 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-12-01 14:37:35.679 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/blootube-wide/themeinfo.xml
2010-12-01 14:37:35.679 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/blootube-wide) is missing a themeinfo.xml file.
2010-12-01 14:37:35.709 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-12-01 14:37:35.709 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-12-01 14:37:35.884 Pulse: PulseAudio not running
2010-12-01 14:37:35.935 AO: Sample rate 48000 is supported
2010-12-01 14:37:35.936 AO: 2 channel(s) are supported
2010-12-01 14:37:35.988 AO: AC3 or DTS capable
2010-12-01 14:37:35.988 AO: 6 channel(s) are supported
2010-12-01 14:37:35.991 AO: Killing AudioOutputDSP
2010-12-01 14:37:35.992 Found ALSA:iec958:CARD=Live,DEV=0 (ALSA:iec958:CARD=Live,DEV=0
Device supports up to 5.1 (digital output, AC3,DTS,))
2010-12-01 14:37:36.235 Registering Internal as a media playback plugin.
2010-12-01 14:37:36.321 Loading en_us translation for module mytharchive
2010-12-01 14:37:36.334 Registering WebBrowser as a media playback plugin.
2010-12-01 14:37:36.344 Loading en_us translation for module mythbrowser
2010-12-01 14:37:36.472 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-01 14:37:36.472 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-01 14:37:36.473 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-01 14:37:36.474 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-01 14:37:36.490 Loading en_us translation for module mythgallery
2010-12-01 14:37:36.571 Loading en_us translation for module mythgame
2010-12-01 14:37:36.760 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-01 14:37:36.847 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-01 14:37:36.857 Loading en_us translation for module mythmusic
2010-12-01 14:37:36.875 Loading en_us translation for module mythnetvision
2010-12-01 14:37:36.897 Loading en_us translation for module mythnews
2010-12-01 14:37:36.937 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-12-01 14:37:36.975 Loading en_us translation for module mythvideo
2010-12-01 14:37:37.080 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/maps/radar/regions/us_rainfall_est_, 1
2010-12-01 14:37:37.080 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/forecast/us_ec_9regwxhi1_large_usen, 1
2010-12-01 14:37:37.080 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/us_ec_9regradar_plus_us, 1
2010-12-01 14:37:37.081 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/atl_oce_sat_720x486/, 1
2010-12-01 14:37:37.082 Starting update of NWS-XML
2010-12-01 14:37:37.083 NWS-XML recently updated, skipping.
2010-12-01 14:37:37.083 Starting update of NDFD-6_day
2010-12-01 14:37:37.084 NDFD-6_day recently updated, skipping.
2010-12-01 14:37:37.085 Loading en_us translation for module mythweather
2010-12-01 14:37:37.784 Found mainmenu.xml for theme 'MythCenter'
2010-12-01 14:37:37.876 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-01 14:37:37.877 Using protocol version 63
2010-12-01 14:38:56.540 TV: Attempting to change from None to WatchingPreRecorded
2010-12-01 14:38:56.943 Pulse: PulseAudio not running
2010-12-01 14:38:56.952 AO: Sample rate 48000 is supported
2010-12-01 14:38:56.952 AO: 2 channel(s) are supported
2010-12-01 14:38:57.007 AO: AC3 or DTS capable
2010-12-01 14:38:57.007 AO: 6 channel(s) are supported
2010-12-01 14:38:57.012 AO: Killing AudioOutputDSP
2010-12-01 14:38:57.130 AFD: Opened codec 0x9aec3a0, id(MPEG2VIDEO) type(Video)
2010-12-01 14:38:57.130 AFD: codec AC3 has 2 channels
2010-12-01 14:38:57.131 AFD: Opened codec 0x9b74320, id(AC3) type(Audio)
2010-12-01 14:38:57.131 AFD: Audio Track #1 is A/V stream #1 and has 2 channels in the English language(6647399).
2010-12-01 14:38:57.138 AFD: Selected track 1: English AC3 2ch (A/V Stream #1)
2010-12-01 14:38:57.138 AFD: Initializing audio parms from audio track #1
2010-12-01 14:38:57.138 AFD: Audio format changed 
            from id(NONE)     -1Hz -1ch -1bps     to id( AC3)  48000Hz  2ch 16bps    
2010-12-01 14:38:57.138 AO: Killing AudioOutputDSP
2010-12-01 14:38:57.246 Pulse: PulseAudio not running
2010-12-01 14:38:57.254 AO: Sample rate 48000 is supported
2010-12-01 14:38:57.254 AO: 2 channel(s) are supported
2010-12-01 14:38:57.306 AO: AC3 or DTS capable
2010-12-01 14:38:57.306 AO: 6 channel(s) are supported
2010-12-01 14:38:57.306 AO: Killing AudioOutputDSP
2010-12-01 14:38:57.306 AO: Original codec was AC3, signed 16 bit, 48 kHz, 2 channels
2010-12-01 14:38:57.306 AO: enc(0), passthru(0), canAC3(1), canDTS(1), canLPCM(0), configured_channels(2), 2 channels supported(1)
2010-12-01 14:38:57.306 AO: Opening audio device 'iec958:CARD=Live,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2010-12-01 14:38:57.308 ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=200000, period_time=50000)
2010-12-01 14:38:57.308 ALSA: Buffer time = 200000 us
2010-12-01 14:38:57.308 ALSA: Period time = 50000 us
2010-12-01 14:38:57.308 ALSA: Buffer size = 9600 | Period size = 2400
2010-12-01 14:38:57.308 AO: Audio fragment size: 4800
2010-12-01 14:38:57.308 AO: Audio Stretch Factor: 1
2010-12-01 14:38:57.309 AO: Ending Reconfigure()
2010-12-01 14:38:57.309 AudioPlayer: Enabling Audio
2010-12-01 14:38:57.309 AO: Reconfigure(): No change -> exiting
2010-12-01 14:38:57.314 AO: kickoffOutputAudioLoop: pid = 17388
2010-12-01 14:38:57.314 AO: OutputAudioLoop: Play Event
2010-12-01 14:39:03.103 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-12-01 14:39:03.175 OSD: Base theme size: 800x600
2010-12-01 14:39:03.176 OSD: Scaling factors: 0.88x0.72
2010-12-01 14:39:03.332 OSD: Base theme size: 800x600
2010-12-01 14:39:03.332 OSD: Scaling factors: 0.88x0.72
2010-12-01 14:39:03.333 OSD: Base theme size: 800x600
2010-12-01 14:39:03.333 OSD: Scaling factors: 0.88x0.72
2010-12-01 14:39:03.348 AO: OutputAudioLoop: Play Event
2010-12-01 14:39:03.357 Player(0): Video timing method: USleep with busy wait
2010-12-01 14:39:03.362 TV: Changing from None to WatchingPreRecorded
2010-12-01 14:39:03.434 VideoOutput: Created YV12 OSD.
2010-12-01 14:39:03.510 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:03.982 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:04.382 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:04.783 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:05.783 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:09.584 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:09.984 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:13.384 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:13.785 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:14.786 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:17.587 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:17.988 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:19.990 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:22.790 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:23.790 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:24.791 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:25.791 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:26.792 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:27.793 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:28.793 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:29.794 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:30.794 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:31.795 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:32.795 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:34.996 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:35.396 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:35.797 ALSA, Error: WriteAudio: buffer underrun
2010-12-01 14:39:36.417 TV: Attempting to change from WatchingPreRecorded to None
2010-12-01 14:39:36.437 AO: Killing AudioOutputDSP
2010-12-01 14:39:36.448 AO: OutputAudioLoop: Stop Event
2010-12-01 14:39:36.448 AO: kickoffOutputAudioLoop exiting
2010-12-01 14:39:36.501 TV: Changing from WatchingPreRecorded to None
2010-12-01 14:40:08.098 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

``````
:~$ mythfrontend -v audio
2010-12-01 15:04:02.592 mythfrontend version: branches/release-0-24-fixes [27352] www.mythtv.org
2010-12-01 15:04:02.593 Using runtime prefix = /usr
2010-12-01 15:04:02.593 Using configuration directory = /home/mythuser/.mythtv
2010-12-01 15:04:02.594 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2010-12-01 15:04:03.057 Empty LocalHostName.
2010-12-01 15:04:03.057 Using localhost value of atoz
2010-12-01 15:04:03.074 New DB connection, total: 1
2010-12-01 15:04:03.078 Connected to database 'mythconverg' at host: localhost
2010-12-01 15:04:03.088 Closing DB connection named 'DBManager0'
2010-12-01 15:04:03.089 Connected to database 'mythconverg' at host: localhost
2010-12-01 15:04:03.092 Current locale en_US
2010-12-01 15:04:03.092 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2010-12-01 15:04:03.317 ScreenSaverX11Private: XScreenSaver support enabled
2010-12-01 15:04:03.317 ScreenSaverX11Private: Gnome screen saver support enabled
2010-12-01 15:04:03.319 DPMS is disabled.
2010-12-01 15:04:03.344 Desktop video mode: 800x600 60.317 Hz
2010-12-01 15:04:03.375 Enabled verbose msgs:  important general audio
2010-12-01 15:04:03.382 Loading en_us translation for module mythfrontend
2010-12-01 15:04:03.399 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2010-12-01 15:04:03.399 JoystickMenuThread: Joystick disabled - Failed to read /home/mythuser/.mythtv/joystickmenurc
2010-12-01 15:04:03.471 Using Frameless Window
2010-12-01 15:04:03.471 Using Full Screen Window
2010-12-01 15:04:03.567 Using the Qt painter
2010-12-01 15:04:03.915 MythFontProperties, Warning: Attempting to define 'small'
            with face 'DejaVu Sans', but it already exists with face 'Arial'
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1006
            Name: 'small'    Type: 'fontdef'
2010-12-01 15:04:03.934 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1012
            Name: 'medium'    Type: 'fontdef'
2010-12-01 15:04:03.952 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1018
            Name: 'large'    Type: 'fontdef'
2010-12-01 15:04:03.960 MythFontProperties, Error: Failed to load 'Thorndale', got 'DejaVu Sans' instead
            Location: /usr/share/mythtv/themes/MythCenter/base.xml @ 1024
            Name: 'clock'    Type: 'fontdef'
2010-12-01 15:04:04.006 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-01 15:04:04.212 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2010-12-01 15:04:04.212 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2010-12-01 15:04:04.213 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/blootube-wide/themeinfo.xml
2010-12-01 15:04:04.213 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/blootube-wide) is missing a themeinfo.xml file.
2010-12-01 15:04:04.216 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2010-12-01 15:04:04.216 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2010-12-01 15:04:04.423 Pulse: PulseAudio not running
2010-12-01 15:04:04.444 AO: Sample rate 48000 is supported
2010-12-01 15:04:04.444 AO: 2 channel(s) are supported
2010-12-01 15:04:04.494 AO: AC3 or DTS capable
2010-12-01 15:04:04.494 AO: 6 channel(s) are supported
2010-12-01 15:04:04.496 AO: Killing AudioOutputDSP
2010-12-01 15:04:04.497 Found ALSA:iec958:CARD=Live,DEV=0 (ALSA:iec958:CARD=Live,DEV=0
Device supports up to 5.1 (digital output, AC3,DTS,))
2010-12-01 15:04:04.719 Registering Internal as a media playback plugin.
2010-12-01 15:04:04.767 Loading en_us translation for module mytharchive
2010-12-01 15:04:04.780 Registering WebBrowser as a media playback plugin.
2010-12-01 15:04:04.780 Loading en_us translation for module mythbrowser
2010-12-01 15:04:04.842 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-01 15:04:04.843 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-01 15:04:04.843 MediaMonitorUnix::AddDevice() - empty device path.
2010-12-01 15:04:04.844 MonitorRegisterExtensions(0x100, gif,jpg,png)
2010-12-01 15:04:04.845 Loading en_us translation for module mythgallery
2010-12-01 15:04:04.866 Loading en_us translation for module mythgame
2010-12-01 15:04:04.918 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-12-01 15:04:05.001 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-12-01 15:04:05.012 Loading en_us translation for module mythmusic
2010-12-01 15:04:05.021 Loading en_us translation for module mythnetvision
2010-12-01 15:04:05.034 Loading en_us translation for module mythnews
2010-12-01 15:04:05.050 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2010-12-01 15:04:05.087 Loading en_us translation for module mythvideo
2010-12-01 15:04:05.109 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/maps/radar/regions/us_rainfall_est_, 1
2010-12-01 15:04:05.109 SourceManager: NeedSourceFor: Unable to find source for 6, http://image.weather.com/web/forecast/us_ec_9regwxhi1_large_usen, 1
2010-12-01 15:04:05.109 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/us_ec_9regradar_plus_us, 1
2010-12-01 15:04:05.110 SourceManager: NeedSourceFor: Unable to find source for 5, http://images.weather.com/looper/archive/atl_oce_sat_720x486/, 1
2010-12-01 15:04:05.111 Starting update of NWS-XML
2010-12-01 15:04:05.111 NWS-XML recently updated, skipping.
2010-12-01 15:04:05.112 Starting update of NDFD-6_day
2010-12-01 15:04:05.113 NDFD-6_day recently updated, skipping.
2010-12-01 15:04:05.114 Loading en_us translation for module mythweather
2010-12-01 15:04:05.488 Found mainmenu.xml for theme 'MythCenter'
2010-12-01 15:04:05.568 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2010-12-01 15:04:05.569 Using protocol version 63
2010-12-01 15:04:28.775 New DB connection, total: 2
2010-12-01 15:04:28.776 Connected to database 'mythconverg' at host: localhost
2010-12-01 15:05:30.881 TV: Attempting to change from None to WatchingPreRecorded
2010-12-01 15:05:31.285 Pulse: PulseAudio not running
2010-12-01 15:05:31.294 AO: Sample rate 48000 is supported
2010-12-01 15:05:31.294 AO: 2 channel(s) are supported
2010-12-01 15:05:31.347 AO: AC3 or DTS capable
2010-12-01 15:05:31.348 AO: 6 channel(s) are supported
2010-12-01 15:05:31.352 AO: Killing AudioOutputDSP
2010-12-01 15:05:31.407 AFD: Opened codec 0xae03d510, id(MPEG2VIDEO) type(Video)
2010-12-01 15:05:31.407 AFD: codec AC3 has 2 channels
2010-12-01 15:05:31.407 AFD: Opened codec 0xae03de40, id(AC3) type(Audio)
2010-12-01 15:05:31.407 AFD: Audio Track #1 is A/V stream #1 and has 2 channels in the English language(6647399).
2010-12-01 15:05:31.408 AFD: Selected track 1: English AC3 2ch (A/V Stream #1)
2010-12-01 15:05:31.408 AFD: Initializing audio parms from audio track #1
2010-12-01 15:05:31.408 AFD: Audio format changed 
            from id(NONE)     -1Hz -1ch -1bps     to id( AC3)  48000Hz  2ch 16bps    
2010-12-01 15:05:31.408 AO: Killing AudioOutputDSP
2010-12-01 15:05:31.486 Pulse: PulseAudio not running
2010-12-01 15:05:31.494 AO: Sample rate 48000 is supported
2010-12-01 15:05:31.494 AO: 2 channel(s) are supported
2010-12-01 15:05:31.546 AO: AC3 or DTS capable
2010-12-01 15:05:31.547 AO: 6 channel(s) are supported
2010-12-01 15:05:31.547 AO: Killing AudioOutputDSP
2010-12-01 15:05:31.547 AO: Original codec was AC3, signed 16 bit, 48 kHz, 2 channels
2010-12-01 15:05:31.547 AO: enc(0), passthru(0), canAC3(1), canDTS(1), canLPCM(0), configured_channels(2), 2 channels supported(1)
2010-12-01 15:05:31.547 AO: Opening audio device 'iec958:CARD=Live,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2010-12-01 15:05:31.548 ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=200000, period_time=50000)
2010-12-01 15:05:31.548 ALSA: Buffer time = 200000 us
2010-12-01 15:05:31.549 ALSA: Period time = 50000 us
2010-12-01 15:05:31.549 ALSA: Buffer size = 9600 | Period size = 2400
2010-12-01 15:05:31.549 AO: Audio fragment size: 4800
2010-12-01 15:05:31.549 AO: Audio Stretch Factor: 1
2010-12-01 15:05:31.549 AO: Ending Reconfigure()
2010-12-01 15:05:31.549 AudioPlayer: Enabling Audio
2010-12-01 15:05:31.549 AO: kickoffOutputAudioLoop: pid = 17771
2010-12-01 15:05:31.550 AO: Reconfigure(): No change -> exiting
2010-12-01 15:05:31.550 AO: Using time stretch 1.3
2010-12-01 15:05:31.550 AO: OutputAudioLoop: Play Event
2010-12-01 15:05:32.467 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-12-01 15:05:32.518 OSD: Base theme size: 800x600
2010-12-01 15:05:32.518 OSD: Scaling factors: 0.9x0.72
Illegal instruction

```

---

### Post by MC_Claus on 2010-12-04
Just wanted to mention, that the latest autobuild update seems to have resolved this issue for me.

---

### Post by Chunk of Earth on 2010-12-05
> **thatguruguy said:**
> The audio framework was completely redone for myth .24, including much-improved pulseaudio support.

I see that now that I've given up on this problem and reinstalled from scratch. My audio choices are completely different now.
Just for the record, I tried applying the latest autobuild with no luck. I was also having the problem other people are reporting where X spontaneously droped me out to the gdm login screen so I tried upgrading from x-swat PPA which gave me a new X and new nVidia driver but that didn't help, either. I finally decided to cut my losses and reinstall. Now I'm on to the [next problem]("http://ubuntuforums.org/showthread.php?t=1638095").

---

### Post by Chunk of Earth on 2010-12-06
Final analysis:
After reinstalling maverick the problem was gone. I then reinstalled the database using mythconverg_restore.pl and the problem returned. All the choppy video and alsa buffer underruns and the missing choices in the audio configuration were back, so the problem is apparently in the database and the way it sets up the internal player. It would probably be a good idea to add some sanity checks to the settings table in mythconverg. Luckily, mythconverg_restore has a partial restore option which allowed me to get the irrecoverable stuff back after I wiped the db again.

---

### Post by Chunk of Earth on 2010-12-13
I can reproduce and suppress this problem at will now.
I'm not getting AC3 or DTS passthrough to my receiver so, at the risk of the wrath of jyavenard, I changed the Audio Output Device setting to "ALSA:iec958:CARD=Live,DEV=0."
That single change brought back the stuttering video and ALSA buffer underruns.
I went back to the audio settings and attempted to set the audio device back to "ALSA:default" but that was no longer a choice. That's apparently why I could never make my upgraded installation work. The only setting that works isn't a choice in the list after scanning for audio devices.
The only way I could get the setting back to ALSA:default was to edit the entry manually. This is a fresh installation. I shouldn't have problems like that. There's something squirrelly about the audio code in MythTV 0.24-fixes.
I still don't have passthrough working again and I don't have any confidence that jyavenard's much-smarter-than-me code is going to figure it all out automatically.

---

### Post by Chunk of Earth on 2011-01-08
TrackBack: Another user with the same problem --
[http://www.gossamer-threads.com/lists/mythtv/users/463105](http://www.gossamer-threads.com/lists/mythtv/users/463105)

---

### Post by Chunk of Earth on 2011-01-08
Problem has resurfaced.
While trying to correct the "motor boating" caused by playing my 44.1 KHz music into my 48 KHz audio card from MythMusic I tried several settings in an .asoundrc file combined with different settings of the audio device in Myth setup. Nothing worked so I removed the .asoundrc file and set the audio device back to ALSA:default -- no sound in any MythTV app (other apps work fine.)
Set the audio device to ALSA:hw:CARD=Live,DEV=2 and returned to the alsa buffer underruns and choppy video (same result for ALSA:iec958:CARD=Live,DEV=0 and ALSA: plughw:CARD=Live,DEV=2)
Set the audio device back to ALSA:default -- **no sound**.
Can anyone at all confirm that there is a SB Live card out there working with Maverick and MythTV 0.24? (or anything else using the EMU10K1 driver?)

---

### Post by jhfry on 2011-03-05
I just spent an hour or two working with JYA  on IRC trying to troubleshoot this exact issue.... no resolution.

I wonder if it has something to do with the older SB cards (EMU10k1)?

---

### Post by jhfry on 2011-03-05
I have done some additional research on my own.  All of my videos play fine on mplayer, so I am confident that it is something with the audio code and my card.

I ran 
```
mplayer -ao alsa:device=iec958 -ac hwac3 idch_AviaSurroundTest-AC3.avi -msglevel all=6
```

And noticed this in the output (emphisis mine):
```
Trying preferred audio driver 'alsa', options 'device=iec958'
alsa-init: requested format: 48000 Hz, 2 channels, 108
alsa-init: using ALSA 1.0.23
alsa-spdif-init: playing AC3, 2 channels
alsa-init: using device iec958
alsa-init: pcm opened in blocking mode
[AO_ALSA] Format ac3be is not supported by hardware, trying default.
[COLOR="DarkRed"][B]alsa-init: got buffersize=65536
alsa-init: got period size 1024[/B][/COLOR]
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch ac3le (2 bytes per sample)

```


Playing the same video in mythtv gives this:
```
2011-03-05 21:31:44.738 AO: Original codec was AC3, signed 16 bit, 48 kHz, 6 channels
2011-03-05 21:31:44.738 AO: enc(0), passthru(1), canAC3(1), canDTS(1), canLPCM(0), configured_channels(6), 6 channels supported(1)
2011-03-05 21:31:44.738 AO: Opening audio device 'iec958:CARD=Live,DEV=0' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2011-03-05 21:31:44.740 ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=200000, period_time=50000)
2011-03-05 21:31:44.740 ALSA: Buffer time = 200000 us
2011-03-05 21:31:44.740 ALSA: Period time = 50000 us
2011-03-05 21:31:44.740 ALSA: [COLOR="DarkRed"]**Buffer size = 9600 | Period size = 2400**[/COLOR]
2011-03-05 21:31:44.740 AO: Audio fragment size: 4800
2011-03-05 21:31:44.741 AO: Audio Stretch Factor: 1
2011-03-05 21:31:44.741 AO: Ending Reconfigure()
```

It appears that perhaps mythtv is calculating much too small a buffer size?  I read through this thread ([http://www.gossamer-threads.com/lists/mythtv/users/464964](http://www.gossamer-threads.com/lists/mythtv/users/464964)), and it appears that a similar issue existed on another device.  To put it in JYA's own words:

> Interesting...

We asked for a 200ms length buffer, yet ALSA gives us 110ms.

To get 200ms of audio, we need:
48000 * 2 (channels) * 2 (bytes per channel) * .2 = 38400 bytes = 37kB.

So a 64kB buffer should be plenty.

I had made some assumptions on how ALSA worked, seems it's not the
case for everyone.. bugger..

JY 

Now if I can only figure out how to force an alsa buffer size on mythtv.

---

### Post by dfacto on 2011-03-06
I too have an SB Live card with Maverick and MythTV 0.24 (updated with autobuilds) and am having this problem.  I actually gave up on trying to fix this problem since I could not previously corroborate this issue.

---

### Post by jhfry on 2011-03-06
I have spent several hours working with JYA on this issue and he was able to resolve it and now I get flawless playback on my EMU10k1 card with SPDIF and AC3/DTS passthrough.

The issue was indeed related to ALSA buffer sizes (if I understood it all correctly), so he worked some magic and has it all working.

If you are following JYA's repos, it should be in tonights build.  Once he has tested it further and confirmed the fix with others he says he will backport it to 0.24-fixes in the near future.

Thank you JYA!!!

---

### Post by jyavenard on 2011-03-08
Note that I have committed those changes to fixes/0.24 now so make sure you upgrade to very recent (e.g. made in the past 12 hours) version of mythtv.

---

### Post by jyavenard on 2011-03-08
> **Chunk of Earth said:**
> I changed the Audio Output Device setting to "ALSA:iec958:CARD=Live,DEV=0."


if you want passthrough to properly work; this is the device you must use (or hdmi something). Using a device like "default" will never 100% work: it's just a matter of luck if it does.

> 
That single change brought back the stuttering video and ALSA buffer underruns.
I went back to the audio settings and attempted to set the audio device back to "ALSA:default" but that was no longer a choice. That's apparently why I could never make my upgraded installation work. The only setting that works isn't a choice in the list after scanning for audio devices.

Myth will show ALSA:default if when you run aplay -L, the device "default" exists. The code scanning for audio devices is virtually identical to what aplay does when listing audio devices.

> The only way I could get the setting back to ALSA:default was to edit the entry manually. This is a fresh installation. I shouldn't have problems like that. There's something squirrelly about the audio code in MythTV 0.24-fixes.
I still don't have passthrough working again and I don't have any confidence that jyavenard's much-smarter-than-me code is going to figure it all out automatically.

It seems that with Live audio card; the 200ms of buffer allocated by default in mythtv isn't sufficient.
Unfortunately, those cards only have 64kB of hardware buffer; which for playing AC3 or DTS passthrough only gives you about 300ms.
Unfortunately, there are bugs in the current alsa-lib; where not all card can be configured to use 300ms.
So I've upped the buffer size to 500ms : if 500ms can't be allocated,  it will reserve as much as it can, but in the logs you will now always get a message that underruns are likely.

Hopefully upgrading mythtv to a package built in the past 12 hours will fix your problem permanently.

Make sure you edit your audio config and select ALSA:iec958 from the list, do not use ALSA:default

---

### Post by Kheops_74 on 2011-09-07
I have this problem and it was suppose to be fix. where i must go to increase the buffer you are talking about?

---

