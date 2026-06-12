---
title: "Screen freezes after video playback"
date: 2012-05-15
forum: Mythbuntu
---

### Post by zuixro on 2012-05-15
I'm running .25-fixes. When I finish watching a video, the screen freezes on the last frame. I've found several things that will clear it; killing mythfrontend.real over ssh, Hitting Ctrl+Alt+F1 to drop to a shell, then Ctrl+alt+F7 to get back, or (strangely enough) changing the channel on the TV, then changing back. I can still control it with the last frame, I can use the remote to blindly select and start another video, and it will play it just fine. I think it's something with the video driver, but it only happens with MythTV, XBMC videos play and exit normally. 

I copied the log while a video was playing, then diffed it with a copy of the log right after a video finished playing (screen still frozen) and here's what I got: 
```
> May 15 14:45:54 saffron mythfrontend[3184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(0): Waited 101ms for video buffers UUUAAAAUAAUAUAAAAuAAAAUUAAALUuAP
> May 15 14:45:55 saffron mythfrontend[3184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(0): Waited 101ms for video buffers UuAALAUUAAAAAAUAAUAAAAAUAAAUULUP
> May 15 14:45:56 saffron mythfrontend[3184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(0): Waited 102ms for video buffers UuAAAAAUALUAAUUAAUAAAAAAAAUUALUP
> May 15 14:45:57 saffron mythfrontend[3184]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Input/output error (5)
> May 15 14:45:57 saffron mythfrontend[3184]: I CoreContext mythplayer.cpp:3362 (SetWatched) Player(0): Marking recording as watched using offset 4 minutes
> May 15 14:45:57 saffron mythfrontend[3184]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingPreRecorded to None
> May 15 14:45:58 saffron mythfrontend[3184]: I CoreContext mythpainter_ogl.cpp:62 (ClearCache) Clearing OpenGL painter cache.
> May 15 14:45:58 saffron mythfrontend[3184]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
> May 15 14:45:58 saffron mythfrontend[3184]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
> May 15 14:45:58 saffron mythfrontend[3184]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingPreRecorded to None
> May 15 14:45:58 saffron mythfrontend[3184]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
> May 15 14:45:58 saffron mythfrontend[3184]: I CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private: DPMS Reactivated 1
> May 15 14:45:58 saffron mythfrontend[3184]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
```

There was nothing added to the log after I cleared the screen. 

My video card is a Radeon HD4200. I've removed and reinstalled the drivers. Didn't help. I've also removed both mythfrontend, and backend, and reinstalled. Didn't help.

I've been using MythTV for over 2 years, and Ubuntu since 6.10, but this has me stumped.

I'm not sure if it's related, but sometimes get segfaults when I try to start the frontend. My icon almost never works, and running it from terminal usually gets me two or three segfaults before the frontend will start. I'll get logs from those when I can. That just started recently (like within the last week), the other problem has been here for about a month.

---

### Post by zuixro on 2012-05-15
Oh look, went to start the front end just now and got a segfault:
```
> May 15 14:53:47 saffron mythfrontend[3812]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-84-g9ccfac1] www.mythtv.org
> May 15 14:53:47 saffron mythfrontend[3812]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
> May 15 14:53:47 saffron mythfrontend[3812]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
> May 15 14:53:47 saffron mythfrontend[3812]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
> May 15 14:53:47 saffron mythfrontend[3812]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
> May 15 14:53:47 saffron mythfrontend[3812]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
> May 15 14:53:47 saffron mythfrontend[3812]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
> May 15 14:53:47 saffron mythfrontend[3812]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
> May 15 14:53:47 saffron mythfrontend[3812]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
> May 15 14:53:47 saffron mythfrontend[3812]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/saffron/.mythtv
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
> May 15 14:53:47 saffron mythfrontend[3812]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of saffron
> May 15 14:53:47 saffron mythfrontend[3812]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
> May 15 14:53:47 saffron mythfrontend[3812]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
> May 15 14:53:47 saffron mythfrontend[3812]: I SystemManager system-unix.cpp:263 (run) Starting process manager
> May 15 14:53:47 saffron mythfrontend[3812]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
> May 15 14:53:47 saffron mythfrontend[3812]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
> May 15 14:53:47 saffron mythfrontend[3812]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
> May 15 14:53:47 saffron mythfrontend[3812]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6547
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.151:6547
> May 15 14:53:47 saffron mythfrontend[3812]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6547
> May 15 14:53:48 saffron mythfrontend[3812]: E CoreContext mythraopconnection.cpp:1276 (LoadKey) RAOP Conn: Failed to read key from: /home/saffron/.mythtv/RAOPKey.rsa
> May 15 14:53:48 saffron mythfrontend[3812]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
> May 15 14:53:48 saffron mythfrontend[3812]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
> May 15 14:53:48 saffron mythfrontend[3812]: E CoreContext lirc.cpp:208 (Init) LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
> May 15 14:53:48 saffron mythfrontend[3812]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/saffron/.mythtv/joystickmenurc
```

And another right after that failed in a different place:
```
< May 15 14:56:18 saffron mythfrontend[3853]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-84-g9ccfac1] www.mythtv.org
< May 15 14:56:18 saffron mythfrontend[3853]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.1, runtime: 4.8.1
< May 15 14:56:18 saffron mythfrontend[3853]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
< May 15 14:56:18 saffron mythfrontend[3853]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
< May 15 14:56:18 saffron mythfrontend[3853]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
< May 15 14:56:18 saffron mythfrontend[3853]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
< May 15 14:56:18 saffron mythfrontend[3853]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
< May 15 14:56:18 saffron mythfrontend[3853]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
< May 15 14:56:18 saffron mythfrontend[3853]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
< May 15 14:56:18 saffron mythfrontend[3853]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/saffron/.mythtv
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
< May 15 14:56:18 saffron mythfrontend[3853]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of saffron
< May 15 14:56:18 saffron mythfrontend[3853]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
< May 15 14:56:18 saffron mythfrontend[3853]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
< May 15 14:56:18 saffron mythfrontend[3853]: I SystemManager system-unix.cpp:263 (run) Starting process manager
< May 15 14:56:18 saffron mythfrontend[3853]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
< May 15 14:56:18 saffron mythfrontend[3853]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
< May 15 14:56:18 saffron mythfrontend[3853]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is active.
< May 15 14:56:18 saffron mythfrontend[3853]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 127.0.0.1:6547
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP 192.168.1.151:6547
< May 15 14:56:18 saffron mythfrontend[3853]: I CoreContext serverpool.cpp:337 (listen) Listening on TCP [::1]:6547
```

---

### Post by simply seth on 2012-05-20
version 0.25 with fixes repo

I get  high I/O  (high amount of writes to storage) ,  and LiveTV quits  and the  frontend log file says:



```

May 20 18:26:17 htpc mythfrontend[9184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(7): Waited 19564ms for video buffers AUAAUULAAUAAUAAAAAAAAUAUuUUAuAAP
May 20 18:26:17 htpc mythfrontend[9184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(7): Waited 19667ms for video buffers AUAAUULAAUAAUAAAAAAAAUAUuUUAuAAP
May 20 18:26:17 htpc mythfrontend[9184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(7): Waited 19771ms for video buffers AUAAUULAAUAAUAAAAAAAAUAUuUUAuAAP
May 20 18:26:17 htpc mythfrontend[9184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(7): Waited 19874ms for video buffers AUAAUULAAUAAUAAAAAAAAUAUuUUAuAAP
May 20 18:26:17 htpc mythfrontend[9184]: N CoreContext mythplayer.cpp:2079 (PrebufferEnoughFrames) Player(7): Waited 19978ms for video buffers AUAAUULAAUAAUAAAAAAAAUAUuUUAuAAP
May 20 18:26:17 htpc mythfrontend[9184]: E CoreContext mythplayer.cpp:2102 (PrebufferEnoughFrames) Player(7): Waited too long for decoder to fill video buffers. Exiting..
May 20 18:26:17 htpc mythfrontend[9184]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
May 20 18:26:17 htpc mythfrontend[9184]: W CoreContext mythplayer.cpp:2959 (PauseDecoder) Player(7): Waited 100ms for decoder to pause
May 20 18:26:32  mythfrontend[9184]: last message repeated 99 times
May 20 18:26:32 htpc mythfrontend[9184]: E CoreContext mythplayer.cpp:3018 (DecoderEnd) Player(7): Failed to stop decoder loop.
May 20 18:28:20 htpc mythfrontend[9184]: I Decoder avformatdecoder.cpp:4201 (ProcessAudioPacket) AFD: Audio stream changed
May 20 18:28:20 htpc mythfrontend[9184]: E Decoder audio/audiooutputalsa.cpp:172 (GetPCMInfo) ALSA: snd_pcm_info_get_card: Operation not permitted
May 20 18:28:20 htpc mythfrontend[9184]: I Decoder audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
May 20 18:28:20 htpc mythfrontend[9184]: E Decoder audio/audiooutputalsa.cpp:975 (OpenMixer) ALSA: no playback control PCM found on mixer device default

```

---

