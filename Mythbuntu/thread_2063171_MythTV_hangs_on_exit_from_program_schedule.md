---
title: "MythTV hangs on exit from program schedule"
date: 2012-09-26
forum: Mythbuntu
---

### Post by nhtrader on 2012-09-26
MythTV v.25.2-15
ubuntu 12.04
MythBox is both FE & BE

I use MythTV FE, I select Watch TV; see TV channel listings plus I see a mini-screen (upper right) with a TV show. I can select shows to record (keystrokes respond). I can watch a show. I can change channels. But I can't exit. 

When I exit using the ESC key, the display shows me a full screen freeze frame of show that was in the upper right mini-screen. At this point the system is frozen. No other keystroke combinations work.

I'm forced to turn off the system and turn it back on.

Why is this happening?

I can add that if I were to enter FE and use the Media Library (recordings or videos), MythTV works as expected. All keystrokes work fine. Why is TV the only section crashing the system?

---

### Post by nickrout on 2012-09-26
The first thing you need to do is look at your frontend logs.

---

### Post by nhtrader on 2012-09-26
> **nickrout said:**
> The first thing you need to do is look at your frontend logs.

Here's the contents of the frontend log.
BTW, I deleted the frontend log and then re-entered MythTV and "WatchTV". Then I exited using ESC. This is the entire log which is rather small.

```

Sep 26 16:59:22 kub3 mythfrontend[2839]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25.2-15-g46cab93] www.mythtv.org
Sep 26 16:59:22 kub3 mythfrontend[2839]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
Sep 26 16:59:22 kub3 mythfrontend[2839]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Sep 26 16:59:22 kub3 mythfrontend[2839]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Sep 26 16:59:22 kub3 mythfrontend[2839]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Sep 26 16:59:22 kub3 mythfrontend[2839]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Sep 26 16:59:22 kub3 mythfrontend[2839]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Sep 26 16:59:22 kub3 mythfrontend[2839]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Sep 26 16:59:22 kub3 mythfrontend[2839]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Sep 26 16:59:22 kub3 mythfrontend[2839]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/dad/.mythtv
Sep 26 16:59:22 kub3 mythfrontend[2839]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Sep 26 16:59:22 kub3 mythfrontend[2839]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Sep 26 16:59:22 kub3 mythfrontend[2839]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of kub3
Sep 26 16:59:22 kub3 mythfrontend[2839]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
Sep 26 16:59:22 kub3 mythfrontend[2839]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
Sep 26 16:59:22 kub3 mythfrontend[2839]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Sep 26 16:59:22 kub3 mythfrontend[2839]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Sep 26 16:59:22 kub3 mythfrontend[2839]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Sep 26 16:59:22 kub3 mythfrontend[2839]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Sep 26 16:59:22 kub3 mythfrontend[2839]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Sep 26 16:59:23 kub3 mythfrontend[2839]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
Sep 26 16:59:23 kub3 mythfrontend[2839]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
Sep 26 16:59:23 kub3 mythfrontend[2839]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1600x900 59.946 Hz
Sep 26 16:59:23 kub3 mythfrontend[2839]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP 127.0.0.1:6547
Sep 26 16:59:23 kub3 mythfrontend[2839]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [::1]:6547
Sep 26 16:59:23 kub3 mythfrontend[2839]: I CoreContext serverpool.cpp:395 (listen) Listening on TCP [fe80::6ef0:49ff:fe73:75f3%eth0]:6547
Sep 26 16:59:24 kub3 mythfrontend[2839]: E CoreContext mythraopconnection.cpp:1276 (LoadKey) RAOP Conn: Failed to read key from: /home/dad/.mythtv/RAOPKey.rsa
Sep 26 16:59:24 kub3 mythfrontend[2839]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
Sep 26 16:59:24 kub3 mythfrontend[2839]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Sep 26 16:59:24 kub3 mythfrontend[2839]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
Sep 26 16:59:24 kub3 mythfrontend[2839]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/dad/.mythtv/joystickmenurc
Sep 26 16:59:24 kub3 mythfrontend[2839]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
Sep 26 16:59:24 kub3 mythfrontend[2839]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP 127.0.0.1:6948
Sep 26 16:59:24 kub3 mythfrontend[2839]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [::1]:6948
Sep 26 16:59:24 kub3 mythfrontend[2839]: I CoreContext serverpool.cpp:482 (bind) Binding to UDP [fe80::6ef0:49ff:fe73:75f3%eth0]:6948
Sep 26 16:59:24 kub3 mythfrontend[2839]: I CoreContext mythmainwindow.cpp:948 (Init) Using Frameless Window
Sep 26 16:59:24 kub3 mythfrontend[2839]: I CoreContext mythmainwindow.cpp:961 (Init) Using Full Screen Window
Sep 26 16:59:25 kub3 mythfrontend[2839]: I CoreContext mythmainwindow.cpp:1051 (Init) Using the Qt painter
Sep 26 16:59:25 kub3 mythfrontend[2839]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Sep 26 16:59:26 kub3 mythfrontend[2839]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Sep 26 16:59:26 kub3 mythfrontend[2839]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Sep 26 16:59:26 kub3 mythfrontend[2839]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Sep 26 16:59:26 kub3 mythfrontend[2839]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Sep 26 16:59:26 kub3 mythfrontend[2839]: N CoreContext mythmainwindow.cpp:1862 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
Sep 26 16:59:26 kub3 mythfrontend[2839]: W CoreContext mythplugin.cpp:164 (MythPluginManager) No plugins directory /usr/lib/mythtv/plugins
Sep 26 16:59:27 kub3 mythfrontend[2839]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'MythCenter-wide'
Sep 26 16:59:27 kub3 mythfrontend[2839]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Sep 26 16:59:27 kub3 mythfrontend[2839]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Sep 26 16:59:27 kub3 mythfrontend[2839]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on kub3' type '_mythfrontend._tcp.' domain: 'local.'
Sep 26 16:59:29 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
Sep 26 16:59:30 kub3 mythfrontend[2839]: N CoreContext mythmainwindow.cpp:2586 (PauseIdleTimer) Suspending idle timer
Sep 26 16:59:30 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
Sep 26 16:59:30 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
Sep 26 16:59:30 kub3 mythfrontend[2839]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
Sep 26 16:59:30 kub3 mythfrontend[2839]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
Sep 26 16:59:30 kub3 mythfrontend[2839]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
Sep 26 16:59:30 kub3 mythfrontend[2839]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
Sep 26 16:59:30 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/3071_20120926165930.mpg) cardtype(DUMMY)
Sep 26 16:59:30 kub3 mythfrontend[2839]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
Sep 26 16:59:30 kub3 mythfrontend[2839]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : ATI Technologies Inc.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: ATI Radeon HD 4200
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 3.3.11627 Compatibility Profile Context
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 8192 x 8192
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext videoout_opengl.cpp:322 (SetupContext) VidOutGL: Created MythRenderOpenGL device.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythpainter_ogl.cpp:27 (MythOpenGLPainter) OpenGL painter using existing OpenGL context.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythpainter_ogl.cpp:29 (MythOpenGLPainter) OpenGL painter using existing QGLWidget.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext mythplayer.cpp:1737 (InitAVSync) Player(0): Video timing method: USleep with busy wait
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
Sep 26 16:59:31 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext mythpainter_ogl.cpp:62 (ClearCache) Clearing OpenGL painter cache.
Sep 26 16:59:32 kub3 mythfrontend[2839]: W CoreContext mythpainter.cpp:32 (~MythPainter) MythPainter: 16 images not yet de-allocated.
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext mythpainter_ogl.cpp:27 (MythOpenGLPainter) OpenGL painter using existing OpenGL context.
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext mythpainter_ogl.cpp:29 (MythOpenGLPainter) OpenGL painter using existing QGLWidget.
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext openglvideo.cpp:230 (Init) GLVid: Using custom UYVY input textures.
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1280x720
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.290625x0.294444
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x55982e0, id(MPEG2VIDEO) type(Video)
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AC3 has 2 channels
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x5402940, id(AC3) type(Audio)
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AC3 has 1 channels
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x53eb530, id(AC3) type(Audio)
Sep 26 16:59:32 kub3 mythfrontend[2839]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
Sep 26 16:59:32 kub3 mythfrontend[2839]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 192
Sep 26 16:59:32 kub3 mythfrontend[2839]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
Sep 26 16:59:32 kub3 mythfrontend[2839]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 192 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
Sep 26 16:59:32 kub3 mythfrontend[2839]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
Sep 26 16:59:32 kub3 mythfrontend[2839]: N CoreContext avformatdecoder.cpp:752 (SetEof) AFD: Resetting byte context eof (livetv 1 was eof 0)
Sep 26 16:59:32 kub3 mythfrontend[2839]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 102ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAuUuLP
Sep 26 16:59:52 kub3 mythfrontend[2839]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/var/lib/mythtv/livetv/3071_20120926165931.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 31888 < 32768
Sep 26 16:59:59 kub3 mythfrontend[2839]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/var/lib/mythtv/livetv/3071_20120926165931.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 25560 < 32768
Sep 26 17:00:03 kub3 mythfrontend[2839]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/var/lib/mythtv/livetv/3071_20120926165931.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 11760 < 32768
Sep 26 17:00:07 kub3 mythfrontend[2839]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/var/lib/mythtv/livetv/3071_20120926165931.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 3116 < 32768
Sep 26 17:00:29 kub3 mythfrontend[2839]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/var/lib/mythtv/livetv/3071_20120926165931.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 16380 < 32768
Sep 26 17:00:49 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
Sep 26 17:00:49 kub3 mythfrontend[2839]: I CoreContext mythpainter_ogl.cpp:62 (ClearCache) Clearing OpenGL painter cache.
Sep 26 17:00:49 kub3 mythfrontend[2839]: W CoreContext mythpainter.cpp:32 (~MythPainter) MythPainter: 16 images not yet de-allocated.
Sep 26 17:00:49 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
Sep 26 17:00:49 kub3 mythfrontend[2839]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
Sep 26 17:00:50 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
Sep 26 17:00:50 kub3 mythfrontend[2839]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
Sep 26 17:00:50 kub3 mythfrontend[2839]: E CoreContext mythdb.cpp:192 (DBError) DB Error (LiveTVChain::DestroyChain):#012Query was:#012DELETE FROM tvchain WHERE chainid = ? ;#012Bindings were:#012:CHAINID="live-kub3-2012-09-26T16:59:30"#012Driver error was [2/126]:#012QMYSQL3: Unable to execute statement#012Database error was:#012Incorrect key file for table './mythconverg/tvchain.MYI'; try to repair it
Sep 26 17:00:50 kub3 mythfrontend[2839]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer

```

---

### Post by nickrout on 2012-09-26
At what point in that log does the problem occur?

---

### Post by nhtrader on 2012-09-26
> **nickrout said:**
> At what point in that log does the problem occur?

It appears that the problem occurs on the second to the last line in the log.

Again, I intentionally started with a blank log file so that the log would only contain the events from a new instance of MythTV FE.

I started MythTV FE.
Then selected Watch TV which displayed the Program Schedule page.
Then pressed ESC to exit
Then program schedule page exited to a TV show (the one in the mini-screen)
Then pressed ESC to exit to the main menu - hangs/frozen/crashed.

---

### Post by nickrout on 2012-09-26
1. Your version of mythtv is several commits behind. Update (I assume with that version you are on mythbuntu-repos already, so you know what to do).

2. When I hit "Watch TV" it goes straight to a channel - usually the last one watched. I am not sure why yours goes to the EPG. I guess there must be a setting somewhere. (Ahh yes there it is, Under Program Guide in Video Settings) - perhaps if it is causing a problem you should switch that setting off.

---

### Post by nickrout on 2012-09-27
PS it is unclear to me whether your bug relates to the EPG and it's interaction with LiveTV, or whether it is LiveTV in general.

---

