---
title: "mythbuntu 9.04 0.23 Upgrade to 0.24 broke liveTV"
date: 2011-03-19
forum: Mythbuntu
---

### Post by macaronij on 2011-03-19
Hi,
upgrated to 0.24 broke my system

Problem: LiveTV work only the first channel, if i change the channel then it exit to menu
mythfrontend log
```
2011-03-19 14:31:52.587 TV: Changing from None to WatchingLiveTV
2011-03-19 14:31:52.587 TV: State is LiveTV & mctx == ctx
2011-03-19 14:31:52.589 TV: UpdateOSDInput done
2011-03-19 14:31:52.589 TV: UpdateLCD done
2011-03-19 14:31:52.589 TV: ITVRestart done
2011-03-19 14:31:52.913 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2011-03-19 14:31:52.939 AO: Opening audio device 'pulse' ch 2(2) sr 32000 sf signed 16 bit reenc 0
2011-03-19 14:31:52.940 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-03-19 14:31:53.144 AudioPlayer: Enabling Audio
2011-03-19 14:31:53.350 Player(4): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUUU
2011-03-19 14:31:53.360 Player(4): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUUU
2011-03-19 14:31:53.375 Player(4): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAUUUUUUUUUUU
2011-03-19 14:31:53.404 VideoOutput: Created YV12 OSD.
2011-03-19 14:31:53.693 Player(4): Waited 100ms for video buffers UUUUUAAAAAAAAAAAAAAAAAAAAUUUUUU
2011-03-19 14:31:53.708 Player(4): Waited 100ms for video buffers UUUUUAAAAAAAAAAAAAAAAAAAAUUUUUU
2011-03-19 14:31:53.820 Player(4): Waited 100ms for video buffers UUUUUAAAAAAAAAAAAAAAAAAAAUUUUUU
2011-03-19 14:31:53.836 Player(4): Waited 100ms for video buffers UUUUUAAAAAAAAAAAAAAAAAAAAUUUUUU
2011-03-19 14:31:53.846 Player(4): Waited 100ms for video buffers UUUUUAAAAAAAAAAAAAAAAAAAAUUUUUU
2011-03-19 14:31:56.778 BrowseDispInfo()
2011-03-19 14:31:56.778 BrowseStart()
2011-03-19 14:31:56.787 browsechanid: 0 -> 1080
2011-03-19 14:31:57.658 BrowseDispInfo()
2011-03-19 14:31:57.658 BrowseStart()
2011-03-19 14:31:57.661 browsechanid: 1080 -> 1079
2011-03-19 14:31:58.178 BrowseDispInfo()
2011-03-19 14:31:58.178 BrowseStart()
2011-03-19 14:31:58.181 browsechanid: 1079 -> 1078
2011-03-19 14:31:58.498 BrowseDispInfo()
2011-03-19 14:31:58.498 BrowseStart()
2011-03-19 14:31:58.507 browsechanid: 1078 -> 1103
2011-03-19 14:31:58.738 BrowseDispInfo()
2011-03-19 14:31:58.738 BrowseStart()
2011-03-19 14:31:58.741 browsechanid: 1103 -> 1076
2011-03-19 14:31:58.909 RingBuf(myth://192.168.0.105:6543/1003_20110319143151.nuv): Waited 0.2 seconds for data 
            to become available... 21228 < 84714
2011-03-19 14:32:00.263 BrowseDispInfo()
2011-03-19 14:32:00.263 BrowseStart()
2011-03-19 14:32:00.266 browsechanid: 0 -> 1107
2011-03-19 14:32:01.498 BrowseEnd()
2011-03-19 14:32:01.996 RingBuf(myth://192.168.0.105:6543/1107_20110319143200.nuv) Warning: Not starting read ahead thread, already running
2011-03-19 14:32:01.997 Player(4): DecoderGetFrame() called with NULL decoder.
2011-03-19 14:32:02.475 Player(4), Error: Couldn't find an A/V decoder for: 'myth://192.168.0.105:6543/1107_20110319143200.nuv'
2011-03-19 14:32:02.475 Player(4), Error: JumpToProgram failed.
2011-03-19 14:32:02.475 Player(4), Error: Unknown recorder error, exiting decoder
2011-03-19 14:32:02.521 TV: Attempting to change from WatchingLiveTV to None
2011-03-19 14:32:03.262 TV: Changing from WatchingLiveTV to None
2011-03-19 14:32:03.264 TV: Attempting to change from None to None
2011-03-19 14:32:03.273 TV: Attempting to change from None to WatchingLiveTV
2011-03-19 14:32:03.273 MythCoreContext: Connecting to backend server: 192.168.0.105:6543 (try 1 of 1)
2011-03-19 14:32:03.274 Using protocol version 63
2011-03-19 14:32:03.302 Spawning LiveTV Recorder -- begin
2011-03-19 14:32:03.411 Spawning LiveTV Recorder -- end
2011-03-19 14:32:03.422 We have a playbackURL(myth://192.168.0.105:6543/1003_20110319143201.nuv) & cardtype(DUMMY)
2011-03-19 14:32:03.422 We have a RingBuffer
2011-03-19 14:32:03.423 playCtx, Error: Attempting to setup a player, but it already exists.
2011-03-19 14:32:03.423 TV Error: LiveTV not successfully started
2011-03-19 14:32:20.301 OpenGL: Deleting OpenGL Resources
2011-03-19 14:32:20.323 Pulse: Cleaning up PulseHandler
2011-03-19 14:32:20.323 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

```recording profile of livetv was set to RTjpeg. If i change it to mpeg4 then i can change the channel, but resolution change and i have NO SOUND

i re-scan the audio devices and tryed whit alsa, pulse, etc
All have the same problem

I have the same problem in the backend+frontend and in the frontend only pc

Recording work OK, whit sound.

---

### Post by macaronij on 2011-03-20
Ok so i had to reinstall coz the waf was lim->0
I will wait to 0.25 to try again
is there a way to try if my hardware work in a new mythtv whitout broking the system?

---

### Post by uteck on 2011-04-05
The live TV playback seems to be caused the default playback option in .24.  On the frontends, go into the setup options for TV and turn off the real-time priority threads in the playback section.  That cleared up my live tv issue for me.

---

### Post by dewmanstl on 2011-04-07
I would say me to, but its not really the same. Upgraded to 10.10 and running .24 trunk with latest fixes:

MythTV Version   : v0.24-235-g80192ec
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0

I removed all the tuners and all the sources,did a fresh scan using hdhomerun (single tuner) 
I didnt populate the guide just wanted to see what would tune and what would not tune. 

Went to nbc (5_1) tuned fine.
System got a little unstable while trying to tune audio channels, did a reboot now none of the channels come back up. Keep getting this crazy error:

11-04-07 22:07:44.477 Player(0), Error: Unknown recorder error, exiting decoder
2011-04-07 22:07:44.514 TV: Attempting to change from WatchingLiveTV to None
2011-04-07 22:07:44.520 VDPAU Painter: Clearing VDPAU painter cache.
2011-04-07 22:07:44.524 MythPainter: 6 images not yet de-allocated.
2011-04-07 22:07:44.658 TV: Changing from WatchingLiveTV to None
2011-04-07 22:07:44.661 TV: Attempting to change from None to None
2011-04-07 22:07:44.667 TV: Attempting to change from None to WatchingLiveTV
2011-04-07 22:07:44.667 MythCoreContext: Connecting to backend server: 192.168.1.251:6543 (try 1 of 1)
2011-04-07 22:07:44.668 Using protocol version 63
2011-04-07 22:07:44.754 Spawning LiveTV Recorder -- begin
2011-04-07 22:07:44.924 Spawning LiveTV Recorder -- end
2011-04-07 22:07:44.933 We have a playbackURL(myth://192.168.1.251:6543/2081_20110407220744.mpg) & cardtype(DUMMY)
2011-04-07 22:07:44.934 We have a RingBuffer
2011-04-07 22:07:44.935 playCtx, Error: Attempting to setup a player, but it already exists.
2011-04-07 22:07:44.935 TV Error: LiveTV not successfully started
2011-04-07 22:07:48.703 OpenGL: Deleting OpenGL Resources
2011-04-07 22:07:48.728 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

:sad:

---

### Post by os2 on 2013-01-07
Was this issue sorted out?

I seem to be having the same problem albeit under slightly different circumstances. Been driving me mad 4 days straight now.

---

### Post by ravenium on 2013-01-12
> **os2 said:**
> Was this issue sorted out?

I seem to be having the same problem albeit under slightly different circumstances. Been driving me mad 4 days straight now.

Having a similar issue that just happened this past Monday.  I'll create a separate thread.

---

