---
title: "LiveTV black screen on local frontend only"
date: 2014-10-18
forum: Mythbuntu
---

### Post by wyliecoyoteuk on 2014-10-18
Mythbuntu 14.04, all patches, on an AMD Kabini quad core APU, TBS 6280 tuner, using latest driver and tried open GL and AMD drivers, no difference.
Everything else works fine, I can record, play music and videos, play recordings, etc.
Remote frontends on PCs and Android tablets play LiveTV no problem, and there are no errors in the logs, but on the local screen, LiveTV is a black screen, no sound, and it just sits there, no errors.
It did work at one point around 2 kernel updates ago.

---

### Post by wyliecoyoteuk on 2014-11-07
Bump

Still no joy.
ran it from a terminal, here is the output:
> 
2014-11-07 20:58:50.574334 I  TV: Creating TV object
2014-11-07 20:58:50.626591 N  Suspending idle timer
2014-11-07 20:58:50.628476 I  TV: Created TvPlayWindow.
2014-11-07 20:58:50.682518 I  TV: Attempting to change from None to WatchingLiveTV
2014-11-07 20:58:50.686081 I  MythCoreContext: Connecting to backend server: 192.168.0.12:6543 (try 1 of 1)
2014-11-07 20:58:50.716862 N  TV: Spawning LiveTV Recorder -- begin
2014-11-07 20:58:50.794963 N  TV: Spawning LiveTV Recorder -- end
2014-11-07 20:58:50.800892 I  TV: playbackURL(/var/lib/mythtv/livetv/1003_20141107205850.mpg) cardtype(DUMMY)
2014-11-07 20:58:51.147617 I  Pulse: PulseAudio suspend OK
2014-11-07 20:58:51.216040 N  AudioPlayer: Enabling Audio
2014-11-07 20:58:51.252053 W  OpenGL: Could not determine whether Sync to VBlank is enabled.
2014-11-07 20:58:51.484740 I  OpenGL1: Fragment program support available
2014-11-07 20:58:51.484855 I  OpenGL: OpenGL vendor  : ATI Technologies Inc.
2014-11-07 20:58:51.484866 I  OpenGL: OpenGL renderer: AMD Radeon HD 8400
2014-11-07 20:58:51.484895 I  OpenGL: OpenGL version : 4.3.12798 Compatibility Profile Context 13.35.1005
2014-11-07 20:58:51.484913 I  OpenGL: Max texture size: 16384 x 16384
2014-11-07 20:58:51.484922 I  OpenGL: Max texture units: 8
2014-11-07 20:58:51.484989 I  OpenGL: Direct rendering: Yes
2014-11-07 20:58:51.484999 I  OpenGL: PixelBufferObject support available
2014-11-07 20:58:51.485006 I  OpenGL: Initialised MythRenderOpenGL
2014-11-07 20:58:51.485112 I  VidOutGL: Created MythRenderOpenGL device.
2014-11-07 20:58:51.486580 I  OpenGL painter using existing OpenGL context.
2014-11-07 20:58:51.486598 I  OpenGL painter using existing QGLWidget.
2014-11-07 20:58:51.490605 I  OSD: Base theme size: 800x600
2014-11-07 20:58:51.490634 I  OSD: Scaling factors: 1.28x1.28
2014-11-07 20:58:51.555260 I  OSD: Base theme size: 800x600
2014-11-07 20:58:51.555300 I  OSD: Scaling factors: 1.28x1.28
2014-11-07 20:58:51.557828 I  Player(0): Video timing method: USleep with busy wait
2014-11-07 20:58:51.558659 I  TV: Created player.
2014-11-07 20:58:51.558711 I  TV: Changing from None to WatchingLiveTV
2014-11-07 20:58:51.558725 I  TV: State is LiveTV & mctx == ctx
2014-11-07 20:58:51.560220 I  TV: UpdateOSDInput done
2014-11-07 20:58:51.560243 I  TV: UpdateLCD done
2014-11-07 20:58:51.560967 I  TV: ITVRestart done
2014-11-07 20:58:51.563435 I  TV: Main UI disabled.
2014-11-07 20:58:51.563489 I  TV: Entering main playback loop.


seems like Myth thinks all is well.

if I access the playback mpg url, with VLC, it plays.
not sure if the cardtype=dummy is the problem

---

### Post by dannyboy79 on 2014-11-07
if your remote mythtv-frontends can access it and watch tv from it than it's not the card itself, it's your playback profile set in mythtv. what are you using for playback settings in your mythtv-frontend?

---

### Post by wyliecoyoteuk on 2014-11-09
I've tried several. The screen set up wizard fails to run.
The monitor is 17" VGA 1280x1024.
(the back-end server sits under a kitchen worksurface)
Although it isn't often needed for LiveTV, it is a little annoying that it doesn't work.

---

### Post by wyliecoyoteuk on 2014-11-25
Sfter the last lot of updates, it has started working again!

---

### Post by wyliecoyoteuk on 2015-01-27
Nuts, latest update has broken LiveTV again, this time on all clients. black screen locally, remote clients say "failed to open jump list"
Plus latest TBS (150109) drivers don't work properly, had to roll back to the last ones.
I can record and then watch the recording OK, and Kodi works fine.

---

### Post by wyliecoyoteuk on 2015-02-04
Well, I deleted the contents of /lib/modules/<kernelversion>/kernel/drivers/media
downloaded and compiled the very latest TBS driver (150130), and now it works again, but remote clients say "failed to open jump program list" and hang.
Kodi frontends work fine.

---

