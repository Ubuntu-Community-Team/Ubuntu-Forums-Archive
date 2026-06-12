---
title: "Natty upgrade (11.04) caused jumpy video playback"
date: 2011-05-01
forum: Mythbuntu
---

### Post by chris_gs on 2011-05-01
Hi everyone,

I'm keen for any help on this one.
I had mythtv running fine on 10.10, no jumpy. 
I upgraded through the update manager (always somewhat of a mistake) to 11.04 to get support for my IR remote (which worked.. at least one positive)
Unfortunately video playback has been jumpy with mythtv since the upgrade.
In desparation I rebuilt the machine using the latest mythbuntu natty live CD, installed the mythbuntu update repositories and updated everything.
The video is still jumpy on SD, and even getting jumpy audio on HD.
I'm running an HP DV1000 - its a single core intel 32bit, 2GB of ram, and intel ?ATI i think video card.
I'm running it to a full HD TV through the VGA cable, and as I said, it was running with no issues.

The rendering profile I used is CPU-- and changing the decoder to stadard and xv-blt (which was the only one that worked on 10.10)... I have turned real-time threads off and extra audio buffering on.

Running programs that have been recorded with mythtv through VLC or mplayer plays back perfectly with no jumping at all.

I've tried using the opengl rendering (having to set the opengloptions=nofrag to get it to work) and that was unwatchably jumpy.

Any ideas would be really welcome!

Cheers,
Chris

---

### Post by kja999 on 2011-05-01
Hi,

launch mythfrontend from the terminal with
mythfrontend -v playback,audio

it may give some clues....

---

### Post by agamotto on 2011-05-01
Possibly stupid thought, but in the Playback setup in the frontend, did you change the screen size to 720x480 for the Live TV and Default playback?  I know that this used to cause all sorts of jumpies with my pvr-150... Also, see if changing your rendering profile to 'Normal' helps.  The HD audio jumpiness might be due to the card's audio sampling rate... I set all of my cards to 48k... seems to work for me.

Hope these help!

---

### Post by chris_gs on 2011-05-02
Hi guys,
thanks for the really fast replies... that's what I love about all the ubuntu stuff, everyone's so willing to help!
[agamotto]("http://ubuntuforums.org/member.php?u=209309"), i'm not sure how to change the screen resolution - there does't seem to be an option on for that on my playback setup in the front end... there's zoom & stretch, but I couldn't find anywhere to set the resolution.
I tried setting all the decoder profiles, normal, CPU++, etc... the CPU-- was not even very good until I changed it to use standard (ffmpeg) instead of libmpeg... all other profiles were absolutly atrocious (even before upgrade to 11.04), but with standard, xv-blit & interlacing none on 10.10 the playback was smooth....
And with the audio, from what I could see (from the log attached) my audio is running at 48khz...
It did seem to have trouble allocating the extended buffer...

[kja999]("http://ubuntuforums.org/member.php?u=942880"), thanks for that tip with the verbosity... very handy... now there's just decoding what the output means...
I've attached the logs running with xv-blit & opengl (opengl is atrocious)
VLC still misses a few frames but appears to be using XVideo with direct rendering for far far better performance.... than myth

thanks,
Chris

---

### Post by kja999 on 2011-05-02
Ok, a couple of things here ..
The log shows the errors from your playback profiles (so it doesn't like your CPU--), so change that for a start, but the log seems to suggest that VDPAU is available, which would be a better option if you can , although I didnt think it was working on Intel yet.
I.e.
2011-05-02 07:47:22.269 VDP: Ignoring profile item 11 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))

Check your CPU usage as the video is playing, and switch the TV playback profiles to see if it is underperforming. Try the Slim profile. 


Then there is these:
2011-05-02 07:47:22.205 ALSA, Error: Setting hardware audio buffer size to 128
2011-05-02 07:47:22.205 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2011-05-02 07:47:22.205 ALSA, Error: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-05-02 07:47:22.205 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely

Not sure the impact of this, but to me it seems your stuttering issue is video and audio getting out of sync, which can be caused by either of the two not working correctly.

---

### Post by ian dobson on 2011-05-02
Hi,

I'm seeing the same error messages about /proc/asound/card0/pcm0p/sub0/prealloc, I can't even change the value as root :(

For me the stuttering happens when I delete a recording on the backend (seperate computer) when watching a recording. It's almost as if the backend process just ignores the frontend for 1 second or so while processing the delete command.

I'll try and see if I can reproduce this with starting a recording and watching at the same time. I'm also seeing messages about "attempting to delete a timer that doesn't belong to this thread" on the frontend.

Frontend is an underclocked Core2Duo with a vdpau capable graphic card. The systems have been running since 8.04ish without any problems/stuttering after enabling vdpau.

EDIT: Here's my frontend log file
```
2011-05-02 19:03:23.912 PlaybackBox: Ignoring PREVIEW_SUCCESS, item no longer on screen.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 19:03:26.480 TV: Attempting to change from None to WatchingPreRecorded
2011-05-02 19:03:27.181 AFD: Opened codec 0x4983710, id(MPEG2VIDEO) type(Video)
2011-05-02 19:03:27.181 AFD: codec MP2 has 2 channels
2011-05-02 19:03:27.182 AFD: Opened codec 0x3e9cbc0, id(MP2) type(Audio)
2011-05-02 19:03:27.314 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2011-05-02 19:03:27.317 ALSA, Error: Setting hardware audio buffer size to 6016
2011-05-02 19:03:27.318 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied.
2011-05-02 19:03:27.318 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-05-02 19:03:27.318 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2011-05-02 19:03:27.323 AudioPlayer: Enabling Audio
2011-05-02 19:03:27.672 VDPAU: Created 2 output surfaces.
2011-05-02 19:03:27.672 VDPAU: Version 1
2011-05-02 19:03:27.672 VDPAU: Information NVIDIA VDPAU Driver Shared Library  270.41.06  Mon Apr 18 15:13:22 PDT 2011
2011-05-02 19:03:27.672 VDPAU: Created VDPAU render device 1920x1080
2011-05-02 19:03:27.693 Player(0): Forcing decode extra audio option on (Video method requires it).
2011-05-02 19:03:27.693 FilterManager: Failed to load filter 'colorspace', no such filter exists
2011-05-02 19:03:27.803 Player(0): Video timing method: USleep with busy wait
2011-05-02 19:03:27.805 TV: Changing from None to WatchingPreRecorded
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 19:03:27.846 VDPAU: Added 2 output surfaces (total 4, max 4)
2011-05-02 19:03:29.091 TV: ASK_RECORDING 1 29 0 0 hasrec: 0 haslater: 0
2011-05-02 19:03:29.091 TV: ASK_RECORDING 2 29 0 0 hasrec: 0 haslater: 0
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 19:04:01.841 PlaybackBoxHelper Error: CHECK_AVAILABILITY 'myth://192.168.0.2:6543/32434_20110502190400.mpg' file not found
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 19:04:02.416 ALSA, Error: WriteAudio: buffer underrun
```Regards
Ian Dobson

---

### Post by haazs on 2011-05-02
Hi,
first of all, thank you all for looking into the problem!
i'm experiencing the same issue, jumpy video after an upgrade from 10.10 => 11.04, audio is working fine.
my core i3 550 had no problems before the upgrade (i had mythtv .24 installed via [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)) with combined front and backend. an other frontend (not upgraded) is still working fine.
i attached the last part of my /var/log/mythfrontend.log
i'm not at home so i can't do: mythfrontend -v playback,audio i'll post it asap.
cheers

---

### Post by haazs on 2011-05-03
could it be all the VPD messeges indicate myth is trying to use VDPAU cause i do not have VDPAU (guess that would be strange as a result from upgrading ubuntu, i did not change mythtv)? 

"/var/log/mythtv/mythfrontend.log" last part:

[PHP]Starting mythfrontend.real..
2011-05-02 00:17:59.968 mythfrontend version: fixes/0.24 [v0.24-250-g56c54fa] www.mythtv.org
2011-05-02 00:17:59.968 Using runtime prefix = /usr
2011-05-02 00:17:59.968 Using configuration directory = /home/henk/.mythtv
2011-05-02 00:18:00.002 Configuration::Load - Error parsing: /home/henk/.mythtv/config.xml at line: 1  column: 1
2011-05-02 00:18:00.002 Configuration::Load - Error Msg: unexpected end of file
2011-05-02 00:18:00.009 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
2011-05-02 00:18:00.632 Empty LocalHostName.
2011-05-02 00:18:00.632 Using localhost value of tvserver
2011-05-02 00:18:00.632 Configuration::Load - Error parsing: /home/henk/.mythtv/config.xml at line: 1  column: 1
2011-05-02 00:18:00.632 Configuration::Load - Error Msg: unexpected end of file
2011-05-02 00:18:00.665 New DB connection, total: 1
2011-05-02 00:18:00.669 Connected to database 'mythconverg' at host: localhost
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
2011-05-02 00:18:00.681 Closing DB connection named 'DBManager0'
2011-05-02 00:18:00.682 Connected to database 'mythconverg' at host: localhost
2011-05-02 00:18:00.684 Current locale EN_US
2011-05-02 00:18:00.697 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-05-02 00:18:00.917 ScreenSaverX11Private: Gnome screen saver support enabled
2011-05-02 00:18:00.919 DPMS is active.
2011-05-02 00:18:01.012 Desktop video mode: 2000x768 60.000 Hz
2011-05-02 00:18:01.618 Enabled verbose msgs:  important general
2011-05-02 00:18:01.647 Loading en_us translation for module mythfrontend
2011-05-02 00:18:01.714 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-05-02 00:18:01.714 JoystickMenuThread: Joystick disabled - Failed to read /home/henk/.mythtv/joystickmenurc
2011-05-02 00:18:01.758 Using Frameless Window
2011-05-02 00:18:01.758 Using Full Screen Window
2011-05-02 00:18:02.212 Using the OpenGL painter
2011-05-02 00:18:02.555 OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
2011-05-02 00:18:02.555 OpenGL: OpenGL renderer: Mesa DRI Intel(R) Ironlake Desktop GEM 20100330 DEVELOPMENT 
2011-05-02 00:18:02.555 OpenGL: OpenGL version : 2.1 Mesa 7.10.2
2011-05-02 00:18:02.555 OpenGL: Max texture size: 4096 x 4096
2011-05-02 00:18:02.555 OpenGL: Max texture units: 8
2011-05-02 00:18:02.555 OpenGL: Direct rendering: Yes
2011-05-02 00:18:02.555 OpenGL: Initialised MythRenderOpenGL
2011-05-02 00:18:03.402 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-02 00:18:04.495 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-02 00:18:04.495 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-02 00:18:04.548 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-02 00:18:04.548 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-02 00:18:05.094 Pulse: PulseAudio suspend OK
2011-05-02 00:18:05.281 Pulse: PulseAudio resume OK
2011-05-02 00:18:05.425 Registering Internal as a media playback plugin.
2011-05-02 00:18:05.546 Loading en_us translation for module mytharchive
2011-05-02 00:18:05.568 Registering WebBrowser as a media playback plugin.
2011-05-02 00:18:05.569 Loading en_us translation for module mythbrowser
2011-05-02 00:18:05.620 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-02 00:18:05.631 Loading en_us translation for module mythgallery
2011-05-02 00:18:05.723 Loading en_us translation for module mythgame
2011-05-02 00:18:06.175 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-02 00:18:06.203 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-02 00:18:06.219 Loading en_us translation for module mythmusic
2011-05-02 00:18:06.262 Loading en_us translation for module mythnetvision
2011-05-02 00:18:06.357 Loading en_us translation for module mythnews
2011-05-02 00:18:06.418 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-02 00:18:06.438 Loading en_us translation for module mythvideo
2011-05-02 00:18:06.469 Loading en_us translation for module mythweather
2011-05-02 00:18:06.674 Found mainmenu.xml for theme 'Mythbuntu'
2011-05-02 00:18:06.903 MythCoreContext: Connecting to backend server: 192.168.2.200:6543 (try 1 of 1)
2011-05-02 00:18:06.904 Using protocol version 63
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
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
Application asked to unregister timer 0x0 which is not registered in this thread. Fix application.
2011-05-02 00:18:10.003 New DB connection, total: 2
2011-05-02 00:18:10.003 Connected to database 'mythconverg' at host: localhost
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
2011-05-02 00:18:14.278 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@tvserver/var/lib/mythtv/videos/)
2011-05-02 00:18:16.629 buildFileList directory = myth://Videos@tvserver/var/lib/mythtv/videos/
2011-05-02 00:18:16.629 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@tvserver/var/lib/mythtv/videos/)
2011-05-02 00:18:16.639 Adding :  : The.KIller.Inside.Me.2010.mkv : 1a0db6ee07297a50
2011-05-02 00:18:16.756 Adding :  : The.Roommate.2011.mkv : d4a55d1e00d9c86c
2011-05-02 00:18:16.774 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@tvserver/var/lib/mythtv/videos/)
2011-05-02 00:18:16.798 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Roommate 2011
2011-05-02 00:18:21.886 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 49950
2011-05-02 00:18:26.266 Returning Metadata Results: The Roommate 0 0
2011-05-02 00:18:26.266 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The KIller Inside Me 2010
2011-05-02 00:18:26.423 Metadata Image Download: http://cf1.imgobject.com/posters/035/4db1b6075e73d6729f000035/the-roommate-original.jpg -> myth://Coverart@192.168.2.200:6543/49950_coverart.jpg
2011-05-02 00:18:27.620 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 37414
2011-05-02 00:18:28.085 Returning Metadata Results: The Killer Inside Me 0 0
2011-05-02 00:18:29.380 Metadata Image Download: http://cf1.imgobject.com/backdrops/0d6/4dab8c417b9aa175f50010d6/the-roommate-original.jpg -> myth://Fanart@192.168.2.200:6543/49950_fanart.jpg
2011-05-02 00:18:31.097 Metadata Image Download: http://cf1.imgobject.com/posters/074/4c746a9d7b9aa16609000074/the-killer-inside-me-original.jpg -> myth://Coverart@192.168.2.200:6543/37414_coverart.jpg
2011-05-02 00:18:33.001 Metadata Image Download: http://cf1.imgobject.com/backdrops/232/4bec4c4a017a3c37a5000232/the-killer-inside-me-original.jpg -> myth://Fanart@192.168.2.200:6543/37414_fanart.jpg
2011-05-02 00:18:34.869 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 37414
2011-05-02 00:18:35.445 Returning Metadata Results: The Killer Inside Me 0 0
2011-05-02 00:20:03.940 TV: Attempting to change from None to WatchingVideo
2011-05-02 00:20:04.500 Pulse: PulseAudio suspend OK
2011-05-02 00:20:04.904 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-05-02 00:20:04.904 AFD: Opened codec 0x3a46da0, id(H264) type(Video)
2011-05-02 00:20:04.904 AFD: codec AAC has 2 channels
2011-05-02 00:20:04.905 AFD: Opened codec 0x390d3f0, id(AAC) type(Audio)
2011-05-02 00:20:04.999 Pulse: PulseAudio resume OK
2011-05-02 00:20:05.099 Pulse: PulseAudio suspend OK
2011-05-02 00:20:05.124 AO: Opening audio device 'hdmi:CARD=Intel,DEV=0' ch 2(2) sr 44100 sf signed 16 bit reenc 0
2011-05-02 00:20:05.178 ALSA, Error: no playback control PCM found on mixer device default
2011-05-02 00:20:05.178 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-02 00:20:05.178 AudioPlayer: Enabling Audio
2011-05-02 00:20:05.235 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-05-02 00:20:05.275 OSD: Base theme size: 1280x720
2011-05-02 00:20:05.275 OSD: Scaling factors: 1x0.955556
2011-05-02 00:20:05.332 OSD: Base theme size: 1280x720
2011-05-02 00:20:05.332 OSD: Scaling factors: 1x0.955556
2011-05-02 00:20:05.355 Player(0): Video timing method: DRM
2011-05-02 00:20:05.371 TV: Changing from None to WatchingVideo
2011-05-02 00:20:05.380 ScreenSaverX11Private: DPMS Deactivated 1
2011-05-02 00:20:05.415 VideoOutput: Created YV12 OSD.
2011-05-02 00:20:22.433 AFD: No DTS Seeking Hack!
2011-05-02 00:20:22.672 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAuULL
2011-05-02 00:20:24.270 TV: Attempting to change from WatchingVideo to None
2011-05-02 00:20:24.416 Pulse: PulseAudio resume OK
2011-05-02 00:20:24.417 TV: Changing from WatchingVideo to None
2011-05-02 00:20:24.417 ScreenSaverX11Private: DPMS Reactivated 1
2011-05-02 00:21:25.862 TV: Attempting to change from None to WatchingVideo
2011-05-02 00:21:26.179 Pulse: PulseAudio suspend OK
2011-05-02 00:21:26.315 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-05-02 00:21:26.315 AFD: Opened codec 0x7f7e804362b0, id(H264) type(Video)
2011-05-02 00:21:26.315 AFD: codec AAC has 2 channels
2011-05-02 00:21:26.317 AFD: Opened codec 0x7f7e80006470, id(AAC) type(Audio)
2011-05-02 00:21:26.480 Pulse: PulseAudio resume OK
2011-05-02 00:21:26.680 Pulse: PulseAudio suspend OK
2011-05-02 00:21:26.707 AO: Opening audio device 'hdmi:CARD=Intel,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-05-02 00:21:26.735 ALSA, Error: no playback control PCM found on mixer device default
2011-05-02 00:21:26.735 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-02 00:21:26.736 AudioPlayer: Enabling Audio
2011-05-02 00:21:26.748 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-05-02 00:21:26.791 OSD: Base theme size: 1280x720
2011-05-02 00:21:26.791 OSD: Scaling factors: 1x0.755556
2011-05-02 00:21:26.813 OSD: Base theme size: 1280x720
2011-05-02 00:21:26.813 OSD: Scaling factors: 1x0.755556
2011-05-02 00:21:26.837 Player(1): Video timing method: DRM
2011-05-02 00:21:26.852 TV: Changing from None to WatchingVideo
2011-05-02 00:21:26.862 ScreenSaverX11Private: DPMS Deactivated 1
2011-05-02 00:21:26.896 VideoOutput: Created YV12 OSD.
2011-05-02 00:21:27.535 AFD: No DTS Seeking Hack!
2011-05-02 00:21:27.774 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-05-02 00:21:27.790 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-05-02 00:21:28.527 AFD: No DTS Seeking Hack!
2011-05-02 00:21:29.260 AFD: No DTS Seeking Hack!
2011-05-02 00:21:35.363 AFD: No DTS Seeking Hack!
2011-05-02 00:21:36.458 AFD: No DTS Seeking Hack!
2011-05-02 00:21:37.597 AFD: No DTS Seeking Hack!
2011-05-02 00:21:43.767 TV: Attempting to change from WatchingVideo to None
2011-05-02 00:21:43.896 Pulse: PulseAudio resume OK
2011-05-02 00:21:43.897 TV: Changing from WatchingVideo to None
2011-05-02 00:21:43.897 ScreenSaverX11Private: DPMS Reactivated 1
2011-05-02 00:22:08.842 Parent is NULL
2011-05-02 00:22:20.890 Parent is NULL
2011-05-02 00:22:26.345 Parent is NULL
2011-05-02 00:22:31.030 MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2011-05-02 00:22:31.055 MythUIWebBrowser: enabling plugins
/build/buildd/icedtea-web-1.1~20110420/build/../plugin/icedteanp/IcedTeaNPPlugin.cc:2033: thread 0x2187400: Error: Invalid plugin function table.
** (<unknown>:10077): DEBUG: NP_Initialize
** (<unknown>:10077): DEBUG: NP_Initialize succeeded
** (<unknown>:10077): DEBUG: NP_Initialize
** (<unknown>:10077): DEBUG: NP_Initialize succeeded
** (<unknown>:10077): DEBUG: NP_Initialize
** (<unknown>:10077): DEBUG: NP_Initialize succeeded
** (<unknown>:10077): DEBUG: NP_Initialize
** (<unknown>:10077): DEBUG: NP_Initialize succeeded
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
2011-05-02 00:22:52.779 Parent is NULL
2011-05-02 00:22:53.845 MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2011-05-02 00:22:53.846 MythUIWebBrowser: enabling plugins
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
2011-05-02 00:23:55.176 OpenGL: Deleting OpenGL Resources
2011-05-02 00:23:55.185 Pulse: Cleaning up PulseHandler
2011-05-02 00:23:55.185 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
[/PHP]"mythfrontend -v playback,audio" output:
[PHP]2011-05-03 00:31:17.822 mythfrontend version: fixes/0.24 [v0.24-250-g56c54fa] www.mythtv.org
2011-05-03 00:31:17.823 Using runtime prefix = /usr
2011-05-03 00:31:17.823 Using configuration directory = /home/henk/.mythtv
2011-05-03 00:31:17.823 Configuration::Load - Error parsing: /home/henk/.mythtv/config.xml at line: 1  column: 1
2011-05-03 00:31:17.823 Configuration::Load - Error Msg: unexpected end of file
2011-05-03 00:31:17.823 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-05-03 00:31:18.415 Empty LocalHostName.
2011-05-03 00:31:18.415 Using localhost value of tvserver
2011-05-03 00:31:18.416 Configuration::Load - Error parsing: /home/henk/.mythtv/config.xml at line: 1  column: 1
2011-05-03 00:31:18.416 Configuration::Load - Error Msg: unexpected end of file
2011-05-03 00:31:18.422 New DB connection, total: 1
2011-05-03 00:31:18.425 Connected to database 'mythconverg' at host: localhost
2011-05-03 00:31:18.428 Closing DB connection named 'DBManager0'
2011-05-03 00:31:18.429 Connected to database 'mythconverg' at host: localhost
2011-05-03 00:31:18.431 Current locale EN_US
2011-05-03 00:31:18.431 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-05-03 00:31:18.646 ScreenSaverX11Private: Gnome screen saver support enabled
2011-05-03 00:31:18.647 DPMS is active.
2011-05-03 00:31:18.669 Desktop video mode: 2000x768 60.015 Hz
2011-05-03 00:31:19.248 The NV-CONTROL X extension is not available on screen 0 of ':0'.
2011-05-03 00:31:19.249 max_width: 1360 max_height: 768
2011-05-03 00:31:19.249 user: 1000 effective user: 1000 before privileged thread
2011-05-03 00:31:19.249 user: 1000 effective user: 1000 after privileged thread
2011-05-03 00:31:19.249 user: 1000 effective user: 1000 run_priv_thread
2011-05-03 00:31:19.250 Enabled verbose msgs:  important general playback audio
2011-05-03 00:31:19.252 Loading en_us translation for module mythfrontend
2011-05-03 00:31:19.257 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)
2011-05-03 00:31:19.257 JoystickMenuThread: Joystick disabled - Failed to read /home/henk/.mythtv/joystickmenurc
2011-05-03 00:31:19.279 Using Frameless Window
2011-05-03 00:31:19.279 Using Full Screen Window
2011-05-03 00:31:19.372 Using the OpenGL painter
2011-05-03 00:31:19.418 OpenGL: OpenGL vendor  : Tungsten Graphics, Inc
2011-05-03 00:31:19.418 OpenGL: OpenGL renderer: Mesa DRI Intel(R) Ironlake Desktop GEM 20100330 DEVELOPMENT 
2011-05-03 00:31:19.418 OpenGL: OpenGL version : 2.1 Mesa 7.10.2
2011-05-03 00:31:19.418 OpenGL: Max texture size: 4096 x 4096
2011-05-03 00:31:19.418 OpenGL: Max texture units: 8
2011-05-03 00:31:19.418 OpenGL: Direct rendering: Yes
2011-05-03 00:31:19.418 OpenGL: Initialised MythRenderOpenGL
2011-05-03 00:31:19.499 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-03 00:31:19.499 VDP: decoder<->render support: ffmpeg      null xlib xshm xv-blit opengl vdpau
2011-05-03 00:31:19.500 VDP: decoder<->render support: vdpau       vdpau
2011-05-03 00:31:19.500 VDP: decoder<->render support: libmpeg2    null xlib xshm xv-blit opengl vdpau
2011-05-03 00:31:19.502 VDP: Ignoring profile item 4 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2011-05-03 00:31:19.502 VDP: Ignoring profile item 6 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2011-05-03 00:31:19.503 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.504 VDP: Ignoring profile item 8 (decoder ivtv is not supported (supported: ffmpeg,vdpau,libmpeg2))
2011-05-03 00:31:19.504 VDP: Ignoring profile item 9 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2011-05-03 00:31:19.504 VDP: Ignoring profile item 10 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2011-05-03 00:31:19.504 VDP: Ignoring profile item 11 (decoder xvmc is not supported (supported: ffmpeg,vdpau,libmpeg2))
2011-05-03 00:31:19.505 VDP: Ignoring profile item 15 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.505 VDP: Ignoring profile item 16 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.505 VDP: Ignoring profile item 19 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.505 VDP: Ignoring profile item 20 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.506 VDP: Ignoring profile item 23 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.506 VDP: Ignoring profile item 24 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:19.563 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2011-05-03 00:31:19.564 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2011-05-03 00:31:19.564 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2011-05-03 00:31:19.564 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2011-05-03 00:31:19.647 Pulse: Created PulseHandler object
2011-05-03 00:31:19.647 Pulse: Callback: State changed Unconnected->Connecting
2011-05-03 00:31:19.648 Pulse: Callback: State changed Connecting->Authorizing
2011-05-03 00:31:19.699 Pulse: Callback: State changed Authorizing->Setting Name
2011-05-03 00:31:19.739 Pulse: Callback: State changed Setting Name->Ready!
2011-05-03 00:31:19.750 Pulse: Initialised handler
2011-05-03 00:31:19.780 Pulse: Operation: success 1 remaining 1
2011-05-03 00:31:19.801 Pulse: Operation: success 1 remaining 0
2011-05-03 00:31:19.811 Pulse: PulseAudio suspend OK
2011-05-03 00:31:19.817 AO: Sample rate 32000 is supported
2011-05-03 00:31:19.817 AO: Sample rate 44100 is supported
2011-05-03 00:31:19.817 AO: Sample rate 48000 is supported
2011-05-03 00:31:19.817 AO: Sample rate 88200 is supported
2011-05-03 00:31:19.817 AO: Sample rate 96000 is supported
2011-05-03 00:31:19.817 AO: Sample rate 176400 is supported
2011-05-03 00:31:19.818 AO: Sample rate 192000 is supported
2011-05-03 00:31:19.818 AO: 2 channel(s) are supported
2011-05-03 00:31:19.818 AO: 4 channel(s) are supported
2011-05-03 00:31:19.818 AO: 6 channel(s) are supported
2011-05-03 00:31:19.818 AO: 8 channel(s) are supported
2011-05-03 00:31:19.836 AO: Killing AudioOutputDSP
2011-05-03 00:31:19.977 Pulse: Operation: success 1 remaining 1
2011-05-03 00:31:19.998 Pulse: Operation: success 1 remaining 0
2011-05-03 00:31:20.008 Pulse: PulseAudio resume OK
2011-05-03 00:31:20.008 Found ALSA:hdmi:CARD=Intel,DEV=0 (ALSA:hdmi:CARD=Intel,DEV=0
Device supports up to 7.1 (digital output, AC3,DTS,multi-channels LPCM))
2011-05-03 00:31:20.133 Registering Internal as a media playback plugin.
2011-05-03 00:31:20.161 Loading en_us translation for module mytharchive
2011-05-03 00:31:20.166 Registering WebBrowser as a media playback plugin.
2011-05-03 00:31:20.167 Loading en_us translation for module mythbrowser
2011-05-03 00:31:20.195 MonitorRegisterExtensions(0x100, gif,jpg,png)
2011-05-03 00:31:20.195 Loading en_us translation for module mythgallery
2011-05-03 00:31:20.207 Loading en_us translation for module mythgame
2011-05-03 00:31:20.223 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2011-05-03 00:31:20.243 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2011-05-03 00:31:20.247 Loading en_us translation for module mythmusic
2011-05-03 00:31:20.249 Loading en_us translation for module mythnetvision
2011-05-03 00:31:20.252 Loading en_us translation for module mythnews
2011-05-03 00:31:20.257 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2011-05-03 00:31:20.274 Loading en_us translation for module mythvideo
2011-05-03 00:31:20.281 Loading en_us translation for module mythweather
2011-05-03 00:31:20.371 Found mainmenu.xml for theme 'Mythbuntu'
2011-05-03 00:31:20.501 MythCoreContext: Connecting to backend server: 192.168.2.200:6543 (try 1 of 1)
2011-05-03 00:31:20.501 Using protocol version 63
2011-05-03 00:31:21.835 TV: StartTV() -- begin
2011-05-03 00:31:21.835 TV: ctor -- begin
2011-05-03 00:31:21.846 TV: ctor -- end
2011-05-03 00:31:21.846 TV: Init -- begin
2011-05-03 00:31:21.849 TV: DrawUnusedRects() -- begin
2011-05-03 00:31:21.849 TV: DrawUnusedRects() -- end
2011-05-03 00:31:21.886 TV: Init -- end
2011-05-03 00:31:21.888 TV: tv->LiveTV() -- begin
2011-05-03 00:31:21.890 TV: HandleStateChange(0) -- begin
2011-05-03 00:31:21.890 TV: Attempting to change from None to WatchingLiveTV
2011-05-03 00:31:21.890 MythCoreContext: Connecting to backend server: 192.168.2.200:6543 (try 1 of 1)
2011-05-03 00:31:21.890 Using protocol version 63
2011-05-03 00:31:21.961 IsTunable(8319)
2011-05-03 00:31:21.964 IsTunable(8319) -> true

2011-05-03 00:31:21.965 Spawning LiveTV Recorder -- begin
2011-05-03 00:31:22.432 Spawning LiveTV Recorder -- end
2011-05-03 00:31:22.433 LiveTVChain(live-tvserver-2011-05-03T00:31:21): ReloadAll(): Added new recording
2011-05-03 00:31:22.438 We have a playbackURL(/var/lib/mythtv/livetv/8319_20110503003122.mpg) & cardtype(DUMMY)
2011-05-03 00:31:22.438 We have a RingBuffer
2011-05-03 00:31:22.438 TV: StartRecorder(): took 0 ms to start recorder.
2011-05-03 00:31:22.438 TV: StartPlayer(0, WatchingLiveTV, main) -- begin
2011-05-03 00:31:22.438 TV: Elapsed time since TV constructor was called: 603 ms
2011-05-03 00:31:22.580 Pulse: Operation: success 1 remaining 1
2011-05-03 00:31:22.601 Pulse: Operation: success 1 remaining 0
2011-05-03 00:31:22.611 Pulse: PulseAudio suspend OK
2011-05-03 00:31:22.616 AO: Sample rate 32000 is supported
2011-05-03 00:31:22.616 AO: Sample rate 44100 is supported
2011-05-03 00:31:22.616 AO: Sample rate 48000 is supported
2011-05-03 00:31:22.616 AO: Sample rate 88200 is supported
2011-05-03 00:31:22.616 AO: Sample rate 96000 is supported
2011-05-03 00:31:22.616 AO: Sample rate 176400 is supported
2011-05-03 00:31:22.616 AO: Sample rate 192000 is supported
2011-05-03 00:31:22.616 AO: 2 channel(s) are supported
2011-05-03 00:31:22.616 AO: 4 channel(s) are supported
2011-05-03 00:31:22.616 AO: 6 channel(s) are supported
2011-05-03 00:31:22.616 AO: 8 channel(s) are supported
2011-05-03 00:31:22.633 AO: Killing AudioOutputDSP
2011-05-03 00:31:22.633 Player(0): detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2011-05-03 00:31:22.635 VideoOutput: Allowed renderers: xv-blit,xshm,xlib,opengl,vdpau
2011-05-03 00:31:22.635 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,xv-blit,opengl,vdpau
2011-05-03 00:31:22.636 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:22.636 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2011-05-03 00:31:22.636 VDP: LoadBestPreferences(2048x2048, 0)
2011-05-03 00:31:22.636 VDP: LoadBestPreferences(2048x2048, 60)
2011-05-03 00:31:22.636 VDP: LoadBestPreferences(720x576, 60)
2011-05-03 00:31:22.636 VideoOutput: Preferred renderer: xv-blit
2011-05-03 00:31:22.636 VideoOutput: Trying video renderer: 'xv-blit'
2011-05-03 00:31:22.642 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:22.642 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2011-05-03 00:31:22.642 VDP: LoadBestPreferences(2048x2048, 0)
2011-05-03 00:31:22.642 VDP: LoadBestPreferences(2048x2048, 60)
2011-05-03 00:31:22.642 VideoOutputXv: ctor
2011-05-03 00:31:22.642 VideoOutWindow::SetPIPState. pip_state: 0]
2011-05-03 00:31:22.642 VDP: LoadBestPreferences(2048x2048, 25)
2011-05-03 00:31:22.643 VideoOutputXv: Creating gc
2011-05-03 00:31:22.643 VideoOutputXv: XJ_screen_num: '0'
2011-05-03 00:31:22.643 VideoOutputXv: XJ_curwin:     '69206019'
2011-05-03 00:31:22.643 VideoOutputXv: XJ_win:        '69206019'
2011-05-03 00:31:22.643 VideoOutputXv: XJ_root:       '183'
2011-05-03 00:31:22.643 VideoOutputXv: XJ_gc:         '0x19663b0'
2011-05-03 00:31:22.643 Snapping height to avoid scaling: height: 576, top: 96
2011-05-03 00:31:22.643 Display Rect  left: 0, top: 96, width: 1360, height: 576, aspect: 1.33333
2011-05-03 00:31:22.643 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.7777
2011-05-03 00:31:22.643 VDP: LoadBestPreferences(720x576, 25)
2011-05-03 00:31:22.643 Snapping height to avoid scaling: height: 576, top: 96
2011-05-03 00:31:22.643 Display Rect  left: 0, top: 96, width: 1360, height: 576, aspect: 1.33333
2011-05-03 00:31:22.643 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.7777
2011-05-03 00:31:22.644 VideoOutput: Pixel dimensions: Screen 1360x768, window 1360x768
2011-05-03 00:31:22.644 VideoOutput: Xinerama display dimensions: 361x203 mm  Aspect: 1.77833
2011-05-03 00:31:22.644 VideoOutput: Estimated window dimensions: 361x203 mm  Aspect: 1.77833
2011-05-03 00:31:22.644 VideoOutputXv: InitSetupBuffers() render: xv-blit, allowed: xv-blit,xshm,xlib
2011-05-03 00:31:22.645 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:22.645 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2011-05-03 00:31:22.645 VDP: LoadBestPreferences(2048x2048, 0)
2011-05-03 00:31:22.645 VDP: LoadBestPreferences(2048x2048, 60)
2011-05-03 00:31:22.645 VDP: LoadBestPreferences(720x576, 60)
2011-05-03 00:31:22.645 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2011-05-03 00:31:22.645 VideoOutputXv: Adaptor#0: Intel(R) Textured Video has flag[s]: XvInputMask XvImageMask 
2011-05-03 00:31:22.645 VideoOutputXv: Has XVideo flags...
2011-05-03 00:31:22.646 VideoOutputXv: Has XV_BRIGHTNESS...
2011-05-03 00:31:22.646 VideoOutputXv: Here...
2011-05-03 00:31:22.646 VideoOutputXv: Grabbed xv port 85
2011-05-03 00:31:22.646 VideoOutputXv: XVideo surface found on port 85
2011-05-03 00:31:22.646 VideoOutputXv: XV_SET_DEFAULTS is not supported on this port
2011-05-03 00:31:22.646 VideoOutputXv: XV_SYNC_TO_VBLANK supported
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Sync to VBlank set
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Format #0 is 'YUY2'
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Format #1 is 'YV12'
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Format #2 is 'I420'
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Format #3 is 'UYVY'
2011-05-03 00:31:22.646 VideoOutputXv: XVideo Format #4 is 'XVMC'
2011-05-03 00:31:22.646 VideoOutputXv: Using XVideo Format 'YV12'
2011-05-03 00:31:22.646 VideoOutputXv: CreateShmImages(32): video_dim: 720x576
2011-05-03 00:31:22.663 VDP: SetVideoRenderer(xv-blit)
2011-05-03 00:31:22.664 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2011-05-03 00:31:22.664 VideoOutputXv: Chromakeying not possible with this XVideo port.
2011-05-03 00:31:22.664 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2011-05-03 00:31:22.664 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.7777
2011-05-03 00:31:22.665 Over/underscan. V: 0, H: 0
2011-05-03 00:31:22.665 Display Rect  left: 0, top: 0, width: 1360, height: 768, aspect: 1.77778
2011-05-03 00:31:22.665 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.7777
2011-05-03 00:31:22.665 Player(0): LoadFilters(''..) -> 0x0
2011-05-03 00:31:22.665 OSD: Base theme size: 1280x720
2011-05-03 00:31:22.666 OSD: Scaling factors: 0.5625x0.8
2011-05-03 00:31:22.666 Player(0): Decoder thread starting.
2011-05-03 00:31:22.669 OSD: Loaded window osd_message
2011-05-03 00:31:22.671 OSD: Loaded window osd_input
2011-05-03 00:31:22.678 OSD: Loaded window program_info
2011-05-03 00:31:22.679 OSD: Loaded window browse_info
2011-05-03 00:31:22.681 OSD: Loaded window osd_status
2011-05-03 00:31:22.683 OSD: Loaded window osd_program_editor
2011-05-03 00:31:22.683 OSD: Loaded OSD: size 720x576 offset 0+0
2011-05-03 00:31:22.683 OSD: Base theme size: 1280x720
2011-05-03 00:31:22.683 OSD: Scaling factors: 0.5625x0.8
2011-05-03 00:31:22.684 Player(0): ClearAfterSeek(0)
2011-05-03 00:31:22.685 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2011-05-03 00:31:22.686 FilterManager: GetFilterInfo(convert) returning: 0x0
2011-05-03 00:31:22.686 FilterManager: GetFilterInfo(bobdeint) returning: 0x19487d0
2011-05-03 00:31:22.686 VideoOutput: Using deinterlace method bobdeint
2011-05-03 00:31:22.694 Player(0): Play speed: rate: 25 speed: 1 skip: 1 => new interval 40000
2011-05-03 00:31:22.713 Player(0): Video timing method: DRM
2011-05-03 00:31:22.713 Player(0): Display Refresh Rate: 60.002 Video Frame Rate: 25.000
2011-05-03 00:31:22.728 playCtx: StartPlaying(): took 0 ms to start player.
2011-05-03 00:31:22.728 TV: StartPlayer(0, WatchingLiveTV, main) -- end ok
2011-05-03 00:31:22.728 TV: Changing from None to WatchingLiveTV
2011-05-03 00:31:22.728 TV: State is LiveTV & mctx == ctx
2011-05-03 00:31:22.735 TV: UpdateOSDInput done
2011-05-03 00:31:22.735 TV: UpdateLCD done
2011-05-03 00:31:22.735 TV: ITVRestart done
2011-05-03 00:31:22.743 TV: DrawUnusedRects() -- begin
2011-05-03 00:31:22.744 TV: DrawUnusedRects() -- end
2011-05-03 00:31:22.744 TV: HandleStateChange(0) -- end
2011-05-03 00:31:22.745 TV: tv->LiveTV() -- end
2011-05-03 00:31:22.745 TV: StartTV -- process events begin
2011-05-03 00:31:22.771 ScreenSaverX11Private: DPMS Deactivated 1
2011-05-03 00:31:22.771 ScreenSaverX11Private: ResetTimer -- begin
2011-05-03 00:31:22.771 ScreenSaverX11Private: StopTimer
2011-05-03 00:31:22.772 ScreenSaverX11Private: StartTimer
2011-05-03 00:31:22.772 ScreenSaverX11Private: ResetTimer -- end
2011-05-03 00:31:22.836 VideoOutput: Created YV12 OSD.
2011-05-03 00:31:22.837 Subtitles: Loaded main subtitle font 'FreeSans'
2011-05-03 00:31:23.562 LiveTVChain(live-tvserver-2011-05-03T00:31:21): ReloadAll(): Added new recording
2011-05-03 00:31:23.562 LiveTVChain(live-tvserver-2011-05-03T00:31:21): SwitchTo(1)
2011-05-03 00:31:23.562 LiveTVChain(live-tvserver-2011-05-03T00:31:21): Entry@1: '8319_20110503003123'
2011-05-03 00:31:23.562 Player(0): JumpToProgram - start
2011-05-03 00:31:23.564 Player(0): LoadFilters(''..) -> 0x0
2011-05-03 00:31:23.564 Player(0): Play speed: rate: 25 speed: 0 skip: 0 => new interval 40000
2011-05-03 00:31:23.564 VDP: GetFilteredDeint(linearblend) : xv-blit -> 'linearblend'
2011-05-03 00:31:23.565 FilterManager: GetFilterInfo(convert) returning: 0x0
2011-05-03 00:31:23.565 FilterManager: GetFilterInfo(linearblend) returning: 0x1739730
2011-05-03 00:31:23.565 VideoOutput: Using deinterlace method linearblend
2011-05-03 00:31:23.566 RingBuf(/var/lib/mythtv/livetv/8319_20110503003122.mpg): OpenFile(/var/lib/mythtv/livetv/8319_20110503003123.mpg, 10000 ms)
2011-05-03 00:31:23.733 [mpeg2video @ 0x7f5ab4074600]ac-tex damaged at 24 13
2011-05-03 00:31:23.734 [mpeg2video @ 0x7f5ab4074600]Warning MVs not available
2011-05-03 00:31:25.221 AFD: Stream #0, has id 0x1450 codec id MPEG2VIDEO, type Video, bitrate 15000000 at 0x2b07360
2011-05-03 00:31:25.223 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:25.223 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2011-05-03 00:31:25.223 VDP: LoadBestPreferences(2048x2048, 0)
2011-05-03 00:31:25.223 VDP: LoadBestPreferences(2048x2048, 60)
2011-05-03 00:31:25.223 VDP: LoadBestPreferences(720x576, 60)
2011-05-03 00:31:25.224 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:25.224 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2011-05-03 00:31:25.224 VDP: LoadBestPreferences(2048x2048, 0)
2011-05-03 00:31:25.225 VDP: LoadBestPreferences(2048x2048, 60)
2011-05-03 00:31:25.225 VDP: LoadBestPreferences(720x576, 60)
2011-05-03 00:31:25.225 AFD: Using 1 CPUs for decoding
2011-05-03 00:31:25.225 AFD: InitVideoCodec() 0x21fa860 id(MPEG2VIDEO) type (Video).
2011-05-03 00:31:25.225 AFD: Selected FPS is 25 (avg 25 stream 25 container 90000 estimated 25)
2011-05-03 00:31:25.225 VideoOutputXv: InputChanged(720,576,1.33333) 'None'->'MPEG2'
2011-05-03 00:31:25.225 VDP: GetFilteredDeint() : xv-blit -> 'bobdeint'
2011-05-03 00:31:25.226 FilterManager: GetFilterInfo(convert) returning: 0x0
2011-05-03 00:31:25.227 FilterManager: GetFilterInfo(bobdeint) returning: 0x181ad50
2011-05-03 00:31:25.227 VideoOutput: Using deinterlace method bobdeint
2011-05-03 00:31:25.227 VideoOutputXv: DiscardFrames(1)
2011-05-03 00:31:25.227 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-05-03 00:31:25.227 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:31:25.227 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2011-05-03 00:31:25.227 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:31:25.227 VideoOutputXv: DiscardFrames(1)
2011-05-03 00:31:25.227 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-05-03 00:31:25.227 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:31:25.228 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2011-05-03 00:31:25.228 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:31:25.229 VideoOutputXv: Closing XVideo port 85
2011-05-03 00:31:25.234 VideoOutputXv: InitSetupBuffers() render: xv-blit, allowed: xv-blit,xshm,xlib
2011-05-03 00:31:25.235 VDP: Ignoring profile item 2 (renderer quartz-blit is not supported w/decoder ffmpeg (supported: null,xlib,xshm,xv-blit,opengl,vdpau))
2011-05-03 00:31:25.235 VDP: Accepting: cmp(> 0 0) dec(ffmpeg) cpus(1) skiploop(disabled) rend(xv-blit) osd(softblend) osdfade(enabled) deint(bobdeint,linearblend) filt()
2011-05-03 00:31:25.236 VDP: LoadBestPreferences(2048x2048, 0)
2011-05-03 00:31:25.236 VDP: LoadBestPreferences(2048x2048, 60)
2011-05-03 00:31:25.236 VDP: LoadBestPreferences(720x576, 60)
2011-05-03 00:31:25.236 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2011-05-03 00:31:25.236 VideoOutputXv: Adaptor#0: Intel(R) Textured Video has flag[s]: XvInputMask XvImageMask 
2011-05-03 00:31:25.236 VideoOutputXv: Has XVideo flags...
2011-05-03 00:31:25.236 VideoOutputXv: Has XV_BRIGHTNESS...
2011-05-03 00:31:25.236 VideoOutputXv: Here...
2011-05-03 00:31:25.236 VideoOutputXv: Grabbed xv port 85
2011-05-03 00:31:25.236 VideoOutputXv: XVideo surface found on port 85
2011-05-03 00:31:25.237 VideoOutputXv: XV_SET_DEFAULTS is not supported on this port
2011-05-03 00:31:25.237 VideoOutputXv: XV_SYNC_TO_VBLANK supported
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Sync to VBlank set
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Format #0 is 'YUY2'
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Format #1 is 'YV12'
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Format #2 is 'I420'
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Format #3 is 'UYVY'
2011-05-03 00:31:25.237 VideoOutputXv: XVideo Format #4 is 'XVMC'
2011-05-03 00:31:25.237 VideoOutputXv: Using XVideo Format 'YV12'
2011-05-03 00:31:25.237 VideoOutputXv: CreateShmImages(32): video_dim: 720x576
2011-05-03 00:31:25.263 VDP: SetVideoRenderer(xv-blit)
2011-05-03 00:31:25.263 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2011-05-03 00:31:25.263 VideoOutputXv: Chromakeying not possible with this XVideo port.
2011-05-03 00:31:25.263 Display Rect  left: 170, top: 0, width: 1020, height: 768, aspect: 1.77778
2011-05-03 00:31:25.263 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2011-05-03 00:31:25.263 Player(0): ClearAfterSeek(1)
2011-05-03 00:31:25.263 VideoOutputXv: ClearAfterSeek()
2011-05-03 00:31:25.263 VideoOutputXv: DiscardFrames(0)
2011-05-03 00:31:25.263 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2011-05-03 00:31:25.263 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2011-05-03 00:31:25.263 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:31:25.263 Player(0): LoadFilters(''..) -> 0x0
2011-05-03 00:31:25.263 Player(0): detectInterlace(Detect Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2011-05-03 00:31:25.263 Player(0): Enabled deinterlacing
2011-05-03 00:31:25.264 AFD: Using ffmpeg for video decoding
2011-05-03 00:31:25.264 AFD: Looking for decoder for MPEG2VIDEO
2011-05-03 00:31:25.264 AFD: Opened codec 0x21fa860, id(MPEG2VIDEO) type(Video)
2011-05-03 00:31:25.264 AFD: Stream #1, has id 0x1451 codec id MP2, type Audio, bitrate 256000 at 0x21f68f0
2011-05-03 00:31:25.264 AFD: codec MP2 has 2 channels
2011-05-03 00:31:25.264 AFD: Looking for decoder for MP2
2011-05-03 00:31:25.264 AFD: Opened codec 0x21f3de0, id(MP2) type(Audio)
2011-05-03 00:31:25.264 AFD: Audio Track #1 is A/V stream #1 and has 2 channels in the English language(6647399).
2011-05-03 00:31:25.264 AFD: Stream #2, has id 0x1452 codec id MP2, type Audio, bitrate 256000 at 0x2af3ec0
2011-05-03 00:31:25.264 AFD: codec MP2 has 2 channels
2011-05-03 00:31:25.264 AFD: Looking for decoder for MP2
2011-05-03 00:31:25.264 AFD: Opened codec 0x199deb0, id(MP2) type(Audio)
2011-05-03 00:31:25.264 AFD: Audio Track #2 is A/V stream #2 and has 2 channels in the Unknown language(5128530).
2011-05-03 00:31:25.264 AFD: Stream #3, has id 0x1453 codec id DVB_TELETEXT, type Subtitle, bitrate 0 at 0x2af1140
2011-05-03 00:31:25.264 AFD: Teletext stream #0 (Menu) is in the English language on page 8 136.
2011-05-03 00:31:25.264 AFD: Teletext stream #1 (Caption) is in the English language on page 8 136.
2011-05-03 00:31:25.264 AFD: subtitle codec (Subtitle)
2011-05-03 00:31:25.264 AFD: Stream #4, has id 0xf06 codec id DSMCC_B, type Data, bitrate 0 at 0x2af1360
2011-05-03 00:31:25.264 AFD: data codec (Data)
2011-05-03 00:31:25.264 AFD: Stream #5, has id 0xf07 codec id DSMCC_B, type Data, bitrate 0 at 0x2aedd70
2011-05-03 00:31:25.264 AFD: data codec (Data)
2011-05-03 00:31:25.264 AFD: Stream #6, has id 0xf08 codec id DSMCC_B, type Data, bitrate 0 at 0x173f200
2011-05-03 00:31:25.264 AFD: data codec (Data)
2011-05-03 00:31:25.264 AFD: Stream #7, has id 0xf09 codec id DSMCC_B, type Data, bitrate 0 at 0x2ae9450
2011-05-03 00:31:25.264 AFD: data codec (Data)
2011-05-03 00:31:25.264 AFD: Stream #8, has id 0x1454 codec id DVB_SUBTITLE, type Subtitle, bitrate 0 at 0x2afa2b0
2011-05-03 00:31:25.264 AFD: subtitle codec (Subtitle)
2011-05-03 00:31:25.264 AFD: Looking for decoder for DVB_SUBTITLE
2011-05-03 00:31:25.264 AFD: Opened codec 0x2afa4d0, id(DVB_SUBTITLE) type(Subtitle)
2011-05-03 00:31:25.264 AFD: Subtitle track #1 is A/V stream #8 and is in the English language(6647399).
2011-05-03 00:31:25.406 AFD: Trying to select audio track (w/lang)
2011-05-03 00:31:25.407 AFD: Selected track 1: English MP2 2ch (A/V Stream #1)
2011-05-03 00:31:25.407 AFD: Initializing audio parms from audio track #1
2011-05-03 00:31:25.407 AFD: Audio format changed 
            from id(NONE)     -1Hz -1ch -1bps     to id( MP2)  48000Hz  2ch 16bps    
2011-05-03 00:31:25.407 AO: Killing AudioOutputDSP
2011-05-03 00:31:25.483 Pulse: Operation: success 1 remaining 1
2011-05-03 00:31:25.503 Pulse: Operation: success 1 remaining 0
2011-05-03 00:31:25.514 Pulse: PulseAudio resume OK
2011-05-03 00:31:25.583 Pulse: Operation: success 1 remaining 1
2011-05-03 00:31:25.604 Pulse: Operation: success 1 remaining 0
2011-05-03 00:31:25.614 Pulse: PulseAudio suspend OK
2011-05-03 00:31:25.618 AO: Sample rate 32000 is supported
2011-05-03 00:31:25.618 AO: Sample rate 44100 is supported
2011-05-03 00:31:25.618 AO: Sample rate 48000 is supported
2011-05-03 00:31:25.618 AO: Sample rate 88200 is supported
2011-05-03 00:31:25.618 AO: Sample rate 96000 is supported
2011-05-03 00:31:25.618 AO: Sample rate 176400 is supported
2011-05-03 00:31:25.618 AO: Sample rate 192000 is supported
2011-05-03 00:31:25.618 AO: 2 channel(s) are supported
2011-05-03 00:31:25.618 AO: 4 channel(s) are supported
2011-05-03 00:31:25.618 AO: 6 channel(s) are supported
2011-05-03 00:31:25.618 AO: 8 channel(s) are supported
2011-05-03 00:31:25.633 AO: Killing AudioOutputDSP
2011-05-03 00:31:25.633 AO: Original codec was MP2, signed 16 bit, 48 kHz, 2 channels
2011-05-03 00:31:25.633 AO: enc(0), passthru(0), canAC3(1), canDTS(1), canLPCM(1), configured_channels(2), 2 channels supported(1)
2011-05-03 00:31:25.633 AO: Opening audio device 'hdmi:CARD=Intel,DEV=0' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-05-03 00:31:25.634 ALSA: SetParameters(format=2, channels=2, rate=48000, buffer_time=500000, period_time=16)
2011-05-03 00:31:25.634 ALSA: Buffer size range from 64 to 1048576
2011-05-03 00:31:25.634 ALSA: Period size range from 32 to 524288
2011-05-03 00:31:25.634 ALSA: Buffer time = 500000 us
2011-05-03 00:31:25.634 ALSA: Period time = 15 periods
2011-05-03 00:31:25.635 ALSA: Buffer size = 24000 | Period size = 1600
2011-05-03 00:31:25.645 ALSA, Error: no playback control PCM found on mixer device default
2011-05-03 00:31:25.645 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-03 00:31:25.645 AO: Audio fragment size: 3200
2011-05-03 00:31:25.645 AO: Audio Stretch Factor: 1
2011-05-03 00:31:25.645 AO: Ending Reconfigure()
2011-05-03 00:31:25.645 AudioPlayer: Enabling Audio
2011-05-03 00:31:25.645 AO: Reconfigure(): No change -> exiting
2011-05-03 00:31:25.645 Dec: Selected track #1 in the Unknown language(0)
2011-05-03 00:31:25.645 Dec: Selected track #1 in the English language(6647399)
2011-05-03 00:31:25.645 Dec: Selected track #1 in the English language(6647399)
2011-05-03 00:31:25.645 Dec: Selected track #1 in the English language(6647399)
2011-05-03 00:31:25.645 Dec: Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(0)
2011-05-03 00:31:25.645 AO: kickoffOutputAudioLoop: pid = 3595
2011-05-03 00:31:25.645 AO: OutputAudioLoop: Play Event
2011-05-03 00:31:25.646 Dec: Position map filled from DB to: 24
2011-05-03 00:31:25.646 Dec: SyncPositionMap watchingrecording, from DB: 3 entries
2011-05-03 00:31:25.646 Player(0): Filling position map from 25 to end
2011-05-03 00:31:25.692 Dec: Position map filled from Encoder to: 48
2011-05-03 00:31:25.693 Dec: SyncPositionMap watchingrecording total: 5 entries
2011-05-03 00:31:25.693 Dec: SyncPositionMap, new totframes: 48, new length: 1, posMap size: 5
2011-05-03 00:31:25.693 AFD: Partial position map found
2011-05-03 00:31:25.693 AFD: Successfully opened decoder for file: "/var/lib/mythtv/livetv/8319_20110503003123.mpg". novideo(0)
2011-05-03 00:31:25.697 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-05-03 00:31:25.903 Player(0): Play(  1.0, normal 1, unpause audio 1)
2011-05-03 00:31:25.903 Dec: Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2011-05-03 00:31:25.903 AO: Pause 0
2011-05-03 00:31:25.904 Dec: Position map filled from DB to: 24
2011-05-03 00:31:25.904 Dec: SyncPositionMap watchingrecording, from DB: 3 entries
2011-05-03 00:31:25.904 Player(0): Filling position map from 25 to end
2011-05-03 00:31:25.982 Dec: Position map filled from Encoder to: 48
2011-05-03 00:31:25.982 Dec: SyncPositionMap watchingrecording total: 5 entries
2011-05-03 00:31:25.983 Player(0): Play speed: rate: 25 speed: 1 skip: 1 => new interval 40000
2011-05-03 00:31:25.983 Player(0): Stretch Factor 1, allow passthru 
2011-05-03 00:31:25.983 Player(0): JumpToProgram - end
2011-05-03 00:31:25.983 Player(0): Waiting for video buffers...
2011-05-03 00:31:25.983 AO: Pause 1
2011-05-03 00:31:25.986 [mpeg2video @ 0x7f5ab4074600]ac-tex damaged at 24 13
2011-05-03 00:31:25.988 AO: OutputAudioLoop: audio paused
2011-05-03 00:31:25.990 [mpeg2video @ 0x7f5ab4074600]Warning MVs not available
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]ac-tex damaged at 24 15
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]invalid mb type in P Frame at 3 14
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]00 motion_type at 2 15
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]ac-tex damaged at 23 17
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]00 motion_type at 19 18
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]invalid cbp at 2 19
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]invalid cbp at 10 20
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]00 motion_type at 18 21
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]invalid cbp at 1 24
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]ac-tex damaged at 1 25
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]00 motion_type at 8 26
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]ac-tex damaged at 0 27
2011-05-03 00:31:26.001 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]00 motion_type at 1 29
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]invalid cbp at 0 32
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]slice mismatch
2011-05-03 00:31:26.002 [mpeg2video @ 0x7f5ab4074600]Warning MVs not available
2011-05-03 00:31:26.027 AO: Pause 0
2011-05-03 00:31:26.054 AO: OutputAudioLoop: Play Event
2011-05-03 00:31:26.194 Player(0): Video is 4.08593 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.261 Player(0): Video is 4.94567 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.345 Player(0): Video is 5.42175 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.411 Player(0): Video is 5.51005 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.478 Player(0): Video is 5.30753 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.561 Player(0): Video is 4.98688 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.628 Player(0): Video is 4.57765 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.711 Player(0): Video is 4.10822 frames ahead of audio,
            doubling video frame interval to slow down.
2011-05-03 00:31:26.778 Player(0): Video is 3.48115 frames ahead of audio,
            doubling video frame interval to slow down.
'video_output' mean = '43652.80', std. dev. = '13038.65', fps = '22.91'
'video_output' mean = '40012.58', std. dev. = '8270.29', fps = '24.99'
'video_output' mean = '39965.18', std. dev. = '8190.29', fps = '25.02'
2011-05-03 00:31:42.274 Player(0): 400 interlaced frames seen.
'video_output' mean = '40013.98', std. dev. = '8276.28', fps = '24.99'
'video_output' mean = '39966.86', std. dev. = '8209.71', fps = '25.02'
'video_output' mean = '40012.54', std. dev. = '7980.37', fps = '24.99'
'video_output' mean = '39966.92', std. dev. = '8131.11', fps = '25.02'
2011-05-03 00:31:57.406 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:31:58.270 Player(0): 800 interlaced frames seen.
'video_output' mean = '39989.14', std. dev. = '8114.91', fps = '25.01'
2011-05-03 00:31:59.072 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:00.252 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:00.252 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:01.805 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:01.807 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39989.38', std. dev. = '8228.74', fps = '25.01'
'video_output' mean = '40013.95', std. dev. = '8419.14', fps = '24.99'
2011-05-03 00:32:09.403 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39965.36', std. dev. = '8318.66', fps = '25.02'
2011-05-03 00:32:12.800 ScreenSaverX11Private: Calling gnome-screensaver-command --poke
2011-05-03 00:32:14.267 Player(0): 1200 interlaced frames seen.
'video_output' mean = '39989.59', std. dev. = '8529.43', fps = '25.01'
'video_output' mean = '39989.88', std. dev. = '8214.48', fps = '25.01'
'video_output' mean = '39989.87', std. dev. = '8244.68', fps = '25.01'
'video_output' mean = '39989.59', std. dev. = '8487.88', fps = '25.01'
2011-05-03 00:32:30.263 Player(0): 1600 interlaced frames seen.
'video_output' mean = '39989.03', std. dev. = '8216.75', fps = '25.01'
'video_output' mean = '39990.27', std. dev. = '8138.26', fps = '25.01'
'video_output' mean = '39991.28', std. dev. = '8352.50', fps = '25.01'
'video_output' mean = '39990.16', std. dev. = '7804.83', fps = '25.01'
2011-05-03 00:32:46.276 Player(0): 2000 interlaced frames seen.
'video_output' mean = '39988.00', std. dev. = '7970.70', fps = '25.01'
'video_output' mean = '39989.34', std. dev. = '7998.60', fps = '25.01'
2011-05-03 00:32:52.309 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:52.311 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39989.89', std. dev. = '8146.05', fps = '25.01'
2011-05-03 00:32:54.510 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:54.513 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:56.508 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:56.510 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39992.11', std. dev. = '7872.08', fps = '25.00'
2011-05-03 00:32:59.508 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:32:59.511 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:02.141 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:02.143 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:02.272 Player(0): 2400 interlaced frames seen.
'video_output' mean = '39986.79', std. dev. = '8167.80', fps = '25.01'
2011-05-03 00:33:02.789 ScreenSaverX11Private: Calling gnome-screensaver-command --poke
2011-05-03 00:33:03.740 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:03.742 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:05.108 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:05.110 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:05.111 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39989.26', std. dev. = '8144.81', fps = '25.01'
2011-05-03 00:33:07.023 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:07.026 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:09.072 LiveTVChain(live-tvserver-2011-05-03T00:31:21): ReloadAll(): Added new recording
2011-05-03 00:33:09.106 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:09.108 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39991.87', std. dev. = '8094.09', fps = '25.01'
2011-05-03 00:33:11.021 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:11.022 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:13.338 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39988.15', std. dev. = '8049.74', fps = '25.01'
2011-05-03 00:33:17.020 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:18.268 Player(0): 2800 interlaced frames seen.
'video_output' mean = '39989.98', std. dev. = '8072.82', fps = '25.01'
2011-05-03 00:33:19.270 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:19.272 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:21.219 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:21.221 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39990.72', std. dev. = '8670.32', fps = '25.01'
2011-05-03 00:33:23.269 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:23.271 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:23.272 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:25.819 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:25.821 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39988.70', std. dev. = '8063.83', fps = '25.01'
2011-05-03 00:33:27.784 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:27.786 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:29.418 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:29.419 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39989.92', std. dev. = '8108.06', fps = '25.01'
2011-05-03 00:33:30.868 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:30.870 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:32.503 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:32.504 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:34.265 Player(0): 3200 interlaced frames seen.
2011-05-03 00:33:34.267 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:34.268 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39989.39', std. dev. = '8081.71', fps = '25.01'
2011-05-03 00:33:35.500 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:35.503 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:37.533 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:37.535 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39989.24', std. dev. = '8203.27', fps = '25.01'
2011-05-03 00:33:39.383 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:40.532 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:40.533 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39990.02', std. dev. = '8179.39', fps = '25.01'
2011-05-03 00:33:43.898 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:43.900 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:45.464 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:45.465 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39990.19', std. dev. = '8138.90', fps = '25.01'
2011-05-03 00:33:46.863 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:46.865 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:48.696 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:48.698 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:50.261 Player(0): 3600 interlaced frames seen.
'video_output' mean = '39988.77', std. dev. = '8054.23', fps = '25.01'
2011-05-03 00:33:51.013 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:51.016 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:52.379 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:52.381 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:52.777 ScreenSaverX11Private: Calling gnome-screensaver-command --poke
2011-05-03 00:33:53.896 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:53.899 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39990.33', std. dev. = '8066.13', fps = '25.01'
2011-05-03 00:33:55.095 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:55.097 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:56.378 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:57.380 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39988.85', std. dev. = '7952.05', fps = '25.01'
2011-05-03 00:33:59.745 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:33:59.746 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:34:01.344 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:34:01.346 Subtitles: Display AV sub for 30000 ms
'video_output' mean = '39987.48', std. dev. = '7663.26', fps = '25.01'
2011-05-03 00:34:02.943 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:34:02.945 Subtitles: Display AV sub for 30000 ms
2011-05-03 00:34:06.257 Player(0): 4000 interlaced frames seen.
'video_output' mean = '39992.14', std. dev. = '7791.72', fps = '25.00'
'video_output' mean = '39990.14', std. dev. = '8089.63', fps = '25.01'
'video_output' mean = '39989.79', std. dev. = '7974.45', fps = '25.01'
'video_output' mean = '39989.16', std. dev. = '8185.71', fps = '25.01'
2011-05-03 00:34:22.269 Player(0): 4400 interlaced frames seen.
'video_output' mean = '40156.84', std. dev. = '8443.04', fps = '24.90'
2011-05-03 00:34:24.337 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2011-05-03 00:34:24.337 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2011-05-03 00:34:24.371 TV: HandleStateChange(0) -- begin
2011-05-03 00:34:24.371 TV: Attempting to change from WatchingLiveTV to None
2011-05-03 00:34:24.371 TV: StopStuff() for player ctx 0 -- begin
2011-05-03 00:34:24.371 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2011-05-03 00:34:24.371 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2011-05-03 00:34:24.371 Player(0): StopPlaying - begin
2011-05-03 00:34:24.375 Player(0): Decoder thread exiting.
2011-05-03 00:34:24.375 Player(0): Exited decoder loop.
2011-05-03 00:34:24.376 VideoOutputXv: dtor
2011-05-03 00:34:24.376 VideoOutputXv: DiscardFrames(1)
2011-05-03 00:34:24.376 VideoBuffers::DiscardFrames(1): UUUUUUUUUUUUUUUUUUUUUUuUULUUUUU
2011-05-03 00:34:24.377 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:34:24.377 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2011-05-03 00:34:24.377 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2011-05-03 00:34:24.378 VideoOutputXv: Closing XVideo port 85
2011-05-03 00:34:24.385 AO: Killing AudioOutputDSP
2011-05-03 00:34:24.389 AO: OutputAudioLoop: Stop Event
2011-05-03 00:34:24.389 AO: kickoffOutputAudioLoop exiting
2011-05-03 00:34:24.456 Pulse: Operation: success 1 remaining 1
2011-05-03 00:34:24.476 Pulse: Operation: success 1 remaining 0
2011-05-03 00:34:24.486 Pulse: PulseAudio resume OK
2011-05-03 00:34:24.487 Player(0): StopPlaying - end
2011-05-03 00:34:24.487 TV: StopStuff(): stopping ring buffer
2011-05-03 00:34:24.546 TV: StopStuff(): stopping player
2011-05-03 00:34:24.546 TV: StopStuff(): stopping recorder
2011-05-03 00:34:24.739 TV: StopStuff() -- end
2011-05-03 00:34:24.739 TV: Changing from WatchingLiveTV to None
2011-05-03 00:34:24.740 TV: HandleStateChange(0) -- end
2011-05-03 00:34:24.740 TV: StartTV -- process events end
2011-05-03 00:34:24.740 TV: StartTV -- process events 2 begin
2011-05-03 00:34:24.740 ScreenSaverX11Private: DPMS Reactivated 1
2011-05-03 00:34:24.741 ScreenSaverX11Private: StopTimer
2011-05-03 00:34:24.741 TV: StartTV -- process events 2 end
2011-05-03 00:34:24.741 TV::~TV() -- begin
2011-05-03 00:34:24.742 TV: DrawUnusedRects() -- begin
2011-05-03 00:34:24.742 TV: DrawUnusedRects() -- end
2011-05-03 00:34:24.742 TV: DrawUnusedRects() -- begin
2011-05-03 00:34:24.742 TV: DrawUnusedRects() -- end
2011-05-03 00:34:24.752 TV::~TV() -- lock
2011-05-03 00:34:24.752 Player(0): StopPlaying - begin
2011-05-03 00:34:24.753 Player(0): Exited decoder loop.
2011-05-03 00:34:24.753 Player(0): StopPlaying - end
2011-05-03 00:34:24.758 TV::~TV() -- end
2011-05-03 00:34:24.759 TV: StartTV -- end
2011-05-03 00:34:25.978 OpenGL: Deleting OpenGL Resources
2011-05-03 00:34:25.981 Pulse: Cleaning up PulseHandler
2011-05-03 00:34:25.981 Pulse: Destroying PulseAudio handler
2011-05-03 00:34:25.981 Deleting UPnP client...[/PHP]

---

### Post by chris_gs on 2011-05-03
Hey,

Hmm... i tried the other profiles... they seemed about the same - slim gave me similar results to my CPU -- : jumpy
CPU usage wasn't too bad, seemed to be between 50-70% on both slim and CPU -- profile.

I tried the VDPAU, but it complained about missing the nvidia library.. i though what the hell and installed that -stranger things have worked - but it was "unable to initialise video display"... so i guess the decoder supports it but my video hardware doesn't.... guess that makes sense...

Yeah, i'm also not sure about the unable to set the audio buffer size, but as many channels are still jumpy video while the audio is fine, i'd kinda put it on the back burner as a problem to solve down the line...

I've attached the log files again...
I'm a bit stumped on this one... I don't know if something in natty broke some video playback for my hardware... I might have to downgrade back to maverick, which'd be a pitty, cos I like the remote working...

Cheers,
Chris

---

### Post by nickrout on 2011-05-03
sorry to say it but upgrading is a BAD idea. 

Having said that, what video card do you have?

---

### Post by pat.osullivan on 2011-07-12
I have been having **exactly** this same problem since upgrading from 10.10 to 11.04. I'm so glad I'm not the only one.

For what it's worth, my card is an on-board Intel card (GMA 3000, I believe).

Really hoping we can find some sort of resolution for this problem.

---

### Post by kingmoffa on 2011-08-22
think I have this problem as well. 

Frontend used to be fine - then after upgrade its jumpy. 

Some TV shows are fine , others are not.

---

### Post by Kheops_74 on 2011-09-04
Maybe same problem here. For the " Error opening /proc/asound/card1/pcm0p/sub0/prealloc. Fix reading permissions." message. Are you able to correct it?

Seem the solution is this command "sudo echo 128 > /proc/asound/card1/pcm0p/sub0/prealloc". I receive an error like i can't create this file. Is it the same for you?

---

### Post by kingmoffa on 2011-09-06
thanks for the reply. Will try adding that to some startup scripts.

---

### Post by Kheops_74 on 2011-09-07
Does it work? Are you able to run the command? In my case, i always get an error telling i can't create prealloc.

---

### Post by nickrout on 2011-09-07
How many sound cards do you have? That command refers to card1, which is the second card on the system. The first card (or only card if you have only one) is card0.

---

### Post by Kheops_74 on 2011-09-08
i don't have card0 only card1. The thing i don't understand is how to create prealloc in the sub0 directory. Are you able? Anybody knows?

---

### Post by nickrout on 2011-09-08
I am very surprised at that as they are automatically created starting at card0. 

What is the output of these commands:```
ls -l /proc/asound
ls -l /proc/asound/card0/pcm0c/sub0/
```

---

### Post by Kheops_74 on 2011-09-09
I don't have 0. But the point is : Was you able to create prealloc in the sub0 folder? Does it solve the issue?

> ls -l /proc/asound
total 0
dr-xr-xr-x 5 root root 0 2011-09-09 08:09 card1
-r--r--r-- 1 root root 0 2011-09-09 08:09 cards
-r--r--r-- 1 root root 0 2011-09-09 08:09 devices
-r--r--r-- 1 root root 0 2011-09-09 08:09 hwdep
-r--r--r-- 1 root root 0 2011-09-09 08:09 modules
-r--r--r-- 1 root root 0 2011-09-09 08:09 pcm
lrwxrwxrwx 1 root root 5 2011-09-09 08:09 S51 -> card1
dr-xr-xr-x 2 root root 0 2011-09-09 08:09 seq
-r--r--r-- 1 root root 0 2011-09-09 08:09 timers
-r--r--r-- 1 root root 0 2011-09-09 08:09 version


---

### Post by nickrout on 2011-09-09
all the files in /proc are created by the kernel drivers.  Maybe your card driver doesn't create that file or the underlying functionality?

On my frontend I have 2 sound cards, one has prealloc, the other doesn't.

---

### Post by Kheops_74 on 2011-09-09
Interesting information. My card is an external Sound Blaster X-Fi Sourrund 5.1. I'm sure it don't have enough memory allocated. I got a lot of "ALSA, Error: WriteAudio: buffer underrun". I really don't know where to look to correct this.

BTW sometimes i got this error too : " ALSA, Error: failed to register mixer device /dev/mixer"

Thanks

---

### Post by nickrout on 2011-09-10
I take it thats a USB device, similarly my device without the /proc entry is a USB external. It uses the snd_usb_audio driver - I suspect yours will too. (cat /proc/asound/modules to check)

Of course your problem may be completely unrelated to audio, and you are following a red herring?

---

### Post by Kheops_74 on 2011-09-10
Here the info
>  cat /proc/asound/modules
 1 snd_usb_audio


I found something else. While watching live TV, if i select M on the keyboard to go in the menu and select audio. I can enable/disable conversion there. If i disable conversion i got a lot less buffer underrun and the video is less laggy. If i enable it again, the video get a lot more laggy. I hope to find it and be able to have good video as in the past.

---

### Post by nickrout on 2011-10-23
> **Kheops_74 said:**
> Here the info


I found something else. While watching live TV, if i select M on the keyboard to go in the menu and select audio. I can enable/disable conversion there. If i disable conversion i got a lot less buffer underrun and the video is less laggy. If i enable it again, the video get a lot more laggy. I hope to find it and be able to have good video as in the past.

that driver doesn't appear to create that file in /proc

---

