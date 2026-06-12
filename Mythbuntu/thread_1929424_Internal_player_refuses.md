---
title: "Internal player refuses"
date: 2012-02-22
forum: Mythbuntu
---

### Post by Endertainer on 2012-02-22
Hi there,

last week i updated my mythbuntu Box to 12.04 und mythbuntu to 0.25 ....
And i got following problem:

It seems to do all the recordings etc...but I cant watch anything which needs the internal player...No recs, no vids, no photos....

All I got is a "please wait" on the screen.

Here are some logs from a try...at this try mythfrontend crashes and restarts. It looks like a buffer-problem.

Anyone an idea? I update every day and hope the problem is gone.



> Feb 22 07:41:58 Wohnzimmer mythfrontend[2674]: TV: Creating TV object
Feb 22 07:41:58 Wohnzimmer mythfrontend[2674]: TV: Created TvPlayWindow.
Feb 22 07:41:58 Wohnzimmer mythfrontend[2674]: TV: Attempting to change from None to WatchingPreRecorded
Feb 22 07:41:58 Wohnzimmer mythfrontend[2674]: Using protocol version 72

==> mythbackend.log <==
Feb 22 07:41:58 Wohnzimmer mythbackend[1320]: MainServer::ANN Playback
Feb 22 07:41:58 Wohnzimmer mythbackend[1320]: adding: wohnzimmer as a client (events: 0)
Feb 22 07:41:58 Wohnzimmer mythbackend[1320]: MainServer::HandleAnnounce FileTransfer
Feb 22 07:41:58 Wohnzimmer mythbackend[1320]: adding: wohnzimmer as a remote file transfer

==> mythfrontend.log <==
Feb 22 07:41:58 Wohnzimmer mythfrontend[2674]: Using protocol version 72
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: AudioPlayer: Enabling Audio
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: AO: Resampling from 48 kHz to 44 kHz with quality medium
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: AO: Opening audio device 'PulseAudio:default' ch 2(2) sr 44100 sf 32 bit floating point reenc 0
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Enabling buffering optimisations for low bitrate stream.
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Enabling buffering optimisations for low bitrate stream.
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: VideoOutputXv: XVideo Adaptor Name: 'AMD Radeon AVIVO Video'
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: OSD: Base theme size: 1280x720
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: OSD: Scaling factors: 0.5625x0.8
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: OSD: Base theme size: 1280x720
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: OSD: Scaling factors: 0.5625x0.8
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Player(0): Video timing method: USleep with busy wait
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: TV: Created player.
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: TV: Changing from None to WatchingPreRecorded
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: TV: Main UI disabled.
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: TV: Entering main playback loop.
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: ScreenSaverX11Private: DPMS Deactivated 1
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Player(0): Waited 102ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Player(0): Waited 205ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Player(0): Waited 309ms for video buffers uAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:41:59 Wohnzimmer mythfrontend[2674]: Player(0): Waited 412ms for video buffers uAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 14969 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 516ms for video buffers uAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 17017 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 19065 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 21113 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 619ms for video buffers uAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 23161 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 25209 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 723ms for video buffers uAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 27257 < 28838
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 827ms for video buffers uuAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 930ms for video buffers uuAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1034ms for video buffers uuAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 14395 < 15539
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1138ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1241ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1345ms for video buffers UuuAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:00 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1448ms for video buffers UUuuAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1552ms for video buffers UUuuAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1655ms for video buffers UUuuAAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1759ms for video buffers UUUuuAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1863ms for video buffers UUUuuAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 1966ms for video buffers UUUuuAAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2070ms for video buffers UUUUuuAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2173ms for video buffers UUUUuuAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 14638 < 14961
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2276ms for video buffers UUUUuuAAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:01 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2381ms for video buffers UUUUUuuAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2484ms for video buffers UUUUUuuAAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2588ms for video buffers UUUUUUuuAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2691ms for video buffers UUUUUUuuAAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2795ms for video buffers UUUUUUUuuAAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 2899ms for video buffers UUUUUUUUuLAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 3003ms for video buffers UUUUUUUUuuAAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 3109ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 3212ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 14753 < 17964
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: Player(0): Waited 3316ms for video buffers UUUUUUUUUuuAAAAAAAAAAAAAAAAAAAAP
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 16801 < 17964
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: VideoOutput: Created YV12 OSD.
Feb 22 07:42:02 Wohnzimmer mythfrontend[2674]: PulseAudio: stream buffer under flow
Feb 22 07:42:04  mythfrontend[2674]: last message repeated 6 times
Feb 22 07:42:04 Wohnzimmer mythfrontend[2674]: Player(0): Waited 102ms for video buffers AAAAAAAAAAAUUUUUUUUUuuAAAAAAAAAP
Feb 22 07:42:04 Wohnzimmer mythfrontend[2674]: Player(0): Waited 103ms for video buffers AAAAAAAAAAAAUUUUUUUUUuuAAAAAAAAP
Feb 22 07:42:04 Wohnzimmer mythfrontend[2674]: Player(0): Waited 104ms for video buffers AAAAAAAAAAAAAUUUUUUUUUuuAAAAAAAP
Feb 22 07:42:05 Wohnzimmer mythfrontend[2674]: Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAUUUUUUUUUuuAAAAAAP
Feb 22 07:42:05 Wohnzimmer mythfrontend[2674]: Player(0): Waited 104ms for video buffers AAAAAAAAAAAAAAAUUUUUUUUUuuAAAAAP
Feb 22 07:42:05 Wohnzimmer mythfrontend[2674]: Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAAAUUUUUUUUUuuAAAAP
Feb 22 07:42:05 Wohnzimmer mythfrontend[2674]: Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAAAAUUUUUUUUUuuAAAP
Feb 22 07:42:05 Wohnzimmer mythfrontend[2674]: Player(0): Waited 103ms for video buffers AAAAAAAAAAAAAAAAAAUUUUUUUUUuuAAP
Feb 22 07:42:05 Wohnzimmer mythfrontend[2674]: Player(0): Waited 104ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: Player(0): Waited 208ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 14536 < 67338
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 16584 < 67338
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: Player(0): Waited 312ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 18632 < 67338
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 20680 < 67338
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: Player(0): Waited 416ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 22728 < 67338
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: RingBuf(myth://127.0.0.1:6543/18504_20111231104700.nuv): Waited 0.2 seconds for data #012#011#011#011to become available... 24776 < 67338
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: Player(0): Waited 520ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: Player(0): Waited 624ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: Player(0): Waited 728ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuAP
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: TV: Attempting to change from WatchingPreRecorded to None
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: TV: Changing from WatchingPreRecorded to None
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: TV: Exiting main playback loop.
Feb 22 07:42:06 Wohnzimmer mythfrontend[2674]: ScreenSaverX11Private: DPMS Reactivated 1
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: mythfrontend version: master [v0.25pre-4653-g765b8e4] [www.mythtv.org]("http://www.mythtv.org")
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Enabled verbose msgs:  general
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Setting Log Level to LOG_INFO
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Added logging to the console
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Added syslogging to facility local7
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Added database logging to table logging
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Setting up SIGHUP handler
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Using runtime prefix = /usr
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Using configuration directory = /home/aysal/.mythtv
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Empty LocalHostName.
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Using localhost value of Wohnzimmer
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Database connection created: DBManager0
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: New DB connection, total: 1
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Connected to database 'mythconverg' at host: localhost
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Closing DB connection named 'DBManager0'
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Database connection created: DBManager1
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: New DB connection, total: 1
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Connected to database 'mythconverg' at host: localhost
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Current locale de_DE
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Reading locale defaults from /usr/share/mythtv//locales/de_de.xml
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Starting process manager
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Starting process signal handler
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Starting IO manager (write)
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Starting IO manager (read)
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Database connection created: DBManager2
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: New DB connection, total: 2
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Connected to database 'mythconverg' at host: localhost
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: ScreenSaverX11Private: DPMS is active.
Feb 22 07:42:07 Wohnzimmer mythfrontend[2722]: Desktop video mode: 1920x1080 60.000 Hz
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: Listening on TCP 127.0.0.1:6547
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: Listening on TCP [::1]:6547
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: RAOP Conn: Failed to read key from: /home/aysal/.mythtv/RAOPKey.rsa
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: RAOP Device: Aborting startup - no key found.
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythfrontend
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: LIRC: Failed to connect to Unix socket '/dev/lircd'#012#011#011#011eno: No such file or directory (2)
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: JoystickMenuThread: Joystick disabled - Failed to read /home/aysal/.mythtv/joystickmenurc
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: Binding to UDP 127.0.0.1:6948
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: Binding to UDP [::1]:6948
Feb 22 07:42:08 Wohnzimmer mythfrontend[2722]: Binding to UDP 255.255.255.255:6948
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: Using Frameless Window
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: Using Full Screen Window
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: Trying the OpenGL painter
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: Could not determine whether Sync to VBlank is enabled.
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL1: Fragment program support available
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: OpenGL vendor  : ATI Technologies Inc.
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: OpenGL renderer: ATI Radeon HD 4300/4500 Series       
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: OpenGL version : 3.3.11251 Compatibility Profile Context
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: Max texture size: 8192 x 8192
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: Max texture units: 8
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: Direct rendering: Yes
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: PixelBufferObject support available
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: OpenGL: Initialised MythRenderOpenGL
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: Current MythTV Schema Version (DBSchemaVer): 1298
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: Database connection created: DBManager3
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: New DB connection, total: 3
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: Connected to database 'mythconverg' at host: localhost
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
Feb 22 07:42:09 Wohnzimmer mythfrontend[2722]: ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Registering Internal as a media playback plugin.
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mytharchive
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Registering WebBrowser as a media playback plugin.
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythbrowser
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythgallery
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythgame
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Current MythMusic Schema Version (MusicDBSchemaVer): 1019
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythmusic
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythnetvision
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythnews
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Loading de translation for module mythweather
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Listening on TCP 127.0.0.1:6546
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Listening on TCP [::1]:6546
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Found mainmenu.xml for theme 'MythCenter-wide'
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Found a handler for MEDIATYPE_DATA - 'MythGallery Media Handler 1/2'
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Database connection created: DBManager4
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: New DB connection, total: 4
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Connected to database 'mythconverg' at host: localhost
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Using protocol version 72
Feb 22 07:42:10 Wohnzimmer mythfrontend[2722]: Bonjour: Service registration complete: name 'Mythfrontend on Wohnzimmer' type '_mythfrontend._tcp.' domain: 'local.'

==> mythbackend.log <==
Feb 22 07:42:10 Wohnzimmer mythbackend[1320]: MainServer::ANN Monitor
Feb 22 07:42:10 Wohnzimmer mythbackend[1320]: adding: Wohnzimmer as a client (events: 0)
Feb 22 07:42:10 Wohnzimmer mythbackend[1320]: MainServer::ANN Monitor
Feb 22 07:42:10 Wohnzimmer mythbackend[1320]: adding: Wohnzimmer as a client (events: 1)

==> mythfrontend.log <==
Feb 22 07:42:11 Wohnzimmer mythfrontend[2722]: Failed to mount /dev/sr0.


---

### Post by Jack Brown on 2012-02-22
I'm not a mythbuntu user,

but by 12.04 you mean using ubuntu  precise pangolin?   If so, you would definitely expect bugs, as it's still in Alpha.

you could now contribute by filing bugs of course.

to get back to reliable operation that you're used to, probably better to go back to your previous version.

---

### Post by nickrout on 2012-02-22
> **Jack Brown said:**
> I'm not a mythbuntu user,

but by 12.04 you mean using ubuntu  precise pangolin?   If so, you would definitely expect bugs, as it's still in Alpha.



so is mythtv-0.25 - actually 0.25 is not even released so you are running master. Experimental code which is likely to break. You need to subscribe to mythtv-dev and mythtv-commits AND READ THEM!!

You are a tester, and all power to you for undertaking that unenviable task, but don't expect a stable system!

---

