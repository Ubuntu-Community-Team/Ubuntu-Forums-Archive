---
title: "Having Trouble with Home Run Prime 3  &amp; Mythtv 0.27 on 12.04 Ubuntu"
date: 2014-05-27
forum: Mythbuntu
---

### Post by mcapaldo on 2014-05-27
I got the cable card paired.  Mythtv will record channels 2-9 fine, but  higher than that and I get 1 of 2 errors when justr tgrying to view live  tv

A. ujnable to read first 2048 bytes

B. Error Opening Program Juimp File Buffer

I am using Bright Hoiuse Cable in Central Floirida

My rig:


Amd 965 Quad Core CPU
4 GB ddr2 Ram
5009 GB HD
ubuntu 12.04
Home Run Prime with SDV TAExternal
Gigabit network

Data is stored on another PC 12.04 Server
Raid 5 mdadm array on gigabit network
using samba (was working with 2 analong tuners fine before switching to HRP3.

my frontend log

May 27 20:35:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:35:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:35:44 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:39:53 mythtvserver mythfrontend.real: mythfrontend[3016]: I CoreContext tv_play.cpp:1058 (TV) TV: Creating TV object
May 27 20:39:53 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2681 (PauseIdleTimer) Suspending idle  timer
May 27 20:39:53 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:1275 (Init) TV: Created TvPlayWindow.
May 27 20:39:53 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingLiveTV
May 27 20:39:53 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:39:53 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2270 (HandleStateChange) TV: Spawning LiveTV  Recorder -- begin
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2277 (HandleStateChange) TV: Spawning LiveTV  Recorder -- end
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2298 (HandleStateChange) TV:  playbackURL(/mnt/mythtv/livetv/1005_20140528003954.mpg) cardtype(DUMMY)
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio suspend OK
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext audioplayer.cpp:164 (ReinitAudio) AudioPlayer: Enabling  Audio
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.8
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.8
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythplayer.cpp:1780 (InitAVSync) Player(1): Video timing  method: USleep with busy wait
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:5595 (StartPlayer) TV: Created player.
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from None  to WatchingLiveTV
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2471 (HandleStateChange) TV: State is LiveTV  & mctx == ctx
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2473 (HandleStateChange) TV: UpdateOSDInput done
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2475 (HandleStateChange) TV: UpdateLCD done
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2477 (HandleStateChange) TV: ITVRestart done
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:39:54 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 2  channels
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x5109920, id(AC3) type(Audio)
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 1  channels
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x4703ec0, id(AC3) type(Audio)
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x49626c0, id(MPEG2VIDEO) type(Video)
May 27 20:39:56 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiooutputbase.cpp:792 (Reconfigure) AOBase: Opening  audio device 'dmix:CARD=NVidia,DEV=8' ch 2(2) sr 48000 sf signed 32 bit  reenc 0
May 27 20:39:57 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA:  Requested 500000us got 170666 buffer time
May 27 20:39:57 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:242 (IncPreallocBufferSize) ALSA:  Try to manually increase audio buffer with: echo 192 | sudo tee  /proc/asound/card1/pcm8p/sub0/prealloc
May 27 20:39:57 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:961 (OpenMixer) ALSA: no playback  control PCM found on mixer device default
May 27 20:39:57 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:497 (OpenDevice) ALSA: Unable to  open audio mixer. Volume control disabled
May 27 20:39:57 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:39:57 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  1.69141x0.472222
May 27 20:41:24 mythtvserver mythfrontend.real: mythfrontend[3016]: W  CoreContext mythplayer.cpp:3128 (PauseDecoder) Player(1): Waited 100ms  for decoder to pause
May 27 20:41:25  mythfrontend.real: last message repeated 9 times
May 27 20:41:25 mythtvserver mythfrontend.real: mythfrontend[3016]: W  Decoder ringbuffer.cpp:1100 (WaitForReadsAllowed)  RingBuf(/mnt/mythtv/livetv/1005_20140528003955.mpg): Taking too long to  be allowed to read..
May 27 20:41:25 mythtvserver mythfrontend.real: mythfrontend[3016]: I  Decoder ringbuffer.cpp:1122 (WaitForAvail)  RingBuf(/mnt/mythtv/livetv/1005_20140528003955.mpg): Checking to see if  there's a new livetv program to switch to..
May 27 20:41:25 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:41:25 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:41:25 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext fileringbuffer.cpp:300 (OpenFile)  FileRingBuf(/mnt/mythtv/livetv/2286_20140528004125.mpg): OpenFile():  File too small (0B).
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext mythplayer.cpp:2718 (JumpToProgram) Player(1):  JumpToProgram's OpenFile failed (card type: HDHOMERUN).
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext mythplayer.cpp:2719 (JumpToProgram) LiveTVChain has 4  entries#012   DUMMY: 1005 (00:39:54 to 00:39:55)#012  HDHOMERUN: 1005  (00:39:55 to 00:41:24) discontinuous#012   DUMMY: 2286 (00:41:24 to  00:41:25) discontinuous#012* HDHOMERUN: 2286 (00:41:25 to 01:00:00)  discontinuous
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext mythplayer.cpp:2960 (EventLoop) Player(1): Unknown recorder  error, exiting decoder
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from WatchingLiveTV to None
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:41:35 mythtvserver mythfrontend.real: mythfrontend[3016]: W  CoreContext mythpainter.cpp:36 (Teardown) MythPainter: 16 images not yet  de-allocated.
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio resume OK
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from  WatchingLiveTV to None
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingLiveTV
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2270 (HandleStateChange) TV: Spawning LiveTV  Recorder -- begin
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2277 (HandleStateChange) TV: Spawning LiveTV  Recorder -- end
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2298 (HandleStateChange) TV:  playbackURL(/mnt/mythtv/livetv/1005_20140528004136.mpg) cardtype(DUMMY)
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext tv_play.cpp:2315 (HandleStateChange) TV: LiveTV not  successfully started
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private:  DPMS Reactivated 1
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:41:36 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: I CoreContext tv_play.cpp:1058 (TV) TV: Creating TV object
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2681 (PauseIdleTimer) Suspending idle  timer
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:1275 (Init) TV: Created TvPlayWindow.
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingLiveTV
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2270 (HandleStateChange) TV: Spawning LiveTV  Recorder -- begin
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2277 (HandleStateChange) TV: Spawning LiveTV  Recorder -- end
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2298 (HandleStateChange) TV:  playbackURL(/mnt/mythtv/livetv/1005_20140528004138.mpg) cardtype(DUMMY)
May 27 20:41:38 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio suspend OK
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext audioplayer.cpp:164 (ReinitAudio) AudioPlayer: Enabling  Audio
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.8
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.8
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythplayer.cpp:1780 (InitAVSync) Player(2): Video timing  method: USleep with busy wait
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:5595 (StartPlayer) TV: Created player.
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from None  to WatchingLiveTV
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2471 (HandleStateChange) TV: State is LiveTV  & mctx == ctx
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2473 (HandleStateChange) TV: UpdateOSDInput done
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2475 (HandleStateChange) TV: UpdateLCD done
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2477 (HandleStateChange) TV: ITVRestart done
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:41:39 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 2  channels
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x17d1240, id(AC3) type(Audio)
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 1  channels
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x4a3e340, id(AC3) type(Audio)
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x44c08a0, id(MPEG2VIDEO) type(Video)
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiooutputbase.cpp:792 (Reconfigure) AOBase: Opening  audio device 'dmix:CARD=NVidia,DEV=8' ch 2(2) sr 48000 sf signed 32 bit  reenc 0
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA:  Requested 500000us got 170666 buffer time
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:242 (IncPreallocBufferSize) ALSA:  Try to manually increase audio buffer with: echo 192 | sudo tee  /proc/asound/card1/pcm8p/sub0/prealloc
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:961 (OpenMixer) ALSA: no playback  control PCM found on mixer device default
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:497 (OpenDevice) ALSA: Unable to  open audio mixer. Volume control disabled
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:41:41 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  1.69141x0.472222
May 27 20:42:03 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:42:03 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:42:03 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:42:03 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext fileringbuffer.cpp:300 (OpenFile)  FileRingBuf(/mnt/mythtv/livetv/2250_20140528004204.mpg): OpenFile():  File too small (0B).
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext mythplayer.cpp:2718 (JumpToProgram) Player(2):  JumpToProgram's OpenFile failed (card type: HDHOMERUN).
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext mythplayer.cpp:2719 (JumpToProgram) LiveTVChain has 4  entries#012   DUMMY: 1005 (00:41:38 to 00:41:39)#012  HDHOMERUN: 1005  (00:41:39 to 00:42:03) discontinuous#012   DUMMY: 2250 (00:42:03 to  00:42:04) discontinuous#012* HDHOMERUN: 2250 (00:42:04 to 01:00:00)  discontinuous
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext mythplayer.cpp:2960 (EventLoop) Player(2): Unknown recorder  error, exiting decoder
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from WatchingLiveTV to None
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio resume OK
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from  WatchingLiveTV to None
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingLiveTV
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2270 (HandleStateChange) TV: Spawning LiveTV  Recorder -- begin
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext tv_play.cpp:2277 (HandleStateChange) TV: Spawning LiveTV  Recorder -- end
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2298 (HandleStateChange) TV:  playbackURL(/mnt/mythtv/livetv/1005_20140528004215.mpg) cardtype(DUMMY)
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext tv_play.cpp:2315 (HandleStateChange) TV: LiveTV not  successfully started
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private:  DPMS Reactivated 1
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:42:15 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I CoreContext tv_play.cpp:1058 (TV) TV: Creating TV object
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2681 (PauseIdleTimer) Suspending idle  timer
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:1275 (Init) TV: Created TvPlayWindow.
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingRecording
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio suspend OK
May 27 20:44:44 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext audioplayer.cpp:164 (ReinitAudio) AudioPlayer: Enabling  Audio
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 6  channels
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0xfc2e240, id(AC3) type(Audio)
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0xfc2daa0, id(MPEG2VIDEO) type(Video)
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiooutputbase.cpp:792 (Reconfigure) AOBase: Opening  audio device 'dmix:CARD=NVidia,DEV=8' ch 2(6) sr 48000 sf signed 32 bit  reenc 0
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA:  Requested 500000us got 170666 buffer time
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:242 (IncPreallocBufferSize) ALSA:  Try to manually increase audio buffer with: echo 192 | sudo tee  /proc/asound/card1/pcm8p/sub0/prealloc
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:961 (OpenMixer) ALSA: no playback  control PCM found on mixer device default
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: E  CoreContext audio/audiooutputalsa.cpp:497 (OpenDevice) ALSA: Unable to  open audio mixer. Volume control disabled
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythplayer.cpp:1780 (InitAVSync) Player(3): Video timing  method: USleep with busy wait
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:5595 (StartPlayer) TV: Created player.
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from None  to WatchingRecording
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:44:45 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:46:19 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythplayer.cpp:2130 (PrebufferEnoughFrames) Player(3):  Waited 101ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAUUUUULLP
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from WatchingRecording to None
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio resume OK
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from  WatchingRecording to None
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private:  DPMS Reactivated 1
May 27 20:49:10 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:50:05 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:50:05 mythtvserver mythfrontend.real: mythfrontend[3016]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:50:07 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour:  De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on  mythtvserver'
May 27 20:50:07 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext AirPlay/mythraopdevice.cpp:71 (Cleanup) RAOP Device:  Cleaning up.
May 27 20:50:07 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext AirPlay/mythairplayserver.cpp:377 (Cleanup) AirPlay:  Cleaning up.
May 27 20:50:07 mythtvserver mythfrontend.real: mythfrontend[3016]: I  thread_unknown bonjourregister.cpp:28 (~BonjourRegister) Bonjour:  De-registering service '_airplay._tcp.' on 'MythTV on mythtvserver'
May 27 20:50:07 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext audio/audiopulsehandler.cpp:48 (Suspend) Pulse: Cleaning up  PulseHandler
May 27 20:50:07 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext main.cpp:262 (cleanup) Shutting down UPnP client...
May 27 20:50:09 mythtvserver mythfrontend.real: mythfrontend[3016]: I  CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to  exit.
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Interrupt handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Terminated handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Segmentation fault handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted  handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus  error handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating  point exception handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal  instruction handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Real-time signal 0 handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User  defined signal 1 handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup User  defined signal 2 handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: C  thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging)  mythfrontend version: fixes/0.27 [v0.27-211-gad2f1ff] [www.mythtv.org]("http://www.mythtv.org")
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: C  thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt  version: compile: 4.8.1, runtime: 4.8.1
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled  verbose msgs:  general
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  thread_unknown logging.cpp:914 (logStart) Setting Log Level to LOG_INFO
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I Logger logging.cpp:315 (run) Added logging to the console
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  thread_unknown mythdirs.cpp:55 (InitializeMythDirs) Using runtime prefix  = /usr
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  thread_unknown mythdirs.cpp:68 (InitializeMythDirs) Using configuration  directory = /home/mediabox/.mythtv
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcorecontext.cpp:254 (Init) Assumed character encoding:  en_US.UTF-8
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext mythcontext.cpp:504 (LoadDatabaseSettings) Empty  LocalHostName.
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost  value of mythtvserver
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcontext.cpp:693 (TestDBconnection) Testing network  connectivity to '192.168.0.100'
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  SystemSignalManager mythsystemunix.cpp:510 (run) Starting process signal  handler
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  SystemManager mythsystemunix.cpp:275 (run) Starting process manager
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  SystemIOHandlerW mythsystemunix.cpp:91 (run) Starting IO manager (write)
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  SystemIOHandlerR mythsystemunix.cpp:91 (run) Starting IO manager (read)
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  LogForward loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext mythcorecontext.cpp:1328 (InitLocale) Setting QT default  locale to en_US
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcorecontext.cpp:1361 (SaveLocaleDefaults) Current locale  en_US
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale  defaults from /usr/share/mythtv//locales/en_us.xml
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext screensaver-x11.cpp:80 (ScreenSaverX11Private)  ScreenSaverX11Private: DPMS is active.
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext DisplayRes.cpp:64 (Initialize) Desktop video mode: 1920x1080  60.053 Hz
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6547
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:399 (listen) Listening on TCP  192.168.0.100:6547
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:399 (listen) Listening on TCP [::1]:6547
May 27 20:55:23 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:399 (listen) Listening on TCP  [fe80::4261:86ff:febf:a673%eth0]:6547
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for  module mythfrontend
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext lirc.cpp:320 (Init) LIRC: Successfully initialized  '/dev/lircd' using '/home/mediabox/.mythtv/lircrc' config
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext jsmenu.cpp:91 (Init) JoystickMenuThread: Joystick disabled -  Failed to read /home/mediabox/.mythtv/joystickmenurc
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext cecadapter.cpp:128 (Open) CECAdapter: Failed to load libcec.
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythudplistener.cpp:32 (Enable) UDPListener: Enabling
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:494 (bind) Binding to UDP 127.0.0.1:6948
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:494 (bind) Binding to UDP 192.168.0.100:6948
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:494 (bind) Binding to UDP [::1]:6948
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:494 (bind) Binding to UDP  [fe80::4261:86ff:febf:a673%eth0]:6948
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext serverpool.cpp:494 (bind) Binding to UDP 192.168.0.255:6948
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythmainwindow.cpp:980 (Init) Using Frameless Window
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythmainwindow.cpp:1089 (Init) Using the Qt painter
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythuiwebbrowser.cpp:1078 (LoadUserStyleSheet)  MythUIWebBrowser: Loading css from -  file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext mythuiwebbrowser.cpp:962 (Init) MythUIWebBrowser: failed to  find our parent screen
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythuiwebbrowser.cpp:991 (Init) MythUIWebBrowser: enabling  plugins
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  SendMessage mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  SendMessage mythcorecontext.cpp:1241 (CheckProtoVersion) Using protocol  version 77
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext AirPlay/mythraopdevice.cpp:30 (Create) RAOP Device: Aborting  startup - no key found.
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext AirPlay/mythairplayserver.cpp:371 (Create) AirPlay: Created  airplay objects.
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown serverpool.cpp:399 (listen) Listening on TCP  127.0.0.1:5100
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown serverpool.cpp:399 (listen) Listening on TCP  192.168.0.100:5100
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown serverpool.cpp:399 (listen) Listening on TCP [::1]:5100
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown serverpool.cpp:399 (listen) Listening on TCP  [fe80::4261:86ff:febf:a673%eth0]:5100
May 27 20:55:24 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext schemawizard.cpp:118 (Compare) Current MythTV Schema Version  (DBSchemaVer): 1317
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: I  AirplayServer bonjourregister.cpp:115 (BonjourCallback) Bonjour: Service  registration complete: name 'MythTV on mythtvserver' type  '_airplay._tcp.' domain: 'local.'
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: W  CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open  themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme  (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml  file.
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: W  CoreContext themeinfo.cpp:74 (parseThemeInfo) ThemeInfo: Unable to open  themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme  (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext mythmainwindow.cpp:1949 (RegisterMediaPlugin) Registering  Internal as a media playback plugin.
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext schemawizard.cpp:118 (Compare) Current MythMusic Schema  Version (MusicDBSchemaVer): 1020
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythtranslation.cpp:65 (load) Loading en_us translation for  module mythmusic
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext main.cpp:1063 (RunMenu) Found mainmenu.xml for theme  'MythCenter-wide'
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext housekeeper.cpp:582 (RegisterTask) Registering  HouseKeeperTask 'HardwareProfiler'.
May 27 20:55:25 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
May 27 20:55:26 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext bonjourregister.cpp:115 (BonjourCallback) Bonjour: Service  registration complete: name 'Mythfrontend on mythtvserver' type  '_mythfrontend._tcp.' domain: 'local.'
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I CoreContext tv_play.cpp:1058 (TV) TV: Creating TV object
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext mythmainwindow.cpp:2681 (PauseIdleTimer) Suspending idle  timer
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:1275 (Init) TV: Created TvPlayWindow.
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingLiveTV
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext tv_play.cpp:2270 (HandleStateChange) TV: Spawning LiveTV  Recorder -- begin
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext tv_play.cpp:2277 (HandleStateChange) TV: Spawning LiveTV  Recorder -- end
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2298 (HandleStateChange) TV:  playbackURL(/mnt/mythtv/livetv/1005_20140528005529.mpg) cardtype(DUMMY)
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio suspend OK
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext audioplayer.cpp:164 (ReinitAudio) AudioPlayer: Enabling  Audio
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:55:29 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.8
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.8
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythplayer.cpp:1780 (InitAVSync) Player(0): Video timing  method: USleep with busy wait
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:5595 (StartPlayer) TV: Created player.
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from None  to WatchingLiveTV
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2471 (HandleStateChange) TV: State is LiveTV  & mctx == ctx
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2473 (HandleStateChange) TV: UpdateOSDInput done
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2475 (HandleStateChange) TV: UpdateLCD done
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2477 (HandleStateChange) TV: ITVRestart done
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:55:30 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 2  channels
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x4b62680, id(AC3) type(Audio)
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext avformatdecoder.cpp:1898 (ScanStreams) AFD: codec AC3 has 1  channels
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x4b5dfc0, id(AC3) type(Audio)
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext videoout_xv.cpp:615 (InitXVideo) VideoOutputXv: XVideo  Adaptor Name: 'NV17 Video Texture'
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext avformatdecoder.cpp:2378 (OpenAVCodec) AFD: Opened codec  0x4f6ffa0, id(MPEG2VIDEO) type(Video)
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext audio/audiooutputbase.cpp:792 (Reconfigure) AOBase: Opening  audio device 'dmix:CARD=NVidia,DEV=8' ch 2(2) sr 48000 sf signed 32 bit  reenc 0
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext audio/audiooutputalsa.cpp:783 (SetParameters) ALSA:  Requested 500000us got 170666 buffer time
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext audio/audiooutputalsa.cpp:242 (IncPreallocBufferSize) ALSA:  Try to manually increase audio buffer with: echo 192 | sudo tee  /proc/asound/card1/pcm8p/sub0/prealloc
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext audio/audiooutputalsa.cpp:961 (OpenMixer) ALSA: no playback  control PCM found on mixer device default
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext audio/audiooutputalsa.cpp:497 (OpenDevice) ALSA: Unable to  open audio mixer. Volume control disabled
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:232 (OverrideUIScale) OSD: Base theme size: 1280x720
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext osd.cpp:234 (OverrideUIScale) OSD: Scaling factors:  0.5625x0.666667
May 27 20:55:32 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext videooutbase.cpp:1391 (DisplayOSD) VideoOutput: Created YV12  OSD.
May 27 20:55:37 mythtvserver mythfrontend.real: mythfrontend[3844]: W  CoreContext ringbuffer.cpp:526 (Start)  RingBuf(/mnt/mythtv/livetv/1070_20140528005536.mpg): Not starting read  ahead thread, already running
May 27 20:55:38 mythtvserver mythfrontend.real: mythfrontend[3844]: W  CoreContext ringbuffer.cpp:1100 (WaitForReadsAllowed)  RingBuf(/mnt/mythtv/livetv/1070_20140528005536.mpg): Taking too long to  be allowed to read..
May 27 20:55:47  mythfrontend.real: last message repeated 138 times
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext ringbuffer.cpp:1105 (WaitForReadsAllowed)  RingBuf(/mnt/mythtv/livetv/1070_20140528005536.mpg): Took more than 10  seconds to be allowed to read, aborting.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: W  CoreContext ringbuffer.cpp:1083 (Peek)  RingBuf(/mnt/mythtv/livetv/1070_20140528005536.mpg): Peek() requested  2048 bytes, but only returning 0
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext mythplayer.cpp:942 (OpenFile) Player(0): OpenFile(): Could  not read first 2048 bytes of  '/mnt/mythtv/livetv/1070_20140528005536.mpg'
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext mythplayer.cpp:5305 (SetErrored) Player(0): Error opening  jump program file
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext mythplayer.cpp:2738 (JumpToProgram) Player(0): JumpToProgram  failed.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext mythplayer.cpp:2960 (EventLoop) Player(0): Unknown recorder  error, exiting decoder
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from WatchingLiveTV to None
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt  handler
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated  handler
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: W  CoreContext mythpainter.cpp:36 (Teardown) MythPainter: 16 images not yet  de-allocated.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext audio/audiopulsehandler.cpp:322 (SuspendInternal) Pulse:  PulseAudio resume OK
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2459 (HandleStateChange) TV: Changing from  WatchingLiveTV to None
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2201 (HandleStateChange) TV: Attempting to  change from None to WatchingLiveTV
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcorecontext.cpp:423 (ConnectCommandSocket)  MythCoreContext: Connecting to backend server: 192.168.0.100:6543 (try 1  of 1)
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext tv_play.cpp:2270 (HandleStateChange) TV: Spawning LiveTV  Recorder -- begin
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext tv_play.cpp:2277 (HandleStateChange) TV: Spawning LiveTV  Recorder -- end
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2298 (HandleStateChange) TV:  playbackURL(/mnt/mythtv/livetv/1005_20140528005547.mpg) cardtype(DUMMY)
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: E  CoreContext tv_play.cpp:2315 (HandleStateChange) TV: LiveTV not  successfully started
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:2550 (HandleStateChange) TV: Main UI disabled.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:411 (StartTV) TV: Entering main playback loop.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private:  DPMS Reactivated 1
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext screensaver-x11.cpp:149 (DisableDPMS) ScreenSaverX11Private:  DPMS Deactivated 1
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext tv_play.cpp:413 (StartTV) TV: Exiting main playback loop.
May 27 20:55:47 mythtvserver mythfrontend.real: mythfrontend[3844]: N  CoreContext mythmainwindow.cpp:2686 (PauseIdleTimer) Resuming idle timer
May 27 20:55:55  mythfrontend.real: last message repeated 2 times
May 27 20:55:55 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext bonjourregister.cpp:28 (~BonjourRegister) Bonjour:  De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on  mythtvserver'
May 27 20:55:55 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext AirPlay/mythraopdevice.cpp:71 (Cleanup) RAOP Device:  Cleaning up.
May 27 20:55:55 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext AirPlay/mythairplayserver.cpp:377 (Cleanup) AirPlay:  Cleaning up.
May 27 20:55:55 mythtvserver mythfrontend.real: mythfrontend[3844]: I  thread_unknown bonjourregister.cpp:28 (~BonjourRegister) Bonjour:  De-registering service '_airplay._tcp.' on 'MythTV on mythtvserver'
May 27 20:55:55 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext audio/audiopulsehandler.cpp:48 (Suspend) Pulse: Cleaning up  PulseHandler
May 27 20:55:55 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext main.cpp:262 (cleanup) Shutting down UPnP client...
May 27 20:55:57 mythtvserver mythfrontend.real: mythfrontend[3844]: I  CoreContext mythcontext.cpp:1194 (~MythContext) Waiting for threads to  ex

my mythtvbackend log

May 27 20:30:11 mythtvserver mythbackend: mythbackend[2268]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1003 at  2014-05-21T22:28:03Z => "FOX 35 News at 6"
May 27 20:30:16  mythtvserver mythbackend: mythbackend[2268]: C CoreContext  signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID  1, UID 0, Value 0x00000000
May 27 20:30:16 mythtvserver mythbackend:  mythbackend[2268]: N CoreContext main_helpers.cpp:706 (run_backend)  MythBackend exiting
May 27 20:30:16 mythtvserver mythbackend:  mythbackend[2268]: I CoreContext bonjourregister.cpp:28  (~BonjourRegister) Bonjour: De-registering service '_mythbackend._tcp.'  on 'Mythbackend on mythtvserver'
May 27 20:30:17 mythtvserver  mythbackend: mythbackend[2268]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[24]: Changing from RecordingOnly to None
May  27 20:30:17 mythtvserver mythbackend: mythbackend[2268]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:30:17 mythtvserver mythbackend: mythbackend[2268]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[24]:  FinishedRecording(1008_2014-05-28T00:30:00Z) damaged  recq:<RecordingQuality overall_score="0"  key="1008_2014-05-28T00:30:00Z" countinuity_error_count="0"  packet_count="23273">#012    <Gap start="2014-05-28T00:30:16Z"  end="2014-05-28T01:00:00Z" duration="1783"  />#012</RecordingQuality>
May 27 20:30:17 mythtvserver  mythbackend: mythbackend[2268]: E TVRecEvent  recorders/hdhrstreamhandler.cpp:389 (TunerGet) HDHRSH(192.168.0.120-3):  DeviceGet(channel): ERROR: unknown getset variable
May 27 20:30:17  mythtvserver mythbackend: mythbackend[2268]: E TVRecEvent  recorders/hdhrstreamhandler.cpp:429 (TunerSet) HDHRSH(192.168.0.120-3):  DeviceSet(channel none): ERROR: unknown getset variable
May 27  20:30:17 mythtvserver mythbackend: mythbackend[2268]: E CoreContext  recorders/hdhrstreamhandler.cpp:389 (TunerGet) HDHRSH(192.168.0.120-3):  DeviceGet(channel): ERROR: unknown getset variable
May 27 20:30:17  mythtvserver mythbackend: mythbackend[2268]: E CoreContext  recorders/hdhrstreamhandler.cpp:429 (TunerSet) HDHRSH(192.168.0.120-3):  DeviceSet(channel none): ERROR: unknown getset variable
May 27  20:30:17 mythtvserver mythbackend: mythbackend[2268]: I CoreContext  mythcontext.cpp:1194 (~MythContext) Waiting for threads to exit.
May  27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: C  thread_unknown mythcommandlineparser.cpp:2595 (ConfigureLogging)  mythbackend version: fixes/0.27 [v0.27-211-gad2f1ff] [www.mythtv.org](www.mythtv.org)
May  27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: C  thread_unknown mythcommandlineparser.cpp:2597 (ConfigureLogging) Qt  version: compile: 4.8.1, runtime: 4.8.1
May 27 20:33:03 mythtvserver  mythbackend: mythbackend[2975]: N thread_unknown  mythcommandlineparser.cpp:2599 (ConfigureLogging) Enabled verbose msgs:   general
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]:  N thread_unknown logging.cpp:914 (logStart) Setting Log Level to  LOG_INFO
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I Logger logging.cpp:315 (run) Added logging to the console
May  27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Interrupt handler
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I thread_unknown signalhandling.cpp:194  (SetHandlerPrivate) Setup Terminated handler
May 27 20:33:03  mythtvserver mythbackend: mythbackend[2975]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault  handler
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted  handler
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]:  I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus  error handler
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I thread_unknown signalhandling.cpp:194  (SetHandlerPrivate) Setup Floating point exception handler
May 27  20:33:03 mythtvserver mythbackend: mythbackend[2975]: I thread_unknown  signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction  handler
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I  thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup  Real-time signal 0 handler
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: N thread_unknown mythdirs.cpp:55 (InitializeMythDirs)  Using runtime prefix = /usr
May 27 20:33:03 mythtvserver  mythbackend: mythbackend[2975]: N thread_unknown mythdirs.cpp:68  (InitializeMythDirs) Using configuration directory =  /home/mythtv/.mythtv
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext mythcorecontext.cpp:254 (Init) Assumed  character encoding: en_US.UTF-8
May 27 20:33:03 mythtvserver  mythbackend: mythbackend[2975]: N CoreContext mythcontext.cpp:504  (LoadDatabaseSettings) Empty LocalHostName.
May 27 20:33:03  mythtvserver mythbackend: mythbackend[2975]: I CoreContext  mythcontext.cpp:512 (LoadDatabaseSettings) Using localhost value of  mythtvserver
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: N CoreContext mythcorecontext.cpp:1328 (InitLocale)  Setting QT default locale to en_US
May 27 20:33:03 mythtvserver  mythbackend: mythbackend[2975]: I CoreContext mythcorecontext.cpp:1361  (SaveLocaleDefaults) Current locale en_US
May 27 20:33:03  mythtvserver mythbackend: mythbackend[2975]: N CoreContext  mythlocale.cpp:121 (LoadDefaultsFromXML) Reading locale defaults from  /usr/share/mythtv//locales/en_us.xml
May 27 20:33:03 mythtvserver  mythbackend: mythbackend[2975]: I CoreContext schemawizard.cpp:118  (Compare) Current MythTV Schema Version (DBSchemaVer): 1317
May 27  20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  mythtranslation.cpp:65 (load) Loading en_us translation for module  mythfrontend
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: N CoreContext main_helpers.cpp:582 (run_backend)  MythBackend: Starting up as the master server.
May 27 20:33:03  mythtvserver mythbackend: mythbackend[2975]: I LogForward  loggingserver.cpp:1372 (forwardMessage) New Client:  (#1)
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
May  27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  programinfo.cpp:2136 (CheckProgramIDAuthorities) Found 1 distinct  programid authorities
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler mythdbcon.cpp:436 (getStaticCon) New  static DB connectionSchedCon
May 27 20:33:03 mythtvserver  mythbackend: mythbackend[2975]: I CoreContext housekeeper.cpp:582  (RegisterTask) Registering HouseKeeperTask 'LogClean'.
May 27  20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask  'DBCleanup'.
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext housekeeper.cpp:582 (RegisterTask)  Registering HouseKeeperTask 'ThemeUpdateNotifications'.
May 27  20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask  'RecordedArtworkUpdate'.
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext housekeeper.cpp:582 (RegisterTask)  Registering HouseKeeperTask 'MythFillDB'.
May 27 20:33:03  mythtvserver mythbackend: mythbackend[2975]: I CoreContext  housekeeper.cpp:582 (RegisterTask) Registering HouseKeeperTask  'JobQueueRecover'.
May 27 20:33:03 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext housekeeper.cpp:582 (RegisterTask)  Registering HouseKeeperTask 'HardwareProfiler'.
May 27 20:33:03  mythtvserver mythbackend: mythbackend[2975]: I CoreContext  housekeeper.cpp:648 (Start) Queueing HouseKeeperTask  'ThemeUpdateNotifications'.
May 27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext housekeeper.cpp:655 (Start) Starting HouseKeeper.
May  27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6544
May 27  20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP 192.168.0.100:6544
May  27 20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP [::1]:6544
May 27  20:33:03 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP  [fe80::4261:86ff:febf:a673%eth0]:6544
May 27 20:33:04 mythtvserver  mythbackend: mythbackend[2975]: I CoreContext main_helpers.cpp:668  (run_backend) Main::Registering HttpStatus Extension
May 27 20:33:04  mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP 127.0.0.1:6543
May 27  20:33:04 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP 192.168.0.100:6543
May  27 20:33:04 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP [::1]:6543
May 27  20:33:04 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  serverpool.cpp:399 (listen) Listening on TCP  [fe80::4261:86ff:febf:a673%eth0]:6543
May 27 20:33:04 mythtvserver  mythbackend: mythbackend[2975]: N CoreContext autoexpire.cpp:264  (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB  w/freq: 15 min
May 27 20:33:05 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext bonjourregister.cpp:115  (BonjourCallback) Bonjour: Service registration complete: name  'Mythbackend on mythtvserver' type '_mythbackend._tcp.' domain: 'local.'
May  27 20:33:06 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH 0 0  0 - SchedulerInit
May 27 20:33:08 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2211 (HandleReschedule)  Scheduled 1179 items in 1.6 = 0.10 match + 0.44 check + 1.02 place
May  27 20:33:08 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2269 (HandleRunSchedulerStartup) Scheduler: AUTO-Startup  assumed
May 27 20:33:08 mythtvserver mythbackend: mythbackend[2975]: I  TVRecEvent tv_rec.cpp:1050 (HandleStateChange) TVRec[24]: Changing from  None to RecordingOnly
May 27 20:33:08 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[24]: HW Tuner: 24->24
May 27 20:33:08 mythtvserver  mythbackend: mythbackend[2975]: N Scheduler autoexpire.cpp:264  (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB  w/freq: 14 min
May 27 20:33:08 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2648  (HandleRecordingStatusChange) Tuning recording: "The Originals":"Always  and Forever": channel 1008 on cardid 24, sourceid 1
May 27 20:33:09  mythtvserver mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[24](192.168.0.120-0): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(14) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      8 has PID 0x0320
May 27 20:33:09 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[24](192.168.0.120-0): But there is only one program in the  PAT, so we'll just use it
May 27 20:33:09 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext scheduler.cpp:704 (UpdateRecStatus)  Updating status for "The Originals":"Always and Forever" on cardid 24  (Tuning => Recording)
May 27 20:33:10 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-0): UpdateFilters called in wrong tune mode
May  27 20:33:10 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:4126 (TuningNewRecorder) TVRec[24]: rec->GetPathname():  '/mnt/mythtv/recordings/1008_20140528003300.mpg'
May 27 20:33:10  mythtvserver mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[24](192.168.0.120-0): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:33:12 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 20:33:12 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 20:33:12  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  20:33:12 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 20:33:13 mythtvserver mythbackend:  mythbackend[2975]: I Metadata_16261 jobqueue.cpp:2156  (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "The  Originals":"Always and Forever" recorded from channel 1008 at  2014-05-28T00:30:00Z
May 27 20:33:13 mythtvserver mythbackend:  mythbackend[2975]: I SystemManager mythsystemunix.cpp:275 (run) Starting  process manager
May 27 20:33:13 mythtvserver mythbackend:  mythbackend[2975]: I SystemSignalManager mythsystemunix.cpp:510 (run)  Starting process signal handler
May 27 20:33:13 mythtvserver  mythbackend: mythbackend[2975]: I SystemIOHandlerR mythsystemunix.cpp:91  (run) Starting IO manager (read)
May 27 20:33:13 mythtvserver  mythbackend: mythbackend[2975]: I SystemIOHandlerW mythsystemunix.cpp:91  (run) Starting IO manager (write)
May 27 20:33:15 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Monitor
May 27 20:33:15 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1422  (HandleAnnounce) adding: mythtvserver as a client (events: 0)
May 27  20:33:15 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  20:33:15 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 20:33:18 mythtvserver mythbackend:  mythbackend[2975]: E ProcessRequest programinfo.cpp:2358  (GetPlaybackURL) ProgramInfo(1041_20140106190000.mpg): GetPlaybackURL:  '1041_20140106190000.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1061_20140106190000.mpg): GetPlaybackURL:  '1061_20140106190000.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215401.mpg): GetPlaybackURL:  '1066_20140207215401.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215203.mpg): GetPlaybackURL:  '1066_20140207215203.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215400.mpg): GetPlaybackURL:  '1066_20140207215400.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215301.mpg): GetPlaybackURL:  '1066_20140207215301.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215500.mpg): GetPlaybackURL:  '1066_20140207215500.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215300.mpg): GetPlaybackURL:  '1066_20140207215300.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215200.mpg): GetPlaybackURL:  '1066_20140207215200.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215402.mpg): GetPlaybackURL:  '1066_20140207215402.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215403.mpg): GetPlaybackURL:  '1066_20140207215403.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215404.mpg): GetPlaybackURL:  '1066_20140207215404.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215405.mpg): GetPlaybackURL:  '1066_20140207215405.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215406.mpg): GetPlaybackURL:  '1066_20140207215406.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215407.mpg): GetPlaybackURL:  '1066_20140207215407.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215408.mpg): GetPlaybackURL:  '1066_20140207215408.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215409.mpg): GetPlaybackURL:  '1066_20140207215409.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215501.mpg): GetPlaybackURL:  '1066_20140207215501.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215502.mpg): GetPlaybackURL:  '1066_20140207215502.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215800.mpg): GetPlaybackURL:  '1066_20140207215800.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215801.mpg): GetPlaybackURL:  '1066_20140207215801.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215802.mpg): GetPlaybackURL:  '1066_20140207215802.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215803.mpg): GetPlaybackURL:  '1066_20140207215803.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215804.mpg): GetPlaybackURL:  '1066_20140207215804.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215805.mpg): GetPlaybackURL:  '1066_20140207215805.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1070_20140513003629.mpg): GetPlaybackURL:  '1070_20140513003629.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1004_20140513003638.mpg): GetPlaybackURL:  '1004_20140513003638.mpg' should be local, but it can not be found.
May  27 20:33:18 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1003_20140521222738.mpg): GetPlaybackURL:  '1003_20140521222738.mpg' should be local, but it can not be found.
May  27 20:33:19 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Monitor
May 27 20:33:19 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 20:33:19 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Monitor
May 27 20:33:19 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1422  (HandleAnnounce) adding: mythtvserver as a client (events: 0)
May 27  20:33:19 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  20:33:19 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 20:33:19 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 20:33:19 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 1)
May 27 20:33:22  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  20:33:22 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:33:22 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 20:33:22 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 1)
May 27 20:33:27  mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for CHECK 0  899 0 DoHandleDelete1 | The Originals | Always and Forever | Klaus  returns to the French Quarter of New Orleans, which his family helped  build 300 years ago; a powerful witch reveals important news about  Hayley, a werewolf who had a fling with Klaus. | EP017316280001
May  27 20:33:28 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2211 (HandleReschedule) Scheduled 1179 items in 1.1 = 0.00  match + 0.00 check + 1.12 place
May 27 20:33:30 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:33:30  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:33:49 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Playback
May 27 20:33:49 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 20:33:49  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:1050 (HandleStateChange) TVRec[27]: Changing from None to  WatchingLiveTV
May 27 20:33:49 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:33:49 mythtvserver  mythbackend: mythbackend[2975]: N CoreContext autoexpire.cpp:264  (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB  w/freq: 7 min
May 27 20:33:50 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(9) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number     10 has PID 0x03e8
May 27 20:33:50 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:33:50 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:33:50 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:33:50 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[27](192.168.0.120-1): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:33:55 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:33:55 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:33:55 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:33:56 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(11) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:33:56 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:33:56 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:33:56 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:02 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:02 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:34:02 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:03 mythtvserver  mythbackend: mythbackend[2975]: I CoreContext housekeeper.cpp:674 (Run)  Queueing HouseKeeperTask 'DBCleanup'.
May 27 20:34:03 mythtvserver  mythbackend: mythbackend[2975]: I CoreContext housekeeper.cpp:674 (Run)  Queueing HouseKeeperTask 'JobQueueRecover'.
May 27 20:34:03  mythtvserver mythbackend: mythbackend[2975]: I CoreContext  housekeeper.cpp:674 (Run) Queueing HouseKeeperTask 'LogClean'.
May 27  20:34:03 mythtvserver mythbackend: mythbackend[2975]: I HouseKeeping  housekeeper.cpp:133 (Run) Running HouseKeeperTask  'ThemeUpdateNotifications'.
May 27 20:34:03 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(13) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      4 has PID 0x0190
May 27 20:34:03 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:34:04 mythtvserver mythbackend:  mythbackend[2975]: N HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:367 (HandlePMT)  DTVSigMon[27](192.168.0.120-1): PMT says program 4 is encrypted
May  27 20:34:04 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:04 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:04 mythtvserver  mythbackend: mythbackend[2975]: I HouseKeeping housekeeper.cpp:151 (Run)  HouseKeeperTask 'ThemeUpdateNotifications' Finished Successfully.
May  27 20:34:04 mythtvserver mythbackend: mythbackend[2975]: I HouseKeeping  housekeeper.cpp:133 (Run) Running HouseKeeperTask 'DBCleanup'.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:22 mythtvserver  mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 10 MB for 1002 at 2014-01-06T17:28:42Z  => "Q Check":"Style Edition"
May 27 20:34:22 mythtvserver  mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 0 MB for 1069 at 2014-05-21T21:41:53Z  => "Lake Placid 3"
May 27 20:34:22 mythtvserver mythbackend:  mythbackend[2975]: E CoreContext programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1002_20140106122842.mpg): GetPlaybackURL:  '1002_20140106122842.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1002_20140106122842.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 65 MB for 1043 at  2014-01-07T16:52:00Z => "Cajun Pawn Stars":"Cash Cows"
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 73 MB for 1020 at  2014-01-07T16:52:00Z => "Law & Order":"Tabula Rasa"
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 75 MB for 1042 at  2014-01-07T16:52:00Z => "CSI: Miami":Dishonor
May 27 20:34:22  mythtvserver mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 80 MB for 1011 at 2014-01-07T16:52:00Z  => Supernatural:Shadow
May 27 20:34:22 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 82 MB for 1036 at 2014-01-07T16:52:00Z => "Looney Tunes"
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 86 MB for 1060 at  2014-01-07T16:52:00Z => "Storage Hunters":"Rhinestones and Thrones"
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1043_20140107115200.mpg): GetPlaybackURL:  '1043_20140107115200.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1043_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1020_20140107115200.mpg): GetPlaybackURL:  '1020_20140107115200.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1020_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1042_20140107115200.mpg): GetPlaybackURL:  '1042_20140107115200.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1042_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1011_20140107115200.mpg): GetPlaybackURL:  '1011_20140107115200.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1011_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1036_20140107115200.mpg): GetPlaybackURL:  '1036_20140107115200.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1036_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1060_20140107115200.mpg): GetPlaybackURL:  '1060_20140107115200.mpg' should be local, but it can not be found.
May  27 20:34:22 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1060_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:34:23 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:1050 (HandleStateChange) TVRec[27]: Changing from  WatchingLiveTV to None
May 27 20:34:23 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:23 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[27]:  FinishedRecording(1041_2014-05-28T00:34:04Z) damaged  recq:<RecordingQuality overall_score="0"  key="1041_2014-05-28T00:34:04Z" countinuity_error_count="1"  packet_count="128">#012    <Gap start="2014-05-28T00:00:00Z"  end="2014-05-28T01:00:00Z" duration="3600"  />#012</RecordingQuality>
May 27 20:34:23 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:34:23  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:34:23 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:34:23  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:34:24 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:24 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:34:24 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(15) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:34:24 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:34:24 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:26 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Playback
May 27 20:34:26 mythtvserver mythbackend: mythbackend[2975]:  I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 20:34:26 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from None to WatchingLiveTV
May  27 20:34:26 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:34:26 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:27 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(17) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:34:27 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:34:27 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:27 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:27 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[27](192.168.0.120-1): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:34:38 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:34:38 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:39 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:57 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:34:57 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:34:57 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[27]:  FinishedRecording(1039_2014-05-28T00:34:39Z) damaged  recq:<RecordingQuality overall_score="0"  key="1005_2014-05-28T00:34:27Z" countinuity_error_count="0"  packet_count="23776">#012    <Gap start="2014-05-28T00:00:00Z"  end="2014-05-28T00:34:27Z" duration="2067" />#012    <Gap  start="2014-05-28T00:34:36Z" end="2014-05-28T01:00:00Z" duration="1523"  />#012</RecordingQuality>
May 27 20:34:57 mythtvserver  mythbackend: mythbackend[2975]: E ProcessRequest mainserver.cpp:1719  (SendResponse) SendResponse: Unable to write to client socket, as it's  no longer there
May 27 20:34:57 mythtvserver mythbackend:  mythbackend[2975]: I HouseKeeping housekeeper.cpp:151 (Run)  HouseKeeperTask 'DBCleanup' Finished Successfully.
May 27 20:34:57  mythtvserver mythbackend: mythbackend[2975]: I HouseKeeping  housekeeper.cpp:133 (Run) Running HouseKeeperTask 'JobQueueRecover'.
May  27 20:34:57 mythtvserver mythbackend: mythbackend[2975]: E  MythSocketThread(71) mythsocket.cpp:685 (WriteStringListReal)  MythSocket(264b7d0:-1): WriteStringList: Error, called with unconnected  socket.
May 27 20:34:57 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Playback
May 27 20:34:57 mythtvserver mythbackend: mythbackend[2975]:  I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 20:34:57 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:34:57  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:34:57 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:34:58  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:34:58 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:34:58 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:34:58 mythtvserver mythbackend: mythbackend[2975]: I HouseKeeping  housekeeper.cpp:151 (Run) HouseKeeperTask 'JobQueueRecover' Finished  Successfully.
May 27 20:34:58 mythtvserver mythbackend:  mythbackend[2975]: I HouseKeeping housekeeper.cpp:133 (Run) Running  HouseKeeperTask 'LogClean'.
May 27 20:34:58 mythtvserver mythbackend:  mythbackend[2975]: I HouseKeeping housekeeper.cpp:151 (Run)  HouseKeeperTask 'LogClean' Finished Successfully.
May 27 20:35:01  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
May 27  20:35:01 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:35:01 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:35:01  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:35:01 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:35:02 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(23) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:35:02 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:35:02 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:35:02 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:35:02 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[27](192.168.0.120-1): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:35:33 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:35:33 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:35:33 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:35:33 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(25) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      4 has PID 0x0190
May 27 20:35:33 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:35:33 mythtvserver mythbackend:  mythbackend[2975]: N HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:367 (HandlePMT)  DTVSigMon[27](192.168.0.120-1): PMT says program 4 is encrypted
May  27 20:35:33 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:35:33 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:35:33 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent recordinginfo.cpp:928  (InsertProgram)  RecordingInfo::InsertProgram(ProgramInfo(1041_20140528003533.mpg):  channame(The Discovery Channel) startts(Wed May 28 00:00:00 2014)  endts(Wed May 28 01:00:00 2014)#012             recstartts(Wed May 28  00:35:33 2014) recendts(Wed May 28 01:00:00 2014)#012              title(Deadliest Catch: The Bait)): recording already exists...
May 27  20:35:44 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:1050 (HandleStateChange) TVRec[27]: Changing from  WatchingLiveTV to None
May 27 20:35:44 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:35:44 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[27]:  FinishedRecording(1041_2014-05-28T00:35:34Z) damaged  recq:<RecordingQuality overall_score="0"  key="1041_2014-05-28T00:35:34Z">#012    <Gap  start="2014-05-28T00:00:00Z" end="2014-05-28T01:00:00Z" duration="3600"  />#012</RecordingQuality>
May 27 20:35:44 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:35:44  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:35:44 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:35:44  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:35:44 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:35:44 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:36:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1003 at  2014-05-28T00:33:49Z => Riot:"Jason Alexander and Cheryl Hines"
May  27 20:36:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 1 MB for 1003 at  2014-05-28T00:33:50Z => Riot:"Jason Alexander and Cheryl Hines"
May  27 20:36:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:33:55Z => Bones:"The Bone That Blew"
May 27 20:36:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 1 MB for 1005 at  2014-05-28T00:33:56Z => Bones:"The Bone That Blew"
May 27 20:36:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1041 at  2014-05-28T00:34:02Z => "Deadliest Catch: The Bait":"Out of Bounds"
May  27 20:36:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1041 at  2014-05-28T00:34:04Z => "Deadliest Catch: The Bait":"Out of Bounds"
May  27 20:36:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:34:24Z => Bones:"The Bone That Blew"
May 27 20:36:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:34:26Z => Bones:"The Bone That Blew"
May 27 20:36:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 4 MB for 1005 at  2014-05-28T00:34:27Z => Bones:"The Bone That Blew"
May 27 20:36:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1039 at  2014-05-28T00:34:39Z => "Modern Family":"Slow Down Your Neighbors"
May  27 20:36:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:34:58Z => Bones:"The Bone That Blew"
May 27 20:36:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:35:01Z => Bones:"The Bone That Blew"
May 27 20:38:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 9 MB for 1005 at  2014-05-28T00:35:02Z => Bones:"The Bone That Blew"
May 27 20:38:21  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1041 at  2014-05-28T00:35:33Z => "Deadliest Catch: The Bait":"Out of Bounds"
May  27 20:38:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1041 at  2014-05-28T00:35:34Z => "Deadliest Catch: The Bait":"Out of Bounds"
May  27 20:38:21 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:35:44Z => Bones:"The Bone That Blew"
May 27 20:39:53  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
May 27  20:39:53 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:39:53 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:39:53  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:39:54 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:39:55 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(29) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:39:55 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:39:55 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:39:55 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:39:55 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[27](192.168.0.120-1): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:41:24 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:41:24 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:41:24 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:41:25 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(31) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number     12 has PID 0x04b0
May 27 20:41:25 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:41:25 mythtvserver mythbackend:  mythbackend[2975]: N HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:367 (HandlePMT)  DTVSigMon[27](192.168.0.120-1): PMT says program 12 is encrypted
May  27 20:41:25 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:41:25 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:41:36 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:41:36 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:41:36 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[27]:  FinishedRecording(2286_2014-05-28T00:41:25Z) damaged  recq:<RecordingQuality overall_score="0"  key="2286_2014-05-28T00:41:25Z">#012    <Gap  start="2014-05-27T22:30:00Z" end="2014-05-28T01:00:00Z" duration="9000"  />#012</RecordingQuality>
May 27 20:41:36 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:41:36  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:41:36 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:41:36  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:41:36 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:41:36 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:41:38 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Playback
May 27 20:41:38 mythtvserver mythbackend: mythbackend[2975]:  I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 20:41:38 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from None to WatchingLiveTV
May  27 20:41:38 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:41:38 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:41:39 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(3) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:41:39 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:41:39 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:41:39 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:41:39 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[27](192.168.0.120-1): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:42:03 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:42:03 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:42:03 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:42:04 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(5) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number     12 has PID 0x04b0
May 27 20:42:04 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:42:04 mythtvserver mythbackend:  mythbackend[2975]: N HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:367 (HandlePMT)  DTVSigMon[27](192.168.0.120-1): PMT says program 12 is encrypted
May  27 20:42:04 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:42:04 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:42:15 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:42:15 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:42:15 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[27]:  FinishedRecording(2250_2014-05-28T00:42:04Z) damaged  recq:<RecordingQuality overall_score="0"  key="2250_2014-05-28T00:42:04Z">#012    <Gap  start="2014-05-28T00:30:00Z" end="2014-05-28T01:00:00Z" duration="1800"  />#012</RecordingQuality>
May 27 20:42:15 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:42:15  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:42:15 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:42:15  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:42:15 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:42:15 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 14 min
May 27 20:42:20 mythtvserver  mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 0 MB for 1005 at 2014-05-28T00:39:54Z  => Bones:"The Bone That Blew"
May 27 20:42:20 mythtvserver  mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 10 MB for 1002 at 2014-01-06T17:28:42Z  => "Q Check":"Style Edition"
May 27 20:42:20 mythtvserver  mythbackend: mythbackend[2975]: E CoreContext programinfo.cpp:2358  (GetPlaybackURL) ProgramInfo(1002_20140106122842.mpg): GetPlaybackURL:  '1002_20140106122842.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1002_20140106122842.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 65 MB for 1043 at  2014-01-07T16:52:00Z => "Cajun Pawn Stars":"Cash Cows"
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 73 MB for 1020 at  2014-01-07T16:52:00Z => "Law & Order":"Tabula Rasa"
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 75 MB for 1042 at  2014-01-07T16:52:00Z => "CSI: Miami":Dishonor
May 27 20:42:20  mythtvserver mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 80 MB for 1011 at 2014-01-07T16:52:00Z  => Supernatural:Shadow
May 27 20:42:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 82 MB for 1036 at 2014-01-07T16:52:00Z => "Looney Tunes"
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 86 MB for 1060 at  2014-01-07T16:52:00Z => "Storage Hunters":"Rhinestones and Thrones"
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 4 MB for 1008 at  2014-05-28T00:30:00Z => "The Originals":"Always and Forever"
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1043_20140107115200.mpg): GetPlaybackURL:  '1043_20140107115200.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1043_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1020_20140107115200.mpg): GetPlaybackURL:  '1020_20140107115200.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1020_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1042_20140107115200.mpg): GetPlaybackURL:  '1042_20140107115200.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1042_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1011_20140107115200.mpg): GetPlaybackURL:  '1011_20140107115200.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1011_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1036_20140107115200.mpg): GetPlaybackURL:  '1036_20140107115200.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1036_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1060_20140107115200.mpg): GetPlaybackURL:  '1060_20140107115200.mpg' should be local, but it can not be found.
May  27 20:42:20 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1060_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:44:20 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 33 MB for 1005 at  2014-05-28T00:39:55Z => Bones:"The Bone That Blew"
May 27 20:44:20  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 2286 at  2014-05-28T00:41:24Z => "Red Riding Hood"
May 27 20:44:20  mythtvserver mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 0 MB for 2286 at 2014-05-28T00:41:25Z  => "Red Riding Hood"
May 27 20:44:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 0 MB for 1005 at 2014-05-28T00:41:36Z => Bones:"The Bone  That Blew"
May 27 20:44:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 0 MB for 1005 at 2014-05-28T00:41:38Z => Bones:"The Bone  That Blew"
May 27 20:44:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 9 MB for 1005 at 2014-05-28T00:41:39Z => Bones:"The Bone  That Blew"
May 27 20:44:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 0 MB for 2250 at 2014-05-28T00:42:03Z => "Flip or  Flop":"Awkward Floor Plan"
May 27 20:44:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 0 MB for 2250 at 2014-05-28T00:42:04Z => "Flip or  Flop":"Awkward Floor Plan"
May 27 20:44:20 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 0 MB for 1005 at 2014-05-28T00:42:15Z => Bones:"The Bone  That Blew"
May 27 20:44:42 mythtvserver mythbackend:  mythbackend[2975]: E ProcessRequest programinfo.cpp:2358  (GetPlaybackURL) ProgramInfo(1041_20140106190000.mpg): GetPlaybackURL:  '1041_20140106190000.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1061_20140106190000.mpg): GetPlaybackURL:  '1061_20140106190000.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215401.mpg): GetPlaybackURL:  '1066_20140207215401.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215203.mpg): GetPlaybackURL:  '1066_20140207215203.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215400.mpg): GetPlaybackURL:  '1066_20140207215400.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215301.mpg): GetPlaybackURL:  '1066_20140207215301.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215500.mpg): GetPlaybackURL:  '1066_20140207215500.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215300.mpg): GetPlaybackURL:  '1066_20140207215300.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215200.mpg): GetPlaybackURL:  '1066_20140207215200.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215402.mpg): GetPlaybackURL:  '1066_20140207215402.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215403.mpg): GetPlaybackURL:  '1066_20140207215403.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215404.mpg): GetPlaybackURL:  '1066_20140207215404.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215405.mpg): GetPlaybackURL:  '1066_20140207215405.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215406.mpg): GetPlaybackURL:  '1066_20140207215406.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215407.mpg): GetPlaybackURL:  '1066_20140207215407.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215408.mpg): GetPlaybackURL:  '1066_20140207215408.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215409.mpg): GetPlaybackURL:  '1066_20140207215409.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215501.mpg): GetPlaybackURL:  '1066_20140207215501.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215502.mpg): GetPlaybackURL:  '1066_20140207215502.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215800.mpg): GetPlaybackURL:  '1066_20140207215800.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215801.mpg): GetPlaybackURL:  '1066_20140207215801.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215802.mpg): GetPlaybackURL:  '1066_20140207215802.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215803.mpg): GetPlaybackURL:  '1066_20140207215803.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215804.mpg): GetPlaybackURL:  '1066_20140207215804.mpg' should be local, but it can not be found.
May  27 20:44:42 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215805.mpg): GetPlaybackURL:  '1066_20140207215805.mpg' should be local, but it can not be found.
May  27 20:44:43 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1070_20140513003629.mpg): GetPlaybackURL:  '1070_20140513003629.mpg' should be local, but it can not be found.
May  27 20:44:43 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1004_20140513003638.mpg): GetPlaybackURL:  '1004_20140513003638.mpg' should be local, but it can not be found.
May  27 20:44:43 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1003_20140521222738.mpg): GetPlaybackURL:  '1003_20140521222738.mpg' should be local, but it can not be found.
May  27 20:44:43 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1005_20140528004136.mpg): GetPlaybackURL:  '1005_20140528004136.mpg' should be local, but it can not be found.
May  27 20:44:44 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Playback
May 27 20:44:44 mythtvserver mythbackend: mythbackend[2975]:  I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 20:46:13 mythtvserver  mythbackend: mythbackend[2975]: W TFWWrite threadedfilewriter.cpp:571  (DiskLoop) TFW(/mnt/mythtv/recordings/1008_20140528003300.mpg:52):  write(63356) cnt 9 total 526212 -- took a long time, 1309 ms
May 27  20:46:17 mythtvserver mythbackend: mythbackend[2975]: W TFWWrite  threadedfilewriter.cpp:571 (DiskLoop)  TFW(/mnt/mythtv/recordings/1008_20140528003300.mpg:52): write(63168) cnt  11 total 643900 -- took a long time, 1592 ms
May 27 20:46:19  mythtvserver mythbackend: mythbackend[2975]: W TFWWrite  threadedfilewriter.cpp:571 (DiskLoop)  TFW(/mnt/mythtv/recordings/1008_20140528003300.mpg:52): write(65424) cnt  10 total 654052 -- took a long time, 1326 ms
May 27 20:49:27  mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH  3944 0 0 - SaveRule Supernatural
May 27 20:49:28 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2211  (HandleReschedule) Scheduled 1179 items in 1.1 = 0.03 match + 0.01 check  + 1.06 place
May 27 20:49:36 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2098 (HandleReschedule)  Reschedule requested for MATCH 3945 0 0 - SaveRule Supernatural
May  27 20:49:37 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2211 (HandleReschedule) Scheduled 1179 items in 1.1 = 0.03  match + 0.01 check + 1.07 place
May 27 20:49:42 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2098  (HandleReschedule) Reschedule requested for MATCH 3946 0 0 - SaveRule  Storage Wars
May 27 20:49:43 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2211 (HandleReschedule)  Scheduled 1179 items in 1.1 = 0.03 match + 0.01 check + 1.10 place
May  27 20:49:44 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH  3947 0 0 - SaveRule Teen Wolf
May 27 20:49:45 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2211  (HandleReschedule) Scheduled 1179 items in 1.1 = 0.03 match + 0.01 check  + 1.08 place
May 27 20:49:47 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2098 (HandleReschedule)  Reschedule requested for MATCH 3948 0 0 - SaveRule Storage Wars
May  27 20:49:48 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2211 (HandleReschedule) Scheduled 1179 items in 1.1 = 0.03  match + 0.01 check + 1.06 place
May 27 20:49:53 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2098  (HandleReschedule) Reschedule requested for MATCH 3949 0 0 - SaveRule  Storage Wars
May 27 20:49:54 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2211 (HandleReschedule)  Scheduled 1179 items in 1.1 = 0.03 match + 0.01 check + 1.09 place
May  27 20:49:58 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for MATCH  3950 0 0 - SaveRule Storage Wars
May 27 20:50:00 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2211  (HandleReschedule) Scheduled 1179 items in 1.1 = 0.03 match + 0.00 check  + 1.05 place
May 27 20:55:24 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 20:55:24 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 20:55:24  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  20:55:24 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 20:55:27 mythtvserver mythbackend:  mythbackend[2975]: E ProcessRequest programinfo.cpp:2358  (GetPlaybackURL) ProgramInfo(1041_20140106190000.mpg): GetPlaybackURL:  '1041_20140106190000.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1061_20140106190000.mpg): GetPlaybackURL:  '1061_20140106190000.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215401.mpg): GetPlaybackURL:  '1066_20140207215401.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215203.mpg): GetPlaybackURL:  '1066_20140207215203.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215400.mpg): GetPlaybackURL:  '1066_20140207215400.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215301.mpg): GetPlaybackURL:  '1066_20140207215301.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215500.mpg): GetPlaybackURL:  '1066_20140207215500.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215300.mpg): GetPlaybackURL:  '1066_20140207215300.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215200.mpg): GetPlaybackURL:  '1066_20140207215200.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215402.mpg): GetPlaybackURL:  '1066_20140207215402.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215403.mpg): GetPlaybackURL:  '1066_20140207215403.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215404.mpg): GetPlaybackURL:  '1066_20140207215404.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215405.mpg): GetPlaybackURL:  '1066_20140207215405.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215406.mpg): GetPlaybackURL:  '1066_20140207215406.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215407.mpg): GetPlaybackURL:  '1066_20140207215407.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215408.mpg): GetPlaybackURL:  '1066_20140207215408.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215409.mpg): GetPlaybackURL:  '1066_20140207215409.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215501.mpg): GetPlaybackURL:  '1066_20140207215501.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215502.mpg): GetPlaybackURL:  '1066_20140207215502.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215800.mpg): GetPlaybackURL:  '1066_20140207215800.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215801.mpg): GetPlaybackURL:  '1066_20140207215801.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215802.mpg): GetPlaybackURL:  '1066_20140207215802.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215803.mpg): GetPlaybackURL:  '1066_20140207215803.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215804.mpg): GetPlaybackURL:  '1066_20140207215804.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215805.mpg): GetPlaybackURL:  '1066_20140207215805.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1070_20140513003629.mpg): GetPlaybackURL:  '1070_20140513003629.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1004_20140513003638.mpg): GetPlaybackURL:  '1004_20140513003638.mpg' should be local, but it can not be found.
May  27 20:55:27 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1003_20140521222738.mpg): GetPlaybackURL:  '1003_20140521222738.mpg' should be local, but it can not be found.
May  27 20:55:29 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Playback
May 27 20:55:29 mythtvserver mythbackend: mythbackend[2975]:  I ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 20:55:29 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from None to WatchingLiveTV
May  27 20:55:29 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:55:29 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:55:30 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(9) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      7 has PID 0x02bc
May 27 20:55:30 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:55:30 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:55:30 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:55:30 mythtvserver  mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[27](192.168.0.120-1): SetStrOption(...recordingtype): Option not  in profile.
May 27 20:55:35 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:3602 (TuningCheckForHWChange)  TVRec[27]: HW Tuner: 27->27
May 27 20:55:35 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:55:35 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:55:36 mythtvserver  mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(11) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      6 has PID 0x0258
May 27 20:55:36 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[27](192.168.0.120-1): But there is only one program in the  PAT, so we'll just use it
May 27 20:55:36 mythtvserver mythbackend:  mythbackend[2975]: N HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:367 (HandlePMT)  DTVSigMon[27](192.168.0.120-1): PMT says program 6 is encrypted
May  27 20:55:36 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:55:36 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:55:47 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:55:47 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-1): UpdateFilters called in wrong tune mode
May  27 20:55:47 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[27]:  FinishedRecording(1070_2014-05-28T00:55:36Z) damaged  recq:<RecordingQuality overall_score="0"  key="1070_2014-05-28T00:55:36Z" countinuity_error_count="0"  packet_count="442">#012    <Gap start="2014-05-28T00:00:00Z"  end="2014-05-28T02:00:00Z" duration="7200"  />#012</RecordingQuality>
May 27 20:55:47 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Playback
May 27 20:55:47  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 20:55:47 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[27]: Changing from None to WatchingLiveTV
May 27 20:55:47  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[27]: HW Tuner: 27->27
May  27 20:55:47 mythtvserver mythbackend: mythbackend[2975]: N CoreContext  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 7 min
May 27 20:55:47 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050  (HandleStateChange) TVRec[27]: Changing from WatchingLiveTV to None
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 14 min
May 27 20:57:19 mythtvserver  mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 10 MB for 1002 at 2014-01-06T17:28:42Z  => "Q Check":"Style Edition"
May 27 20:57:19 mythtvserver  mythbackend: mythbackend[2975]: E CoreContext programinfo.cpp:2358  (GetPlaybackURL) ProgramInfo(1002_20140106122842.mpg): GetPlaybackURL:  '1002_20140106122842.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1002_20140106122842.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 65 MB for 1043 at  2014-01-07T16:52:00Z => "Cajun Pawn Stars":"Cash Cows"
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 73 MB for 1020 at  2014-01-07T16:52:00Z => "Law & Order":"Tabula Rasa"
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 75 MB for 1042 at  2014-01-07T16:52:00Z => "CSI: Miami":Dishonor
May 27 20:57:19  mythtvserver mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 80 MB for 1011 at 2014-01-07T16:52:00Z  => Supernatural:Shadow
May 27 20:57:19 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 82 MB for 1036 at 2014-01-07T16:52:00Z => "Looney Tunes"
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 86 MB for 1060 at  2014-01-07T16:52:00Z => "Storage Hunters":"Rhinestones and Thrones"
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1043_20140107115200.mpg): GetPlaybackURL:  '1043_20140107115200.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1043_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1020_20140107115200.mpg): GetPlaybackURL:  '1020_20140107115200.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1020_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1042_20140107115200.mpg): GetPlaybackURL:  '1042_20140107115200.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1042_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1011_20140107115200.mpg): GetPlaybackURL:  '1011_20140107115200.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1011_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1036_20140107115200.mpg): GetPlaybackURL:  '1036_20140107115200.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1036_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1060_20140107115200.mpg): GetPlaybackURL:  '1060_20140107115200.mpg' should be local, but it can not be found.
May  27 20:57:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1060_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  20:58:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1005 at  2014-05-28T00:55:29Z => Bones:"The Bone That Blew"
May 27 20:58:19  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 2 MB for 1005 at  2014-05-28T00:55:30Z => Bones:"The Bone That Blew"
May 27 20:58:19  mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1070 at  2014-05-28T00:55:35Z => "Horrible Bosses"
May 27 20:58:19  mythtvserver mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 0 MB for 1070 at 2014-05-28T00:55:36Z  => "Horrible Bosses"
May 27 20:58:19 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 0 MB for 1005 at 2014-05-28T00:55:47Z => Bones:"The Bone  That Blew"
May 27 20:59:00 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2098 (HandleReschedule)  Reschedule requested for PLACE PrepareToRecord
May 27 20:59:01  mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2211 (HandleReschedule) Scheduled 1179 items in 1.7 = 0.00  match + 0.00 check + 1.67 place
May 27 20:59:31 mythtvserver  mythbackend: mythbackend[2975]: I TVRecEvent tv_rec.cpp:1567  (HandlePendingRecordings) TVRec[24]: ASK_RECORDING 24 29 0 0
May 27  21:00:00 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:1050 (HandleStateChange) TVRec[24]: Changing from  RecordingOnly to None
May 27 21:00:00 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-0): UpdateFilters called in wrong tune mode
May  27 21:00:00 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  recordinginfo.cpp:1075 (FinishedRecording) Finished recording The  Originals "Always and Forever": channel 1008
May 27 21:00:00  mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:947 (customEvent) MainServer: PREVIEW_SUCCESS but no  receivers.
May 27 21:00:00 mythtvserver mythbackend:  mythbackend[2975]: I CoreContext scheduler.cpp:704 (UpdateRecStatus)  Updating status for "The Originals":"Always and Forever" on cardid 24  (Recording => Recorded)
May 27 21:00:00 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[24]: Changing from None to RecordingOnly
May 27 21:00:00  mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:3602 (TuningCheckForHWChange) TVRec[24]: HW Tuner: 24->24
May  27 21:00:00 mythtvserver mythbackend: mythbackend[2975]: N Scheduler  autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required  Free Space: 3.0 GB w/freq: 14 min
May 27 21:00:00 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2648  (HandleRecordingStatusChange) Tuning recording: "Deadliest  Catch":"Falling Down": channel 1041 on cardid 24, sourceid 1
May 27  21:00:00 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for CHECK -3  899 0 UpdateRecStatus2 | The Originals | Always and Forever | Klaus  returns to the French Quarter of New Orleans, which his family helped  build 300 years ago; a powerful witch reveals important news about  Hayley, a werewolf who had a fling with Klaus. | EP017316280001
May  27 21:00:01 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/dtvsignalmonitor.cpp:322 (HandlePAT)  DTVSigMon[24](192.168.0.120-0): Program #0 not found in PAT!#012Program  Association Section#012 PSIP tableID(0x0) length(13)  extension(0x0)#012      version(16) current(1) section(0)  last_section(0)#012      tsid(0) programCount(1)#012  program number      4 has PID 0x0190
May 27 21:00:01 mythtvserver mythbackend:  mythbackend[2975]: E HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:328 (HandlePAT)  DTVSigMon[24](192.168.0.120-0): But there is only one program in the  PAT, so we'll just use it
May 27 21:00:01 mythtvserver mythbackend:  mythbackend[2975]: N HDHRStreamHandler  recorders/dtvsignalmonitor.cpp:367 (HandlePMT)  DTVSigMon[24](192.168.0.120-0): PMT says program 4 is encrypted
May  27 21:00:01 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  scheduler.cpp:704 (UpdateRecStatus) Updating status for "Deadliest  Catch":"Falling Down" on cardid 24 (Tuning => Recording)
May 27  21:00:01 mythtvserver mythbackend: mythbackend[2975]: E  HDHRStreamHandler recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-0): UpdateFilters called in wrong tune mode
May  27 21:00:01 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:4126 (TuningNewRecorder) TVRec[24]: rec->GetPathname():  '/mnt/mythtv/recordings/1041_20140528010000.mpg'
May 27 21:00:01  mythtvserver mythbackend: mythbackend[2975]: E TVRecEvent  recorders/recorderbase.cpp:206 (SetStrOption)  RecBase[24](192.168.0.120-0): SetStrOption(...recordingtype): Option not  in profile.
May 27 21:00:01 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2202 (HandleReschedule)  Reschedule interrupted, will retry
May 27 21:00:01 mythtvserver  mythbackend: mythbackend[2975]: I Scheduler scheduler.cpp:2098  (HandleReschedule) Reschedule requested for PLACE Interrupted
May 27  21:00:03 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2211 (HandleReschedule) Scheduled 1175 items in 1.1 = 0.00  match + 0.00 check + 1.09 place
May 27 21:00:24 mythtvserver  mythbackend: mythbackend[2975]: I Metadata_16266 jobqueue.cpp:2156  (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "The  Originals":"Always and Forever" recorded from channel 1008 at  2014-05-28T00:33:00Z
May 27 21:00:25 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:00:25 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 21:00:25  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:00:25 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 21:00:29 mythtvserver mythbackend:  mythbackend[2975]: I Commflag_16267 jobqueue.cpp:2281  (DoFlagCommercialsThread) JobQueue: Commercial Detection Starting for  "The Originals":"Always and Forever" recorded from channel 1008 at  2014-05-28T00:33:00Z
May 27 21:00:29 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:00:29 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 21:00:29  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:00:29 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 21:09:18 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:09:18 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 21:09:18  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:09:18 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 21:09:25 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:09:25 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 21:09:25  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:09:25 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 1)
May 27 21:09:33 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Playback
May 27 21:09:33 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 0)
May 27 21:09:33  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1538 (HandleAnnounce) MainServer::HandleAnnounce  FileTransfer
May 27 21:09:33 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1540 (HandleAnnounce)  adding: mythtvserver as a remote file transfer
May 27 21:09:36  mythtvserver mythbackend: mythbackend[2975]: E ProcessRequest  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1041_20140106190000.mpg): GetPlaybackURL:  '1041_20140106190000.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1061_20140106190000.mpg): GetPlaybackURL:  '1061_20140106190000.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215401.mpg): GetPlaybackURL:  '1066_20140207215401.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215203.mpg): GetPlaybackURL:  '1066_20140207215203.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215400.mpg): GetPlaybackURL:  '1066_20140207215400.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215301.mpg): GetPlaybackURL:  '1066_20140207215301.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215500.mpg): GetPlaybackURL:  '1066_20140207215500.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215300.mpg): GetPlaybackURL:  '1066_20140207215300.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215200.mpg): GetPlaybackURL:  '1066_20140207215200.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215402.mpg): GetPlaybackURL:  '1066_20140207215402.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215403.mpg): GetPlaybackURL:  '1066_20140207215403.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215404.mpg): GetPlaybackURL:  '1066_20140207215404.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215405.mpg): GetPlaybackURL:  '1066_20140207215405.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215406.mpg): GetPlaybackURL:  '1066_20140207215406.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215407.mpg): GetPlaybackURL:  '1066_20140207215407.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215408.mpg): GetPlaybackURL:  '1066_20140207215408.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215409.mpg): GetPlaybackURL:  '1066_20140207215409.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215501.mpg): GetPlaybackURL:  '1066_20140207215501.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215502.mpg): GetPlaybackURL:  '1066_20140207215502.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215800.mpg): GetPlaybackURL:  '1066_20140207215800.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215801.mpg): GetPlaybackURL:  '1066_20140207215801.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215802.mpg): GetPlaybackURL:  '1066_20140207215802.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215803.mpg): GetPlaybackURL:  '1066_20140207215803.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215804.mpg): GetPlaybackURL:  '1066_20140207215804.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215805.mpg): GetPlaybackURL:  '1066_20140207215805.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1070_20140513003629.mpg): GetPlaybackURL:  '1070_20140513003629.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1004_20140513003638.mpg): GetPlaybackURL:  '1004_20140513003638.mpg' should be local, but it can not be found.
May  27 21:09:36 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1003_20140521222738.mpg): GetPlaybackURL:  '1003_20140521222738.mpg' should be local, but it can not be found.
May  27 21:09:37 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Monitor
May 27 21:09:37 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 21:09:37 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Monitor
May 27 21:09:37 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1422  (HandleAnnounce) adding: mythtvserver as a client (events: 1)
May 27  21:09:37 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:09:37 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 21:09:37 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:09:37 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 1)
May 27 21:09:38  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Playback
May 27  21:09:38 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 21:09:49 mythtvserver mythbackend:  mythbackend[2975]: I TVRecEvent tv_rec.cpp:1050 (HandleStateChange)  TVRec[24]: Changing from RecordingOnly to None
May 27 21:09:49  mythtvserver mythbackend: mythbackend[2975]: E HDHRStreamHandler  recorders/hdhrstreamhandler.cpp:206 (UpdateFilters)  HDHRSH(192.168.0.120-0): UpdateFilters called in wrong tune mode
May  27 21:09:49 mythtvserver mythbackend: mythbackend[2975]: I TVRecEvent  tv_rec.cpp:834 (FinishedRecording) TVRec[24]:  FinishedRecording(1041_2014-05-28T01:00:00Z) damaged  recq:<RecordingQuality overall_score="0"  key="1041_2014-05-28T01:00:00Z" countinuity_error_count="1"  packet_count="303">#012    <Gap start="2014-05-28T01:00:01Z"  end="2014-05-28T01:09:49Z" duration="587"  />#012</RecordingQuality>
May 27 21:09:49 mythtvserver  mythbackend: mythbackend[2975]: E CoreContext mainserver.cpp:947  (customEvent) MainServer: PREVIEW_SUCCESS but no receivers.
May 27  21:09:49 mythtvserver mythbackend: mythbackend[2975]: I CoreContext  scheduler.cpp:704 (UpdateRecStatus) Updating status for "Deadliest  Catch":"Falling Down" on cardid 24 (Recording => Recorded)
May 27  21:09:49 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for CHECK -3  3800 0 UpdateRecStatus2 | Deadliest Catch | Falling Down | Fishing is  halted with one captain in the hospital and one on a bender; a boat goes  dark. | EP007331290236
May 27 21:09:50 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2211 (HandleReschedule)  Scheduled 1175 items in 1.0 = 0.00 match + 0.01 check + 1.04 place
May  27 21:09:50 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for CHECK -3  3800 0 DoHandleDelete3 | Deadliest Catch | Falling Down | Fishing is  halted with one captain in the hospital and one on a bender; a boat goes  dark. | EP007331290236
May 27 21:09:51 mythtvserver mythbackend:  mythbackend[2975]: I Scheduler scheduler.cpp:2211 (HandleReschedule)  Scheduled 1175 items in 1.1 = 0.00 match + 0.01 check + 1.09 place
May  27 21:09:52 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN  Monitor
May 27 21:09:52 mythtvserver mythbackend: mythbackend[2975]: I  ProcessRequest mainserver.cpp:1422 (HandleAnnounce) adding:  mythtvserver as a client (events: 0)
May 27 21:09:52 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1420  (HandleAnnounce) MainServer::ANN Monitor
May 27 21:09:52 mythtvserver  mythbackend: mythbackend[2975]: I ProcessRequest mainserver.cpp:1422  (HandleAnnounce) adding: mythtvserver as a client (events: 1)
May 27  21:09:54 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:09:54 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 21:09:54 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:09:54 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 1)
May 27 21:09:54  mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1420 (HandleAnnounce) MainServer::ANN Monitor
May 27  21:09:54 mythtvserver mythbackend: mythbackend[2975]: I ProcessRequest  mainserver.cpp:1422 (HandleAnnounce) adding: mythtvserver as a client  (events: 0)
May 27 21:09:54 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1420 (HandleAnnounce)  MainServer::ANN Monitor
May 27 21:09:54 mythtvserver mythbackend:  mythbackend[2975]: I ProcessRequest mainserver.cpp:1422 (HandleAnnounce)  adding: mythtvserver as a client (events: 1)
May 27 21:10:10  mythtvserver mythbackend: mythbackend[2975]: E ProcessRequest  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1041_20140106190000.mpg): GetPlaybackURL:  '1041_20140106190000.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1061_20140106190000.mpg): GetPlaybackURL:  '1061_20140106190000.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215401.mpg): GetPlaybackURL:  '1066_20140207215401.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215203.mpg): GetPlaybackURL:  '1066_20140207215203.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215400.mpg): GetPlaybackURL:  '1066_20140207215400.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215301.mpg): GetPlaybackURL:  '1066_20140207215301.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215500.mpg): GetPlaybackURL:  '1066_20140207215500.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215300.mpg): GetPlaybackURL:  '1066_20140207215300.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215200.mpg): GetPlaybackURL:  '1066_20140207215200.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215402.mpg): GetPlaybackURL:  '1066_20140207215402.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215403.mpg): GetPlaybackURL:  '1066_20140207215403.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215404.mpg): GetPlaybackURL:  '1066_20140207215404.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215405.mpg): GetPlaybackURL:  '1066_20140207215405.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215406.mpg): GetPlaybackURL:  '1066_20140207215406.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215407.mpg): GetPlaybackURL:  '1066_20140207215407.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215408.mpg): GetPlaybackURL:  '1066_20140207215408.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215409.mpg): GetPlaybackURL:  '1066_20140207215409.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215501.mpg): GetPlaybackURL:  '1066_20140207215501.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215502.mpg): GetPlaybackURL:  '1066_20140207215502.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215800.mpg): GetPlaybackURL:  '1066_20140207215800.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215801.mpg): GetPlaybackURL:  '1066_20140207215801.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215802.mpg): GetPlaybackURL:  '1066_20140207215802.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215803.mpg): GetPlaybackURL:  '1066_20140207215803.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215804.mpg): GetPlaybackURL:  '1066_20140207215804.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1066_20140207215805.mpg): GetPlaybackURL:  '1066_20140207215805.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1070_20140513003629.mpg): GetPlaybackURL:  '1070_20140513003629.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1004_20140513003638.mpg): GetPlaybackURL:  '1004_20140513003638.mpg' should be local, but it can not be found.
May  27 21:10:10 mythtvserver mythbackend: mythbackend[2975]: E  ProcessRequest programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1003_20140521222738.mpg): GetPlaybackURL:  '1003_20140521222738.mpg' should be local, but it can not be found.
May  27 21:10:15 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2098 (HandleReschedule) Reschedule requested for CHECK 0  899 0 DoHandleDelete1 | The Originals | Always and Forever | Klaus  returns to the French Quarter of New Orleans, which his family helped  build 300 years ago; a powerful witch reveals important news about  Hayley, a werewolf who had a fling with Klaus. | EP017316280001
May  27 21:10:16 mythtvserver mythbackend: mythbackend[2975]: I Scheduler  scheduler.cpp:2211 (HandleReschedule) Scheduled 1175 items in 1.1 = 0.00  match + 0.00 check + 1.12 place
May 27 21:12:19 mythtvserver  mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:264 (CalcParams)  AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15  min
May 27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: N  Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 10 MB for 1002  at 2014-01-06T17:28:42Z => "Q Check":"Style Edition"
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1002_20140106122842.mpg): GetPlaybackURL:  '1002_20140106122842.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1002_20140106122842.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 65 MB for 1043 at  2014-01-07T16:52:00Z => "Cajun Pawn Stars":"Cash Cows"
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 73 MB for 1020 at  2014-01-07T16:52:00Z => "Law & Order":"Tabula Rasa"
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 75 MB for 1042 at  2014-01-07T16:52:00Z => "CSI: Miami":Dishonor
May 27 21:12:19  mythtvserver mythbackend: mythbackend[2975]: N Expire autoexpire.cpp:641  (SendDeleteMessages) Expiring 80 MB for 1011 at 2014-01-07T16:52:00Z  => Supernatural:Shadow
May 27 21:12:19 mythtvserver mythbackend:  mythbackend[2975]: N Expire autoexpire.cpp:641 (SendDeleteMessages)  Expiring 82 MB for 1036 at 2014-01-07T16:52:00Z => "Looney Tunes"
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: N Expire  autoexpire.cpp:641 (SendDeleteMessages) Expiring 86 MB for 1060 at  2014-01-07T16:52:00Z => "Storage Hunters":"Rhinestones and Thrones"
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1043_20140107115200.mpg): GetPlaybackURL:  '1043_20140107115200.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1043_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1020_20140107115200.mpg): GetPlaybackURL:  '1020_20140107115200.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1020_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1042_20140107115200.mpg): GetPlaybackURL:  '1042_20140107115200.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1042_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1011_20140107115200.mpg): GetPlaybackURL:  '1011_20140107115200.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1011_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1036_20140107115200.mpg): GetPlaybackURL:  '1036_20140107115200.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1036_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.
May 27  21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  programinfo.cpp:2358 (GetPlaybackURL)  ProgramInfo(1060_20140107115200.mpg): GetPlaybackURL:  '1060_20140107115200.mpg' should be local, but it can not be found.
May  27 21:12:19 mythtvserver mythbackend: mythbackend[2975]: E CoreContext  mainserver.cpp:2672 (DoHandleDeleteRecording) ERROR when trying to  delete file:  GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvserver/1060_20140107115200.mpg.  File doesn't exist.  Database metadata will not be removed.

---

### Post by dannyboy79 on 2014-05-28
are you certain any channel higher than 9 isn't encrypted? what type of tv signal do you pay for?

---

### Post by drink1297 on 2014-05-28
It looks like either the cards inputs are already recording, or you need to have them rescan for channels.

I just added an HDMRP3, mythbackend picked it up right away, but I didn't realize to add the IP address in place of the mac address, or whatever code it inserted, but after I added the IP, I then scanned each input, and have had no issues, other than recently when the frontends would freeze up after 20 minutes playing.  Updates appeared to solve that issue.

If you note in the backend log, it looks like it can't find the program you want to tune too.  I would scan the channels on the cards, and make sure the DB is good, you should be able to run something like mythfilldatabase --repair, or if you have mythweb enabled you can do it from there.

---

### Post by drink1297 on 2014-05-28
Personally, I won't pay for cable, I use a cable internet, and split it before the ISP modem, run the split into the HDHR, scan on QAM256, I check test dycrypt, and pick up close to 100 useable channels, several I delete.....
On the down side, you have to go in and edit the database with the correct channel info, and download some icons....and if your like me in Chicago, the cable company is moving channels every couple of days, so there is always an edit to be made.....

But the card should just work if it was scanned correctly.

---

### Post by dannyboy79 on 2014-05-28
hang on, you're saying that you pay for internet only BUT you're still receiving clear QAM256 digital channels over the coax line? I'm in Milwaukee, WI and I only pay for internet and I receive analog cable over the coax line still. So I am still using a PVR-350 and a PVR-500. LOL  Once TWC here in Milwaukee stops transmitting the analog stations i'll be switching to something BUT I was unaware I could just get an HDHR and plug straight into it and get clear QAM256 channels.

---

### Post by drink1297 on 2014-05-29
The cable companies run Cable & Internet in the same band over the cable...not too many people realize it, but instead of paying $40 a month for internet, $60 for cable, and $4 or 5 for their box, I just get the internet...
Of course...if cable goes out, you can't really complain either, but for me it works great...more or less it's just basic cable.

They CAN, add something to cut it off, but I think they have to go to the city/state for some type of injuction or something.

I hate to say it, but all the cable channels show just about reruns all month...why would I pay so much a year to watch what boils down to 12 program rotations??  I try to spread the word, I hate to see people pay for something they could get free.

Not only are they paying for cable, but they pay for internet, they pay for DVR boxes....and it's all right HERE...free in the world of open source...we are living large over here.........

---

