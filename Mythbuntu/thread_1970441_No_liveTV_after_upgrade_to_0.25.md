---
title: "No liveTV after upgrade to 0.25"
date: 2012-05-01
forum: Mythbuntu
---

### Post by Chewiesw on 2012-05-01
Hello
Signal 0% (_L) Partial Lock
Recently upgraded from  11.04 0.24 fixes to 0.25. Live TV no longer works all I get is a black screen and then eventually a prompt that there isn’t a signal and I have to pres OK.  I have increased the timeout and I have also tried to start the mythfrontend  with

mythfrontend -O ThemePainter=qt
mythfrontend -O ThemePainter=opengl
mythfrontend -O ThemePainter=mythbuntu

all with the same black screen.
Coincidently is doesn’t seem like the blaster is working either. I use a STB to get my signal /channels and that is working fine. Mythvideo is working perfectly.

C

---

### Post by nickrout on 2012-05-01
> **Chewiesw said:**
> Hello
Signal 0% (_L) Partial Lock
Recently upgraded from  11.04 0.24 fixes to 0.25. Live TV no longer works all I get is a black screen and then eventually a prompt that there isn’t a signal and I have to pres OK.  I have increased the timeout and I have also tried to start the mythfrontend  with

mythfrontend -O ThemePainter=qt
mythfrontend -O ThemePainter=opengl
mythfrontend -O ThemePainter=mythbuntu

all with the same black screen.
Coincidently is doesn’t seem like the blaster is working either. I use a STB to get my signal /channels and that is working fine. Mythvideo is working perfectly.

C

Is recording working?

What do your logs say?

---

### Post by Chewiesw on 2012-05-02
recording doesn't seem to work when I select a program via mythweb, I am trying again after having selected a program from the front end.
```
2.=== Mythfrontend Log ===
3. 
4.=== Mythfrontend Log ===
5.=== /var/log/mythtv/mythfrontend.log ===
6.May  1 10:05:52 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
7.May  1 10:05:52 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
8.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
9.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
10.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
11.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
12.May  1 10:08:45 hdpvr mythfrontend[3898]: E CoreContext xmlparsebase.cpp:542 (ParseUIType) XMLParseBase: Type of new widget 'background' doesn't match old 'base_background_shape'#012#011#011#011Location: /usr/share/mythtv/themes/blue/settings-ui.xml @ 225#012#011#011#011Name: 'background'#011Type: 'imagetype'
13.May  1 10:08:45 hdpvr mythfrontend[3898]: W ScreenLoad themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
14.May  1 10:08:45 hdpvr mythfrontend[3898]: E ScreenLoad themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
15.May  1 10:08:45 hdpvr mythfrontend[3898]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
16.May  1 10:08:45 hdpvr mythfrontend[3898]: W ScreenLoad themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
17.May  1 10:08:45 hdpvr mythfrontend[3898]: E ScreenLoad themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
18.May  1 10:08:56 hdpvr mythfrontend[3898]: N CoreContext mythcorecontext.cpp:1283 (ReInitLocale) Setting QT default locale to EN_US
19.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
20.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
21.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
22.May  1 10:08:56 hdpvr mythfrontend[3898]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
23.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
24.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
25.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
26.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythpainter_ogl.cpp:62 (ClearCache) Clearing OpenGL painter cache.
27.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
28.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
29.May  1 10:08:56 hdpvr mythfrontend[3898]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
30.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
31.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
32.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
33.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
34.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
35.May  1 10:10:17 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
36.May  1 10:10:17 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
37.May  1 10:10:19 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
38.May  1 10:10:19 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
39.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
40.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
41.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
42.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
43.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
44.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
45.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
46.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
47.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
48.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501101106.mpg) cardtype(DUMMY)
49.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
50.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
51.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
52.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
53.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
54.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
55.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
56.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
57.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(5): Video timing method: DRM
58.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
59.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
60.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
61.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
62.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
63.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
64.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
65.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
66.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
67.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
68.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
69.May  1 10:11:09 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
70.May  1 10:11:09 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
71.May  1 10:11:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
72.May  1 10:11:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
73.May  1 10:11:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
74.May  1 10:11:21 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
75.May  1 10:17:20 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
76.May  1 10:17:20 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
77.May  1 10:17:20 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
78.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
79.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
80.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
81.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
82.May  1 10:17:21 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
83.May  1 10:17:21 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
84.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501101720.mpg) cardtype(DUMMY)
85.May  1 10:17:21 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
86.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
87.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
88.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
89.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
90.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
91.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
92.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
93.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(6): Video timing method: DRM
94.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
95.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
96.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
97.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
98.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
99.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
100.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
101.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
102.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
103.May  1 10:17:24 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
104.May  1 10:17:24 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
105.May  1 10:17:46 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
106.May  1 10:17:46 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
107.May  1 10:17:49 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
108.May  1 10:17:49 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
109.May  1 10:19:26 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
110.May  1 10:19:26 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
111.May  1 10:19:26 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
112.May  1 10:19:26 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
113.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
114.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
115.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
116.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
117.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
118.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
119.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
120.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
121.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
122.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501101928.mpg) cardtype(DUMMY)
123.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
124.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
125.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
126.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
127.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
128.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
129.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
130.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
131.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(7): Video timing method: DRM
132.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
133.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
134.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
135.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
136.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
137.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
138.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
139.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
140.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
141.May  1 10:19:32 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
142.May  1 10:19:32 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
143.May  1 10:19:42 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
144.May  1 10:19:42 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
145.May  1 10:20:25 hdpvr mythfrontend[3898]: N LIRC lirc.cpp:504 (GetCodes) LIRC: GetCodes -- eof?
146.May  1 10:21:19 hdpvr mythfrontend[3898]: I LIRC lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
147.May  1 10:21:38 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
148.May  1 10:21:38 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
149.May  1 10:21:38 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
150.May  1 10:21:38 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
151.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
152.May  1 10:21:41 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
153.May  1 10:21:41 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
154.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
155.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
156.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
157.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
158.May  1 10:21:41 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
159.May  1 10:21:42 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
160.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501102141.mpg) cardtype(DUMMY)
161.May  1 10:21:42 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
162.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
163.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
164.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
165.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
166.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
167.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
168.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
169.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(8): Video timing method: DRM
170.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
171.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
172.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
173.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
174.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
175.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
176.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
177.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
178.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
179.May  1 10:21:45 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
180.May  1 10:21:45 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
181.May  1 10:22:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
182.May  1 10:22:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
183.May  1 10:22:44 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
184.May  1 10:22:44 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
185.May  1 10:23:13 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
186.May  1 10:23:14 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
187.May  1 10:23:14 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
188.May  1 10:23:14 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
189.May  1 10:30:54 hdpvr mythfrontend[3898]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
190.May  1 10:30:54 hdpvr mythfrontend[3898]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
191.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
192.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
193.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
194.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
195.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
196.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
197.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
198.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
199.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
200.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501104424.mpg) cardtype(DUMMY)
201.May  1 10:44:25 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
202.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
203.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
204.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
205.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
206.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
207.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
208.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
209.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(6): Video timing method: DRM
210.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
211.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
212.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
213.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
214.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
215.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
216.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
217.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
218.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
219.May  1 10:44:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
220.May  1 10:44:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
221.May  1 10:44:55 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
222.May  1 10:44:55 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
223.May  1 10:44:55 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
224.May  1 10:44:55 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
225.May  1 10:47:31 hdpvr mythfrontend[3898]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
226.May  1 10:47:37 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
227.May  1 10:47:37 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
228.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
229.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
230.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
231.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
232.May  1 10:47:38 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
233.May  1 10:47:38 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
234.May  1 11:24:50 hdpvr mythfrontend[8039]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
235.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
236.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
237.May  1 11:24:50 hdpvr mythfrontend[8039]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
238.May  1 11:24:50 hdpvr mythfrontend[8039]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
239.May  1 11:24:50 hdpvr mythfrontend[8039]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
240.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
241.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
242.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
243.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
244.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
245.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
246.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
247.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
248.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
249.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemManager system-unix.cpp:263 (run) Starting process manager
250.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
251.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
252.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
253.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
254.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
255.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
256.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
257.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
258.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
259.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
260.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
261.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
262.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
263.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
264.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
265.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
266.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
267.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
268.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
269.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
270.May  1 11:24:51 hdpvr mythfrontend[8039]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
271.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
272.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
273.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT 
274.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 2.1 Mesa 7.10.2
275.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 4096 x 4096
276.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
277.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
278.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
279.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
280.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
281.May  1 11:24:52 hdpvr mythfrontend[8039]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
282.May  1 11:24:52 hdpvr mythfrontend[8039]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
283.May  1 11:24:52 hdpvr mythfrontend[8039]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
284.May  1 11:24:52 hdpvr mythfrontend[8039]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
285.May  1 11:24:52 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
286.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
287.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
288.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
289.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
290.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
291.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
292.May  1 11:24:52 hdpvr mythfrontend[8039]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
293.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
294.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
295.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
296.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
297.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
298.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
299.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
300.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
301.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
302.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
303.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
304.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
305.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501112457.mpg) cardtype(DUMMY)
306.May  1 11:24:58 hdpvr mythfrontend[8039]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
307.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
308.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
309.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
310.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
311.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
312.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
313.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
314.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
315.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
316.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
317.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
318.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
319.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
320.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
321.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
322.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
323.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
324.May  1 11:25:04 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
325.May  1 11:25:04 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
326.May  1 11:29:56 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
327.May  1 11:29:56 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
328.May  1 11:29:56 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
329.May  1 11:29:56 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
330.May  1 11:30:00 hdpvr mythfrontend[8039]: last message repeated 2 times
331.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
332.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
333.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
334.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
335.May  1 11:30:01 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
336.May  1 11:30:01 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
337.May  1 11:30:01 hdpvr mythfrontend[8039]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
338.May  1 11:38:55 hdpvr mythfrontend[8833]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
339.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
340.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
341.May  1 11:38:55 hdpvr mythfrontend[8833]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
342.May  1 11:38:55 hdpvr mythfrontend[8833]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
343.May  1 11:38:55 hdpvr mythfrontend[8833]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
344.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
345.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
346.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
347.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
348.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
349.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
350.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
351.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
352.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
353.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
354.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemManager system-unix.cpp:263 (run) Starting process manager
355.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
356.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
357.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
358.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
359.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
360.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythcommandlineparser.cpp:2566 (ApplySettingsOverride) Setting 'ThemePainter' being forced to 'qt'
361.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
362.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
363.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
364.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
365.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
366.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
367.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
368.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
369.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
370.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
371.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
372.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
373.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
374.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
375.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
376.May  1 11:38:56 hdpvr mythfrontend[8833]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
377.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
378.May  1 11:38:56 hdpvr mythfrontend[8833]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
379.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
380.May  1 11:38:56 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
381.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
382.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
383.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
384.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
385.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
386.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
387.May  1 11:38:56 hdpvr mythfrontend[8833]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
388.May  1 11:38:57 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
389.May  1 11:38:57 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
390.May  1 11:38:57 hdpvr mythfrontend[8833]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
391.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
392.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
393.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
394.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
395.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
396.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
397.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
398.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
399.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
400.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501113901.mpg) cardtype(DUMMY)
401.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
402.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
403.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
404.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
405.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
406.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
407.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
408.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
409.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
410.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
411.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
412.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
413.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
414.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
415.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
416.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
417.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
418.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
419.May  1 11:39:08 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
420.May  1 11:39:08 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
421.May  1 11:39:12 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
422.May  1 11:39:12 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
423.May  1 11:39:12 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
424.May  1 11:39:12 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
425.May  1 11:39:15 hdpvr mythfrontend[8833]: last message repeated 2 times
426.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
427.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
428.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
429.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
430.May  1 11:39:16 hdpvr mythfrontend[8833]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
431.May  1 11:40:11 hdpvr mythfrontend[8888]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
432.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
433.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
434.May  1 11:40:11 hdpvr mythfrontend[8888]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
435.May  1 11:40:11 hdpvr mythfrontend[8888]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
436.May  1 11:40:11 hdpvr mythfrontend[8888]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
437.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
438.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
439.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
440.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
441.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
442.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
443.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
444.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
445.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
446.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemManager system-unix.cpp:263 (run) Starting process manager
447.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
448.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
449.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
450.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
451.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
452.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
453.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythcommandlineparser.cpp:2566 (ApplySettingsOverride) Setting 'ThemePainter' being forced to 'opengl'
454.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
455.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
456.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
457.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
458.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
459.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
460.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
461.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
462.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
463.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
464.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
465.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
466.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
467.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
468.May  1 11:40:12 hdpvr mythfrontend[8888]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
469.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
470.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
471.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT 
472.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 2.1 Mesa 7.10.2
473.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 4096 x 4096
474.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
475.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
476.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
477.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
478.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
479.May  1 11:40:13 hdpvr mythfrontend[8888]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
480.May  1 11:40:13 hdpvr mythfrontend[8888]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
481.May  1 11:40:13 hdpvr mythfrontend[8888]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
482.May  1 11:40:13 hdpvr mythfrontend[8888]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
483.May  1 11:40:13 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
484.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
485.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
486.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
487.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
488.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
489.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
490.May  1 11:40:13 hdpvr mythfrontend[8888]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
491.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
492.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
493.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
494.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
495.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
496.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
497.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
498.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
499.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
500.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
501.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
502.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
503.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501114017.mpg) cardtype(DUMMY)
504.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
505.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
506.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
507.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
508.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
509.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
510.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
511.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
512.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
513.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
514.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
515.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
516.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
517.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
518.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
519.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
520.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
521.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
522.May  1 11:40:23 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
523.May  1 11:40:23 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
524.May  1 11:40:40 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
525.May  1 11:40:40 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
526.May  1 11:40:40 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
527.May  1 11:40:40 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
528.May  1 11:40:43 hdpvr mythfrontend[8888]: last message repeated 2 times
529.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
530.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
531.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
532.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
533.May  1 11:40:44 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
534.May  1 11:40:44 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
535.May  1 11:40:44 hdpvr mythfrontend[8888]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
536.May  1 11:41:14 hdpvr mythfrontend[8934]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
537.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
538.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
539.May  1 11:41:14 hdpvr mythfrontend[8934]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
540.May  1 11:41:14 hdpvr mythfrontend[8934]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
541.May  1 11:41:14 hdpvr mythfrontend[8934]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
542.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
543.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
544.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
545.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
546.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
547.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
548.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
549.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
550.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
551.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
552.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
553.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
554.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemManager system-unix.cpp:263 (run) Starting process manager
555.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
556.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
557.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
558.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythcommandlineparser.cpp:2566 (ApplySettingsOverride) Setting 'ThemePainter' being forced to 'mythbuntu'
559.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
560.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
561.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
562.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
563.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
564.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
565.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
566.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
567.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
568.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
569.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
570.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
571.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
572.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
573.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
574.May  1 11:41:15 hdpvr mythfrontend[8934]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
575.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
576.May  1 11:41:15 hdpvr mythfrontend[8934]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
577.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
578.May  1 11:41:16 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
579.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
580.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
581.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
582.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
583.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
584.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
585.May  1 11:41:16 hdpvr mythfrontend[8934]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
586.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
587.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
588.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
589.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
590.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
591.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
592.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
593.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
594.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
595.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
596.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
597.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
598.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501114120.mpg) cardtype(DUMMY)
599.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
600.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
601.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
602.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
603.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
604.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
605.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
606.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
607.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
608.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
609.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
610.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
611.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
612.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
613.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
614.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
615.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
616.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
617.May  1 11:41:26 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
618.May  1 11:41:26 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
619.May  1 11:41:42 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
620.May  1 11:41:42 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
621.May  1 11:46:09 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
622.May  1 11:46:09 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
623.May  1 11:46:09 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
624.May  1 11:46:09 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
625.May  1 11:46:12 hdpvr mythfrontend[8934]: last message repeated 2 times
626.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
627.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
628.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
629.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
630.May  1 11:46:13 hdpvr mythfrontend[8934]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
631.May  1 17:10:22 hdpvr mythfrontend[9710]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
632.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
633.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
634.May  1 17:10:22 hdpvr mythfrontend[9710]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
635.May  1 17:10:22 hdpvr mythfrontend[9710]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
636.May  1 17:10:22 hdpvr mythfrontend[9710]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
637.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
638.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
639.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
640.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
641.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
642.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
643.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
644.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
645.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
646.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemManager system-unix.cpp:263 (run) Starting process manager
647.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
648.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
649.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
650.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
651.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
652.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
653.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
654.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
655.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
656.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
657.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
658.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
659.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
660.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
661.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
662.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
663.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
664.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
665.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
666.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
667.May  1 17:10:23 hdpvr mythfrontend[9710]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
668.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
669.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
670.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT 
671.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 2.1 Mesa 7.10.2
672.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 4096 x 4096
673.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
674.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
675.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
676.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
677.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
678.May  1 17:10:23 hdpvr mythfrontend[9710]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
679.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
680.May  1 17:10:23 hdpvr mythfrontend[9710]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
681.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
682.May  1 17:10:23 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
683.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
684.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
685.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
686.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
687.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
688.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
689.May  1 17:10:23 hdpvr mythfrontend[9710]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
690.May  1 17:10:24 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
691.May  1 17:10:24 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
692.May  1 17:10:24 hdpvr mythfrontend[9710]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
693.May  1 17:10:38 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
694.May  1 17:10:38 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
695.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
696.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
697.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
698.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
699.May  1 17:11:16 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
700.May  1 17:11:21 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Puss In Boots
701.May  1 17:11:22 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Puss In Boots 0 0
702.May  1 17:11:33 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 58423
703.May  1 17:11:34 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Puss in Boots 0 0
704.May  1 17:11:34 hdpvr mythfrontend[9710]: I MetadataImageDownload metadataimagedownload.cpp:143 (run) Metadata Image Download: http://cf2.imgobject.com/t/p/original/tkvBU9bwUIHv4MOc3BZuTfzKt8t.jpg ->/var/lib/mythtv/coverart/58423_coverart.jpg
705.May  1 17:11:41 hdpvr mythfrontend[9710]: I MetadataImageDownload metadataimagedownload.cpp:143 (run) Metadata Image Download: http://cf2.imgobject.com/t/p/original/7TrIKc2PXiFdxOeukPZIIHZGqRP.jpg ->/var/lib/mythtv/fanart/58423_fanart.jpg
706.May  1 17:11:48 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
707.May  1 17:11:53 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Rio
708.May  1 17:11:54 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Rio 0 0
709.May  1 17:11:57 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 46195
710.May  1 17:11:58 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Rio 0 0
711.May  1 17:12:06 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
712.May  1 17:12:06 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
713.May  1 17:12:06 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
714.May  1 17:12:06 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
715.May  1 17:12:06 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
716.May  1 17:12:06 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
717.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
718.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
719.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
720.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
721.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc570e6e3d0, id(MPEG4) type(Video)
722.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
723.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc570d1b540, id(MP3) type(Audio)
724.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:697 (Reconfigure) AO: Resampling from 44 kHz to 48 kHz with quality medium
725.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
726.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
727.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
728.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
729.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
730.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
731.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
732.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
733.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
734.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.333333x0.444444
735.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
736.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.333333x0.444444
737.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
738.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
739.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
740.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
741.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
742.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
743.May  1 19:12:01 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
744.May  1 19:12:02 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
745.May  1 19:12:02 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
746.May  1 19:12:02 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
747.May  1 20:00:21 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 3
748.May  1 20:00:28 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
749.May  1 20:00:28 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
750.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
751.May  1 20:00:41 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
752.May  1 20:00:41 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
753.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
754.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
755.May  1 20:00:41 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
756.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
757.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
758.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
759.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
760.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc572a82e70, id(MPEG4) type(Video)
761.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
762.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc572a87aa0, id(MP3) type(Audio)
763.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
764.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
765.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
766.May  1 20:00:42 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
767.May  1 20:00:42 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
768.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
769.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
770.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
771.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
772.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
773.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
774.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
775.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(1): Video timing method: DRM
776.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
777.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
778.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
779.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
780.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
781.May  1 20:21:40 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
782.May  1 20:21:40 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
783.May  1 20:21:40 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
784.May  1 20:21:40 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
785.May  1 20:21:40 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
786.May  1 20:22:00 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
787.May  1 20:22:05 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Images/Graphite/mv_browse_nocover_large.png)Unable to find image file
788.May  1 20:22:36 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
789.May  1 20:22:36 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
790.May  1 20:22:38 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
791.May  1 20:22:38 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
792.May  1 20:22:50 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
793.May  1 20:22:56 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Castle 2009 - S04E22 
794.May  1 20:22:58 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Castle 2009 - S04E22  0 0
795.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
796.May  1 20:23:22 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
797.May  1 20:23:22 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
798.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
799.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
800.May  1 20:23:22 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
801.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
802.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
803.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
804.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
805.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571e97210, id(MPEG4) type(Video)
806.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
807.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571d90d70, id(MP3) type(Audio)
808.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
809.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
810.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
811.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
812.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
813.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
814.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
815.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
816.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
817.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
818.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
819.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
820.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(2): Video timing method: DRM
821.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
822.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
823.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
824.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
825.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
826.May  1 21:05:18 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
827.May  1 21:05:18 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
828.May  1 21:05:18 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
829.May  1 21:05:18 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
830.May  1 21:05:18 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
831.May  1 22:35:18 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 3
832.May  1 22:35:18 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2608 (IdleTimeout) Entering standby mode after 90 minutes of inactivity
833.May  2 08:15:07 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2651 (ExitStandby) Leaving standby mode
834.May  2 08:15:07 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 3
835.May  2 08:15:07 hdpvr mythfrontend[9710]: I DBLogger mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
836.May  2 08:15:30 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
837.May  2 08:15:31 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
838.May  2 08:15:31 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
839.May  2 08:15:31 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
840.May  2 08:15:49 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
841.May  2 08:15:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
842.May  2 08:15:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
843.May  2 08:15:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
844.May  2 08:15:53 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M castle.2009.s04e22.hdtv.xvid-2hd
845.May  2 08:15:54 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M the.mentalist.s04e21.hdtv.xvid-fqm
846.May  2 08:15:54 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for castle.2009.s04e22.hdtv.xvid-2hd 0 0
847.May  2 08:15:55 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M sample-the.mentalist.s04e21.hdtv.xvid-fqm
848.May  2 08:15:55 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for the.mentalist.s04e21.hdtv.xvid-fqm 0 0
849.May  2 08:15:56 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M NCIS.S09E22.HDTV.x264-LOL
850.May  2 08:15:56 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for sample-the.mentalist.s04e21.hdtv.xvid-fqm 0 0
851.May  2 08:15:58 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Ncis - S09E21
852.May  2 08:15:58 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for NCIS.S09E22.HDTV.x264-LOL 0 0
853.May  2 08:15:59 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M in.plain.sight.s05e07
854.May  2 08:15:59 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for Ncis - S09E21 0 0
855.May  2 08:15:59 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M how.i.met.your.mother.s07e22.hdtv.xvid-2hd
856.May  2 08:15:59 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for in.plain.sight.s05e07 0 0
857.May  2 08:16:00 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M How I Met Your Mother - S07E22 
858.May  2 08:16:00 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for how.i.met.your.mother.s07e22.hdtv.xvid-2hd 0 0
859.May  2 08:16:01 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M How I Met Your Mother - S07E21 
860.May  2 08:16:01 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for How I Met Your Mother - S07E22  0 0
861.May  2 08:16:02 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M sample-glee.s03e18.choke.hdtv.xvid-2hd
862.May  2 08:16:02 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for How I Met Your Mother - S07E21  0 0
863.May  2 08:16:03 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M glee.s03e18.choke.hdtv.xvid-2hd
864.May  2 08:16:03 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for sample-glee.s03e18.choke.hdtv.xvid-2hd 0 0
865.May  2 08:16:04 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Castle 2009 - S04E22 
866.May  2 08:16:04 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for glee.s03e18.choke.hdtv.xvid-2hd 0 0
867.May  2 08:16:05 hdpvr mythfrontend[9710]: E MetadataDownload metadatadownload.cpp:190 (findBestMatch) No adequate match or multiple matches found for Castle 2009 - S04E22 .  Update manually.
868.May  2 08:16:05 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Robots (2005)
869.May  2 08:16:05 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for Castle 2009 - S04E22  0 0
870.May  2 08:16:06 hdpvr mythfrontend[9710]: E MetadataDownload metadatadownload.cpp:190 (findBestMatch) No adequate match or multiple matches found for Robots (2005).  Update manually.
871.May  2 08:16:06 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for Robots (2005) 0 0
872.May  2 09:46:14 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2608 (IdleTimeout) Entering standby mode after 90 minutes of inactivity
873.May  2 19:01:45 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2651 (ExitStandby) Leaving standby mode
874.May  2 19:01:45 hdpvr mythfrontend[9710]: I DBLogger mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
875.May  2 19:10:23 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
876.May  2 19:10:23 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
877.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 4
878.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
879.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
880.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
881.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
882.May  2 19:57:56 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
883.May  2 19:57:56 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
884.May  2 19:58:12 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
885.May  2 19:58:12 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
886.May  2 19:58:12 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
887.May  2 19:58:12 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
888.May  2 19:58:12 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
889.May  2 19:58:12 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
890.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
891.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
892.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
893.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
894.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x4204820, id(MPEG4) type(Video)
895.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
896.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x434f770, id(MP3) type(Audio)
897.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
898.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
899.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
900.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
901.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
902.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
903.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
904.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
905.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
906.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
907.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
908.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
909.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(3): Video timing method: DRM
910.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
911.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
912.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
913.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
914.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
915.May  2 20:43:32 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
916.May  2 20:43:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
917.May  2 20:43:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
918.May  2 20:43:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
919.May  2 20:43:33 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
920.May  2 20:43:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
921.May  2 20:43:51 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
922.May  2 20:43:51 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
923.May  2 20:43:51 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
924.May  2 20:43:58 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
925.May  2 20:43:58 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
926.May  2 20:44:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
927.May  2 20:44:33 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
928.May  2 20:44:33 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
929.May  2 20:44:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
930.May  2 20:44:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
931.May  2 20:44:34 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
932.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571685370, id(H264) type(Video)
933.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AAC has 2 channels
934.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571686730, id(AAC) type(Audio)
935.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
936.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
937.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
938.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
939.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
940.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
941.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
942.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
943.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
944.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.374074
945.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
946.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.374074
947.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(4): Video timing method: DRM
948.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
949.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
950.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
951.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
952.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
953.May  2 21:26:41 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
954.May  2 21:26:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
955.May  2 21:26:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
956.May  2 21:26:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to None
957.May  2 21:26:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
958.May  2 21:26:42 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
959.May  2 21:31:12 hdpvr mythfrontend[9710]: I ImageLoad mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
960.May  2 21:32:12 hdpvr mythfrontend[9710]: last message repeated 31 times
961.May  2 21:33:12 hdpvr mythfrontend[9710]: last message repeated 10 times
962.May  2 21:34:04 hdpvr mythfrontend[9710]: E CoreContext weatherScreen.cpp:122 (prepareScreen) Widget not found updatetime
963.May  2 21:34:04 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-3day-XML
964.May  2 21:34:04 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-Current-XML
965.May  2 21:34:06 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
966.May  2 21:34:06 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
967.May  2 21:34:24 hdpvr mythfrontend[9710]: E CoreContext weatherScreen.cpp:122 (prepareScreen) Widget not found updatetime
968.May  2 21:34:24 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-3day-XML
969.May  2 21:34:24 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-Current-XML
970.May  2 21:34:25 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
971.May  2 21:34:25 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
972.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
973.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
974.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
975.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
976.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
977.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
978.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
979.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
980.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
981.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120502213431.mpg) cardtype(DUMMY)
982.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
983.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
984.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
985.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
986.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
987.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
988.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
989.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
990.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(5): Video timing method: DRM
991.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
992.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
993.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
994.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
995.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
996.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
997.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
998.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
999.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
1000.May  2 21:34:37 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
1001.May  2 21:34:37 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
1002.May  2 21:34:55 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
1003.May  2 21:34:55 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
1004.May  2 21:35:09 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
1005.May  2 21:35:09 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
1006.May  2 21:35:09 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
1007.May  2 21:35:09 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
1008.May  2 21:48:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
1009.May  2 21:48:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
1010.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
1011.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
1012.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
1013.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
1014.May  2 21:48:32 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
1015.May  2 21:48:32 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
```

I can't gleem anything from the frontend log

---

### Post by Chewiesw on 2012-05-02
It doesn't seem like recordings are working either.

```
2.=== Mythfrontend Log ===
3. 
4.=== Mythfrontend Log ===
5.=== /var/log/mythtv/mythfrontend.log ===
6.May  1 10:05:52 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
7.May  1 10:05:52 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
8.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
9.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
10.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
11.May  1 10:07:17 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
12.May  1 10:08:45 hdpvr mythfrontend[3898]: E CoreContext xmlparsebase.cpp:542 (ParseUIType) XMLParseBase: Type of new widget 'background' doesn't match old 'base_background_shape'#012#011#011#011Location: /usr/share/mythtv/themes/blue/settings-ui.xml @ 225#012#011#011#011Name: 'background'#011Type: 'imagetype'
13.May  1 10:08:45 hdpvr mythfrontend[3898]: W ScreenLoad themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
14.May  1 10:08:45 hdpvr mythfrontend[3898]: E ScreenLoad themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
15.May  1 10:08:45 hdpvr mythfrontend[3898]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
16.May  1 10:08:45 hdpvr mythfrontend[3898]: W ScreenLoad themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
17.May  1 10:08:45 hdpvr mythfrontend[3898]: E ScreenLoad themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
18.May  1 10:08:56 hdpvr mythfrontend[3898]: N CoreContext mythcorecontext.cpp:1283 (ReInitLocale) Setting QT default locale to EN_US
19.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
20.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
21.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
22.May  1 10:08:56 hdpvr mythfrontend[3898]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
23.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
24.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
25.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
26.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythpainter_ogl.cpp:62 (ClearCache) Clearing OpenGL painter cache.
27.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
28.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
29.May  1 10:08:56 hdpvr mythfrontend[3898]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
30.May  1 10:08:56 hdpvr mythfrontend[3898]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
31.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
32.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
33.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
34.May  1 10:09:09 hdpvr mythfrontend[3898]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
35.May  1 10:10:17 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
36.May  1 10:10:17 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
37.May  1 10:10:19 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
38.May  1 10:10:19 hdpvr mythfrontend[3898]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
39.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
40.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
41.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
42.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
43.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
44.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
45.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
46.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
47.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
48.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501101106.mpg) cardtype(DUMMY)
49.May  1 10:11:06 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
50.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
51.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
52.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
53.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
54.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
55.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
56.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
57.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(5): Video timing method: DRM
58.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
59.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
60.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
61.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
62.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
63.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
64.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
65.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
66.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
67.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
68.May  1 10:11:06 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
69.May  1 10:11:09 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
70.May  1 10:11:09 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
71.May  1 10:11:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
72.May  1 10:11:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
73.May  1 10:11:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
74.May  1 10:11:21 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
75.May  1 10:17:20 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
76.May  1 10:17:20 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
77.May  1 10:17:20 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
78.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
79.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
80.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
81.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
82.May  1 10:17:21 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
83.May  1 10:17:21 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
84.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501101720.mpg) cardtype(DUMMY)
85.May  1 10:17:21 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
86.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
87.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
88.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
89.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
90.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
91.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
92.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
93.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(6): Video timing method: DRM
94.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
95.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
96.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
97.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
98.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
99.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
100.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
101.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
102.May  1 10:17:21 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
103.May  1 10:17:24 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
104.May  1 10:17:24 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
105.May  1 10:17:46 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
106.May  1 10:17:46 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
107.May  1 10:17:49 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
108.May  1 10:17:49 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
109.May  1 10:19:26 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
110.May  1 10:19:26 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
111.May  1 10:19:26 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
112.May  1 10:19:26 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
113.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
114.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
115.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
116.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
117.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
118.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
119.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
120.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
121.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
122.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501101928.mpg) cardtype(DUMMY)
123.May  1 10:19:28 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
124.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
125.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
126.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
127.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
128.May  1 10:19:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
129.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
130.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
131.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(7): Video timing method: DRM
132.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
133.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
134.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
135.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
136.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
137.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
138.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
139.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
140.May  1 10:19:29 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
141.May  1 10:19:32 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
142.May  1 10:19:32 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
143.May  1 10:19:42 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
144.May  1 10:19:42 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
145.May  1 10:20:25 hdpvr mythfrontend[3898]: N LIRC lirc.cpp:504 (GetCodes) LIRC: GetCodes -- eof?
146.May  1 10:21:19 hdpvr mythfrontend[3898]: I LIRC lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
147.May  1 10:21:38 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
148.May  1 10:21:38 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
149.May  1 10:21:38 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
150.May  1 10:21:38 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
151.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
152.May  1 10:21:41 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
153.May  1 10:21:41 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
154.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
155.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
156.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
157.May  1 10:21:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
158.May  1 10:21:41 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
159.May  1 10:21:42 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
160.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501102141.mpg) cardtype(DUMMY)
161.May  1 10:21:42 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
162.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
163.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
164.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
165.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
166.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
167.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
168.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
169.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(8): Video timing method: DRM
170.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
171.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
172.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
173.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
174.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
175.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
176.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
177.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
178.May  1 10:21:42 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
179.May  1 10:21:45 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
180.May  1 10:21:45 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
181.May  1 10:22:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
182.May  1 10:22:41 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
183.May  1 10:22:44 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
184.May  1 10:22:44 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
185.May  1 10:23:13 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
186.May  1 10:23:14 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
187.May  1 10:23:14 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
188.May  1 10:23:14 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
189.May  1 10:30:54 hdpvr mythfrontend[3898]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
190.May  1 10:30:54 hdpvr mythfrontend[3898]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
191.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
192.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
193.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
194.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
195.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
196.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
197.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
198.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
199.May  1 10:44:24 hdpvr mythfrontend[3898]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
200.May  1 10:44:24 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501104424.mpg) cardtype(DUMMY)
201.May  1 10:44:25 hdpvr mythfrontend[3898]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
202.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
203.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
204.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
205.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
206.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
207.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
208.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
209.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(6): Video timing method: DRM
210.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
211.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
212.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
213.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
214.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
215.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
216.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
217.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
218.May  1 10:44:25 hdpvr mythfrontend[3898]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
219.May  1 10:44:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
220.May  1 10:44:28 hdpvr mythfrontend[3898]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
221.May  1 10:44:55 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
222.May  1 10:44:55 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
223.May  1 10:44:55 hdpvr mythfrontend[3898]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
224.May  1 10:44:55 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
225.May  1 10:47:31 hdpvr mythfrontend[3898]: I Socket mythcorecontext.cpp:1103 (readyRead) Received remote 'Clear Cache' request
226.May  1 10:47:37 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
227.May  1 10:47:37 hdpvr mythfrontend[3898]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
228.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
229.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
230.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
231.May  1 10:47:37 hdpvr mythfrontend[3898]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
232.May  1 10:47:38 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
233.May  1 10:47:38 hdpvr mythfrontend[3898]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
234.May  1 11:24:50 hdpvr mythfrontend[8039]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
235.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
236.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
237.May  1 11:24:50 hdpvr mythfrontend[8039]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
238.May  1 11:24:50 hdpvr mythfrontend[8039]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
239.May  1 11:24:50 hdpvr mythfrontend[8039]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
240.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
241.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
242.May  1 11:24:50 hdpvr mythfrontend[8039]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
243.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
244.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
245.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
246.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
247.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
248.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
249.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemManager system-unix.cpp:263 (run) Starting process manager
250.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
251.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
252.May  1 11:24:50 hdpvr mythfrontend[8039]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
253.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
254.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
255.May  1 11:24:50 hdpvr mythfrontend[8039]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
256.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
257.May  1 11:24:50 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
258.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
259.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
260.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
261.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
262.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
263.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
264.May  1 11:24:51 hdpvr mythfrontend[8039]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
265.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
266.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
267.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
268.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
269.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
270.May  1 11:24:51 hdpvr mythfrontend[8039]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
271.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
272.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
273.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT 
274.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 2.1 Mesa 7.10.2
275.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 4096 x 4096
276.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
277.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
278.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
279.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
280.May  1 11:24:51 hdpvr mythfrontend[8039]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
281.May  1 11:24:52 hdpvr mythfrontend[8039]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
282.May  1 11:24:52 hdpvr mythfrontend[8039]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
283.May  1 11:24:52 hdpvr mythfrontend[8039]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
284.May  1 11:24:52 hdpvr mythfrontend[8039]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
285.May  1 11:24:52 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
286.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
287.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
288.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
289.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
290.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
291.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
292.May  1 11:24:52 hdpvr mythfrontend[8039]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
293.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
294.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
295.May  1 11:24:52 hdpvr mythfrontend[8039]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
296.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
297.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
298.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
299.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
300.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
301.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
302.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
303.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
304.May  1 11:24:57 hdpvr mythfrontend[8039]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
305.May  1 11:24:57 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501112457.mpg) cardtype(DUMMY)
306.May  1 11:24:58 hdpvr mythfrontend[8039]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
307.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
308.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
309.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
310.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
311.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
312.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
313.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
314.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
315.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
316.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
317.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
318.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
319.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
320.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
321.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
322.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
323.May  1 11:24:58 hdpvr mythfrontend[8039]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
324.May  1 11:25:04 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
325.May  1 11:25:04 hdpvr mythfrontend[8039]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
326.May  1 11:29:56 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
327.May  1 11:29:56 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
328.May  1 11:29:56 hdpvr mythfrontend[8039]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
329.May  1 11:29:56 hdpvr mythfrontend[8039]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
330.May  1 11:30:00 hdpvr mythfrontend[8039]: last message repeated 2 times
331.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
332.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
333.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
334.May  1 11:30:00 hdpvr mythfrontend[8039]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
335.May  1 11:30:01 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
336.May  1 11:30:01 hdpvr mythfrontend[8039]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
337.May  1 11:30:01 hdpvr mythfrontend[8039]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
338.May  1 11:38:55 hdpvr mythfrontend[8833]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
339.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
340.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
341.May  1 11:38:55 hdpvr mythfrontend[8833]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
342.May  1 11:38:55 hdpvr mythfrontend[8833]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
343.May  1 11:38:55 hdpvr mythfrontend[8833]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
344.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
345.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
346.May  1 11:38:55 hdpvr mythfrontend[8833]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
347.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
348.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
349.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
350.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
351.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
352.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
353.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
354.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemManager system-unix.cpp:263 (run) Starting process manager
355.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
356.May  1 11:38:55 hdpvr mythfrontend[8833]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
357.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
358.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
359.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
360.May  1 11:38:55 hdpvr mythfrontend[8833]: N CoreContext mythcommandlineparser.cpp:2566 (ApplySettingsOverride) Setting 'ThemePainter' being forced to 'qt'
361.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
362.May  1 11:38:55 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
363.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
364.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
365.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
366.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
367.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
368.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
369.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
370.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
371.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
372.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
373.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
374.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
375.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
376.May  1 11:38:56 hdpvr mythfrontend[8833]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
377.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
378.May  1 11:38:56 hdpvr mythfrontend[8833]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
379.May  1 11:38:56 hdpvr mythfrontend[8833]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
380.May  1 11:38:56 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
381.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
382.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
383.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
384.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
385.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
386.May  1 11:38:56 hdpvr mythfrontend[8833]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
387.May  1 11:38:56 hdpvr mythfrontend[8833]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
388.May  1 11:38:57 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
389.May  1 11:38:57 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
390.May  1 11:38:57 hdpvr mythfrontend[8833]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
391.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
392.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
393.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
394.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
395.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
396.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
397.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
398.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
399.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
400.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501113901.mpg) cardtype(DUMMY)
401.May  1 11:39:01 hdpvr mythfrontend[8833]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
402.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
403.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
404.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
405.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
406.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
407.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
408.May  1 11:39:01 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
409.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
410.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
411.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
412.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
413.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
414.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
415.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
416.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
417.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
418.May  1 11:39:02 hdpvr mythfrontend[8833]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
419.May  1 11:39:08 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
420.May  1 11:39:08 hdpvr mythfrontend[8833]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
421.May  1 11:39:12 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
422.May  1 11:39:12 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
423.May  1 11:39:12 hdpvr mythfrontend[8833]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
424.May  1 11:39:12 hdpvr mythfrontend[8833]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
425.May  1 11:39:15 hdpvr mythfrontend[8833]: last message repeated 2 times
426.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
427.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
428.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
429.May  1 11:39:15 hdpvr mythfrontend[8833]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
430.May  1 11:39:16 hdpvr mythfrontend[8833]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
431.May  1 11:40:11 hdpvr mythfrontend[8888]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
432.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
433.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
434.May  1 11:40:11 hdpvr mythfrontend[8888]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
435.May  1 11:40:11 hdpvr mythfrontend[8888]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
436.May  1 11:40:11 hdpvr mythfrontend[8888]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
437.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
438.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
439.May  1 11:40:11 hdpvr mythfrontend[8888]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
440.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
441.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
442.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
443.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
444.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
445.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
446.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemManager system-unix.cpp:263 (run) Starting process manager
447.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
448.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
449.May  1 11:40:11 hdpvr mythfrontend[8888]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
450.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
451.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
452.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
453.May  1 11:40:11 hdpvr mythfrontend[8888]: N CoreContext mythcommandlineparser.cpp:2566 (ApplySettingsOverride) Setting 'ThemePainter' being forced to 'opengl'
454.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
455.May  1 11:40:11 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
456.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
457.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
458.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
459.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
460.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
461.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
462.May  1 11:40:12 hdpvr mythfrontend[8888]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
463.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
464.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
465.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
466.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
467.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
468.May  1 11:40:12 hdpvr mythfrontend[8888]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
469.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
470.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
471.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT 
472.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 2.1 Mesa 7.10.2
473.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 4096 x 4096
474.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
475.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
476.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
477.May  1 11:40:12 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
478.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
479.May  1 11:40:13 hdpvr mythfrontend[8888]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
480.May  1 11:40:13 hdpvr mythfrontend[8888]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
481.May  1 11:40:13 hdpvr mythfrontend[8888]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
482.May  1 11:40:13 hdpvr mythfrontend[8888]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
483.May  1 11:40:13 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
484.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
485.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
486.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
487.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
488.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
489.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
490.May  1 11:40:13 hdpvr mythfrontend[8888]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
491.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
492.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
493.May  1 11:40:13 hdpvr mythfrontend[8888]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
494.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
495.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
496.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
497.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
498.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
499.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
500.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
501.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
502.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
503.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501114017.mpg) cardtype(DUMMY)
504.May  1 11:40:17 hdpvr mythfrontend[8888]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
505.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
506.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
507.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
508.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
509.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
510.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
511.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
512.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
513.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
514.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
515.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
516.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
517.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
518.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
519.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
520.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
521.May  1 11:40:17 hdpvr mythfrontend[8888]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
522.May  1 11:40:23 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
523.May  1 11:40:23 hdpvr mythfrontend[8888]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
524.May  1 11:40:40 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
525.May  1 11:40:40 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
526.May  1 11:40:40 hdpvr mythfrontend[8888]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
527.May  1 11:40:40 hdpvr mythfrontend[8888]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
528.May  1 11:40:43 hdpvr mythfrontend[8888]: last message repeated 2 times
529.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
530.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
531.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
532.May  1 11:40:43 hdpvr mythfrontend[8888]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
533.May  1 11:40:44 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
534.May  1 11:40:44 hdpvr mythfrontend[8888]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
535.May  1 11:40:44 hdpvr mythfrontend[8888]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
536.May  1 11:41:14 hdpvr mythfrontend[8934]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
537.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
538.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
539.May  1 11:41:14 hdpvr mythfrontend[8934]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
540.May  1 11:41:14 hdpvr mythfrontend[8934]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
541.May  1 11:41:14 hdpvr mythfrontend[8934]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
542.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
543.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
544.May  1 11:41:14 hdpvr mythfrontend[8934]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
545.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
546.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
547.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
548.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
549.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
550.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
551.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
552.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
553.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
554.May  1 11:41:14 hdpvr mythfrontend[8934]: I SystemManager system-unix.cpp:263 (run) Starting process manager
555.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
556.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
557.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
558.May  1 11:41:14 hdpvr mythfrontend[8934]: N CoreContext mythcommandlineparser.cpp:2566 (ApplySettingsOverride) Setting 'ThemePainter' being forced to 'mythbuntu'
559.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
560.May  1 11:41:14 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
561.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
562.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
563.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
564.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
565.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
566.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
567.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
568.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
569.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
570.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
571.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
572.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext mythmainwindow.cpp:1050 (Init) Using the Qt painter
573.May  1 11:41:15 hdpvr mythfrontend[8934]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
574.May  1 11:41:15 hdpvr mythfrontend[8934]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
575.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
576.May  1 11:41:15 hdpvr mythfrontend[8934]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
577.May  1 11:41:15 hdpvr mythfrontend[8934]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
578.May  1 11:41:16 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
579.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
580.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
581.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
582.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
583.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
584.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
585.May  1 11:41:16 hdpvr mythfrontend[8934]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
586.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
587.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
588.May  1 11:41:16 hdpvr mythfrontend[8934]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
589.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
590.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
591.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
592.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
593.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
594.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
595.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
596.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
597.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
598.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120501114120.mpg) cardtype(DUMMY)
599.May  1 11:41:20 hdpvr mythfrontend[8934]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
600.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
601.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
602.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
603.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
604.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
605.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
606.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
607.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
608.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
609.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
610.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
611.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
612.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
613.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
614.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
615.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
616.May  1 11:41:20 hdpvr mythfrontend[8934]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
617.May  1 11:41:26 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
618.May  1 11:41:26 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
619.May  1 11:41:42 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
620.May  1 11:41:42 hdpvr mythfrontend[8934]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
621.May  1 11:46:09 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
622.May  1 11:46:09 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
623.May  1 11:46:09 hdpvr mythfrontend[8934]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
624.May  1 11:46:09 hdpvr mythfrontend[8934]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
625.May  1 11:46:12 hdpvr mythfrontend[8934]: last message repeated 2 times
626.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
627.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
628.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
629.May  1 11:46:12 hdpvr mythfrontend[8934]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
630.May  1 11:46:13 hdpvr mythfrontend[8934]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.
631.May  1 17:10:22 hdpvr mythfrontend[9710]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythfrontend version: fixes/0.25 [v0.25-60-gf444358] www.mythtv.org
632.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
633.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
634.May  1 17:10:22 hdpvr mythfrontend[9710]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
635.May  1 17:10:22 hdpvr mythfrontend[9710]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
636.May  1 17:10:22 hdpvr mythfrontend[9710]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
637.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
638.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
639.May  1 17:10:22 hdpvr mythfrontend[9710]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/andrew/.mythtv
640.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
641.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
642.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of hdpvr
643.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to EN_US
644.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale EN_US
645.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
646.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemManager system-unix.cpp:263 (run) Starting process manager
647.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
648.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
649.May  1 17:10:22 hdpvr mythfrontend[9710]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
650.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext screensaver-x11.cpp:51 (ScreenSaverX11Private) ScreenSaverX11Private: XScreenSaver support enabled
651.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext screensaver-x11.cpp:82 (ScreenSaverX11Private) ScreenSaverX11Private: DPMS is disabled.
652.May  1 17:10:22 hdpvr mythfrontend[9710]: N CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080 60.000 Hz
653.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6547
654.May  1 17:10:22 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6547
655.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext mythraopconnection.cpp:769 (LoadKey) RAOP Conn: Failed to read key from: /home/andrew/.mythtv/RAOPKey.rsa
656.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext mythraopdevice.cpp:26 (Create) RAOP Device: Aborting startup - no key found.
657.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext lcddevice.cpp:167 (connectToHost) Connecting to lcd server: 127.0.0.1:6545 (try 1 of 10)
658.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
659.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext lirc.cpp:308 (Init) LIRC: Successfully initialized '/dev/lircd' using '/home/andrew/.mythtv/lircrc' config
660.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled - Failed to read /home/andrew/.mythtv/joystickmenurc
661.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
662.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP 127.0.0.1:6948
663.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:366 (bind) Binding to UDP [0:0:0:0:0:0:0:1]:6948
664.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythmainwindow.cpp:947 (Init) Using Frameless Window
665.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythmainwindow.cpp:960 (Init) Using Full Screen Window
666.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythmainwindow.cpp:1012 (Init) Trying the OpenGL painter
667.May  1 17:10:23 hdpvr mythfrontend[9710]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
668.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl1.cpp:77 (InitFeatures) OpenGL1: Fragment program support available
669.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:932 (InitFeatures) OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
670.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:934 (InitFeatures) OpenGL: OpenGL renderer: Mesa DRI Intel(R) G41 GEM 20100330 DEVELOPMENT 
671.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:936 (InitFeatures) OpenGL: OpenGL version : 2.1 Mesa 7.10.2
672.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:938 (InitFeatures) OpenGL: Max texture size: 4096 x 4096
673.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:940 (InitFeatures) OpenGL: Max texture units: 8
674.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:942 (InitFeatures) OpenGL: Direct rendering: Yes
675.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:949 (InitFeatures) OpenGL: PixelBufferObject support available
676.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:127 (Init) OpenGL: Initialised MythRenderOpenGL
677.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
678.May  1 17:10:23 hdpvr mythfrontend[9710]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
679.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
680.May  1 17:10:23 hdpvr mythfrontend[9710]: W CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
681.May  1 17:10:23 hdpvr mythfrontend[9710]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
682.May  1 17:10:23 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:1861 (RegisterMediaPlugin) Registering Internal as a media playback plugin.
683.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythgallery
684.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext schemawizard.cpp:117 (Compare) Current MythMusic Schema Version (MusicDBSchemaVer): 1019
685.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythmusic
686.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythweather
687.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6546
688.May  1 17:10:23 hdpvr mythfrontend[9710]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6546
689.May  1 17:10:23 hdpvr mythfrontend[9710]: N CoreContext main.cpp:1074 (RunMenu) Found mainmenu.xml for theme 'Steppes'
690.May  1 17:10:24 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
691.May  1 17:10:24 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
692.May  1 17:10:24 hdpvr mythfrontend[9710]: I CoreContext bonjourregister.cpp:103 (BonjourCallback) Bonjour: Service registration complete: name 'Mythfrontend on hdpvr' type '_mythfrontend._tcp.' domain: 'local.'
693.May  1 17:10:38 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
694.May  1 17:10:38 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
695.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
696.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
697.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
698.May  1 17:10:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
699.May  1 17:11:16 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
700.May  1 17:11:21 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Puss In Boots
701.May  1 17:11:22 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Puss In Boots 0 0
702.May  1 17:11:33 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 58423
703.May  1 17:11:34 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Puss in Boots 0 0
704.May  1 17:11:34 hdpvr mythfrontend[9710]: I MetadataImageDownload metadataimagedownload.cpp:143 (run) Metadata Image Download: http://cf2.imgobject.com/t/p/original/tkvBU9bwUIHv4MOc3BZuTfzKt8t.jpg ->/var/lib/mythtv/coverart/58423_coverart.jpg
705.May  1 17:11:41 hdpvr mythfrontend[9710]: I MetadataImageDownload metadataimagedownload.cpp:143 (run) Metadata Image Download: http://cf2.imgobject.com/t/p/original/7TrIKc2PXiFdxOeukPZIIHZGqRP.jpg ->/var/lib/mythtv/fanart/58423_fanart.jpg
706.May  1 17:11:48 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
707.May  1 17:11:53 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Rio
708.May  1 17:11:54 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Rio 0 0
709.May  1 17:11:57 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 46195
710.May  1 17:11:58 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Rio 0 0
711.May  1 17:12:06 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
712.May  1 17:12:06 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
713.May  1 17:12:06 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
714.May  1 17:12:06 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
715.May  1 17:12:06 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
716.May  1 17:12:06 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
717.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
718.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
719.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
720.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
721.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc570e6e3d0, id(MPEG4) type(Video)
722.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
723.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc570d1b540, id(MP3) type(Audio)
724.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:697 (Reconfigure) AO: Resampling from 44 kHz to 48 kHz with quality medium
725.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
726.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
727.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
728.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
729.May  1 17:12:07 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
730.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
731.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
732.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
733.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
734.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.333333x0.444444
735.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
736.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.333333x0.444444
737.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(0): Video timing method: DRM
738.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
739.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
740.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
741.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
742.May  1 17:12:07 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
743.May  1 19:12:01 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
744.May  1 19:12:02 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
745.May  1 19:12:02 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
746.May  1 19:12:02 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
747.May  1 20:00:21 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 3
748.May  1 20:00:28 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
749.May  1 20:00:28 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
750.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
751.May  1 20:00:41 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
752.May  1 20:00:41 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
753.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
754.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
755.May  1 20:00:41 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
756.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
757.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
758.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
759.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
760.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc572a82e70, id(MPEG4) type(Video)
761.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
762.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc572a87aa0, id(MP3) type(Audio)
763.May  1 20:00:41 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
764.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
765.May  1 20:00:41 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
766.May  1 20:00:42 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
767.May  1 20:00:42 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
768.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
769.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
770.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
771.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
772.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
773.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
774.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
775.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(1): Video timing method: DRM
776.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
777.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
778.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
779.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
780.May  1 20:00:42 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
781.May  1 20:21:40 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
782.May  1 20:21:40 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
783.May  1 20:21:40 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
784.May  1 20:21:40 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
785.May  1 20:21:40 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
786.May  1 20:22:00 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
787.May  1 20:22:05 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Images/Graphite/mv_browse_nocover_large.png)Unable to find image file
788.May  1 20:22:36 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
789.May  1 20:22:36 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
790.May  1 20:22:38 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
791.May  1 20:22:38 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
792.May  1 20:22:50 hdpvr mythfrontend[9710]: E CoreContext xmlparsebase.cpp:350 (ParseChildren) XMLParseBase: Parent is NULL
793.May  1 20:22:56 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Castle 2009 - S04E22 
794.May  1 20:22:58 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: Castle 2009 - S04E22  0 0
795.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
796.May  1 20:23:22 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
797.May  1 20:23:22 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
798.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
799.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
800.May  1 20:23:22 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
801.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
802.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
803.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
804.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
805.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571e97210, id(MPEG4) type(Video)
806.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
807.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571d90d70, id(MP3) type(Audio)
808.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
809.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
810.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
811.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
812.May  1 20:23:22 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
813.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
814.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
815.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
816.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
817.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
818.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
819.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
820.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(2): Video timing method: DRM
821.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
822.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
823.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
824.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
825.May  1 20:23:22 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
826.May  1 21:05:18 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
827.May  1 21:05:18 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
828.May  1 21:05:18 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
829.May  1 21:05:18 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
830.May  1 21:05:18 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
831.May  1 22:35:18 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 3
832.May  1 22:35:18 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2608 (IdleTimeout) Entering standby mode after 90 minutes of inactivity
833.May  2 08:15:07 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2651 (ExitStandby) Leaving standby mode
834.May  2 08:15:07 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 3
835.May  2 08:15:07 hdpvr mythfrontend[9710]: I DBLogger mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
836.May  2 08:15:30 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
837.May  2 08:15:31 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
838.May  2 08:15:31 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
839.May  2 08:15:31 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
840.May  2 08:15:49 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
841.May  2 08:15:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
842.May  2 08:15:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
843.May  2 08:15:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
844.May  2 08:15:53 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M castle.2009.s04e22.hdtv.xvid-2hd
845.May  2 08:15:54 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M the.mentalist.s04e21.hdtv.xvid-fqm
846.May  2 08:15:54 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for castle.2009.s04e22.hdtv.xvid-2hd 0 0
847.May  2 08:15:55 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M sample-the.mentalist.s04e21.hdtv.xvid-fqm
848.May  2 08:15:55 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for the.mentalist.s04e21.hdtv.xvid-fqm 0 0
849.May  2 08:15:56 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M NCIS.S09E22.HDTV.x264-LOL
850.May  2 08:15:56 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for sample-the.mentalist.s04e21.hdtv.xvid-fqm 0 0
851.May  2 08:15:58 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Ncis - S09E21
852.May  2 08:15:58 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for NCIS.S09E22.HDTV.x264-LOL 0 0
853.May  2 08:15:59 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M in.plain.sight.s05e07
854.May  2 08:15:59 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for Ncis - S09E21 0 0
855.May  2 08:15:59 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M how.i.met.your.mother.s07e22.hdtv.xvid-2hd
856.May  2 08:15:59 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for in.plain.sight.s05e07 0 0
857.May  2 08:16:00 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M How I Met Your Mother - S07E22 
858.May  2 08:16:00 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for how.i.met.your.mother.s07e22.hdtv.xvid-2hd 0 0
859.May  2 08:16:01 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M How I Met Your Mother - S07E21 
860.May  2 08:16:01 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for How I Met Your Mother - S07E22  0 0
861.May  2 08:16:02 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M sample-glee.s03e18.choke.hdtv.xvid-2hd
862.May  2 08:16:02 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for How I Met Your Mother - S07E21  0 0
863.May  2 08:16:03 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M glee.s03e18.choke.hdtv.xvid-2hd
864.May  2 08:16:03 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for sample-glee.s03e18.choke.hdtv.xvid-2hd 0 0
865.May  2 08:16:04 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Castle 2009 - S04E22 
866.May  2 08:16:04 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for glee.s03e18.choke.hdtv.xvid-2hd 0 0
867.May  2 08:16:05 hdpvr mythfrontend[9710]: E MetadataDownload metadatadownload.cpp:190 (findBestMatch) No adequate match or multiple matches found for Castle 2009 - S04E22 .  Update manually.
868.May  2 08:16:05 hdpvr mythfrontend[9710]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Robots (2005)
869.May  2 08:16:05 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for Castle 2009 - S04E22  0 0
870.May  2 08:16:06 hdpvr mythfrontend[9710]: E MetadataDownload metadatadownload.cpp:190 (findBestMatch) No adequate match or multiple matches found for Robots (2005).  Update manually.
871.May  2 08:16:06 hdpvr mythfrontend[9710]: I CoreContext videodlg.cpp:3262 (customEvent) No results found for Robots (2005) 0 0
872.May  2 09:46:14 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2608 (IdleTimeout) Entering standby mode after 90 minutes of inactivity
873.May  2 19:01:45 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2651 (ExitStandby) Leaving standby mode
874.May  2 19:01:45 hdpvr mythfrontend[9710]: I DBLogger mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
875.May  2 19:10:23 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
876.May  2 19:10:23 hdpvr mythfrontend[9710]: I RemoteFileDownload mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
877.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 4
878.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
879.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
880.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
881.May  2 19:57:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
882.May  2 19:57:56 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
883.May  2 19:57:56 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
884.May  2 19:58:12 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
885.May  2 19:58:12 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
886.May  2 19:58:12 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
887.May  2 19:58:12 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
888.May  2 19:58:12 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
889.May  2 19:58:12 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
890.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1539 (CreateDevice) VDPAU: Error at mythrender_vdpau.cpp:1539 (#1, Unknown)
891.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:1543 (CreateDevice) VDPAU: Failed to create VDPAU device.
892.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:343 (CreateDummy) VDPAU: No VDPAU device
893.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext mythrender_vdpau.cpp:348 (CreateDummy) VDPAU: Failed to create dummy device.
894.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x4204820, id(MPEG4) type(Video)
895.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec MP3 has 2 channels
896.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x434f770, id(MP3) type(Audio)
897.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
898.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
899.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
900.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
901.May  2 19:58:13 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
902.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
903.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
904.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
905.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
906.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
907.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
908.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.325x0.325926
909.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(3): Video timing method: DRM
910.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
911.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
912.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
913.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
914.May  2 19:58:13 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
915.May  2 20:43:32 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
916.May  2 20:43:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
917.May  2 20:43:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
918.May  2 20:43:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
919.May  2 20:43:33 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
920.May  2 20:43:50 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/videos)
921.May  2 20:43:51 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/NewSeason/TV)
922.May  2 20:43:51 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/1080p)
923.May  2 20:43:51 hdpvr mythfrontend[9710]: I CoreContext dirscan.cpp:245 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning (/var/lib/mythtv/movies/KIDZ)
924.May  2 20:43:58 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_coverart.jpg)Unable to find image file
925.May  2 20:43:58 hdpvr mythfrontend[9710]: E ImageLoad mythuihelper.cpp:1323 (LoadScaleImage) MythUIHelper: LoadScaleImage(Chuck Season 5_fanart.jpg)Unable to find image file
926.May  2 20:44:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
927.May  2 20:44:33 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
928.May  2 20:44:33 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
929.May  2 20:44:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
930.May  2 20:44:33 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingVideo
931.May  2 20:44:34 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
932.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571685370, id(H264) type(Video)
933.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:1960 (ScanStreams) AFD: codec AAC has 2 channels
934.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext avformatdecoder.cpp:2102 (ScanStreams) AFD: Opened codec 0x7fc571686730, id(AAC) type(Audio)
935.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext audio/audiooutputbase.cpp:791 (Reconfigure) AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
936.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:195 (SetPreallocBufferSize) ALSA: Setting hardware audio buffer size to 6016
937.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:211 (SetPreallocBufferSize) ALSA: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
938.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:213 (SetPreallocBufferSize) ALSA: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
939.May  2 20:44:34 hdpvr mythfrontend[9710]: E CoreContext audio/audiooutputalsa.cpp:545 (OpenDevice) ALSA: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
940.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
941.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
942.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
943.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
944.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.374074
945.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
946.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.374074
947.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(4): Video timing method: DRM
948.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
949.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingVideo
950.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
951.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
952.May  2 20:44:34 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
953.May  2 21:26:41 hdpvr mythfrontend[9710]: E Decoder avformatdecoder.cpp:4376 (GetFrame) decoding error#012#011#011#011eno: Broken pipe (32)
954.May  2 21:26:41 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingVideo to None
955.May  2 21:26:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingVideo to None
956.May  2 21:26:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to None
957.May  2 21:26:42 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
958.May  2 21:26:42 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
959.May  2 21:31:12 hdpvr mythfrontend[9710]: I ImageLoad mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
960.May  2 21:32:12 hdpvr mythfrontend[9710]: last message repeated 31 times
961.May  2 21:33:12 hdpvr mythfrontend[9710]: last message repeated 10 times
962.May  2 21:34:04 hdpvr mythfrontend[9710]: E CoreContext weatherScreen.cpp:122 (prepareScreen) Widget not found updatetime
963.May  2 21:34:04 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-3day-XML
964.May  2 21:34:04 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-Current-XML
965.May  2 21:34:06 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
966.May  2 21:34:06 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
967.May  2 21:34:24 hdpvr mythfrontend[9710]: E CoreContext weatherScreen.cpp:122 (prepareScreen) Widget not found updatetime
968.May  2 21:34:24 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-3day-XML
969.May  2 21:34:24 hdpvr mythfrontend[9710]: I CoreContext weatherSource.cpp:424 (startUpdate) Starting update of BBC-Current-XML
970.May  2 21:34:25 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
971.May  2 21:34:25 hdpvr mythfrontend[9710]: E CoreContext weatherSource.cpp:518 (processExit) script exit status 255
972.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:987 (TV) TV: Creating TV object
973.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
974.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2585 (PauseIdleTimer) Suspending idle timer
975.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:1206 (Init) TV: Created TvPlayWindow.
976.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from None to WatchingLiveTV
977.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:371 (ConnectCommandSocket) MythCoreContext: Connecting to backend server: ::1:6543 (try 1 of 1)
978.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext mythcorecontext.cpp:1178 (CheckProtoVersion) Using protocol version 72
979.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext tv_play.cpp:2188 (HandleStateChange) TV: Spawning LiveTV Recorder -- begin
980.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext tv_play.cpp:2195 (HandleStateChange) TV: Spawning LiveTV Recorder -- end
981.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2216 (HandleStateChange) TV: playbackURL(/var/lib/mythtv/livetv/1038_20120502213431.mpg) cardtype(DUMMY)
982.May  2 21:34:31 hdpvr mythfrontend[9710]: N CoreContext audioplayer.cpp:167 (ReinitAudio) AudioPlayer: Enabling Audio
983.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videoout_xv.cpp:611 (InitXVideo) VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
984.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1858 (CalcHueBase) VideoOutput: CalcHueBase(Intel(R) Textured Video): Unknown adaptor, hue may be wrong.
985.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1860 (CalcHueBase) VideoOutput: Please open a ticket if you need to adjust the hue.
986.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
987.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
988.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
989.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
990.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext mythplayer.cpp:1738 (InitAVSync) Player(5): Video timing method: DRM
991.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:5169 (StartPlayer) TV: Created player.
992.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from None to WatchingLiveTV
993.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2372 (HandleStateChange) TV: State is LiveTV & mctx == ctx
994.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2374 (HandleStateChange) TV: UpdateOSDInput done
995.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2376 (HandleStateChange) TV: UpdateLCD done
996.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2378 (HandleStateChange) TV: ITVRestart done
997.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2451 (HandleStateChange) TV: Main UI disabled.
998.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:378 (StartTV) TV: Entering main playback loop.
999.May  2 21:34:31 hdpvr mythfrontend[9710]: I CoreContext videooutbase.cpp:1369 (DisplayOSD) VideoOutput: Created YV12 OSD.
1000.May  2 21:34:37 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
1001.May  2 21:34:37 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
1002.May  2 21:34:55 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:228 (OverrideUIScale) OSD: Base theme size: 1920x1080
1003.May  2 21:34:55 hdpvr mythfrontend[9710]: I CoreContext osd.cpp:233 (OverrideUIScale) OSD: Scaling factors: 0.375x0.533333
1004.May  2 21:35:09 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
1005.May  2 21:35:09 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
1006.May  2 21:35:09 hdpvr mythfrontend[9710]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
1007.May  2 21:35:09 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
1008.May  2 21:48:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
1009.May  2 21:48:31 hdpvr mythfrontend[9710]: N CoreContext mythmainwindow.cpp:2590 (PauseIdleTimer) Resuming idle timer
1010.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on hdpvr'
1011.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext mythraopdevice.cpp:64 (Cleanup) RAOP Device: Cleaning up.
1012.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext mythairplayserver.cpp:262 (Cleanup) AirPay: Cleaning up.
1013.May  2 21:48:31 hdpvr mythfrontend[9710]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
1014.May  2 21:48:32 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
1015.May  2 21:48:32 hdpvr mythfrontend[9710]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
```

I can't gleem anything from the frontend log

---

### Post by tgm4883 on 2012-05-02
You'll want to post/review your backend log, not frontend log

---

### Post by jyavenard on 2012-05-03
> **Chewiesw said:**
> Hello
Signal 0% (_L) Partial Lock
Recently upgraded from  11.04 0.24 fixes to 0.25. Live TV no longer works all I get is a black screen and then eventually a prompt that there isn’t a signal and I have to pres OK.

C

Have you thought of checking your antenna cable?

Because that's what the problem is: you've got no signal

---

### Post by Chewiesw on 2012-05-03
One of the first tings checked was the cables, the all look fine. I am using a STB which has the ouput split directly into the TV and also my mythbox.

Backend Log

```
1019.=== Mythbackend Log ===
1020.=== /var/log/mythtv/mythbackend.log ===
1021.May  1 11:41:16 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1022.May  1 11:41:16 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1023.May  1 11:41:16 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1024.May  1 11:41:16 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 1)
1025.May  1 11:41:20 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1026.May  1 11:41:20 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1027.May  1 11:41:20 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
1028.May  1 11:41:20 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
1029.May  1 11:41:20 hdpvr mythbackend[7996]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2) input_switch: 0 mode_switch: 0
1030.May  1 11:41:20 hdpvr mythbackend[7996]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
1031.May  1 11:41:36 hdpvr mythbackend[7996]: E ProcessRequest tv_rec.cpp:2807 (PauseRecorder) TVRec(1): PauseRecorder() called with no recorder
1032.May  1 11:41:36 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
1033.May  1 11:41:36 hdpvr mythbackend[7996]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2) input_switch: 0 mode_switch: 0
1034.May  1 11:41:36 hdpvr mythbackend[7996]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
1035.May  1 11:41:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
1036.May  1 11:42:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1038 at 2012-05-01T11:40:17 => "Vodacom Super Rugby 2012":"Blues vs Reds"
1037.May  1 11:44:44 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1038.May  1 11:46:09 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None
1039.May  1 11:49:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1040.May  1 11:54:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1041.May  1 11:56:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1042.May  1 11:59:54 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1043.May  1 12:05:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1044.May  1 12:10:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1045.May  1 12:11:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1046.May  1 12:15:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1047.May  1 12:20:08 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1048.May  1 12:25:10 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1049.May  1 12:26:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1050.May  1 12:30:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1051.May  1 12:35:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1052.May  1 12:40:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1053.May  1 12:41:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1054.May  1 12:45:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1055.May  1 12:50:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1056.May  1 12:55:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1057.May  1 12:56:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1058.May  1 13:00:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1059.May  1 13:05:31 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1060.May  1 13:10:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1061.May  1 13:12:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1062.May  1 13:15:39 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1063.May  1 13:20:40 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1064.May  1 13:25:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1065.May  1 13:27:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1066.May  1 13:30:44 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1067.May  1 13:35:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1068.May  1 13:40:50 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1069.May  1 13:42:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1070.May  1 13:45:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1071.May  1 13:51:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1072.May  1 13:56:02 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1073.May  1 13:57:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1074.May  1 14:01:08 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1075.May  1 14:06:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1076.May  1 14:11:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1077.May  1 14:12:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1078.May  1 14:16:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1079.May  1 14:21:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1080.May  1 14:26:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1081.May  1 14:27:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1082.May  1 14:31:30 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1083.May  1 14:36:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1084.May  1 14:41:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1085.May  1 14:42:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1086.May  1 14:46:39 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1087.May  1 14:51:45 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1088.May  1 14:56:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1089.May  1 14:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1090.May  1 15:01:51 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1091.May  1 15:06:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1092.May  1 15:11:54 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1093.May  1 15:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1094.May  1 15:16:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1095.May  1 15:22:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1096.May  1 15:27:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1097.May  1 15:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1098.May  1 15:32:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1099.May  1 15:37:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1100.May  1 15:42:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1101.May  1 15:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1102.May  1 15:47:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1103.May  1 15:52:23 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1104.May  1 15:57:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1105.May  1 15:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1106.May  1 16:02:31 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1107.May  1 16:07:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1108.May  1 16:12:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1109.May  1 16:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1110.May  1 16:17:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1111.May  1 16:22:39 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1112.May  1 16:27:44 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1113.May  1 16:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1114.May  1 16:32:44 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1115.May  1 16:37:46 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1116.May  1 16:42:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1117.May  1 16:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1118.May  1 16:47:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1119.May  1 16:52:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1120.May  1 16:58:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1121.May  1 16:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1122.May  1 17:03:04 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1123.May  1 17:08:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1124.May  1 17:10:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1125.May  1 17:10:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1126.May  1 17:10:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1127.May  1 17:10:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 1)
1128.May  1 17:10:38 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1129.May  1 17:10:38 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1130.May  1 17:10:38 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1131.May  1 17:10:38 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1132.May  1 17:12:06 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 9
1133.May  1 17:13:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1134.May  1 17:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1135.May  1 17:18:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1136.May  1 17:23:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1137.May  1 17:28:21 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1138.May  1 17:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1139.May  1 17:33:23 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1140.May  1 17:38:28 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1141.May  1 17:43:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1142.May  1 17:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1143.May  1 17:48:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1144.May  1 17:53:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1145.May  1 17:58:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1146.May  1 17:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1147.May  1 18:03:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1148.May  1 18:08:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1149.May  1 18:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1150.May  1 18:13:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1151.May  1 18:18:56 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1152.May  1 18:23:56 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1153.May  1 18:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1154.May  1 18:28:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1155.May  1 18:33:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1156.May  1 18:38:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1157.May  1 18:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1158.May  1 18:43:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1159.May  1 18:49:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1160.May  1 18:54:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1161.May  1 18:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1162.May  1 18:59:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1163.May  1 19:04:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1164.May  1 19:09:22 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1165.May  1 19:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1166.May  1 19:14:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1167.May  1 19:19:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1168.May  1 19:24:30 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1169.May  1 19:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1170.May  1 19:29:35 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1171.May  1 19:34:40 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1172.May  1 19:39:45 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1173.May  1 19:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1174.May  1 19:44:51 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1175.May  1 19:49:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1176.May  1 19:54:58 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1177.May  1 19:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1178.May  1 20:00:04 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1179.May  1 20:05:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1180.May  1 20:10:12 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1181.May  1 20:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1182.May  1 20:15:12 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1183.May  1 20:20:13 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1184.May  1 20:25:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1185.May  1 20:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1186.May  1 20:30:19 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1187.May  1 20:35:22 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1188.May  1 20:40:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1189.May  1 20:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1190.May  1 20:45:28 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1191.May  1 20:50:30 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1192.May  1 20:55:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1193.May  1 20:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1194.May  1 21:00:41 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1195.May  1 21:05:46 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1196.May  1 21:10:46 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1197.May  1 21:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1198.May  1 21:15:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1199.May  1 21:20:50 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1200.May  1 21:25:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1201.May  1 21:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1202.May  1 21:30:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1203.May  1 21:35:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1204.May  1 21:40:58 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1205.May  1 21:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1206.May  1 21:46:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1207.May  1 21:51:10 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1208.May  1 21:56:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1209.May  1 21:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1210.May  1 22:01:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1211.May  1 22:06:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1212.May  1 22:08:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1213.May  1 22:08:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1214.May  1 22:08:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1215.May  1 22:08:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1216.May  1 22:08:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1217.May  1 22:08:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1218.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1219.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1220.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1221.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1222.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1223.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1224.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1225.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1226.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1227.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1228.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1229.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1230.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1231.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1232.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1233.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1234.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1235.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1236.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1237.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1238.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1239.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1240.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1241.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1242.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1243.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1244.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1245.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1246.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1247.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1248.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1249.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1250.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1251.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1252.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1253.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1254.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1255.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1256.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1257.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1258.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1259.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1260.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1261.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1262.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1263.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1264.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1265.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1266.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1267.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1268.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1269.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1270.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1271.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1272.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1273.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1274.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1275.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1276.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1277.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1278.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1279.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1280.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1281.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1282.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1283.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1284.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1285.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1286.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1287.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1288.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1289.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1290.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1291.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1292.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1293.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1294.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1295.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1296.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1297.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1298.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1299.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1300.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1301.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1302.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1303.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1304.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1305.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1306.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1307.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1308.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1309.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1310.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1311.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1312.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1313.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1314.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1315.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1316.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1317.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1318.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1319.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1320.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1321.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1322.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1323.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1324.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1325.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1326.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1327.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1328.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1329.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1330.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1331.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1332.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1333.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1334.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1335.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1336.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1337.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1338.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1339.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1340.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1341.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1342.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1343.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1344.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1345.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1346.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1347.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1348.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1349.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1350.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1351.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1352.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1353.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1354.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1355.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1356.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1357.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1358.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1359.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1360.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1361.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1362.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1363.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1364.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1365.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1366.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1367.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1368.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1369.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1370.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1371.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1372.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1373.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1374.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1375.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1376.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1377.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1378.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1379.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1380.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1381.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1382.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1383.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1384.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1385.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1386.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1387.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1388.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1389.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1390.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1391.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1392.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1393.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1394.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1395.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1396.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1397.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1398.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1399.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1400.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1401.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1402.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1403.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1404.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1405.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1406.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1407.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1408.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1409.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1410.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1411.May  1 22:08:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1412.May  1 22:08:29 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1413.May  1 22:08:29 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1414.May  1 22:08:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1415.May  1 22:08:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1416.May  1 22:08:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1417.May  1 22:08:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1418.May  1 22:08:55 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1419.May  1 22:08:55 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Bourne Supremacy
1420.May  1 22:09:00 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M The Bourne Supremacy
1421.May  1 22:09:02 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1422.May  1 22:09:02 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1423.May  1 22:09:02 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1424.May  1 22:09:02 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1425.May  1 22:09:02 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 21.
1426.May  1 22:09:02 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
1427.May  1 22:09:03 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 2502
1428.May  1 22:09:03 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 9
1429.May  1 22:09:03 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.2 = 0.00 match + 0.22 place
1430.May  1 22:09:03 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1431.May  1 22:09:03 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1432.May  1 22:09:03 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Bourne Supremacy
1433.May  1 22:09:06 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M The Bourne Supremacy
1434.May  1 22:09:07 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 2502
1435.May  1 22:09:08 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: The Bourne Supremacy 0 0
1436.May  1 22:09:09 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: The Bourne Supremacy 0 0
1437.May  1 22:09:13 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1438.May  1 22:09:13 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1439.May  1 22:11:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1440.May  1 22:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1441.May  1 22:13:52 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1442.May  1 22:13:52 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1443.May  1 22:14:02 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1444.May  1 22:14:02 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1445.May  1 22:14:42 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1446.May  1 22:14:42 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1447.May  1 22:14:51 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1448.May  1 22:14:51 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1449.May  1 22:16:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1450.May  1 22:21:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1451.May  1 22:26:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1452.May  1 22:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1453.May  1 22:31:28 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1454.May  1 22:36:35 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1455.May  1 22:41:36 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1456.May  1 22:43:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1457.May  1 22:46:39 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1458.May  1 22:51:44 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1459.May  1 22:56:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1460.May  1 22:58:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1461.May  1 23:01:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1462.May  1 23:06:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1463.May  1 23:11:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1464.May  1 23:13:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1465.May  1 23:16:50 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1466.May  1 23:21:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1467.May  1 23:26:58 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1468.May  1 23:28:03 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1469.May  1 23:28:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1470.May  1 23:29:03 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1471.May  1 23:29:03 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1472.May  1 23:29:03 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.1 = 0.00 match + 0.05 place
1473.May  1 23:29:33 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1521 (HandlePendingRecordings) TVRec(1): ASK_RECORDING 1 25 0 0
1474.May  1 23:30:00 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to RecordingOnly
1475.May  1 23:30:00 hdpvr mythbackend[7996]: I TVRecEvent mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1476.May  1 23:30:00 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
1477.May  1 23:30:00 hdpvr mythbackend[7996]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2) input_switch: 0 mode_switch: 0
1478.May  1 23:30:00 hdpvr mythbackend[7996]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
1479.May  1 23:30:00 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Tuning recording: "The Bourne Supremacy": channel 1003 on cardid 1, sourceid 1
1480.May  1 23:31:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1481.May  1 23:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2505 (HandleTuning) Canceling recording since tuning timeout, 180 seconds, has been exceeded.
1482.May  1 23:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Canceled recording (Recorder Failed): "The Bourne Supremacy": channel 1003 on cardid 1, sourceid 1
1483.May  1 23:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1484.May  1 23:33:01 hdpvr mythbackend[7996]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1003_20120501233000.mpg): GetPlaybackURL: '1003_20120501233000.mpg' should be local, but it can not be found.
1485.May  1 23:33:01 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
1486.May  1 23:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.0 = 0.00 match + 0.05 place
1487.May  1 23:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1488.May  1 23:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.1 = 0.00 match + 0.08 place
1489.May  1 23:33:04 hdpvr mythbackend[7996]: E DeleteThread mainserver.cpp:2218 (OpenAndUnlink) Error deleting 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/hdpvr/1003_20120501233000.mpg' could not open #012#011#011#011eno: No such file or directory (2)
1490.May  1 23:33:04 hdpvr mythbackend[7996]: E DeleteThread mainserver.cpp:2196 (DeleteFile) Delete Error 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/hdpvr/1003_20120501233000.mpg'#012#011#011#011eno: No such file or directory (2)
1491.May  1 23:33:08 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1492.May  1 23:33:08 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.1 = 0.00 match + 0.09 place
1493.May  1 23:37:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1494.May  1 23:42:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1495.May  1 23:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1496.May  1 23:47:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1497.May  1 23:52:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1498.May  1 23:57:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1499.May  1 23:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1500.May  2 00:02:21 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1501.May  2 00:07:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1502.May  2 00:12:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1503.May  2 00:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1504.May  2 00:17:35 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1505.May  2 00:22:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1506.May  2 00:27:41 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1507.May  2 00:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1508.May  2 00:32:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1509.May  2 00:37:50 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1510.May  2 00:42:51 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1511.May  2 00:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1512.May  2 00:47:58 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1513.May  2 00:52:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1514.May  2 00:58:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1515.May  2 00:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1516.May  2 01:03:04 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1517.May  2 01:08:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1518.May  2 01:13:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1519.May  2 01:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1520.May  2 01:18:12 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1521.May  2 01:23:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1522.May  2 01:28:19 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1523.May  2 01:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1524.May  2 01:33:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1525.May  2 01:38:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1526.May  2 01:43:30 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1527.May  2 01:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1528.May  2 01:48:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1529.May  2 01:53:35 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1530.May  2 01:58:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1531.May  2 01:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1532.May  2 02:03:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1533.May  2 02:08:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1534.May  2 02:13:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1535.May  2 02:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1536.May  2 02:18:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1537.May  2 02:23:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1538.May  2 02:29:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1539.May  2 02:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1540.May  2 02:34:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1541.May  2 02:39:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1542.May  2 02:44:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1543.May  2 02:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1544.May  2 02:49:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1545.May  2 02:54:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1546.May  2 02:59:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1547.May  2 02:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1548.May  2 03:04:38 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1549.May  2 03:09:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1550.May  2 03:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1551.May  2 03:14:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1552.May  2 03:19:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1553.May  2 03:24:58 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1554.May  2 03:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1555.May  2 03:30:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1556.May  2 03:35:05 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1557.May  2 03:40:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1558.May  2 03:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1559.May  2 03:45:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1560.May  2 03:50:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1561.May  2 03:55:19 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1562.May  2 03:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1563.May  2 04:00:22 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1564.May  2 04:05:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1565.May  2 04:10:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1566.May  2 04:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1567.May  2 04:15:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1568.May  2 04:20:38 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1569.May  2 04:25:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1570.May  2 04:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1571.May  2 04:30:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1572.May  2 04:35:46 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1573.May  2 04:40:51 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1574.May  2 04:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1575.May  2 04:45:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1576.May  2 04:50:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1577.May  2 04:55:56 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1578.May  2 04:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1579.May  2 05:00:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1580.May  2 05:06:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1581.May  2 05:11:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1582.May  2 05:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1583.May  2 05:16:13 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1584.May  2 05:21:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1585.May  2 05:26:23 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1586.May  2 05:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1587.May  2 05:31:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1588.May  2 05:36:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1589.May  2 05:41:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1590.May  2 05:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1591.May  2 05:46:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1592.May  2 05:51:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1593.May  2 05:56:38 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1594.May  2 05:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1595.May  2 06:01:41 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1596.May  2 06:06:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1597.May  2 06:11:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1598.May  2 06:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1599.May  2 06:16:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1600.May  2 06:21:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1601.May  2 06:26:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1602.May  2 06:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1603.May  2 06:32:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1604.May  2 06:37:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1605.May  2 06:42:08 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1606.May  2 06:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1607.May  2 06:47:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1608.May  2 06:52:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1609.May  2 06:57:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1610.May  2 06:59:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1611.May  2 07:02:31 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1612.May  2 07:07:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1613.May  2 07:12:35 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1614.May  2 07:14:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1615.May  2 07:17:41 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1616.May  2 07:22:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1617.May  2 07:27:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1618.May  2 07:29:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1619.May  2 07:32:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1620.May  2 07:37:51 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1621.May  2 07:42:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1622.May  2 07:44:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1623.May  2 07:48:04 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1624.May  2 07:53:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1625.May  2 07:58:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1626.May  2 08:00:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1627.May  2 08:03:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1628.May  2 08:08:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1629.May  2 08:13:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1630.May  2 08:13:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1631.May  2 08:13:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1632.May  2 08:13:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1633.May  2 08:13:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1634.May  2 08:13:47 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1635.May  2 08:13:47 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1636.May  2 08:13:53 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1637.May  2 08:13:53 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1638.May  2 08:13:53 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1639.May  2 08:13:53 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1640.May  2 08:16:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1641.May  2 08:17:07 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1642.May  2 08:17:07 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1643.May  2 08:17:08 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1644.May  2 08:17:08 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1645.May  2 08:17:11 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1646.May  2 08:17:11 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1647.May  2 08:17:16 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1648.May  2 08:17:16 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1649.May  2 08:17:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1650.May  2 08:17:17 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1651.May  2 08:17:17 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Ident X
1652.May  2 08:17:19 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Ident X
1653.May  2 08:17:21 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1654.May  2 08:17:21 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1655.May  2 08:17:21 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1656.May  2 08:17:21 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1657.May  2 08:17:21 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 22.
1658.May  2 08:17:21 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
1659.May  2 08:17:21 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.1 = 0.01 match + 0.11 place
1660.May  2 08:17:21 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 10
1661.May  2 08:17:21 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 73499
1662.May  2 08:17:21 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1663.May  2 08:17:21 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1664.May  2 08:17:22 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Ident X
1665.May  2 08:17:23 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Ident X
1666.May  2 08:17:23 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 73499
1667.May  2 08:17:24 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: The Double 0 0
1668.May  2 08:17:27 hdpvr mythbackend[7996]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: The Double 0 0
1669.May  2 08:17:32 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1670.May  2 08:17:32 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1671.May  2 08:17:41 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1672.May  2 08:17:41 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1673.May  2 08:18:31 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1674.May  2 08:23:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1675.May  2 08:28:41 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1676.May  2 08:29:21 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1677.May  2 08:29:21 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.1 = 0.00 match + 0.06 place
1678.May  2 08:29:32 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1521 (HandlePendingRecordings) TVRec(1): ASK_RECORDING 1 27 0 0
1679.May  2 08:30:00 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to RecordingOnly
1680.May  2 08:30:00 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
1681.May  2 08:30:00 hdpvr mythbackend[7996]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2) input_switch: 0 mode_switch: 0
1682.May  2 08:30:00 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1683.May  2 08:30:00 hdpvr mythbackend[7996]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
1684.May  2 08:30:00 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Tuning recording: "Ident X": channel 1005 on cardid 1, sourceid 1
1685.May  2 08:32:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
1686.May  2 08:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2505 (HandleTuning) Canceling recording since tuning timeout, 180 seconds, has been exceeded.
1687.May  2 08:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2459 (HandleRecordingStatusChange) Canceled recording (Recorder Failed): "Ident X": channel 1005 on cardid 1, sourceid 1
1688.May  2 08:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1689.May  2 08:33:01 hdpvr mythbackend[7996]: E CoreContext programinfo.cpp:2278 (GetPlaybackURL) ProgramInfo(1005_20120502083000.mpg): GetPlaybackURL: '1005_20120502083000.mpg' should be local, but it can not be found.
1690.May  2 08:33:01 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from RecordingOnly to None
1691.May  2 08:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.1 = 0.00 match + 0.11 place
1692.May  2 08:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1693.May  2 08:33:01 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.2 = 0.00 match + 0.23 place
1694.May  2 08:33:04 hdpvr mythbackend[7996]: E DeleteThread mainserver.cpp:2218 (OpenAndUnlink) Error deleting 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/hdpvr/1005_20120502083000.mpg' could not open #012#011#011#011eno: No such file or directory (2)
1695.May  2 08:33:04 hdpvr mythbackend[7996]: E DeleteThread mainserver.cpp:2196 (DeleteFile) Delete Error 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/hdpvr/1005_20120502083000.mpg'#012#011#011#011eno: No such file or directory (2)
1696.May  2 08:33:08 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 0.
1697.May  2 08:33:08 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.0 = 0.00 match + 0.04 place
1698.May  2 08:33:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1699.May  2 08:38:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1700.May  2 08:43:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1701.May  2 08:47:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1702.May  2 08:48:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1703.May  2 08:54:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1704.May  2 08:59:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1705.May  2 09:02:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1706.May  2 09:04:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1707.May  2 09:09:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1708.May  2 09:14:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1709.May  2 09:17:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1710.May  2 09:19:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1711.May  2 09:24:20 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1712.May  2 09:29:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1713.May  2 09:32:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1714.May  2 09:34:28 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1715.May  2 09:39:35 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1716.May  2 09:44:40 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1717.May  2 09:47:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1718.May  2 09:49:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1719.May  2 09:54:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1720.May  2 09:59:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1721.May  2 10:02:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1722.May  2 10:04:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1723.May  2 10:09:56 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1724.May  2 10:14:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1725.May  2 10:17:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1726.May  2 10:20:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1727.May  2 10:25:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1728.May  2 10:30:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1729.May  2 10:32:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1730.May  2 10:32:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1038 at 2012-05-01T10:19:28 => "Vodacom Super Rugby 2012":"Blues vs Reds"
1731.May  2 10:32:38 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1732.May  2 10:35:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1733.May  2 10:40:08 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1734.May  2 10:45:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1735.May  2 10:47:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1736.May  2 10:50:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1737.May  2 10:55:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1738.May  2 11:00:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1739.May  2 11:02:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1740.May  2 11:05:28 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1741.May  2 11:10:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1742.May  2 11:15:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1743.May  2 11:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1744.May  2 11:20:41 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1745.May  2 11:25:45 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1746.May  2 11:30:45 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1747.May  2 11:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1748.May  2 11:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1038 at 2012-05-01T11:24:57 => "Vodacom Super Rugby 2012":"Blues vs Reds"
1749.May  2 11:33:38 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 7
1750.May  2 11:35:46 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1751.May  2 11:40:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1752.May  2 11:45:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1753.May  2 11:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1754.May  2 11:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1000 at 2012-05-01T11:41:36 => "The Wild":"S1/E225 - 1/225"
1755.May  2 11:50:56 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1756.May  2 11:56:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1757.May  2 12:01:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1758.May  2 12:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1759.May  2 12:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1038 at 2012-05-01T10:17:20 => "Vodacom Super Rugby 2012":"Blues vs Reds"
1760.May  2 12:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1038 at 2012-05-01T10:21:41 => "Vodacom Super Rugby 2012":"Blues vs Reds"
1761.May  2 12:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1038 at 2012-05-01T11:41:20 => "Vodacom Super Rugby 2012":"Blues vs Reds"
1762.May  2 12:06:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1763.May  2 12:11:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1764.May  2 12:16:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1765.May  2 12:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1766.May  2 12:21:13 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1767.May  2 12:26:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1768.May  2 12:31:21 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1769.May  2 12:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1770.May  2 12:36:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1771.May  2 12:41:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1772.May  2 12:46:27 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1773.May  2 12:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1774.May  2 12:51:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1775.May  2 12:56:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1776.May  2 13:01:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1777.May  2 13:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1778.May  2 13:06:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1779.May  2 13:11:40 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1780.May  2 13:16:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1781.May  2 13:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1782.May  2 13:21:50 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1783.May  2 13:26:51 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1784.May  2 13:31:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1785.May  2 13:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1786.May  2 13:36:57 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1787.May  2 13:42:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1788.May  2 13:47:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1789.May  2 13:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1790.May  2 13:52:02 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1791.May  2 13:57:05 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1792.May  2 14:02:06 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1793.May  2 14:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1794.May  2 14:07:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1795.May  2 14:12:13 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1796.May  2 14:17:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1797.May  2 14:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1798.May  2 14:22:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1799.May  2 14:27:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1800.May  2 14:32:29 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1801.May  2 14:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1802.May  2 14:37:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1803.May  2 14:42:40 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1804.May  2 14:47:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1805.May  2 14:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1806.May  2 14:52:48 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1807.May  2 14:57:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1808.May  2 15:02:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1809.May  2 15:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1810.May  2 15:08:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1811.May  2 15:13:05 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1812.May  2 15:18:10 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1813.May  2 15:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1814.May  2 15:23:14 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1815.May  2 15:28:16 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1816.May  2 15:33:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1817.May  2 15:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1818.May  2 15:38:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1819.May  2 15:43:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1820.May  2 15:48:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1821.May  2 15:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1822.May  2 15:53:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1823.May  2 15:58:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1824.May  2 16:03:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1825.May  2 16:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1826.May  2 16:08:36 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1827.May  2 16:13:39 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1828.May  2 16:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1829.May  2 16:18:45 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1830.May  2 16:23:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1831.May  2 16:28:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1832.May  2 16:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1833.May  2 16:34:02 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1834.May  2 16:39:04 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1835.May  2 16:44:09 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1836.May  2 16:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1837.May  2 16:49:15 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1838.May  2 16:54:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1839.May  2 16:59:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1840.May  2 17:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1841.May  2 17:04:24 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1842.May  2 17:09:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1843.May  2 17:14:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1844.May  2 17:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1845.May  2 17:19:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1846.May  2 17:24:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1847.May  2 17:29:34 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1848.May  2 17:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1849.May  2 17:34:38 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1850.May  2 17:39:40 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1851.May  2 17:44:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1852.May  2 17:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1853.May  2 17:49:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1854.May  2 17:54:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1855.May  2 17:59:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1856.May  2 18:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1857.May  2 18:05:05 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1858.May  2 18:10:12 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1859.May  2 18:15:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1860.May  2 18:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1861.May  2 18:20:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1862.May  2 18:25:21 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1863.May  2 18:30:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1864.May  2 18:30:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1865.May  2 18:30:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1866.May  2 18:30:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
1867.May  2 18:30:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
1868.May  2 18:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1869.May  2 18:35:28 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1870.May  2 18:40:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1871.May  2 18:45:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1872.May  2 18:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1873.May  2 18:50:43 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1874.May  2 18:55:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1875.May  2 19:00:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1876.May  2 19:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1877.May  2 19:05:49 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1878.May  2 19:10:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1879.May  2 19:10:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1880.May  2 19:10:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1881.May  2 19:10:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1882.May  2 19:10:55 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1883.May  2 19:16:00 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1884.May  2 19:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1885.May  2 19:21:04 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1886.May  2 19:26:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1887.May  2 19:31:11 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1888.May  2 19:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1889.May  2 19:36:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1890.May  2 19:41:18 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1891.May  2 19:46:21 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1892.May  2 19:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1893.May  2 19:51:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1894.May  2 19:51:26 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:233 (RunHouseKeeping) Running LogClean
1895.May  2 19:56:32 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1896.May  2 20:01:37 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1897.May  2 20:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1898.May  2 20:06:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1899.May  2 20:11:47 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1900.May  2 20:16:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1901.May  2 20:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1902.May  2 20:21:59 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1903.May  2 20:27:01 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1904.May  2 20:32:07 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1905.May  2 20:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1906.May  2 20:37:13 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1907.May  2 20:42:19 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1908.May  2 20:47:25 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1909.May  2 20:48:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1910.May  2 20:52:30 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1911.May  2 20:57:33 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1912.May  2 21:02:36 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1913.May  2 21:03:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1914.May  2 21:07:42 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1915.May  2 21:12:46 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1916.May  2 21:17:52 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1917.May  2 21:18:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
1918.May  2 21:22:53 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1919.May  2 21:27:58 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
1920.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1921.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1922.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1923.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1924.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1925.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1926.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1927.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1928.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1929.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1930.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1931.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1932.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1933.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1934.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1935.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1936.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1937.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1938.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1939.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1940.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1941.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1942.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1943.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1944.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1945.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1946.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1947.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1948.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1949.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1950.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1951.May  2 21:31:12 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1952.May  2 21:31:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1953.May  2 21:31:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1954.May  2 21:31:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1955.May  2 21:31:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1956.May  2 21:31:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1957.May  2 21:31:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1958.May  2 21:31:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1959.May  2 21:31:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1960.May  2 21:31:28 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1961.May  2 21:31:28 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1962.May  2 21:31:28 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1963.May  2 21:31:28 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1964.May  2 21:31:30 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1965.May  2 21:31:30 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1966.May  2 21:31:30 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1967.May  2 21:31:30 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1968.May  2 21:31:33 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1969.May  2 21:31:33 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1970.May  2 21:31:33 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1971.May  2 21:31:33 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1972.May  2 21:31:36 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1973.May  2 21:31:36 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1974.May  2 21:31:36 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1975.May  2 21:31:36 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1976.May  2 21:31:39 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1977.May  2 21:31:39 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1978.May  2 21:31:39 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1979.May  2 21:31:39 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1980.May  2 21:31:41 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1981.May  2 21:31:41 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1982.May  2 21:31:41 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1983.May  2 21:31:41 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1984.May  2 21:32:08 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 23.
1985.May  2 21:32:08 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
1986.May  2 21:32:08 hdpvr mythbackend[7996]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 1 items in 0.2 = 0.00 match + 0.20 place
1987.May  2 21:32:08 hdpvr mythbackend[7996]: I Scheduler mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 11
1988.May  2 21:32:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1989.May  2 21:32:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1990.May  2 21:32:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1991.May  2 21:32:22 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1992.May  2 21:32:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1993.May  2 21:32:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1994.May  2 21:32:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1995.May  2 21:32:23 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
1996.May  2 21:32:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
1997.May  2 21:32:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
1998.May  2 21:32:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
1999.May  2 21:32:24 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
2000.May  2 21:32:43 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
2001.May  2 21:32:43 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
2002.May  2 21:32:43 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
2003.May  2 21:32:43 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
2004.May  2 21:32:46 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
2005.May  2 21:32:46 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
2006.May  2 21:32:46 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
2007.May  2 21:32:46 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: hdpvr as a remote file transfer
2008.May  2 21:33:03 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
2009.May  2 21:33:38 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010.May  2 21:34:31 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
2011.May  2 21:34:31 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 0)
2012.May  2 21:34:31 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from None to WatchingLiveTV
2013.May  2 21:34:31 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
2014.May  2 21:34:31 hdpvr mythbackend[7996]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2) input_switch: 0 mode_switch: 0
2015.May  2 21:34:31 hdpvr mythbackend[7996]: I CoreContext mythdbcon.cpp:395 (PurgeIdleConnections) New DB connection, total: 9
2016.May  2 21:34:31 hdpvr mythbackend[7996]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2017.May  2 21:34:49 hdpvr mythbackend[7996]: E ProcessRequest tv_rec.cpp:2807 (PauseRecorder) TVRec(1): PauseRecorder() called with no recorder
2018.May  2 21:34:49 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:3459 (TuningCheckForHWChange) TVRec(1): HW Tuner: 1->1
2019.May  2 21:34:49 hdpvr mythbackend[7996]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2) input_switch: 0 mode_switch: 0
2020.May  2 21:34:49 hdpvr mythbackend[7996]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2021.May  2 21:35:09 hdpvr mythbackend[7996]: I TVRecEvent tv_rec.cpp:1014 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None
2022.May  2 21:36:37 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1000 at 2012-05-02T21:34:49 => CSI:"S12/E14 - Seeing Red"
2023.May  2 21:38:10 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
2024.May  2 21:43:12 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
2025.May  2 21:47:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
2026.May  2 21:47:55 hdpvr mythbackend[7996]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: hdpvr as a client (events: 2)
2027.May  2 21:48:17 hdpvr mythbackend[7996]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
2028.May  2 21:49:37 hdpvr mythbackend[7996]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
```

---

### Post by azmyth on 2012-05-03
> **jyavenard said:**
> Have you thought of checking your antenna cable?

Because that's what the problem is: you've got no signal

I think it's a bug because mine says no signal yet it still works.

---

### Post by azmyth on 2012-05-03
can you provide the output of

mythbackend --version

---

### Post by Chewiesw on 2012-05-04
andrew@hdpvr:~$ mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version : v0.25-60-gf444358
MythTV Branch : fixes/0.25
Network Protocol : 72
Library API : 0.25.20120408-1
QT Version : 4.7.2
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_iptv using_ivtv using_joystick_menu using_libcec using_libcrypto using_libdns_sd using_libxml2 using_lirc using_mheg using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_live using_mheg using_libass using_libxml2
andrew@hdpvr:~$

---

### Post by azmyth on 2012-05-04
Your version should have the patch. I have no other ideas.

---

### Post by anonymousdog on 2012-05-04
It sounds like you're running a set top box and your PC's capture card is accepting a feed from that STB vs actually using an embedded tuner (in the card).  Is that right?

If so, what is the output from VLC reading from that card (as in 'vlc /dev/video0')?

---

### Post by Chewiesw on 2012-05-05
That right, I am not using the pvr-150 turner.

```
andrew@hdpvr:~$ vlc /dev/video0
VLC media player 1.1.9 The Luggage (revision exported)
Warning: call to srand(1336203786)
Warning: call to rand()
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xc0eab0] inhibit interface error: Failed to connect to the D-Bus session daemon: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0xc0eab0] main interface error: no suitable interface module
[0xc2db70] main interface error: no suitable interface module
[0xafa120] main libvlc error: interface "globalhotkeys,none" initialization failed
[0xafa120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xc2ec40] qt4 interface error: Could not connect to X server
[0xc2ec40] skins2 interface error: Cannot open display
[0xc2ec40] skins2 interface error: cannot initialize OSFactory
[0xafa120] main libvlc error: interface "default" initialization failed
andrew@hdpvr:~$
```

---

### Post by someitalian123 on 2012-12-08
I'm having the same issue with the same card, the most annoying thing is it used to work until i formatted my harddrive and reinstalled ubuntu

---

### Post by nickrout on 2012-12-08
It's by no means clear what card is involved in this thread, but if it is the PVR-150 there has been a recent fix applied in 0.25-fixes, 0.26-fixes and master. Update to the current -fixes package using the mythbuntu repos and you will get the fix.

---

### Post by someitalian123 on 2012-12-08
i don't want add the ppa, because last time i had stablity isues when doing that,

---

### Post by nickrout on 2012-12-09
> **someitalian123 said:**
> i don't want add the ppa, because last time i had stablity isues when doing that,If you don't like the answers why are you even asking here for help.

I'l say again, if you have a problem with your PVR-150/250/350/500 get the latest fixes, with the fix incorporated as from 29 November. If you don't like that answer, theres nothing more we can suggest.

---

### Post by someitalian123 on 2012-12-09
as for your advice i tried upgrading and not only did it not solve the problem but it caused mythfrontend to have problems with lockups. I purged everything and removed the ppa and reinstalled the stock version from the ubuntu repo.

I then replaced my change channel script with a much less convoluted one and it fixed the problem

---

### Post by anonymousdog on 2012-12-09
> **someitalian123 said:**
> as for your advice i tried upgrading and not only did it not solve the problem but it caused mythfrontend to have problems with lockups. I purged everything and removed the ppa and reinstalled the stock version from the ubuntu repo.

I then replaced my change channel script with a much less convoluted one and it fixed the problem

Now that you fixed the problem, I would definitely activate the MB repo.  The recent fix has been a God send for PVR-150 (and similar) users.  It fixed the tuning issues noted in code.mythtv.org/trac/ticket/10732.  Yaaaay!

---

### Post by someitalian123 on 2012-12-09
I have not experienced that bug, but if I do i'll try it. but .26 locksup every time i try to exit the front end, idk if .25 the with the newest fixes is much better. However right now that I finally have it working again, after obsessing over it over the last day and a half, staying up till 6 am scouring goggle trying to find an anwser, I don't feel like messing with it anymore.

---

