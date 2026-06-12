---
title: "[SOLVED] .21 upgrade SPDIF only plays 2ch"
date: 2008-04-12
forum: Mythbuntu
---

### Post by volkswagner on 2008-04-12
After upgrade to Mythtv .21 spdif passthrough is not working correctly.  After the upgrade I had to set max channels to 2, rather than 5.1.  That has gave me sound for, live tv, music, etc.

I have been working on firewire capture.  These streams are 6 channel.  When I try to play them, video freezes and I get errors "WriteAudio: buffer underrun".  If I enable max channels to 5.1, video plays and no buffer errors display.  Unfortunately I do not get sound output either.

I am certain sound worked via firewire capture prior to .21 upgrade.

Here are logs.

Start Firewire recording and audio set to 2channel
```

2008-04-12 15:17:10.033 TV: Attempting to change from None to WatchingPreRecorded
2008-04-12 15:17:10.208 DPMS Deactivated 
2008-04-12 15:17:10.387 AFD: Opened codec 0x4dc95d0, id(MPEG2VIDEO) type(Video)
2008-04-12 15:17:10.387 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 15:17:10.388 AFD: Opened codec 0xfff500, id(AC3) type(Audio)
2008-04-12 15:17:10.388 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-12 15:17:10.388 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-12 15:17:10.408 Mixer unable to find control Master
2008-04-12 15:17:10.408 Mixer unable to find control Master
2008-04-12 15:17:10.424 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-12 15:17:10.424 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-12 15:17:10.440 Mixer unable to find control Master
2008-04-12 15:17:10.440 Mixer unable to find control Master
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-04-12 15:17:10.673 Failed to approve 'opengllinearblend' deinterlacer
2008-04-12 15:17:10.673 Couldn't load deinterlace filter 
2008-04-12 15:17:10.674 OSD Theme Dimensions W: 640 H: 480
2008-04-12 15:17:10.811 Realtime priority would require SUID as root.
2008-04-12 15:17:10.816 TV: Changing from None to WatchingPreRecorded
2008-04-12 15:17:10.993 OpenGLVideoSync()
2008-04-12 15:17:10.993 ~OpenGLVideoSync() -- begin
2008-04-12 15:17:10.993 ~OpenGLVideoSync() -- middle
2008-04-12 15:17:10.993 ~OpenGLVideoSync() -- end
2008-04-12 15:17:10.993 Video timing method: USleep with busy wait
2008-04-12 15:17:11.094 AFD: Opened codec 0x8b90f00, id(MPEG2VIDEO) type(Video)
2008-04-12 15:17:11.094 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 15:17:11.094 AFD: Opened codec 0x4d81ed0, id(AC3) type(Audio)
2008-04-12 15:17:12.376 WriteAudio: buffer underrun
2008-04-12 15:17:13.127 WriteAudio: buffer underrun
2008-04-12 15:17:13.840 WriteAudio: buffer underrun
2008-04-12 15:17:14.510 WriteAudio: buffer underrun
```



Start firewire playback with audio set to 5.1max
```

2008-04-12 17:24:49.810 AFD: Opened codec 0x3fcf130, id(MPEG2VIDEO) type(Video)
2008-04-12 17:24:49.810 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 17:24:49.811 AFD: Opened codec 0x699a360, id(AC3) type(Audio)
2008-04-12 17:24:50.834 AFD: Opened codec 0xaae7b80, id(MPEG2VIDEO) type(Video)
2008-04-12 17:24:50.834 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 17:24:50.834 AFD: Opened codec 0x3fce2f0, id(AC3) type(Audio)
2008-04-12 17:24:59.054 AFD: Opened codec 0xa837480, id(MPEG2VIDEO) type(Video)
2008-04-12 17:24:59.054 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 17:24:59.055 AFD: Opened codec 0xf647c0, id(AC3) type(Audio)
2008-04-12 17:25:00.913 TV: Attempting to change from None to WatchingPreRecorded
2008-04-12 17:25:01.089 DPMS Deactivated 
2008-04-12 17:25:01.240 AFD: Opened codec 0x9baba0, id(MPEG2VIDEO) type(Video)
2008-04-12 17:25:01.240 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 17:25:01.240 AFD: Opened codec 0x3fcf130, id(AC3) type(Audio)
2008-04-12 17:25:01.242 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-12 17:25:01.242 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-12 17:25:01.243 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-12 17:25:01.243 AudioOutput Error: Unable to set ALSA parameters
2008-04-12 17:25:01.249 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-04-12 17:25:01.485 Failed to approve 'opengllinearblend' deinterlacer
2008-04-12 17:25:01.485 Couldn't load deinterlace filter 
2008-04-12 17:25:01.488 OSD Theme Dimensions W: 640 H: 480
2008-04-12 17:25:01.641 TV: Changing from None to WatchingPreRecorded
2008-04-12 17:25:01.642 Realtime priority would require SUID as root.
2008-04-12 17:25:01.766 AFD: Opened codec 0x2aaad83af3e0, id(MPEG2VIDEO) type(Video)
2008-04-12 17:25:01.766 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-12 17:25:01.767 AFD: Opened codec 0x2aaad83ab1e0, id(AC3) type(Audio)
2008-04-12 17:25:01.819 OpenGLVideoSync()
2008-04-12 17:25:01.819 ~OpenGLVideoSync() -- begin
2008-04-12 17:25:01.819 ~OpenGLVideoSync() -- middle
2008-04-12 17:25:01.819 ~OpenGLVideoSync() -- end
2008-04-12 17:25:01.819 Video timing method: USleep with busy wait
```

Do I need additional codecs?
Anyone have spdif working with mythtv .21?

---

### Post by superm1 on 2008-04-12
I have it working via this method:

1) Set all devices to output to ALSA:default.
2) Create this ~/.asoundrc
```

pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
```

---

### Post by volkswagner on 2008-04-12
> **superm1 said:**
> I have it working via this method:

1) Set all devices to output to ALSA:default.
2) Create this ~/.asoundrc
```

pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
```

Thanks, I have completed the above to get it working under myth .20.  When you say set "all devices" to ALSA:default, I have this in general tv playback and music playback.  Am I missing any.

I also noticed this when playing music.
```

2008-04-12 19:19:34.147 DPMS Deactivated 
2008-04-12 19:19:34.180 AFD: Opened codec 0x4f310e0, id(MPEG2VIDEO) type(Video)
2008-04-12 19:19:34.180 AFD: codec MP2 has 2 channels
2008-04-12 19:19:34.180 AFD: Opened codec 0x5330a90, id(MP2) type(Audio)
2008-04-12 19:19:34.181 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-12 19:19:34.181 Opening ALSA audio device 'default'.
2008-04-12 19:19:34.197 Mixer unable to find control Master
2008-04-12 19:19:34.197 Mixer unable to find control Master
```


I have run alsamixer.  IEC958 is not muted.  It is @ [00].  From what I can remember when first setting it up, this was not adjustable, just unmute.

I even added ~.asoundrc to /home/mythtv.  No joy there.

---

### Post by superm1 on 2008-04-12
> **volkswagner said:**
> Thanks, I have completed the above to get it working under myth .20.  When you say set "all devices" to ALSA:default, I have this in general tv playback and music playback.  Am I missing any.

Only if you call external apps anywhere (xine mplayer tetc)

> 

I also noticed this when playing music.
```

2008-04-12 19:19:34.147 DPMS Deactivated 
2008-04-12 19:19:34.180 AFD: Opened codec 0x4f310e0, id(MPEG2VIDEO) type(Video)
2008-04-12 19:19:34.180 AFD: codec MP2 has 2 channels
2008-04-12 19:19:34.180 AFD: Opened codec 0x5330a90, id(MP2) type(Audio)
2008-04-12 19:19:34.181 Opening audio device 'default'. ch 2(2) sr 48000
2008-04-12 19:19:34.181 Opening ALSA audio device 'default'.
2008-04-12 19:19:34.197 Mixer unable to find control Master
2008-04-12 19:19:34.197 Mixer unable to find control Master
```
I have run alsamixer.  IEC958 is not muted.  It is @ [00].  From what I can remember when first setting it up, this was not adjustable, just unmute.

I even added ~.asoundrc to /home/mythtv.  No joy there.
IEC958 is only a switch not a mixer control.  Unmute or mute is all it will do.  Volume is supposed to be adjusted by your home theatre receiver when you do SPDIF.

---

### Post by volkswagner on 2008-04-13
I am at a stand still.  VLC does not output via spdif when enabled.  It will however play the sound in 2ch if passthrough is disabled in VLC.  So I know there is a sound track.  I am not able to get any sound for these files via myth.  Is this a 6 channel problem.  Does the system know what to do with 6ch?  My receiver is only 5.1.

I am not sure if this is related.  What should the file permissions be for the following?  Are these correct?

```
-rw-r--r-- 1 root root 77 2008-03-13 14:53 /etc/mythtv/mysql.txt
lrwxrwxrwx 1 eric eric 21 2008-03-13 14:57 /home/eric/.mythtv/mysql.txt -> /etc/mythtv/mysql.txt
```


I ask because when watching frontend log and making changes to settings I get the following.

```
2008-04-13 09:01:34.262 edit #0 rejected
```

I have also found this in frontend log

```
2008-04-12 14:27:48.070 Could not open settings file /home/eric/.mythtv/mysql.txt for writing
```




Does this mean anything?

```
2008-04-13 08:48:18.564 AFD: Opened codec 0x10adc00, id(AC3) type(Audio)
2008-04-13 08:48:18.565 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-13 08:48:18.565 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-13 08:48:18.566 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-13 08:48:18.566 AudioOutput Error: Unable to set ALSA parameters
2008-04-13 08:48:18.577 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
libGL error: drmGetMagic failed
```

---

### Post by volkswagner on 2008-04-13
Here is what I get when playing a DVD.  The DVD is Dolby Digital 5.1.

```
2008-04-13 09:21:22.809 TV: Attempting to change from None to WatchingPreRecorded
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000142
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000458
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004c8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000004df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002b54
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000628b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003b171
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0009ad10
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x000ae85b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x000b36c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00302cdd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003b0f0e
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: YOURS_MINE_OURS_16X9
libdvdnav: DVD Serial Number: 34384D96
libdvdnav: DVD Title (Alternative): YOURS_MINE_OURS_16X9
libdvdnav: Unable to find map file '/home/eric/.dvdnav/YOURS MINE OURS 16X9.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-04-13 09:21:22.822 Opened DVD device at //dev/dvd
libdvdnav: Suspected RCE Region Protection!!!
2008-04-13 09:21:22.822 There are 18 titles on the disk
2008-04-13 09:21:22.822 Title 0 has 0 parts.
2008-04-13 09:21:22.822 Title 1 has 12 parts.
2008-04-13 09:21:22.822 Title 2 has 2 parts.
2008-04-13 09:21:22.822 Title 3 has 2 parts.
2008-04-13 09:21:22.822 Title 4 has 2 parts.
2008-04-13 09:21:22.822 Title 5 has 2 parts.
2008-04-13 09:21:22.822 Title 6 has 2 parts.
2008-04-13 09:21:22.822 Title 7 has 2 parts.
2008-04-13 09:21:22.822 Title 8 has 2 parts.
2008-04-13 09:21:22.822 Title 9 has 2 parts.
2008-04-13 09:21:22.822 Title 10 has 2 parts.
2008-04-13 09:21:22.822 Title 11 has 3 parts.
2008-04-13 09:21:22.822 Title 12 has 2 parts.
2008-04-13 09:21:22.822 Title 13 has 2 parts.
2008-04-13 09:21:22.822 Title 14 has 3 parts.
2008-04-13 09:21:22.823 Title 15 has 5 parts.
2008-04-13 09:21:22.823 Title 16 has 2 parts.
2008-04-13 09:21:22.823 Title 17 has 5 parts.
2008-04-13 09:21:22.839 AFD: Opened codec 0x45b89a0, id(MPEG2VIDEO) type(Video)
2008-04-13 09:21:22.839 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-13 09:21:22.839 NVP: Disabling Audio, params(0,-1,-1)
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-04-13 09:21:22.972 Failed to approve 'opengllinearblend' deinterlacer
2008-04-13 09:21:22.973 Couldn't load deinterlace filter 
2008-04-13 09:21:22.974 OSD Theme Dimensions W: 640 H: 480
2008-04-13 09:21:23.129 TV: Changing from None to WatchingPreRecorded
2008-04-13 09:21:23.283 OpenGLVideoSync()
2008-04-13 09:21:23.283 ~OpenGLVideoSync() -- begin
2008-04-13 09:21:23.283 ~OpenGLVideoSync() -- middle
2008-04-13 09:21:23.283 ~OpenGLVideoSync() -- end
2008-04-13 09:21:23.283 Video timing method: USleep with busy wait
2008-04-13 09:21:23.288 AFD: Warning, video codec 0x45b89a0 id(MPEG2VIDEO) type (Video) already open.
2008-04-13 09:21:23.389 AFD: codec AC3 has 0 channels
No accelerated IMDCT transform found
2008-04-13 09:21:23.390 AFD: Opened codec 0x1068a50, id(AC3) type(Audio)
2008-04-13 09:21:23.392 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-13 09:21:23.392 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-13 09:21:23.393 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-13 09:21:23.393 AudioOutput Error: Unable to set ALSA parameters
2008-04-13 09:21:23.401 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
2008-04-13 09:21:43.472 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-13 09:21:43.515 NVP: prebuffering pause
2008-04-13 09:21:43.565 NVP: Disabling Audio, params(0,-1,-1)
2008-04-13 09:21:43.577 AFD: Warning, video codec 0x45b89a0 id(MPEG2VIDEO) type (Video) already open.
2008-04-13 09:21:43.598 NVP: prebuffering pause
2008-04-13 09:21:43.659 AFD: codec AC3 has 0 channels
No accelerated IMDCT transform found
2008-04-13 09:21:43.660 AFD: Opened codec 0x2aaad76d39e0, id(AC3) type(Audio)
2008-04-13 09:21:43.661 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-13 09:21:43.661 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-13 09:21:43.662 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-13 09:21:43.662 AudioOutput Error: Unable to set ALSA parameters
2008-04-13 09:21:43.670 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
2008-04-13 09:22:20.754 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-13 09:22:20.801 NVP: prebuffering pause
2008-04-13 09:22:20.847 NVP: Disabling Audio, params(0,-1,-1)
2008-04-13 09:22:20.855 AFD: Warning, video codec 0x45b89a0 id(MPEG2VIDEO) type (Video) already open.
2008-04-13 09:22:20.919 AFD: codec AC3 has 0 channels
No accelerated IMDCT transform found
2008-04-13 09:22:20.920 AFD: Opened codec 0x2aaad75eaec0, id(AC3) type(Audio)
2008-04-13 09:22:20.921 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-13 09:22:20.921 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-13 09:22:20.922 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-13 09:22:20.922 AudioOutput Error: Unable to set ALSA parameters
2008-04-13 09:22:20.929 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
```

---

### Post by superm1 on 2008-04-13
You do have the pass-through dialog checked right in myth?  If you don't, you can expect errors like that...

---

### Post by volkswagner on 2008-04-13
Here are my settings for mythfrontend General Setup.


AUDIO OUTPUT DEVICE = ALSA:default
PASSTHROUGH OUTPUT DEVICE = ALSA:iec958:{ AES0 0x02 }
MAX AUDIO CHANNELS = 5.1
UPMIX = tried passive, active simple, active linear
X=Enable AC3 to SPDIF Passthrough
X=Enable DTS to SPDIF Passthrough
_=Aggressive Sound Card Buffering
X=Use internal Volume Controls
MIXER DEVICE = ALSA:default
MIXER CONTROLS = Tried both PCM and Master


Here is an odd thing.  I unchecked the two passthrough boxes.  I then played a recording and I still Had Sound.  I tried the digital recording and it had choppy sound.  The thing that is odd, my only sound connection is optical out.  I thought I would have no sound when the boxes were unchecked.

---

### Post by volkswagner on 2008-04-13
What is the default player for recorded tv?
I tried to see if problem exists with VLC (yes it does), and now Xine.  Xine had crashed when I first tried to open it.  I tried to reinstall it via synaptic.  Now it opens ok, but when I go to settings it locks up under settings for audio output.  I have now removed it completely.  When I try to play HD recording in mythtv it appears to have a scrammbled screen containing Xine This only happens the first time trying to play).

Do I need Xine?  Shall I try to reinstall it again?  Here is what is left after removal.
```

aptitude search xine
p   amarok-xine                     - xine engine for the Amarok audio player   
p   gxine                           - the xine video player, GTK+/Gnome user int
p   gxineplugin                     - the xine video player, GTK+/Gnome; launche
p   ion3-mod-xinerama               - Xinerama support for the Ion3 window manag
p   kaffeine-xine                   - Xine engine for kaffeine media player     
p   libarts1-xine                   - aRts plugin enabling xine support         
p   libxcb-xinerama0                - X C Binding, xinerama extension           
p   libxcb-xinerama0-dbg            - X C Binding, xinerama extension, debugging
p   libxcb-xinerama0-dev            - X C Binding, xinerama extension, developme
p   libxine-dev                     - the xine video player library, development
v   libxine-doc                     -                                           
p   libxine-xvdr                    - Xine input plugin for vdr-plugin-xinelibou
idA libxine1                        - the xine video/media player library, meta-
p   libxine1-all-plugins            - the xine video/media player library, meta 
idA libxine1-bin                    - the xine video/media player library, binar
idA libxine1-console                - libaa/libcaca/framebuffer/directfb related
p   libxine1-dbg                    - debug symbols for libxine1                
p   libxine1-doc                    - the xine video player library, documentati
idA libxine1-ffmpeg                 - MPEG-related plugins for libxine1         
idA libxine1-gnome                  - GNOME-related plugins for libxine1        
idA libxine1-misc-plugins           - Input, audio output and post plugins for l
idA libxine1-plugins                - the xine video/media player library, meta 
idA libxine1-x                      - X desktop video output plugins for libxine
p   libxineliboutput-fbfe           - Local Frambebuffer frontend for the xineli
p   libxineliboutput-sxfe           - Local X-Server frontend for the xinelibout
p   libxinerama-dev                 - X11 Xinerama extension library (developmen
i A libxinerama1                    - X11 Xinerama extension library            
p   libxinerama1-dbg                - X11 Xinerama extension library (debug pack
p   oxine                           - xine OSD (on screen display) GUI          
p   python-pyxine                   - interface to the xine media player for Pyt
p   totem-xine                      - A simple media player for the Gnome deskto
v   totem-xine-firefox-plugin       -                                           
p   ultrastar-ng-xine               - karaoke game that allows user supplied son
p   vdr-plugin-xineliboutput        - VDR plugin for Xine based sofdevice fronte
p   x11proto-xinerama-dev           - X11 Xinerama extension wire protocol      
p   xine-plugin                     - xine-based media player plugin for Mozilla
p   xine-ui                         - the xine video player, user interface     
p   xineliboutput-fbfe              - Remote Framebuffer frontend for vdr-plugin
p   xineliboutput-sxfe              - Remote X-Server frontend for vdr-plugin-xi
p   xinetd                          - replacement for inetd with many enhancemen
```

How do I search for installed codecs?  Can this be a Codec problem?

---

### Post by superm1 on 2008-04-13
> **volkswagner said:**
> Here are my settings for mythfrontend General Setup.


AUDIO OUTPUT DEVICE = ALSA:default
PASSTHROUGH OUTPUT DEVICE = ALSA:iec958:{ AES0 0x02 }
MAX AUDIO CHANNELS = 5.1
UPMIX = tried passive, active simple, active linear
X=Enable AC3 to SPDIF Passthrough
X=Enable DTS to SPDIF Passthrough
_=Aggressive Sound Card Buffering
X=Use internal Volume Controls
MIXER DEVICE = ALSA:default
MIXER CONTROLS = Tried both PCM and Master


Here is an odd thing.  I unchecked the two passthrough boxes.  I then played a recording and I still Had Sound.  I tried the digital recording and it had choppy sound.  The thing that is odd, my only sound connection is optical out.  I thought I would have no sound when the boxes were unchecked.
This makes me wonder about two things.

1) Do you have COAX & Optical?  Can you try COAX?

2) Do you have some mixer switches in alsamixer that toggle the behavior of your outputs possibly?

---

### Post by volkswagner on 2008-04-14
My spdif only has optical.   I have tried so many things, .rsoundrc variations, various frontend general settings.  I keep getting the same error.
```

2008-04-14 19:36:21.785 Opening audio device 'spdif'. ch 6(2) sr 48000
2008-04-14 19:36:21.785 Opening ALSA audio device 'iec958:{ AES0 0x04 }'.
2008-04-14 19:36:21.786 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-14 19:36:21.786 AudioOutput Error: Unable to set ALSA parameters
2008-04-14 19:36:21.794 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
```

This is with DVD and Firewire recordings.

I do not have alsmixer conf is the normal.

More info here not sure what it means.  This is way over my head.  It is very frustrating since it did work in .20.

```
amixer -c0 contents
numid=27,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=28,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=29,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x82 AES2=0x00 AES3=0x02]
numid=30,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on

```

```
 sudo alsaconf
sudo: alsaconf: command not found
```

If the parameters are not correct. How do I set the parameters?

---

### Post by volkswagner on 2008-04-28
Well I still do not know what is wrong.  I do realize the problem is deeper than mythtv and spdif passthrough.  I can not play any multichannel audio in any player.

Any ideas where to go from here?  

I am using onboard sound. Gigabyte GA-MA69GM-S2H with Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller, Audio device: ATI Technologies Inc SBx00 Azalia.

```
List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
aplay -L
front:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
iec958:CARD=HDMI,DEV=0
    HDA ATI HDMI
    IEC958 (S/PDIF) Digital Audio Output
```

Here is a portion of amixer -c0 contents , I am not sure what all the numbers mean. When I had the 5.1 working, passthrough device in myth was listed as "ALSA:iec958AESO 0x02)". I have tried other combinations here but not all. 
```

numid=27,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=28,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=29,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x82 AES2=0x00 AES3=0x02]
numid=30,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=32,iface=MIXER,name='IEC958 Capture Default'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=31,iface=MIXER,name='IEC958 Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
```

---

### Post by rusty- on 2008-04-29
I feel your pain on this, it took me a few hours of futzing to get my digital audio output to work.  Like you, I think that I tried every possible solution listed in any forum or wiki.

The thing that ultimately fixed it for me was [COLOR="Blue"]changing MAX AUDIO CHANNELS from [COLOR="Red"]5.1[/COLOR] back to [COLOR="red"]Stereo[/COLOR][/COLOR].

Don't know if it will work for you, but figured I'd offer what worked for me.

My current settings are:
```
AUDIO OUTPUT DEVICE = ALSA:default
PASSTHROUGH OUTPUT DEVICE = ALSA:iec958:{ AES0 0x02 }
MAX AUDIO CHANNELS = Stereo
UPMIX = Passive
X=Enable AC3 to SPDIF Passthrough
X=Enable DTS to SPDIF Passthrough
_=Aggressive Sound Card Buffering
X=Use internal Volume Controls
MIXER DEVICE = ALSA:default
MIXER CONTROLS = Master
```

---

### Post by volkswagner on 2008-04-30
Rusty, when I have max set to stereo is the only way for me to get sound.  This still does not allow me to hear sound in multi channel media, only 2ch encoded media.

More info:  Seems I only have generic kernel.

Followed this page:

[http://ubuntuforums.org/showthread.php?t=575653&page=2]("http://ubuntuforums.org/showthread.php?t=575653&page=2")

```
eric@FamilyRoom:~$ sudo m-a prepare
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
```

Still no joy!

---

### Post by volkswagner on 2008-05-01
Still talking to myself.  Does anyone know if the following means my kernel was changed?  Can I find out when/why it was changed?  Could this be why I lost spdif?

 ```
ls /usr/src/
alsa-driver.tar.bz2
alsa-modules-2.6.22-14-generic_1.0.14-1ubuntu2+2.6.22-14.52_amd64.deb
fglrx-8.443.1
linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-OLDVERSION.1209560196
linux-OLDVERSION.1209567200
modules
```

I thought I would try Hardy, it seems support for this card is not working in hardy.

[http://ubuntuforums.org/showthread.php?t=776958]("http://ubuntuforums.org/showthread.php?t=776958")

Looks like my only solution would be a clean install for mythbuntu 7.10 and not allow upgrade to mythtv .21.  Is that even possible?  I would need to do this on my remote machine also.  Bogus!

I can't believe nobody has any input in this matter.  Since it looks like a reinstall is in my future.  I am willing to try anything.

:confused:

---

### Post by rusty- on 2008-05-02
No clue on the kernel question, but there was one other nugget of info I came across on a post somewhere... the IEC958 Playback volume needs to be zero.  I just tried googling for the page/post but couldn't find it again.

Anyway, I went into alsamixer and unmuted the IEC958 control (the one without a volume control) and then set the IEC958 Playback volume, next control over, to zero.  Similar to [[COLOR="Red"]this image[/COLOR]]("http://www.mythtv.org/wiki/index.php/Image:Alsamixer_iec598.png") on the mythtv wiki.

---

### Post by volkswagner on 2008-05-02
Rusty,

What version of alsa are you running.  The screen shot is v1.0.10rc3.  I have v1.0.14.  I only have one slider for IEC958.  It is just a switch for MM, or 00.  I don't recall have another slider back when I originally had it working either.  Strange indeed.  

Thanks for not letting me talk to myself.  :)

---

### Post by volkswagner on 2008-05-06
Is there no one who can help?

Still plugging away at this. Maybe someone can chime in here. I am trying to get this to work in mplayer.

Mplayer preferences= Audio>ALSA-0.9x-1.x audio output
>device hw=0,1
>mixer default
>mixer_channel Master
When I play a DVD with these settings I get two warnings


```
error opening/initializing the selected video_out (-vo) device.
```
```

[AO_ALSA] alsa-lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AESO=6
```

I click ok for each warning. I loose picture, but I get dolby digital out to my receiver.

Please tell me I am getting somewhere. I feel I have messed with ALSA so much now it may be a problem. I have followed the comprehensive guide to remove and reinstall but no luck. Is my version of mplayer dated. I just reinstalled it via synaptic because it was borked. Reason I ask it seems it is set up for alsa pre-version .1.0.4.

Also within Mplayer I notice the following. If I try to play the DVD directly from the menu I get the following.


OK, I messed with the video settings.
When I select xv, I get the above scenario.

When I have any of the following, X11, gl, gl2, xvidix, I get the following.

```

Waring MVs not available
```

I do however get dolby sound out of spdif and video.
Now it is back to mythtv. Maybe someone can help sort out the above.

Also when I close Mplayer after using the few working video profiles, I get a Gnome screen saver warning.
__________________

---

### Post by jrockinl on 2008-05-07
I am having a problem with 5.1 sound in MythTV .21 also.  I was using the new 8.04 Mythbuntu.  At the time I didn't know if Stereo worked since I never tried it, but I suspect it would have if I tried.  I never had the problem with 7.10.  I went back to 7.10 and then updated to .21 thinking I might be having kernel/modules trouble.

I am a noobie and I cannot help anymore than to bump the problem.

I am using Asus p5b-vm with two pcHDTV 5500's.  In 7.10, I did have to make sure the 5500's cx88_alsa module was loaded as index 1,2 and snd_hda_intel as index 0.  Everything worked after that, but that doesn't help the problem in 8.04.

---

### Post by joe0815 on 2008-05-13
Hello,

I have the same problem with no 5.1 sound via the analog interface.
It's strange because speaker-test has good results.
Anyone already a solution for this problem?

Regards
Jo

---

### Post by Monsieur Gonzalez on 2008-05-13
Well, for me what did it was to follow the directions in [http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound") . 

Since I only use the SPDIF, I make it the default alsa output by adding a .asoundrc file in the home folder, with this text :
pcm.!default { 
type hw 
card 0 
device 1 
} 

Assuming, of course, device 1 is the IEC958 for your soundcard. Then, uncheck the myhthtv mixer options, and tell it to use the default alsa device. You might need to restart alsa, and/or logout one time for it to work. I don't know about your stereo, buth in mine, when correctly configured, there's a 44.1 khz (for music) and 48 khz (for most of the movies, tv....), since there's no need for resampling, thus getting better quality.

Good luck.

---

### Post by volkswagner on 2008-05-13
I wish.  Something is broken but nobody knows what.  When I have 5.1 selected I get errors "6ch invalid argument" when playing 2ch media.  When playing multichannel audio I get "buffer errors".  If I switch back to 5.1 and play multichannel I get NVP pause errors.  I see more sound problems with 8.04 so  I won't go there.  It looks like my only solution is reinstall and don't allow .21 upgrade.  

It seems 7.10 is no longer supported.  I see this thread has had a lot of views, but little response.  My guess it is folks are looking for answers not looking to offer help.

I think my ATI HDA SB onboard sound is not correctly supported.  It wants to use Intel HDA drivers.  I don't think the ATI has separate drivers.

---

### Post by kidcharles on 2008-05-19
> **rusty- said:**
> The thing that ultimately fixed it for me was [COLOR="Blue"]changing MAX AUDIO CHANNELS from [COLOR="Red"]5.1[/COLOR] back to [COLOR="red"]Stereo[/COLOR][/COLOR].

This worked for me too. I would say this is a bug then in MythTV that choosing a maximum of 5.1 channels means you have a maximum of 0 channels. I'm going to post this on the MythTV bug tracker.

---

### Post by volkswagner on 2008-05-19
Sure rub my nose in it!  ;)

Could you give more info on your setup?  Which version of mythbuntu, amd64 or x86?  Are you using ac3 and dts passthrough?

Using Alsa?  What sound card?  What is in your .asoundrc?

Do you get any errors at all in mythfrontend.log when playing multichannel audio?   Even if it plays fine.

---

### Post by kidcharles on 2008-05-21
> **volkswagner said:**
> Sure rub my nose in it!  ;)

Could you give more info on your setup?

Sure:

Distro: Ubuntu 8.04 x86 desktop

Sound Card lspci output:
Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Contents of /etc/asound.conf (I have no .asoundrc file):

```

pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}

```

Mythtv Version: 0.21

Settings -> General -> Audio:

Audio output device: ALSA:default
Passthrough output device: ALSA:iec958:{AES0 0x02}
Max Audio Channels: Stereo
Upmix: Passive
"Enable AC3 to SPDIF passthrough" and "Use internal volume controls" checked
Mixer Device: ALSA:default
Mixer Controls: PCM

There are no errors in the log output when watching AC3 content, it just reports successfully opening the Alsa audio device.

I only use AC3 passthrough, my oldy-but-a-goody digital receiver only handles AC3.

Hope this helps, let me know if you need more.

---

### Post by volkswagner on 2008-08-03
It has been a long hard road.

Lessons learned....

Keep track of ALL changes to system.  Don't make multiple changes.  Check system functions after updates.  Haste makes waste, etc, etc.

Thanks to this thread I have a working system. I had the same prebuffering pauses.  No I see only a few.

[http://ubuntuforums.org/showthread.php?t=839883&highlight=ALSA%3Ahw%3A1%2C1]("http://ubuntuforums.org/showthread.php?t=839883&highlight=ALSA%3Ahw%3A1%2C1")

I would like to sum up if I may.  Each system must be unique.  What works for some may not for others.  Syntax is important.  

My General sound settings in mythfrontend....
Audio output device = ALSA:hw:0,1
Passthrough output device = ALSA:iec958( AES0 0x02 )
Max Audio Channels = Stereo
Upmix = Passive
Enable AC3 to SPDIF passthrough = checked box
Enable DTS to SPDIF passthrough = Checked box
Aggressive Sound Card = Not checked box
Use internal volume control = Not checked box

Even though the max is set to stereo I get perfect passthrough for AC3, DTS, and dolby digital to my receiver. 

I have tried all of the above in the past, but apparently not all at the same time!

Problems making this difficult were determining what errors were related to sound and what was due to video.  Trying to fix both at the same time proved difficult.

I hope others can benefit.  Thanks to all for the replies.

Kill all commercials!

---

### Post by AntX on 2008-08-03
This thing is far from solved!!

You say you get perfect passthrough... is it in 5.1 channels?

What mythtv does with these settings is downmixing the 5 channels... to stereo, which is crap!!!

Try speaker-test -D spdif -c 5 and tell me if you got all 5 channels, cause I sure don't.

---

### Post by volkswagner on 2008-08-03
I certainly am enjoying full 5.1 passthrough.  No downmix.  I see on my receiver display "Dolby D" when playing a dvd, or live tv via firewire.  I do get a mix of sound from all five speakers.

See from the log, it does not look pretty but 6 channels is recognized.  The setting for stereo is a work around in mythtv settings.  I wish it worked better but it does work.  I have annoying unstable video driver issues making this difficult to pin down.

```
2008-08-03 12:31:38.868 TV: Attempting to change from None to WatchingLiveTV
2008-08-03 12:31:38.869 Using protocol version 40
2008-08-03 12:31:41.103 NVP: Disabling Audio, params(-1,2,44100)
2008-08-03 12:31:41.110 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-08-03 12:31:41.110 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2008-08-03 12:31:41.110 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x3040330) visual(0xa07890)
                        XJ_depth(16) WxH(640x480) bpl(1280)
2008-08-03 12:31:41.111 VideoOutputXv Error: Failed to create X buffers.
2008-08-03 12:31:41.112 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-08-03 12:31:41.112 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***
2008-08-03 12:31:41.127 OSD Theme Dimensions W: 640 H: 480
2008-08-03 12:31:41.286 Using realtime priority.
2008-08-03 12:31:41.287 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-08-03 12:31:41.292 TV: Changing from None to WatchingLiveTV
2008-08-03 12:31:41.406 OpenGLVideoSync()
2008-08-03 12:31:41.406 ~OpenGLVideoSync() -- begin
2008-08-03 12:31:41.406 ~OpenGLVideoSync() -- middle
2008-08-03 12:31:41.406 ~OpenGLVideoSync() -- end
2008-08-03 12:31:41.406 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-08-03 12:31:41.406 Video timing method: USleep with busy wait
2008-08-03 12:31:43.653 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-08-03 12:31:43.654 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2008-08-03 12:31:43.654 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x3040330) visual(0xa07890)
                        XJ_depth(16) WxH(640x480) bpl(1280)
2008-08-03 12:31:43.654 VideoOutputXv Error: Failed to create X buffers.
2008-08-03 12:31:43.655 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-08-03 12:31:43.655 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***
2008-08-03 12:31:43.789 AFD: Opened codec 0x914250, id(MPEG2VIDEO) type(Video)
2008-08-03 12:31:43.789 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-08-03 12:31:43.790 AFD: Opened codec 0x1f59480, id(AC3) type(Audio)
2008-08-03 12:31:43.795 Opening audio device 'hw:0,1'. ch 2(2) sr 48000
2008-08-03 12:31:43.795 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-08-03 12:31:43.808 NVP: Enabling Audio
2008-08-03 12:31:43.824 Opening audio device 'hw:0,1'. ch 2(2) sr 48000
2008-08-03 12:31:43.824 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-08-03 12:31:46.002 VideoOutputXv Error:
***
* Your system is not capable of displaying the
* full framerate at 640x480 resolution.  Frames
* will be skipped in order to keep the audio and
* video in sync.

2008-08-03 12:31:49.301 TV: Attempting to change from WatchingLiveTV to None
2008-08-03 12:31:49.597 TV: Changing from WatchingLiveTV to None
```


You may have a point about marking this as solved.  I did have it working this morning after disabling restricted video drivers.  After a couple reboots from mythtv wake, I had to reinstall the restricted drivers to get my video to playback more than six frames a minute.  Yes minute!!!

After looking at the logs and the display on my receiver there seems to be a fight with multichannel.  When I have the prebuffering errors, the receiver changes from DTS, to dolby stereo everytime the sound shutters and the prebuffering pause writes to the log.

So do I have a video, Xorg, or sound issue?

Here is a portion of the log when I get audio buffer underruns.  Notice the codec number opened.  Why would they be different?

```
2008-08-03 19:50:31.289 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-08-03 19:50:31.289 AFD: Opened codec 0x1d75960, id(AC3) type(Audio)
2008-08-03 19:50:31.331 Opening audio device 'hw:0,1'. ch 2(2) sr 48000
2008-08-03 19:50:31.331 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-08-03 19:50:31.348 NVP: Enabling Audio
2008-08-03 19:50:31.364 Opening audio device 'hw:0,1'. ch 2(2) sr 48000
2008-08-03 19:50:31.364 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-08-03 19:50:31.892 NVP: Prebuffer wait timed out 10 times.
2008-08-03 19:50:33.268 WriteAudio: buffer underrun
2008-08-03 19:50:33.932 WriteAudio: buffer underrun
2008-08-03 19:50:34.657 WriteAudio: buffer underrun
2008-08-03 19:50:35.317 WriteAudio: buffer underrun

```

---

### Post by NoThanksM$ on 2008-12-01
What sound card are you using that you get full dolby digital output to your receiver?  I use a Dolby Digital Live card, specifically the Montego DDL, and have seen several posts that say none of these types of cards can output AC3/DDL in Ubuntu, they need specific drivers from the manufacturer so the most they are good for in Linux is a single, digital stereo (not 5.1) connection to your receiver.  Is that not the case?

---

### Post by quasifly on 2008-12-11
Just got my DVD audio fixed using your settings below. Thanks for the post.

> **volkswagner said:**
> It has been a long hard road.

My General sound settings in mythfrontend....
Audio output device = ALSA:hw:0,1
Passthrough output device = ALSA:iec958( AES0 0x02 )
Max Audio Channels = Stereo
Upmix = Passive
Enable AC3 to SPDIF passthrough = checked box
Enable DTS to SPDIF passthrough = Checked box
Aggressive Sound Card = Not checked box
Use internal volume control = Not checked box


---

### Post by volkswagner on 2008-12-12
> **NoThanksM$ said:**
> What sound card are you using that you get full dolby digital output to your receiver?  I use a Dolby Digital Live card, specifically the Montego DDL, and have seen several posts that say none of these types of cards can output AC3/DDL in Ubuntu, they need specific drivers from the manufacturer so the most they are good for in Linux is a single, digital stereo (not 5.1) connection to your receiver.  Is that not the case?

My sound is onboard:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128056]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128056")

More info
```

card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I still have a major issue.  I am not sure if it is a myth, linux or cable co. issue.

On HD capture there are two audio streams.  The sound capture has a difficult time locking on the ac3 steam.  It toggles every second or so and cause choppy sound with prebuffer errors.  Totally unplayable.  I can actually see the display on my receiver show this action.

---

### Post by NoThanksM$ on 2008-12-12
I wonder if this is even a worthwhile pursuit, though.  I realized a bit after my last post that it's most likely not your sound card doing the encoding but the software doing it.  Aside from the load that puts on your computer, is that really any better than having your receiver do the conversion to 5.1?

---

