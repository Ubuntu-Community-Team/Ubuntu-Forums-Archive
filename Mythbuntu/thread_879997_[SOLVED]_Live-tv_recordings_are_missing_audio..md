---
title: "[SOLVED] Live-tv recordings are missing audio."
date: 2008-08-04
forum: Mythbuntu
---

### Post by JugeHuge on 2008-08-04
Hello..

I'm having problems with missing audio on recorded live-tv shows.
Watching live-tv is no problem at all. Audio is heard loud and clear. When i open recordings in vlc or mplayer audio is heard also. 
:confused:
Here is frontend log from start to end watching recording.
```
Starting mythfrontend.real..
2008-08-04 22:14:32.091 New DB connection, total: 2
2008-08-04 22:14:32.092 Connected to database 'mythconverg' at host: localhost
2008-08-04 22:14:32.095 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-08-04 22:14:32.096 Enabled verbose msgs:  important general
2008-08-04 22:14:32.247 Unable to parse themeinfo.xml for glass-wide
2008-08-04 22:14:32.248 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-04 22:14:32.549 Unable to parse themeinfo.xml for glass-wide
2008-08-04 22:14:32.549 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-04 22:14:33.024 No theme dir: /home/juge/.mythtv/themes/blootube-wide
2008-08-04 22:14:33.026 Primary screen 0.
2008-08-04 22:14:33.026 Using screen 0, 1280x720 at 0,0
2008-08-04 22:14:33.028 No theme dir: /home/juge/.mythtv/themes/blootube-wide
2008-08-04 22:14:33.030 Switching to wide mode (blootube-wide)
2008-08-04 22:14:33.348 Using the OpenGL painter
2008-08-04 22:14:33.350 lirc init success using configuration file: /home/juge/.mythtv/lircrc
2008-08-04 22:14:33.351 JoystickMenuClient Error: Joystick disabled - Failed to read /home/juge/.mythtv/joystickmenurc
2008-08-04 22:14:33.993 Specified base font 'medium' does not exist for font clock
2008-08-04 22:14:33.993 Specified base font 'medium' does not exist for font small
2008-08-04 22:14:33.993 Specified base font 'medium' does not exist for font medium
2008-08-04 22:14:33.993 Specified base font 'medium' does not exist for font large
2008-08-04 22:14:33.995 Loading from: /usr/share/mythtv/themes/blootube-wide/base.xml
2008-08-04 22:14:34.048 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-04 22:14:34.130 Registering Internal as a media playback plugin.
2008-08-04 22:14:34.204 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-04 22:14:34.289 Failed to run 'cdrecord --scanbus'
2008-08-04 22:14:34.303 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-04 22:14:34.329 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-04 22:14:34.387 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-08-04 22:14:34.514 Starting update of BBC-Current-XML
2008-08-04 22:14:34.533 Starting update of BBC-3day-XML
2008-08-04 22:14:34.562 No theme dir: /home/juge/.mythtv/themes/blootube-wide
2008-08-04 22:14:37.018 Using ARB NPOT texture extension
2008-08-04 22:14:37.201 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl -u ENG -d /home/juge/.mythtv/MythWeather/BBC-Current-XML W4732 has exited
2008-08-04 22:14:39.120 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-08-04 22:14:39.341 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-04 22:14:39.343 Using protocol version 40
2008-08-04 22:14:41.076 AFD: Opened codec 0x8356d30, id(MPEG2VIDEO) type(Video)
2008-08-04 22:14:41.076 AFD: codec MP3 has 0 channels
2008-08-04 22:14:41.077 AFD: Opened codec 0x83565b0, id(MP3) type(Audio)
2008-08-04 22:14:41.077 AFD: Opened codec 0x8357fe0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:41.292 TV: Attempting to change from None to WatchingPreRecorded
2008-08-04 22:14:41.395 DPMS Deactivated 
2008-08-04 22:14:41.462 AFD: Opened codec 0x8341950, id(MPEG2VIDEO) type(Video)
2008-08-04 22:14:41.462 AFD: codec MP3 has 0 channels
2008-08-04 22:14:41.462 AFD: Opened codec 0x8341cd0, id(MP3) type(Audio)
2008-08-04 22:14:41.462 AFD: Opened codec 0x8342150, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:41.544 AFD: Warning, video codec 0x8356d30 id(MPEG2VIDEO) type (Video) already open.
2008-08-04 22:14:41.544 AFD: Warning, audio codec 0x83565b0 id(MP3) type (Audio) already open, leaving it alone.
2008-08-04 22:14:41.544 AFD: codec MP3 has 0 channels
2008-08-04 22:14:41.545 NVP: Disabling Audio, params(0,0,0)
2008-08-04 22:14:41.581 AFD: Warning, video codec 0x8341950 id(MPEG2VIDEO) type (Video) already open.
2008-08-04 22:14:41.581 AFD: Warning, audio codec 0x8341cd0 id(MP3) type (Audio) already open, leaving it alone.
2008-08-04 22:14:41.581 AFD: codec MP3 has 0 channels
2008-08-04 22:14:41.581 NVP: Disabling Audio, params(0,0,0)
2008-08-04 22:14:41.667 AFD: Opened codec 0x837a3a0, id(MPEG2VIDEO) type(Video)
2008-08-04 22:14:41.668 AFD: codec MP3 has 0 channels
2008-08-04 22:14:41.668 AFD: Opened codec 0x837a710, id(MP3) type(Audio)
2008-08-04 22:14:41.668 AFD: Opened codec 0x837ad50, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:41.668 AFD: Opened codec 0x837b9d0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:41.670 NVP: Disabling Audio, params(16,2,0)
2008-08-04 22:14:41.833 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2008-08-04 22:14:41.964 OSD Theme Dimensions W: 640 H: 480
2008-08-04 22:14:42.612 TV: Changing from None to WatchingPreRecorded
2008-08-04 22:14:42.613 New DB connection, total: 3
2008-08-04 22:14:42.614 Realtime priority would require SUID as root.
2008-08-04 22:14:42.615 Connected to database 'mythconverg' at host: localhost
greedyhdeint: size changed from 0 x 0 -> 640 x 480
2008-08-04 22:14:42.632 AFD: Opened codec 0x94595c40, id(MPEG2VIDEO) type(Video)
2008-08-04 22:14:42.632 AFD: codec MP3 has 0 channels
2008-08-04 22:14:42.632 AFD: Opened codec 0x94597e70, id(MP3) type(Audio)
2008-08-04 22:14:42.632 AFD: Opened codec 0x945981f0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:42.632 AFD: Opened codec 0x945971a0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:42.636 NVP: Disabling Audio, params(16,2,0)
2008-08-04 22:14:42.648 Opening audio device 'hw:0,3'. ch 2(2) sr 48000
2008-08-04 22:14:42.648 Opening ALSA audio device 'hw:0,3'.
2008-08-04 22:14:42.659 OpenGLVideoSync()
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-08-04 22:14:42.736 ~OpenGLVideoSync() -- begin
2008-08-04 22:14:42.736 ~OpenGLVideoSync() -- middle
2008-08-04 22:14:42.736 ~OpenGLVideoSync() -- end
2008-08-04 22:14:42.737 Video timing method: USleep with busy wait
2008-08-04 22:14:42.756 Mixer unable to find control Master
2008-08-04 22:14:42.756 Mixer unable to find control Master
2008-08-04 22:14:42.758 Mixer unable to find control PCM
2008-08-04 22:14:42.758 Mixer unable to find control PCM
2008-08-04 22:14:42.758 Mixer unable to find control Master
2008-08-04 22:14:42.760 NVP: Enabling Audio
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-08-04 22:14:46.714 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbcthreedayxml.pl -u ENG -d /home/juge/.mythtv/MythWeather/BBC-3day-XML W4732 has exited
2008-08-04 22:14:48.730 TV: Attempting to change from WatchingPreRecorded to None
2008-08-04 22:14:48.851 TV: Changing from WatchingPreRecorded to None
2008-08-04 22:14:48.951 DPMS Reactivated.
2008-08-04 22:14:49.052 AFD: Opened codec 0x8336b50, id(MPEG2VIDEO) type(Video)
2008-08-04 22:14:49.052 AFD: codec MP3 has 0 channels
2008-08-04 22:14:49.052 AFD: Opened codec 0x8336ed0, id(MP3) type(Audio)
2008-08-04 22:14:49.053 AFD: Opened codec 0x8337250, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:49.178 AFD: Warning, video codec 0x8336b50 id(MPEG2VIDEO) type (Video) already open.
2008-08-04 22:14:49.178 AFD: Warning, audio codec 0x8336ed0 id(MP3) type (Audio) already open, leaving it alone.
2008-08-04 22:14:49.178 AFD: codec MP3 has 0 channels
2008-08-04 22:14:49.179 NVP: Disabling Audio, params(0,0,0)
2008-08-04 22:14:49.275 AFD: Opened codec 0x832a650, id(MPEG2VIDEO) type(Video)
2008-08-04 22:14:49.275 AFD: codec MP3 has 0 channels
2008-08-04 22:14:49.275 AFD: Opened codec 0x830f840, id(MP3) type(Audio)
2008-08-04 22:14:49.275 AFD: Opened codec 0x830fe70, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:49.276 AFD: Opened codec 0x8310af0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-04 22:14:49.276 NVP: Disabling Audio, params(16,2,0)
2008-08-04 22:14:49.317 [mpeg2video @ 0xb735dc28]ac-tex damaged at 25 12
2008-08-04 22:14:49.318 [mpeg2video @ 0xb735dc28]Warning MVs not available
```

---

### Post by nickrout on 2008-08-04
can you post the output of:

ffmpeg -i FILENAME

where FILENAME is the name of the live recording file?

What sort of sound are you using? Analogue or digital (SPDIF)?

---

### Post by JugeHuge on 2008-08-05
Hello..

Here is ffmpeg output on one of the recordings..

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpegts, from '1001_20080731200000.mpg':
  Duration: 00:35:11.9, start: 16395.673589, bitrate: 3947 kb/s
  Stream #0.0[0x200]: Video: mpeg2video, yuv420p, 720x576, 8400 kb/s, 25.00 fps(r)
  Stream #0.1[0x28a](fin): Audio: mp2, 48000 Hz, stereo, 224 kb/s
  Stream #0.2[0x403](fin): Subtitle: dvbsub
  Stream #0.3[0x404](dut): Subtitle: dvbsub

```

Audio is going through HDMI

---

### Post by nickrout on 2008-08-05
What strikes me as odd is that your logs show:

 ```
codec MP3 has 0 channels
```

What does it show when you successfully play a show with sound?

---

### Post by JugeHuge on 2008-08-05
Here is log from watching live-tv

```

Starting mythfrontend.real..
2008-08-05 12:02:52.698 New DB connection, total: 2
2008-08-05 12:02:52.699 Connected to database 'mythconverg' at host: localhost
2008-08-05 12:02:52.703 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-08-05 12:02:52.703 Enabled verbose msgs:  important general
2008-08-05 12:02:52.883 Unable to parse themeinfo.xml for glass-wide
2008-08-05 12:02:52.883 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-05 12:02:53.054 Unable to parse themeinfo.xml for glass-wide
2008-08-05 12:02:53.054 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-05 12:02:53.335 No theme dir: /home/juge/.mythtv/themes/blootube-wide
2008-08-05 12:02:53.336 Primary screen 0.
2008-08-05 12:02:53.337 Using screen 0, 1280x720 at 0,0
2008-08-05 12:02:53.338 No theme dir: /home/juge/.mythtv/themes/blootube-wide
2008-08-05 12:02:53.338 Switching to wide mode (blootube-wide)
2008-08-05 12:02:53.490 Using the OpenGL painter
2008-08-05 12:02:53.491 lirc init success using configuration file: /home/juge/.mythtv/lircrc
2008-08-05 12:02:53.492 JoystickMenuClient Error: Joystick disabled - Failed to read /home/juge/.mythtv/joystickmenurc
2008-08-05 12:02:53.811 Specified base font 'medium' does not exist for font clock
2008-08-05 12:02:53.812 Specified base font 'medium' does not exist for font small
2008-08-05 12:02:53.812 Specified base font 'medium' does not exist for font medium
2008-08-05 12:02:53.812 Specified base font 'medium' does not exist for font large
2008-08-05 12:02:53.813 Loading from: /usr/share/mythtv/themes/blootube-wide/base.xml
2008-08-05 12:02:53.836 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-05 12:02:53.877 Registering Internal as a media playback plugin.
2008-08-05 12:02:53.910 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-05 12:02:53.958 Failed to run 'cdrecord --scanbus'
2008-08-05 12:02:53.967 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-05 12:02:53.975 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-05 12:02:54.004 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-08-05 12:02:54.063 Starting update of BBC-Current-XML
2008-08-05 12:02:54.070 Starting update of BBC-3day-XML
2008-08-05 12:02:54.086 No theme dir: /home/juge/.mythtv/themes/blootube-wide
2008-08-05 12:02:55.915 Using ARB NPOT texture extension
2008-08-05 12:02:56.594 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-05 12:02:56.594 Using protocol version 40
2008-08-05 12:02:56.611 TV: Attempting to change from None to WatchingLiveTV
2008-08-05 12:02:56.612 Using protocol version 40
2008-08-05 12:02:57.685 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbcthreedayxml.pl -u ENG -d /home/juge/.mythtv/MythWeather/BBC-3day-XML W4732 has exited
2008-08-05 12:02:57.988 DPMS Deactivated 
2008-08-05 12:02:58.047 New DB connection, total: 3
2008-08-05 12:02:58.048 Connected to database 'mythconverg' at host: localhost
2008-08-05 12:02:58.125 NVP: Disabling Audio, params(-1,2,44100)
2008-08-05 12:02:58.415 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2008-08-05 12:02:58.719 OSD Theme Dimensions W: 640 H: 480
2008-08-05 12:02:59.504 TV: Changing from None to WatchingLiveTV
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-08-05 12:02:59.520 Realtime priority would require SUID as root.
2008-08-05 12:02:59.555 OpenGLVideoSync()
2008-08-05 12:02:59.720 ~OpenGLVideoSync() -- begin
2008-08-05 12:02:59.720 ~OpenGLVideoSync() -- middle
2008-08-05 12:02:59.720 ~OpenGLVideoSync() -- end
2008-08-05 12:02:59.720 Video timing method: USleep with busy wait
2008-08-05 12:02:59.793 nice /usr/share/mythtv/mythweather/scripts/uk_bbc/bbccurrentxml.pl -u ENG -d /home/juge/.mythtv/MythWeather/BBC-Current-XML W4732 has exited
2008-08-05 12:03:01.745 NVP: Prebuffer wait timed out 10 times.
2008-08-05 12:03:03.126 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-08-05 12:03:03.548 AFD: Opened codec 0x86d95d0, id(MPEG2VIDEO) type(Video)
2008-08-05 12:03:03.548 AFD: codec MP3 has 2 channels
2008-08-05 12:03:03.549 AFD: Opened codec 0x87ab8d0, id(MP3) type(Audio)
2008-08-05 12:03:03.586 AFD: Opened codec 0x86e0da0, id(DVB_SUBTITLE) type(Subtitle)
2008-08-05 12:03:03.586 AFD: codec MP3 has 2 channels
2008-08-05 12:03:03.586 AFD: Opened codec 0x991d100, id(MP3) type(Audio)
2008-08-05 12:03:03.704 Opening audio device 'hw:0,3'. ch 2(2) sr 48000
2008-08-05 12:03:03.704 Opening ALSA audio device 'hw:0,3'.
2008-08-05 12:03:03.765 Mixer unable to find control Master
2008-08-05 12:03:03.766 Mixer unable to find control Master
2008-08-05 12:03:03.767 Mixer unable to find control PCM
2008-08-05 12:03:03.767 Mixer unable to find control PCM
2008-08-05 12:03:03.768 Mixer unable to find control Master
2008-08-05 12:03:03.769 NVP: Enabling Audio
2008-08-05 12:03:15.360 TV: Attempting to change from WatchingLiveTV to None
2008-08-05 12:03:15.560 TV: Changing from WatchingLiveTV to None
2008-08-05 12:03:15.637 DPMS Reactivated.
```

---

### Post by nickrout on 2008-08-05
I cannot fathom this at all. May I suggest searching the mythtv-user mailing list archives? I think that line ```
codec MP3 has 0 channels
``` may contain the clue, but its not in my realm of knowledge.

---

### Post by JugeHuge on 2008-08-05
Thanks nickrout for trying to solve this. Have to look up those archives if there is similar cases..

---

### Post by JugeHuge on 2008-08-12
Latest mythtv update fixed that "codec MP3 has 0 channels" problem.
Then i had to change audiosettings from ALSA:hw0,3 to ALSA:default to get audio.. I had tried to change this earlier but it always reverted back to that ALSA:hw0,3 setting.. Dunno why.

Funny thought that live-tv worked on that earlier setting but recorded shows didn't.. :) 

Oh well.. Now it works and i'm happy about it.. 

Now only if ATI would get their drives on decent level so it wouldn't crash frontend when exiting live-tv and from watching recorded shows..

---

