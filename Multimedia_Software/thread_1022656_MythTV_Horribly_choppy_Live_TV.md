---
title: "MythTV Horribly choppy Live TV"
date: 2008-12-27
forum: Multimedia Software
---

### Post by ironslave on 2008-12-27
I am trying to setup this HTPC for about a year now and it STILL!!!!! wont work.

I used every Windows Media center possible. none of them supported my crappy TV tuner card v4l Analog Card (72 -> Prolink Pixelview PV-BT878P+9B [1554:4011])

I am running the ATI X1300 I payed alot of money for along time ago. I would hate to be forced into buying another card.

now here I am with an idea to use Linux and I finally have a system that works with my card... Kinda it at least displays my channels.

whenever I run Live Tv (I havent done anything else yet) the sound wont work until about 15 seconds into the channel or until I change channels. also I am getting 1 FPS due to audio sync issues (audio buffer issues)
I am also having major problems with enabling Xv. Myth tv keeps falling back to X11

I ran```
 sudo aticonfig --overlay-type=Xv
```

but still no Xv :(

```
 mythtv -v playback
2008-12-27 02:06:35.871 Using runtime prefix = /usr, libdir = /usr/lib
2008-12-27 02:06:35.892 XScreenSaver support enabled
2008-12-27 02:06:35.893 DPMS is active.
2008-12-27 02:06:35.904 Empty LocalHostName.
2008-12-27 02:06:35.904 Using localhost value of HTPC
2008-12-27 02:06:35.928 New DB connection, total: 1
2008-12-27 02:06:35.958 Connected to database 'mythconverg' at host: localhost
2008-12-27 02:06:35.961 Closing DB connection named 'DBManager0'
2008-12-27 02:06:35.963 Primary screen 0.
2008-12-27 02:06:35.963 Connected to database 'mythconverg' at host: localhost
2008-12-27 02:06:35.965 Using screen 0, 1680x1050 at 0,0
2008-12-27 02:06:36.011 max_width: 1680 max_height: 1050
2008-12-27 02:06:36.014 Primary screen 0.
2008-12-27 02:06:36.015 Using screen 0, 1680x1050 at 0,0
2008-12-27 02:06:36.048 Switching to square mode (G.A.N.T)
[B]2008-12-27 02:06:36.253 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory[/B]
2008-12-27 02:06:36.253 lirc_init failed for mythtv, see preceding messages
2008-12-27 02:06:36.254 JoystickMenuClient Error: Joystick disabled - Failed to read /home/htpc/.mythtv/joystickmenurc
2008-12-27 02:06:37.264 New DB connection, total: 2
2008-12-27 02:06:37.265 Connected to database 'mythconverg' at host: localhost
2008-12-27 02:06:37.426 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-12-27 02:06:37.428 Using protocol version 40
2008-12-27 02:06:37.449 TV: Attempting to change from None to WatchingLiveTV
2008-12-27 02:06:37.451 Using protocol version 40
2008-12-27 02:06:38.735 LiveTVChain(live-HTPC-2008-12-27T02:06:37): ReloadAll(): Added new recording
2008-12-27 02:06:38.745 RingBuf(/var/lib/mythtv/recordings/1033_20081227020637.nuv): OpenFile(/var/lib/mythtv/recordings/1033_20081227020637.nuv, 12)
2008-12-27 02:06:38.745 RingBuf(/var/lib/mythtv/recordings/1033_20081227020637.nuv): CalcReadAheadThresh(3086593104 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-12-27 02:06:38.772 TV: StartRecorder(): took 27 ms to start recorder.
2008-12-27 02:06:38.860 DPMS Deactivated 
2008-12-27 02:06:38.930 detectInterlace(Ignore Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2008-12-27 02:06:38.941 Opening audio device 'default'. ch 2(2) sr 32000
2008-12-27 02:06:38.956 Opening ALSA audio device 'default'.
2008-12-27 02:06:39.105 RingBuf(/var/lib/mythtv/recordings/1033_20081227020637.nuv): CalcReadAheadThresh(3086360916 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-12-27 02:06:39.106 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(0)
2008-12-27 02:06:39.108 SyncPositionMap watchingrecording, from DB: 0 entries
2008-12-27 02:06:39.109 Filling position map from 0 to 8
2008-12-27 02:06:39.111 Position map filled from Encoder to: 0
2008-12-27 02:06:39.111 SyncPositionMap watchingrecording total: 1 entries
2008-12-27 02:06:39.111 SyncPositionMap, new totframes: 0, new length: 0, posMap size: 1
2008-12-27 02:06:39.296 VideoOutput: Allowed renderers: xv-blit,xshm,opengl,xlib
2008-12-27 02:06:39.297 VideoOutput: Allowed renderers (filt: nuppel): xlib,xshm,xv-blit,opengl
2008-12-27 02:06:39.305 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(disabled) deint(onefield,onefield) filt()
2008-12-27 02:06:39.320 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.320 VDP: Rejecting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(disabled) deint(onefield,onefield) filt()
			deinterlacer onefield is not supported w/renderer quartz-blit (supported: linearblend,kerneldeint,greedyhdeint,greedyhdoubleprocessdeint,yadifdeint,yadifdoubleprocessdeint,none)
2008-12-27 02:06:39.321 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.342 VDP: LoadBestPreferences(2048x2048, 0)
2008-12-27 02:06:39.352 VDP: LoadBestPreferences(2048x2048, 60)
2008-12-27 02:06:39.360 VDP: LoadBestPreferences(480x480, 60)
2008-12-27 02:06:39.361 VideoOutput: Preferred renderer: xv-blit
2008-12-27 02:06:39.363 VideoOutput: Trying video renderer: xv-blit
2008-12-27 02:06:39.371 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(disabled) deint(onefield,onefield) filt()
2008-12-27 02:06:39.372 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.373 VDP: Rejecting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(disabled) deint(onefield,onefield) filt()
			deinterlacer onefield is not supported w/renderer quartz-blit (supported: linearblend,kerneldeint,greedyhdeint,greedyhdoubleprocessdeint,yadifdeint,yadifdoubleprocessdeint,none)
2008-12-27 02:06:39.374 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.375 VDP: LoadBestPreferences(2048x2048, 0)
2008-12-27 02:06:39.375 VDP: LoadBestPreferences(2048x2048, 60)
2008-12-27 02:06:39.454 VideoOutputXv: ctor
2008-12-27 02:06:39.537 XOff: 0, YOff: 0
2008-12-27 02:06:39.537 VDP: LoadBestPreferences(480x480, 60)
2008-12-27 02:06:39.537 Display Rect  left: 0, top: 0, width: 1680, height: 1050, aspect: 1.33333
2008-12-27 02:06:39.537 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333
2008-12-27 02:06:39.538 VideoOutputXv: Pixel dimensions: Screen 1680x1050, window 1680x1050
2008-12-27 02:06:39.539 VideoOutputXv: Estimated display dimensions: 474x303 mm  Aspect: 1.56436
2008-12-27 02:06:39.539 VideoOutputXv: Estimated window dimensions: 474x303 mm  Aspect: 1.56436
2008-12-27 02:06:39.540 VideoOutputXv: InitSetupBuffers() render: xv-blit, allowed: xv-blit,xshm,opengl,xlib
2008-12-27 02:06:39.543 VDP: Accepting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(disabled) deint(onefield,onefield) filt()
2008-12-27 02:06:39.544 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(xv-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.544 VDP: Rejecting: cmp(>= 1280 720) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(disabled) deint(onefield,onefield) filt()
			deinterlacer onefield is not supported w/renderer quartz-blit (supported: linearblend,kerneldeint,greedyhdeint,greedyhdoubleprocessdeint,yadifdeint,yadifdoubleprocessdeint,none)
2008-12-27 02:06:39.544 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) rend(quartz-blit) osd(softblend) osdfade(enabled) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.544 VDP: LoadBestPreferences(2048x2048, 0)
2008-12-27 02:06:39.544 VDP: LoadBestPreferences(2048x2048, 60)
2008-12-27 02:06:39.544 VDP: LoadBestPreferences(480x480, 60)
2[B]008-12-27 02:06:39.558 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2008-12-27 02:06:39.558 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  0
2008-12-27 02:06:39.559 VideoOutputXv: No suitable XVideo port found
2008-12-27 02:06:39.559 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-12-27 02:06:39.559 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-12-27 02:06:39.559 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x81841d8) visual(0x8180200) 
                        XJ_depth(24) WxH(1680x1050) bpl(5040)
2008-12-27 02:06:39.560 VideoOutputXv Error: Failed to create X buffers.[/B]
2008-12-27 02:06:39.560 VideoOutputXv: DiscardFrames(1)
2008-12-27 02:06:39.561 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-12-27 02:06:39.561 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:39.561 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-12-27 02:06:39.561 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:39.561 VideoOutputXv: DiscardFrames(1)
2008-12-27 02:06:39.561 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-12-27 02:06:39.561 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:39.562 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-12-27 02:06:39.562 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:39.562 VDP: SetVideoRenderer(unknown)
2008-12-27 02:06:39.562 VDP: Old preferences: rend(xv-blit) osd(softblend) deint(linearblend,linearblend) filt()
2008-12-27 02:06:39.562 VDP: New preferences: rend(unknown) osd() deint(,) filt()
2008-12-27 02:06:39.930 GLCtx: Created window and context.
2008-12-27 02:06:39.940 GLCtx: GLX Version: 1.2
2008-12-27 02:06:39.952 GLCtx: Direct rendering: Yes
2008-12-27 02:06:39.952 GLCtx: OpenGL vendor  : ATI Technologies Inc.
2008-12-27 02:06:39.952 GLCtx: OpenGL renderer: Radeon X1300 / X1550 Series
2008-12-27 02:06:39.953 GLCtx: OpenGL version : 2.1.7412 Release
2008-12-27 02:06:39.953 GLCtx: Max texture size: 4096 x 4096
2008-12-27 02:06:39.954 GLVid: Viewport: 1680x1050
2008-12-27 02:06:39.998 GLVid: Created main input texture 240x240
2008-12-27 02:06:40.007 GLVid: Created main input texture 240x240
2008-12-27 02:06:40.094 GLVid: Created main input texture 480x480
2008-12-27 02:06:40.095 GLVid: Creating master filter.
2008-12-27 02:06:40.100 GLVid: Created fragment program master.
2008-12-27 02:06:40.100 GLVid: Creating resize filter.
2008-12-27 02:06:40.120 GLCtx: Created frame buffer object (480x480).
2008-12-27 02:06:40.120 GLVid: Turning off deinterlacing.
2008-12-27 02:06:40.121 GLVid: Turning off deinterlacing.
2008-12-27 02:06:40.143 Created data @0x920fa40->0x9264042
2008-12-27 02:06:40.143 Created data @0x92640b0->0x92b86b2
2008-12-27 02:06:40.143 Created data @0x92b8720->0x930cd22
2008-12-27 02:06:40.143 Created data @0x930cd90->0x9361392
2008-12-27 02:06:40.143 Created data @0x9361400->0x93b5a02
2008-12-27 02:06:40.151 Created data @0x93b5a70->0x940a072
2008-12-27 02:06:40.152 Created data @0x940a0e0->0x945e6e2
2008-12-27 02:06:40.152 Created data @0x945e750->0x94b2d52
2008-12-27 02:06:40.152 Created data @0x94b2dc0->0x95073c2
2008-12-27 02:06:40.152 Created data @0x9507430->0x955ba32
2008-12-27 02:06:40.152 Created data @0x955baa0->0x95b00a2
2008-12-27 02:06:40.152 Created data @0x95b0110->0x9604712
2008-12-27 02:06:40.153 Created data @0x9604780->0x9658d82
2008-12-27 02:06:40.153 Created data @0x9658df0->0x96ad3f2
2008-12-27 02:06:40.163 Created data @0x96ad460->0x9701a62
2008-12-27 02:06:40.163 Created data @0x9701ad0->0x97560d2
2008-12-27 02:06:40.164 Created data @0x9756140->0x97aa742
2008-12-27 02:06:40.164 Created data @0x97aa7b0->0x97fedb2
2008-12-27 02:06:40.164 Created data @0x97fee20->0x9853422
2008-12-27 02:06:40.165 Created data @0x9853490->0x98a7a92
2008-12-27 02:06:40.165 Created data @0x98a7b00->0x98fc102
2008-12-27 02:06:40.166 Created data @0x98fc170->0x9950772
2008-12-27 02:06:40.166 Created data @0x99507e0->0x99a4de2
2008-12-27 02:06:40.166 Created data @0x99a4e50->0x99f9452
2008-12-27 02:06:40.167 Created data @0x99f94c0->0x9a4dac2
2008-12-27 02:06:40.167 Created data @0x9a4db30->0x9aa2132
2008-12-27 02:06:40.167 Created data @0x9aa21a0->0x9af67a2
2008-12-27 02:06:40.168 Created data @0x9af6810->0x9b4ae12
2008-12-27 02:06:40.168 Created data @0x9b4ae80->0x9b9f482
2008-12-27 02:06:40.168 Created data @0x9b9f4f0->0x9bf3af2
2008-12-27 02:06:40.168 Created data @0x9bf3b60->0x9c48162
2008-12-27 02:06:40.169 Created data @0x9c481d0->0x9c9c7d2
2008-12-27 02:06:40.302 VDP: GetFilteredDeint() : unknown -> ''
2008-12-27 02:06:40.304 Couldn't load deinterlace filter 
2008-12-27 02:06:40.304 Using deinterlace method 
2008-12-27 02:06:40.304 VDP: SetVideoRenderer(opengl)
2008-12-27 02:06:40.304 VDP: Old preferences: rend(unknown) osd() deint(,) filt()
2008-12-27 02:06:40.305 VDP: New preferences: rend(opengl) osd(softblend) deint(linearblend,linearblend) filt()
2008-12-27 02:06:40.305 Display Rect  left: 124, top: 0, width: 1432, height: 1050, aspect: 1.56436
2008-12-27 02:06:40.305 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333
2008-12-27 02:06:40.309 Over/underscan. V: 0, H: 0
2008-12-27 02:06:40.309 Display Rect  left: 124, top: 0, width: 1432, height: 1050, aspect: 1.56436
2008-12-27 02:06:40.309 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333
2008-12-27 02:06:40.309 VDP: LoadBestPreferences(480x480, 29.97)
2008-12-27 02:06:40.314 NVP: LoadFilters(''..) -> 0
2008-12-27 02:06:40.318 OSD Theme Dimensions W: 640 H: 480
2008-12-27 02:06:41.270 TV: StartPlayer(): took 2407 ms to start player.
2008-12-27 02:06:41.270 TV: Changing from None to WatchingLiveTV
2008-12-27 02:06:41.270 NVP: ClearAfterSeek(1)
2008-12-27 02:06:41.272 VideoOutputXv: ClearAfterSeek()
2008-12-27 02:06:41.272 VideoOutputXv: DiscardFrames(0)
2008-12-27 02:06:41.272 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-12-27 02:06:41.272 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-12-27 02:06:41.272 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:41.275 VDP: GetFilteredDeint() : opengl -> 'linearblend'
2008-12-27 02:06:41.275 VDP: GetFilteredDeint() : opengl -> 'linearblend'
2008-12-27 02:06:41.277 Using deinterlace method linearblend
2008-12-27 02:06:41.298 Realtime priority would require SUID as root.
2008-12-27 02:06:41.511 nVidiaVideoSync: Could not open device /dev/nvidia0, No such device or address
[B]2008-12-27 02:06:41.511 DRMVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2008-12-27 02:06:41.511 OpenGLVideoSync()
2008-12-27 02:06:41.512 OpenGLVideoSync: GLX Video Sync not available
2008-12-27 02:06:41.512 ~OpenGLVideoSync() -- begin
2008-12-27 02:06:41.512 ~OpenGLVideoSync() -- middle
2008-12-27 02:06:41.512 ~OpenGLVideoSync() -- end
2008-12-27 02:06:41.525 RTCVideoSync: Could not set RTC frequency, Permission denied.[/B]
2008-12-27 02:06:41.527 Using audio as timebase
2008-12-27 02:06:41.527 Video timing method: USleep with busy wait
2008-12-27 02:06:41.527 Refresh rate: 16679, frame interval: 33366
2008-12-27 02:06:41.527 NVP: Waiting for prebuffer.. 0 UUUUUuLAAAAAAAAAAAAAAAAAAAAAAAA
2008-12-27 02:06:42.142 NVP: Video is 3.35989 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.233 NVP: Video is 4.17578 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.328 NVP: Video is 5.17731 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.424 NVP: Video is 6.35554 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.508 NVP: Video is 7.6738 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.600 NVP: Video is 9.01466 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.696 NVP: Video is 10.6422 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.779 NVP: Video is 12.2899 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.873 NVP: Video is 13.9678 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:42.976 NVP: Video is 15.5259 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.071 NVP: Video is 17.1665 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.163 NVP: Video is 18.809 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.267 NVP: Video is 20.4381 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.359 NVP: Video is 22.1469 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.364 WriteAudio: buffer underrun
2008-12-27 02:06:43.444 NVP: Video is 23.7506 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.445 WriteAudio: buffer underrun
2008-12-27 02:06:43.538 NVP: Video is 25.2757 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.633 NVP: Video is 26.4794 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.635 WriteAudio: buffer underrun
2008-12-27 02:06:43.712 NVP: Video is 27.1349 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.806 NVP: Video is 27.8813 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.894 NVP: Video is 28.6584 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:43.897 WriteAudio: buffer underrun
2008-12-27 02:06:43.993 NVP: Video is 28.9639 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.081 NVP: Video is 29.2681 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.082 WriteAudio: buffer underrun
2008-12-27 02:06:44.178 NVP: Video is 29.2564 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.179 WriteAudio: buffer underrun
2008-12-27 02:06:44.276 NVP: Video is 29.5623 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.374 NVP: Video is 29.8667 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.375 WriteAudio: buffer underrun
2008-12-27 02:06:44.472 NVP: Video is 29.8252 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.476 WriteAudio: buffer underrun
2008-12-27 02:06:44.570 NVP: Video is 29.8766 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.571 WriteAudio: buffer underrun
2008-12-27 02:06:44.661 NVP: Video is 29.9975 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.745 NVP: Video is 30 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.748 WriteAudio: buffer underrun
2008-12-27 02:06:44.837 NVP: Video is 30 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.927 NVP: Video is 29.9646 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:44.931 WriteAudio: buffer underrun
2008-12-27 02:06:45.026 NVP: Video is 29.6814 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.029 WriteAudio: buffer underrun
2008-12-27 02:06:45.109 NVP: Video is 29.7911 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.207 NVP: Video is 29.9484 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.208 WriteAudio: buffer underrun
2008-12-27 02:06:45.299 NVP: Video is 29.7966 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.302 WriteAudio: buffer underrun
2008-12-27 02:06:45.401 NVP: Video is 29.7577 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.404 WriteAudio: buffer underrun
2008-12-27 02:06:45.498 NVP: Video is 29.8259 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.582 NVP: Video is 29.952 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.596 WriteAudio: buffer underrun
2008-12-27 02:06:45.681 NVP: Video is 29.7693 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.776 NVP: Video is 29.7072 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.779 WriteAudio: buffer underrun
2008-12-27 02:06:45.870 NVP: Video is 29.4134 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:45.874 WriteAudio: buffer underrun
2008-12-27 02:06:45.951 TV: Attempting to change from WatchingLiveTV to None
2008-12-27 02:06:45.952 TV: StopStuff() -- begin
2008-12-27 02:06:45.952 TV: StopStuff(): stopping ring buffer[s]
2008-12-27 02:06:45.977 NVP: Video is 29.5078 frames behind audio (too slow), dropping frame to catch up.
2008-12-27 02:06:46.000 TV: StopStuff(): stopping player[s] (1/2)
2008-12-27 02:06:46.012 TV: StopStuff(): stopping recorder[s]
2008-12-27 02:06:46.016 NVP: Exited decoder loop.
2008-12-27 02:06:46.028 VideoOutputXv: dtor
2008-12-27 02:06:46.032 VideoOutputXv: DiscardFrames(1)
2008-12-27 02:06:46.032 VideoBuffers::DiscardFrames(1): UUUUUUUUUUUUUUuuAUUUUUUUUUUUUUU
2008-12-27 02:06:46.034 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:46.034 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-12-27 02:06:46.034 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:46.034 VideoOutputXv: DiscardFrames(1)
2008-12-27 02:06:46.034 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2008-12-27 02:06:46.035 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:46.035 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2008-12-27 02:06:46.035 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2008-12-27 02:06:46.261 TV: StopStuff(): stopping player[s] (2/2)
2008-12-27 02:06:46.314 TV: StopStuff() -- end
2008-12-27 02:06:46.314 TV: Changing from WatchingLiveTV to None
2008-12-27 02:06:46.360 DPMS Reactivated.
Segmentation fault
htpc@HTPC:~$ 
```

---

### Post by ironslave on 2008-12-27
nevermind problem soled, My Motherboard died. easy fix :)

---

