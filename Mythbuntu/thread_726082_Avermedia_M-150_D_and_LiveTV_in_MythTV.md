---
title: "Avermedia M-150 D and LiveTV in MythTV"
date: 2008-03-16
forum: Mythbuntu
---

### Post by punkrawker82 on 2008-03-16
I'm having a rather weird issue with my Avermedia M-150 D.  I have been following the wiki [here]("http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D"), and I have managed to get the MPEG-2 encoder (/dev/video1) to work fine with audio and video under mplayer.  But before I can get audio I need to run:

> v4lctl -c /dev/video1 volume mute off

So I created the script described in the wiki which un-mutes the audio and sets the channel:

> #!/bin/bash
v4lctl -c /dev/video1 setchannel $1
v4lctl -c /dev/video1 volume mute off
#sleep 1

I can watch live tv in mplayer after running the script and mplayer in a terminal.  However, whenever I try to watch live tv within mythtv, all I receive is a black screen; no audio, and no video.  Should I be telling mythtv to run this script somehow upon livetv playback or channel changes?  If so, where?

---

### Post by punkrawker82 on 2008-03-16
Here is the output I receive when I run mythtv from a terminal:

> 2008-03-19 17:27:58.876 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 17:27:58.884 XScreenSaver support enabled
2008-03-19 17:27:58.884 DPMS is disabled.
2008-03-19 17:27:58.885 Empty LocalHostName.
2008-03-19 17:27:58.885 Using localhost value of james-desktop
2008-03-19 17:27:58.898 New DB connection, total: 1
2008-03-19 17:27:58.903 Connected to database 'mythconverg' at host: localhost
2008-03-19 17:27:58.919 Closing DB connection named 'DBManager0'
2008-03-19 17:27:58.920 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-19 17:27:58.920 Connected to database 'mythconverg' at host: localhost
2008-03-19 17:27:58.922 Using screen 0, 1280x1024 at 0,0
2008-03-19 17:27:58.937 max_width: 1280 max_height: 1024
2008-03-19 17:27:58.939 max_width: 1280 max_height: 1024
2008-03-19 17:27:58.939 Trying 1280x1024 50 Hz
2008-03-19 17:27:58.940 SwitchToGUI: Switched to 1280 x 1024
2008-03-19 17:27:58.940 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-19 17:27:58.940 Using screen 0, 1280x1024 at 0,0
2008-03-19 17:27:58.942 Switching to square mode (Mythbuntu)
2008-03-19 17:27:58.973 Using the OpenGL painter
2008-03-19 17:27:58.975 lirc init success using configuration file: /home/james/.mythtv/lircrc
2008-03-19 17:27:58.976 JoystickMenuClient Error: Joystick disabled - Failed to read /home/james/.mythtv/joystickmenurc
2008-03-19 17:27:59.550 New DB connection, total: 2
2008-03-19 17:27:59.551 Connected to database 'mythconverg' at host: localhost
2008-03-19 17:27:59.592 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-19 17:27:59.593 Using protocol version 40
2008-03-19 17:27:59.606 TV: Attempting to change from None to WatchingLiveTV
2008-03-19 17:27:59.621 Using protocol version 40
2008-03-19 17:28:00.882 LiveTVChain(live-james-desktop-2008-03-19T17:27:59): ReloadAll(): Added new recording
2008-03-19 17:28:00.888 RingBuf(/var/lib/mythtv/recordings/1001_20080319172759.mpg): OpenFile(/var/lib/mythtv/recordings/1001_20080319172759.mpg, 12)
2008-03-19 17:28:07.389 RingBuf(/var/lib/mythtv/recordings/1001_20080319172759.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1001_20080319172759.mpg'.
2008-03-19 17:28:07.389 RingBuf(/var/lib/mythtv/recordings/1001_20080319172759.mpg): CalcReadAheadThresh(1 KB)
                         -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-03-19 17:28:47.392 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-03-19 17:28:47.392 TV Error: LiveTV not successfully started
2008-03-19 17:28:47.434 TV: Deleting TV Chain in destructor
Mutex destroy failure: Device or resource busy


It crashed....didn't even have to kill it :(

---

### Post by punkrawker82 on 2008-03-19
Ny ideas why mplayer has no problem, but mythTV dies like that?

---

### Post by punkrawker82 on 2008-03-19
Also,

> mythfrontend -v playback

Returns:

> 2008-03-19 18:32:47.768 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-19 18:32:48.381 XScreenSaver support enabled
2008-03-19 18:32:48.381 DPMS is disabled.
2008-03-19 18:32:48.381 Empty LocalHostName.
2008-03-19 18:32:48.381 Using localhost value of james-desktop
2008-03-19 18:32:48.395 New DB connection, total: 1
2008-03-19 18:32:48.399 Connected to database 'mythconverg' at host: localhost
2008-03-19 18:32:48.401 Closing DB connection named 'DBManager0'
2008-03-19 18:32:48.401 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-19 18:32:48.401 Connected to database 'mythconverg' at host: localhost
2008-03-19 18:32:48.403 Using screen 0, 1280x1024 at 0,0
2008-03-19 18:32:48.406 user: 1000 effective user: 1000 before privileged thread
2008-03-19 18:32:48.423 user: 1000 effective user: 1000 after privileged thread
2008-03-19 18:32:48.423 user: 1000 effective user: 1000 run_priv_thread
2008-03-19 18:32:48.425 New DB connection, total: 2
2008-03-19 18:32:48.425 Connected to database 'mythconverg' at host: localhost
2008-03-19 18:32:48.427 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-03-19 18:32:48.427 Enabled verbose msgs:  important general playback
2008-03-19 18:32:48.940 Connecting to lcd server: localhost:6545 (try 1 of 10)
2008-03-19 18:32:49.116 max_width: 1280 max_height: 1024
2008-03-19 18:32:49.231 Could not open settings file /home/james/.mythtv/mysql.txt for writing
2008-03-19 18:32:49.237 max_width: 1280 max_height: 1024
2008-03-19 18:32:49.238 Trying 1280x1024 50 Hz
2008-03-19 18:32:49.238 SwitchToGUI: Switched to 1280 x 1024
2008-03-19 18:32:49.238 Total desktop dim: 1280x1024, with 1 screen[s].
2008-03-19 18:32:49.239 Using screen 0, 1280x1024 at 0,0
2008-03-19 18:32:49.240 Switching to square mode (Mythbuntu)
2008-03-19 18:32:49.255 Using the OpenGL painter
2008-03-19 18:32:49.286 lirc init success using configuration file: /home/james/.mythtv/lircrc
2008-03-19 18:32:49.303 JoystickMenuClient Error: Joystick disabled - Failed to read /home/james/.mythtv/joystickmenurc
2008-03-19 18:32:50.489 Loading from: /usr/share/mythtv/themes/Mythbuntu/base.xml
2008-03-19 18:32:50.545 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-03-19 18:32:50.599 Registering Internal as a media playback plugin.
2008-03-19 18:32:50.714 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-03-19 18:32:50.768 Failed to run 'cdrecord --scanbus'
2008-03-19 18:32:50.771 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-03-19 18:32:50.789 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-03-19 18:32:50.829 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2008-03-19 18:32:50.884 Unable to initialize plugin 'mythstream'.
SIP listening on IP Address 192.168.1.2:5060 NAT address 192.168.1.2
SIP: Cannot register; proxy, username or password not set
2008-03-19 18:32:50.969 MythThemedMenuPrivate: Unknown tag image in background
2008-03-19 18:32:52.192 Using NV NPOT texture extension
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab
2008-03-19 18:32:52.382 Failed to mount /dev/sdb.
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2008-03-19 18:32:52.430 Failed to mount /dev/sdc.
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2008-03-19 18:32:52.468 Failed to mount /dev/sdd.
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2008-03-19 18:32:52.518 Failed to mount /dev/sde.
2008-03-19 18:32:53.729 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-19 18:32:53.729 Using protocol version 40
2008-03-19 18:32:54.094 TV: Attempting to change from None to WatchingLiveTV
2008-03-19 18:32:54.097 Using protocol version 40
2008-03-19 18:32:55.466 LiveTVChain(live-james-desktop-2008-03-19T18:32:54): ReloadAll(): Added new recording
2008-03-19 18:32:55.471 RingBuf(/var/lib/mythtv/recordings/livetv/1001_20080319183254.mpg): OpenFile(/var/lib/mythtv/recordings/livetv/1001_20080319183254.mpg, 12)
2008-03-19 18:33:01.971 RingBuf(/var/lib/mythtv/recordings/livetv/1001_20080319183254.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/livetv/1001_20080319183254.mpg'.
2008-03-19 18:33:01.971 RingBuf(/var/lib/mythtv/recordings/livetv/1001_20080319183254.mpg): CalcReadAheadThresh(1 KB)
                         -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-03-19 18:33:41.974 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-03-19 18:33:41.974 TV Error: LiveTV not successfully started
2008-03-19 18:33:42.036 TV: Deleting TV Chain in destructor
Destroying SipFsm object 
2008-03-19 18:33:50.592 Deleting UPnP client...


---

### Post by punkrawker82 on 2008-03-19
mplayer's output is:

> MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing /dev/video1.
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
gnome_screensaver_control()06 ct: -3.375 49084/49084  9%  1%  2.1% 13 0 
Exiting... (Quit)


---

