---
title: "Is anyone else getting stuttering output with &quot;Waited 100ms for video buffers&quot; Errors"
date: 2011-01-30
forum: Mythbuntu
---

### Post by johnlatz on 2011-01-30
I have archived a bunch of kiddie shows off to .m4v files using HandBrake.  It seems that if I attempt to play back anything that was encoded with v0.9.3 or later, the video/audio will stutter to the point of being unwatchable, and the mythfrontend.log file complains about waiting for video buffers:

```

2011-01-30 14:49:20.740 Received a remote 'Clear Cache' request
2011-01-30 14:49:26.492 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@Mythbox/myth/video/)
2011-01-30 14:49:37.375 TV: Attempting to change from None to WatchingVideo
2011-01-30 14:49:44.311 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-01-30 14:49:44.312 AFD: Opened codec 0x7fdaac0c7690, id(H264) type(Video)
2011-01-30 14:49:44.323 AFD: codec AAC has 2 channels
2011-01-30 14:49:44.326 AFD: Opened codec 0x7fdaac07a6a0, id(AAC) type(Audio)
2011-01-30 14:49:44.327 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2011-01-30 14:49:44.434 AO: Opening audio device 'default:CARD=NVidia' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-01-30 14:49:44.439 AudioPlayer: Enabling Audio
2011-01-30 14:49:44.807 VDPAU: Created 2 output surfaces.
2011-01-30 14:49:44.807 VDPAU: Version 1
2011-01-30 14:49:44.808 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 04:58:44 PDT 2010
2011-01-30 14:49:44.808 VDPAU: Created VDPAU render device 1280x720
2011-01-30 14:49:45.016 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-01-30 14:49:45.062 Player(0): Video timing method: USleep with busy wait
2011-01-30 14:49:45.062 TV: Changing from None to WatchingVideo
2011-01-30 14:49:45.081 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-01-30 14:49:48.093 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAaaaa
....   much of the same (100ms errors) clipped ....
2011-01-30 14:49:53.410 Player(0): Waited 100ms for video buffers AAAAaaaaAAAAAAAAA
2011-01-30 14:49:53.694 TV: Attempting to change from WatchingVideo to None
2011-01-30 14:49:53.859 VDPAU Painter: Clearing VDPAU painter cache.
2011-01-30 14:49:53.859 MythPainter: 2 images not yet de-allocated.
2011-01-30 14:49:53.987 TV: Changing from WatchingVideo to None

```Seems to have started shortly after I installed 0.24 from scratch on a new (bigger) HD.  I never had this issue on using 0.24 off the old HD (I had gotten to 0.24 and 10.10 via updates on the old HD.  Rather than trying to clone the old system, I simply installed 10.10/0.24 from scratch and moved my recordings, archive files, and database).

I've been finding here and there others reporting errors with this same 100ms tag ex: [http://code.mythtv.org/trac/ticket/9511](http://code.mythtv.org/trac/ticket/9511) but that would seem to apply to live TV, and not M4V file playback.  Yes - m4v format because the kids (2 and 4) can work my iPod Touch...

My config:  combined FE/BE system, NVIDA 8200 IGP, using VPDAU Slim profile (didn't help when I tried Normal or CPU--)

I downloaded the most recent 0.24 release today (30012011):
```

MythTV Version   : v0.24-133-g06c8142
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0
Options compiled in:
 linux debug using_alsa using_jack using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg

```
Spending far too long for my wife's sanity attempting to diagnose one night, I found the following characteristics.
1) files play splendidly via vlc or mplayer - my issue seems to be confined to the MythTV internal player

2) if I elected NOT to use Storage Groups, and instead set up the filename directly in the FE, it seemed to play back fine.  I did this because when I was attempting to set up an alternate player within MythTV, I noticed that %s resulted in a pseudo URL:  something like mythtv://Videos@MyMythBox/abbreviated/pathname/filename, and I wondered if Myth is attempting to get to the file via a network connection.  note, an "ifconfig" gives
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6883476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6883476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72164314460 (72.1 GB)  TX bytes:72164314460 (72.1 GB)

```  Why would I get such a HUGE amount of data transferred through the loopback?

3) if I pass the offending files through ffmpeg (-vcodec copy -acodec copy), things seem to get better.  The stuttering doesn't disappear completely, but reduces to once in a while as opposed to unwatchable.  The output from HandBrake -i on both versions:
Good File (after ffmpeg passthrough):
  Metadata:
    major_brand     : M4V 
    minor_version   : 512
    compatible_brands: isomiso2avc1
    encoder         : Lavf52.64.2

Bad File:
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isom
    encoder         : HandBrake 0.9.3 2008112300

4) if I encode a video from scratch, using HandBrake v0.9.5, it seems to work just fine:
New encode:
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    encoder         : HandBrake 0.9.5 2011010300

What is the significance of mp42isom versus mp42isomavc1?



Can anyone point me in a good direction?  I saw a brief mention in the release notes for 0.24-fixes that there was a 100ms issue addressed about Dec-17-2010, and had hoped that that fix would be wrapped into the latest Mythbuntu release (again, I downloaded the latest today), but it hasn't seemed to hit yet, or at least what may have been addressed may not be what's affecting me.

Thanks
John Latz

---

### Post by johnlatz on 2011-01-30
And now I just got the same error when playing back recorded TV:

```
2011-01-30 18:45:34.957 ALSA, Error: WriteAudio: buffer underrun
2011-01-30 18:45:35.049 Player(2): Waited 100ms for video buffers LALAAAAAAAAAAAAaA
2011-01-30 18:45:35.058 Player(2): Waited 100ms for video buffers LALAAAAAAAAAAAAaA
2011-01-30 18:45:35.177 Player(2): Waited 100ms for video buffers LALAAAAAAAAAAAAaA
2011-01-30 18:45:35.185 Player(2): Waited 100ms for video buffers uAULULAAAAAAAAAAA
2011-01-30 18:45:35.403 Player(2): Waited 100ms for video buffers aAALALAAAAAAAAAAA
2011-01-30 18:45:35.412 Player(2): Waited 100ms for video buffers AAAuAULLAAAAAAAAA
2011-01-30 18:45:35.756 ALSA, Error: WriteAudio: buffer underrun

```

ALSA - Could this be an audio issue?

---

### Post by michcook on 2011-02-20
Did you find an solution to this problem? I had problem with mythtv 0.23 not working with U10.10 (failed to playback, presented with login screen).
So I upgraded the kernel to 2.6.36 and this didnt' work, then tried upgrading 0.24.  I can now get playback with the same problems you've reported and it seems to not exit Mythtv when I try and exit playback.

Setup: I am trying to play an HD stream (8Mbps) to a Zotac Zbox front end.  MYthtv 0.23 in 10.04 worked fine.  I had to upgrade to get NVIDIA drivers with Zbox to work.  I also upgraded the backend to 10.10.

---

### Post by nickrout on 2011-02-20
Are you using vdpau? If so try increasing vdpaubuffersize.

---

### Post by rhpot1991 on 2011-02-21
> **nickrout said:**
> Are you using vdpau? If so try increasing vdpaubuffersize.

I second this, you should try the other tweaks here as well: [http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering](http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering)

Normally these kind of issues are caused by a bottleneck somewhere, what does your usage look like when the issues are occurring?

---

### Post by rejze on 2011-03-07
Hello. I examined the problem at the terminal and a stuttering video with sound at the 41000 If the sound of 48000 video works properly. The reason I do not know yet. Does anyone know why?

---

### Post by jlazkano on 2011-03-07
> **rejze said:**
> Hello. I examined the problem at the terminal and a stuttering video with sound at the 41000 If the sound of 48000 video works properly. The reason I do not know yet. Does anyone know why?

Thanks for your post, is possible to force the audio to 48000? It will great to fix this problems.

Thanks and best regards.

---

### Post by kja999 on 2011-03-07
I have been having the same issues on TV playback but not on encoded video (I also use HandBrake but encode to mp4 with H264).
I have got around it by the simple change of the playback profile, changing from VDPAU High Quality to VDPAU Slim. 

 
@nickrout : How do I set the vdpaubuffersize ?
<edit> Found it on the wiki link for tearing... thx <edit>


@jlazkano : you can force the audio in the audio settings and switch on the advanced section (on the screen where you select the device), there are 3 tick boxes, one forces the audio rate.

---

### Post by TrevorBradley on 2011-05-02
I'm getting identical errors when I attempt to play video that is presently recording, but not live TV, and not TV that's finished recording (possibly transcoded?)

I've tried adjusting VDPAU settings, and even turning it off, no difference.  Everything was working great before upgrading to natty.

Any ideas what might be wrong?  

My own log output:
```
$ mythfrontend
2011-05-02 14:43:03.406 mythfrontend version: fixes/0.24 [v0.24-243-g9ba3ece] www.mythtv.org
2011-05-02 14:43:03.407 Using runtime prefix = /usr
2011-05-02 14:43:03.407 Using configuration directory = /home/trevor/.mythtv
2011-05-02 14:43:03.409 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-05-02 14:43:04.880 Empty LocalHostName.
2011-05-02 14:43:04.880 Using localhost value of alexandria
2011-05-02 14:43:04.881 Testing network connectivity to '192.168.11.1'
2011-05-02 14:43:05.047 New DB connection, total: 1
2011-05-02 14:43:05.057 Connected to database 'mythconverg' at host: 192.168.11.1
2011-05-02 14:43:05.115 Closing DB connection named 'DBManager0'
2011-05-02 14:43:05.117 Connected to database 'mythconverg' at host: 192.168.11.1
2011-05-02 14:43:05.121 Current locale EN_CA
2011-05-02 14:43:05.121 Reading locale defaults from /usr/share/mythtv//locales/en_ca.xml
2011-05-02 14:43:05.285 ScreenSaverX11Private: Gnome screen saver support enabled
2011-05-02 14:43:05.288 DPMS is disabled.
2011-05-02 14:43:05.337 Desktop video mode: 1920x1200 59.950 Hz
2011-05-02 14:43:05.392 Enabled verbose msgs:  important general
2011-05-02 14:43:05.401 Loading en_us translation for module mythfrontend
2011-05-02 14:43:05.428 LIRC, Error: Failed to read config file '/home/trevor/.lircrc'
2011-05-02 14:43:05.429 JoystickMenuThread: Joystick disabled - Failed to read /home/trevor/.mythtv/joystickmenurc
2011-05-02 14:43:05.516 Using Frameless Window
2011-05-02 14:43:05.517 Using Full Screen Window
2011-05-02 14:43:05.698 Using the OpenGL painter
2011-05-02 14:43:05.817 OpenGL: OpenGL vendor  : NVIDIA Corporation
2011-05-02 14:43:05.817 OpenGL: OpenGL renderer: GeForce 8400 GS/PCI/SSE2/3DNOW!
2011-05-02 14:43:05.817 OpenGL: OpenGL version : 3.3.0 NVIDIA 270.41.06
2011-05-02 14:43:05.817 OpenGL: Max texture size: 8192 x 8192
2011-05-02 14:43:05.817 OpenGL: Max texture units: 4
2011-05-02 14:43:05.817 OpenGL: Direct rendering: Yes
2011-05-02 14:43:05.817 OpenGL: Initialised MythRenderOpenGL
2011-05-02 14:43:06.290 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-02 14:43:06.553 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-02 14:43:06.554 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-02 14:43:06.556 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-02 14:43:06.556 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-02 14:43:07.200 Registering Internal as a media playback plugin.
2011-05-02 14:43:07.275 Loading en_us translation for module mytharchive
2011-05-02 14:43:07.291 Registering WebBrowser as a media playback plugin.
2011-05-02 14:43:07.292 Loading en_us translation for module mythbrowser
2011-05-02 14:43:07.401 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.401 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.401 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.402 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.402 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.402 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.403 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.403 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.403 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.404 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.404 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.404 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.405 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.405 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.406 MediaMonitorUnix::AddDevice() - empty device path.
2011-05-02 14:43:07.406 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-02 14:43:07.406 Loading en_us translation for module mythgallery
2011-05-02 14:43:07.417 Loading en_us translation for module mythgame
2011-05-02 14:43:07.432 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-02 14:43:07.512 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-02 14:43:07.523 Loading en_us translation for module mythmusic
2011-05-02 14:43:07.528 Loading en_us translation for module mythnetvision
2011-05-02 14:43:07.535 Loading en_us translation for module mythnews
2011-05-02 14:43:07.553 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-02 14:43:07.594 Loading en_us translation for module mythvideo
2011-05-02 14:43:07.608 Loading en_us translation for module mythweather
2011-05-02 14:43:07.672 Found mainmenu.xml for theme 'Arclight'
2011-05-02 14:43:08.063 MythCoreContext: Connecting to backend server: 192.168.11.1:6543 (try 1 of 1)
2011-05-02 14:43:08.064 Using protocol version 63
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 14:43:11.552 New DB connection, total: 2
2011-05-02 14:43:11.553 Connected to database 'mythconverg' at host: 192.168.11.1
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 14:43:13.032 TV: Attempting to change from None to WatchingRecording
2011-05-02 14:43:13.053 MythCoreContext: Connecting to backend server: 192.168.11.1:6543 (try 1 of 1)
2011-05-02 14:43:13.054 Using protocol version 63
2011-05-02 14:43:14.273 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-05-02 14:43:14.273 AFD Error: Probing of stream #0 unsuccesful, ignoring.
2011-05-02 14:43:14.274 AFD: codec MP2 has 2 channels
2011-05-02 14:43:14.274 AFD: Opened codec 0xa9eea00, id(MP2) type(Audio)
2011-05-02 14:43:14.297 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-05-02 14:43:14.302 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-05-02 14:43:14.396 ALSA, Error: no playback control PCM found on mixer device default
2011-05-02 14:43:14.396 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-02 14:43:14.396 AudioPlayer: Enabling Audio
2011-05-02 14:43:14.565 Clearing OpenGL painter cache.
2011-05-02 14:43:14.651 VDPAU: Created 2 output surfaces.
2011-05-02 14:43:14.651 VDPAU: Version 1
2011-05-02 14:43:14.651 VDPAU: Information NVIDIA VDPAU Driver Shared Library  270.41.06  Mon Apr 18 15:14:35 PDT 2011
2011-05-02 14:43:14.651 VDPAU: Created VDPAU render device 1920x1200
2011-05-02 14:43:14.719 Player(0): Video timing method: USleep with busy wait
2011-05-02 14:43:14.720 TV: Changing from None to WatchingRecording
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 14:43:15.001 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAA
*** REPEAT APPROX 550 TIMES)
2011-05-02 14:43:34.899 Player(0), Error: Waited too long for decoder to fill video buffers. Exiting..
2011-05-02 14:43:35.073 TV: Attempting to change from WatchingRecording to None
2011-05-02 14:43:40.179 Player(0), Error: Failed to stop decoder loop.
2011-05-02 14:43:40.183 VDPAU Painter: Clearing VDPAU painter cache.
2011-05-02 14:43:40.183 MythPainter: 43 images not yet de-allocated.
2011-05-02 14:43:40.266 TV: Changing from WatchingRecording to None
2011-05-02 14:43:40.281 TV: Attempting to change from None to WatchingRecording
2011-05-02 14:43:40.306 MythCoreContext: Connecting to backend server: 192.168.11.1:6543 (try 1 of 1)
2011-05-02 14:43:40.307 Using protocol version 63
2011-05-02 14:43:40.435 playCtx, Error: Attempting to setup a player, but it already exists.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 14:43:41.318 Preview: RemotePreviewRun() -- no reply..
2011-05-02 14:43:43.845 OpenGL: Deleting OpenGL Resources
2011-05-02 14:43:43.883 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

```

---

### Post by jyavenard on 2011-05-02
> **kja999 said:**
> 
@jlazkano : you can force the audio in the audio settings and switch on the advanced section (on the screen where you select the device), there are 3 tick boxes, one forces the audio rate.

Those options should be left alone in 99% of the time ; the only time I've seen forcing 48kHz useful is with some old audio card that reported they supported 44.1khZ when they didn't.

If using VDPAU, the audio buffer is always increased so no need to tweak that either

---

### Post by Dr Bones on 2011-09-15
I just wanted to point out an observation I made while I had this problem.  I would get the waited for video buffers and RingBuf Waited 0.2 seconds for data occasionally while watching either live tv or a recording. I tried a few different things involving the differing playback profiles (CPU++, VDPAU and the likes) to no avail.  

I tried using my PS3 to see if I got the same stuttering every second and I found that the playback was perfectly smooth so the problem lied with the frontend.  Knowing this I tried using a Mythbuntu 11.04 live cd and had the exact same problem.  When rebooting I went back to 2.6.35.22 instead of the 2.6.35.30 I was using before.  Started mythfrontend and ran perfectly. 

I am not sure what was changed between the kernels that could have caused this but I wanted to let someone who may have an idea give anyone still interested a helping hand.  Good luck!

---

### Post by jlazkano on 2011-09-16
> **Dr Bones said:**
> I just wanted to point out an observation I made while I had this problem.  I would get the waited for video buffers and RingBuf Waited 0.2 seconds for data occasionally while watching either live tv or a recording. I tried a few different things involving the differing playback profiles (CPU++, VDPAU and the likes) to no avail.  

I tried using my PS3 to see if I got the same stuttering every second and I found that the playback was perfectly smooth so the problem lied with the frontend.  Knowing this I tried using a Mythbuntu 11.04 live cd and had the exact same problem.  When rebooting I went back to 2.6.35.22 instead of the 2.6.35.30 I was using before.  Started mythfrontend and ran perfectly. 

I am not sure what was changed between the kernels that could have caused this but I wanted to let someone who may have an idea give anyone still interested a helping hand.  Good luck!

Thanks for your post, I am having this problem lots of time. I am on Debian Squeeze (2.6.32-5-686) with debian-mutimedia repository on a Nvidia ION board.

This is what I get on the frontend log:

```

2011-09-12 16:36:28.333 [mp2 @ 0xb4c7df60]Header missing
2011-09-12 16:36:28.333 AFD Error: Unknown audio decoding error
2011-09-12 16:36:28.361 AO: OutputAudioLoop: Play Event
2011-09-12 16:36:28.572 AO: Pause 1
2011-09-12 16:36:28.575 [mp2 @ 0xb4c7df60]Header missing
2011-09-12 16:36:28.575 AFD Error: Unknown audio decoding error
2011-09-12 16:36:28.580 AO: OutputAudioLoop: audio paused
2011-09-12 16:36:28.682 Player(0): Waited 100ms for video buffers
(AF)(ad)(AD)(ad)AAAAAAAAAALAAAAAAAAAAAAAAAAA(AF)(ad)(AD)(ad)
2011-09-12 16:36:28.698 Player(0): Waited 100ms for video buffers
(AF)(ad)(AD)(ad)AAAAAAAAAALAAAAAAAAAAAAAAAAA(AF)(ad)(AD)(ad)
2011-09-12 16:36:28.804 Player(0): Waited 100ms for video buffers
(AF)(ad)(AD)(ad)AAAAAAAAAALAAAAAAAAAAAAAAAAA(AF)(ad)(AD)(ad)
2011-09-12 16:36:28.810 Player(0): Waited 100ms for video buffers
(AF)(ad)(AD)(ad)AAAAAAAAAALAAAAAAAAAAAAAAAAA(AF)(ad)(AD)(ad)
2011-09-12 16:36:28.825 [mp2 @ 0xb4c7df60]Header missing
2011-09-12 16:36:28.826 AFD Error: Unknown audio decoding error
2011-09-12 16:36:28.826 [mp2 @ 0xb4c7df60]Header missing
2011-09-12 16:36:28.826 AFD Error: Unknown audio decoding error
2011-09-12 16:36:28.826 Player(0): Waited 100ms for video buffers
(UF)(AD)(AD)(AD)AAAAAAALAAuAAAAAAAAAAAAAAAAA(UF)(AD)(AD)(AD)
2011-09-12 16:36:28.827 AO: Pause 0
2011-09-12 16:36:28.831 AO: OutputAudioLoop: Play Event
2011-09-12 16:36:28.947 AO: Pause 1
2011-09-12 16:36:28.956 AO: OutputAudioLoop: audio paused
2011-09-12 16:36:28.979 AO: Pause 0
2011-09-12 16:36:29.001 AO: OutputAudioLoop: Play Event

```

I will appreciate any help, I don't know what else to try.

Thanks and best regards.

---

### Post by rhpot1991 on 2011-09-16
These issues are often network related as well, so make sure to look at that.

---

### Post by bblboy54 on 2011-12-05
I started having this issue with a video file and have been trying to figure out exactly what is going on but I think I may have narrowed this down to the version of the codec used.  I opened up multiple videos in VLC and all of them are MPEG-4 Video but the one that I am having problems with is DX50 while all of the other ones that work are (XVID).  I also loaded up iptraf while starting a video on my front end and I'm seeing that the network load is drastically different.  When I open the video using DX50 my throughput runs around 88000 kbits/sec and stays constant around that mark... when I start playing a video other than that one I'm looking at around 15000 kbits/sec and it does not stay up that high constantly but only in short bursts.  I then played the same DX50 file from my backend server to my laptop using VLC and it played fine with only around 200kbits/sec peak which, interestingly enough, is about the same as any of my XviD videos.  It would seem like mythtv has an issue with streaming DX50 from storage groups requiring an insanely high bandwidth requirement.  I still haven't found a solution, unfortunately.

---

### Post by nickrout on 2011-12-05
> **bblboy54 said:**
> I started having this issue with a video file and have been trying to figure out exactly what is going on but I think I may have narrowed this down to the version of the codec used.  I opened up multiple videos in VLC and all of them are MPEG-4 Video but the one that I am having problems with is DX50 while all of the other ones that work are (XVID).  I also loaded up iptraf while starting a video on my front end and I'm seeing that the network load is drastically different.  When I open the video using DX50 my throughput runs around 88000 kbits/sec and stays constant around that mark... when I start playing a video other than that one I'm looking at around 15000 kbits/sec and it does not stay up that high constantly but only in short bursts.  I then played the same DX50 file from my backend server to my laptop using VLC and it played fine with only around 200kbits/sec peak which, interestingly enough, is about the same as any of my XviD videos.  It would seem like mythtv has an issue with streaming DX50 from storage groups requiring an insanely high bandwidth requirement.  I still haven't found a solution, unfortunately.

What you haven't told us is the bitrate of the various files. mediainfo is the best tool for checking. Your logs are also worth looking at.

---

### Post by rdreeves on 2012-10-12
> **bblboy54 said:**
> I started having this issue with a video file and have been trying to figure out exactly what is going on but I think I may have narrowed this down to the version of the codec used.  I opened up multiple videos in VLC and all of them are MPEG-4 Video but the one that I am having problems with is DX50 while all of the other ones that work are (XVID).  I also loaded up iptraf while starting a video on my front end and I'm seeing that the network load is drastically different.  When I open the video using DX50 my throughput runs around 88000 kbits/sec and stays constant around that mark... when I start playing a video other than that one I'm looking at around 15000 kbits/sec and it does not stay up that high constantly but only in short bursts.  I then played the same DX50 file from my backend server to my laptop using VLC and it played fine with only around 200kbits/sec peak which, interestingly enough, is about the same as any of my XviD videos.  It would seem like mythtv has an issue with streaming DX50 from storage groups requiring an insanely high bandwidth requirement.  I still haven't found a solution, unfortunately.


I have found a similar problem with some AVI-files using the DX50 codec. The problem is only evident when trying to stream the file from a media server.

It seems to be associated with the audio stream. 

I fixed the stutter by using VirtualDub (1.9.11) with the video set to Direct Stream Copy and the audio set to Full Stream Processing: MPEG Layer 3: 160 kBit/s, 48,000 Hz, Stereo.

The meta data in the original file (using GSpot)was:
[JUNK]	VirtualDub build 32842/release
[ISFT]	VirtualDubMod 1.5.10.2 (build 2540/release)
[USER]	DivX503b1393p
[USER]	XviD0050

And the original audio format was: 48000Hz  160 kb/s tot , Joint Stereo (i.e the same as the converted-fixed file). The converted file is practically the same size as the original as would be expected.

I assume there must have been a problem with how the original file was constructed by the earlier version of VirtualDub.

---

### Post by rdreeves on 2012-10-12
Edit: Corrected metadata from original file

I have found a similar problem with some AVI-files using the DX50 codec. The problem is only evident when trying to stream the file from a media server. As you observed, the expected data rates were well within the capabilities of the network that I was using.

The problem I had seemed to be associated with the audio stream. 

I fixed the stutter by using VirtualDub (1.9.11, Build 32842) with the video set to Direct Stream Copy and the audio set to Full Stream Processing: MPEG Layer 3: 160 kBit/s, 48,000 Hz, Stereo.

The meta data in the original file (using GSpot) was an earlier version:
[ISFT]	VirtualDubMod 1.5.10.2 (build 2540/release)
[JUNK]	VirtualDubMod build 2540/release
[USER]	DivX503b1393p
[USER]	XviD0050


And the original audio format was: 48000Hz 160 kb/s tot , Joint Stereo (i.e the same as the converted-fixed file). The converted file is practically the same size as the original as would be expected.

I assume there must have been a problem with how the original file was constructed by the earlier version of VirtualDub.

---

### Post by tgm4883 on 2012-10-12
Please check the date of the thread you reply to and if it's old, open a new thread. Closing zombie thread.

---

