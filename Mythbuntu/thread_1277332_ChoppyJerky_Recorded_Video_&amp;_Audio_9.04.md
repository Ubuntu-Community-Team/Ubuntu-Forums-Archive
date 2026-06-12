---
title: "Choppy/Jerky Recorded Video &amp; Audio 9.04"
date: 2009-09-28
forum: Mythbuntu
---

### Post by Crash87ss on 2009-09-28
Choppy/Jerky Recorded Video & Audio 9.04

	I upgraded to a new HD and 9.04 & got the tuner & audio up and running. Live TV seems to work great. However recorded programs have large sections that have skips and pauses in both video and audio. Not all parts of the recording will have this & live TV is ok. Its happened on all three recording I&#8217;ve tried so far. 

	I tried changing around the playback profile to set it on something less demanding (even though the system ran fine with 8.04) but it did not help. Not too sure what else to try&#8230; and kinda confused&#8230; any suggestions?

	System:
		Biostar Mobo
		AMD Athlon  2.4GHZ
		Nvidia 8400 GS hooked up DVI to HDMI (running   restricted drivers version 8.somthing)
		Audio: SPDIF (through custom optical out card)
		Tuner: Pinnacle 800i
		HD: WD 160GB SATA
		Distro: 9.04, with latest Kernel package.

---

### Post by bsntech on 2009-09-28
Does your tuner also work for analog mode?  You may try to see how it records for analog recordings and it is choppy then.

For your processor - are you sure it is a 2.4 GHz or not?  The old Athlons were marked like XP3200+ - although the clock rate on this process was only about 1.9 GHz.

I have the XP3200+ and when I record any ATSC or HD programs, my processor is fully maxed out and sometimes it does skip audio/video.

---

### Post by Crash87ss on 2009-09-29
The processor is a 4000 series. I know for a fact it runs over 2 Ghz. I think this one is 2.2 instead of the previously stated 2.4 (which is in my other machine). 

Right now I only have OTA stations, so I don't think I can try analog. I had an hour last night to try some things. Here is what I found:

Altering the playback profiles to reduce CPU load makes no difference on the Jerky recordings. Double checked all my backend and capture card settings, changed my guide to EIT, and set my tuner to allow only 1 recording (was on two for some reason). 

I watched 5-10 minutes of live TV, skipped back, watched it again and no jerkyness or skipping at all. 

I recorded a five minute block of TV. Watched while recording, no skipping. Allowed it to finsih and watched again, no skipping. Other recordings still skip (i'm pretty sure the issue is in the file of the recordings now).  

I recorded an hour of programing last night so I will check it after work to see how it is. I will post the results tonight or first thing tomorrow.

---

### Post by klc5555 on 2009-09-29
> **Crash87ss said:**
> The processor is a 4000 series. I know for a fact it runs over 2 Ghz. I think this one is 2.2 instead of the previously stated 2.4 (which is in my other machine). 

Right now I only have OTA stations, so I don't think I can try analog. I had an hour last night to try some things. Here is what I found:

Altering the playback profiles to reduce CPU load makes no difference on the Jerky recordings. Double checked all my backend and capture card settings, changed my guide to EIT, and set my tuner to allow only 1 recording (was on two for some reason). 

I watched 5-10 minutes of live TV, skipped back, watched it again and no jerkyness or skipping at all. 

I recorded a five minute block of TV. Watched while recording, no skipping. Allowed it to finsih and watched again, no skipping. Other recordings still skip (i'm pretty sure the issue is in the file of the recordings now).  

I recorded an hour of programing last night so I will check it after work to see how it is. I will post the results tonight or first thing tomorrow.

Time to check the backend & frontend logs from the times that a successful recording from livetv takes place and an unsuccessful scheduled recording takes place to see if differences might give you some clues.

---

### Post by Crash87ss on 2009-09-29
> **klc5555 said:**
> Time to check the backend & frontend logs from the times that a successful recording from livetv takes place and an unsuccessful scheduled recording takes place to see if differences might give you some clues.

Please excuse the novice question, but where do I find/access the logs? Sounds like they'd be extremly helpful.

---

### Post by klc5555 on 2009-09-29
> **Crash87ss said:**
> Please excuse the novice question, but where do I find/access the logs? Sounds like they'd be extremly helpful.

/var/logs/mythtv/

If just the last few entries in a log is what you want, use the "tail" command to retrieve them. Otherwise, use whatever your usual editor is (pico, nano, vim, etc.) to read the sections that pertain to what you're looking for. The logs can be a trifle long.

---

### Post by Crash87ss on 2009-09-29
Thanks for the tip KLC5555. 

Look like i have a prebuffer pause problem, the log is loaded with that error. 

I found the Wiki article on it here:
[http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause]("http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause")

I'm will read & work through that and post if I find anything. Any further suggestions are greatly appreciated. Thanks for the help so far!

---

### Post by Crash87ss on 2009-10-01
Still no luck…

CPU usage (according to mpstat) is low 50% during good playback and high 50’s when prebuffer pause occurs. 

I have plackback set to the SLIM profile. No noticeable difference

I do notice a slight difference when enabling extra sound card buffer. 

Currently audio setting are:
ALSA:SPDIF
Passthrough: Alsa:IEC958 (something like that)
Both Passtrough options are enabled
Aggressive buffer is not enabled

I tried aggressive buffering, disabling passthrough, disabling internal controls. 

A recent post [http://ubuntuforums.org/showthread.php?t=1273595](http://ubuntuforums.org/showthread.php?t=1273595) mentioned enabling real time priority threads. No luck. 

I did optimize SQL, tried the 173 NVidia driver (instead of the 180). 

Upgraded to ALSA version 1.0.21

I tried playing the recording outside myth. One was real screwy in VLC, but worked with xine and mplayer. But I don’t have any sound output outside of myth (haven’t figure out how to get SPDIF working there). The video seemed fine. 

Here is the problem statement again:

Issue – Recorded video & audio is choppy

-	Mythfrontend log shows “Prebuffer Pause” and  “writeAudio: buffer underrun”
-	LiveTV has no issues, can skip around with no playback issue
-	Error is inconsistent on recorded TV, errors do not occur at the same point each time
-	Extra audio buffering helps, but does not solve problem
-	If I pause the recording during the prebuffer pause, audio and video will be smooth for an unknown amount of time
-	It doesn’t discriminate between SD & HD
-	Same system worked in 8.04, only difference is new HD (160 SATA – replaced 80gig SATA) and 9.04

I’m quickly running out of ideas. I haven’t made any new recording since optimize SQL, so I’ll give that a try. I was also suspicious about RAM (1 gig) any thoughts? 

Some more suggestions would be great

---

### Post by klc5555 on 2009-10-01
9.04 is a bit more resource-intensive than 7.10 or 8.04 were. Even on 7.10 I found I needed 1.5 Gigs of RAM to get reliable playback. I also found that playback was a bit better when the OS & swap were on an entirely different drive than the recording drive(s).

But regarding your harddisk: some SATA drives I've seen (but not most of them) require a jumper block to be removed to run at full SATA transfer speed. Otherwise a default install runs at ordinary IDE transfer rates. Is your new drive running at full speed?

Finally, 8.04 will still be under long-term support well after the date when 9.04 will be done. If 8.04 plus Myth 0.21 was a well-functioning version for you, but 9.04 plus the very same Myth 0.21 is causing problems, the most efficient solution might be simply to back-level to 8.04, until a version comes out that has a killer new feature (e.g. Myth 0.22) or particular expanded hardware support that you find you really need.

---

### Post by zymurgist on 2009-10-01
Summary of below: It appears playing recordings does not use hardware acceleration. If this is correct .. how can I fix it?
--- 

I am enjoying the same problems as the original poster (livetv is fine, recorded shows are jerky).

I am also running 9.04 and have tried changing a variety of settings.

I know my hardware can handle it (Huappage 2250, nVidia 9400GT w/JAvenard's VDPAU, 3.2ghz P4, 2GB ram, separate SATA drives for Ubuntu/swap and recordings).

My log is also full of the 'pre-buffering pause' messages.

I can play the recording in Xine and VLC with no issues, both on my Myth system and a Windows XP system. Thus I know the recording is fine.

Perhaps this may be a clue: 

When watching liveTV, TOP shows the %CPU at 27-30.
When watching recorded TV, TOP shows %CPU at 100-120.

(keep in mind this system claims to have 2 CPUs hence 100-120 is prolly 50-60 on each one)

So it is quite interesting that recorded TV is using so much more CPU than LiveTV. Just to test .. I went into the playback settings and changed from VDPAU to the High Quality setting .. and then my LiveTV was jerky just like the recorded shows were.

What all this tells me is that it appears VDPAU isn't being used when watching recorded shows.

Any ideas?

---

### Post by zymurgist on 2009-10-01
Did some reading and turned on logging (-v playback) and here's what I get:

```
2009-10-01 22:32:18.595 Using runtime prefix = /usr
QServerSocket: failed to bind or listen to the socket
2009-10-01 22:32:18.596 MediaRenderer::HttpServer Create Error
2009-10-01 22:32:18.612 XScreenSaver support enabled
2009-10-01 22:32:18.612 DPMS is active.
2009-10-01 22:32:18.613 Empty LocalHostName.
2009-10-01 22:32:18.613 Using localhost value of MythBuntuServer
2009-10-01 22:32:18.622 New DB connection, total: 1
2009-10-01 22:32:18.627 Connected to database 'mythconverg' at host: localhost
2009-10-01 22:32:18.629 Closing DB connection named 'DBManager0'
2009-10-01 22:32:18.630 Primary screen 0.
2009-10-01 22:32:18.631 Connected to database 'mythconverg' at host: localhost
2009-10-01 22:32:18.632 Using screen 0, 1280x720 at 0,0
2009-10-01 22:32:18.662 user: 1000 effective user: 1000 before privileged thread
2009-10-01 22:32:18.662 user: 1000 effective user: 1000 run_priv_thread
2009-10-01 22:32:18.662 user: 1000 effective user: 1000 after privileged thread
2009-10-01 22:32:18.663 New DB connection, total: 2
2009-10-01 22:32:18.664 Connected to database 'mythconverg' at host: localhost
2009-10-01 22:32:18.666 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-10-01 22:32:18.666 Enabled verbose msgs:  important general playback
2009-10-01 22:32:19.088 max_width: 1280 max_height: 720
2009-10-01 22:32:19.172 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-01 22:32:19.174 Primary screen 0.
2009-10-01 22:32:19.175 Using screen 0, 1280x720 at 0,0
2009-10-01 22:32:19.175 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-01 22:32:19.176 Switching to wide mode (metallurgy-wide)
2009-10-01 22:32:19.199 Using the Qt painter
2009-10-01 22:32:19.200 JoystickMenuClient Error: Joystick disabled - Failed to read /home/aasland/.mythtv/joystickmenurc
2009-10-01 22:32:19.201 lirc init success using configuration file: /home/aasland/.mythtv/lircrc
2009-10-01 22:32:19.516 Loading from: /usr/share/mythtv/themes/metallurgy-wide/base.xml
2009-10-01 22:32:19.525 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-01 22:32:19.564 Registering Internal as a media playback plugin.
2009-10-01 22:32:19.638 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-01 22:32:19.686 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-01 22:32:19.736 Starting update of NWS-XML
2009-10-01 22:32:19.745 Starting update of NDFD-6_day
2009-10-01 22:32:19.762 Starting update of NDFD-18_Hour
QServerSocket: failed to bind or listen to the socket
2009-10-01 22:32:19.826 NetworkControl: Listening for remote connections on port 6546
2009-10-01 22:32:19.826 NetworkControl failed to bind to port 6546.
2009-10-01 22:32:19.827 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-01 22:32:20.549 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NWS-XML KRGK has exited
2009-10-01 22:32:20.549 pressure_string::
2009-10-01 22:32:20.550 nrecoverable error parsing script output 
2009-10-01 22:32:22.660 XMLParse::LoadTheme using /usr/share/mythtv/themes/metallurgy-wide/ui.xml
2009-10-01 22:32:22.918 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-01 22:32:22.919 Using protocol version 40
2009-10-01 22:32:25.369 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NDFD-18_Hour +44.35,-092.29 has exited
2009-10-01 22:32:25.452 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): OpenFile(/Storage/mythTVRecordings/1051_20090929195900.mpg, 1)
2009-10-01 22:32:25.452 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): CalcReadAheadThresh(3046578769 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-01 22:32:25.639 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NDFD-6_day +44.35,-092.29 has exited
2009-10-01 22:32:25.665 AFD: Stream #0, has id 0x2112 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa2bd990
2009-10-01 22:32:25.668 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:25.668 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:25.668 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:25.668 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:25.668 Using 4 CPUs for decoding
2009-10-01 22:32:25.668 AFD: InitVideoCodec() 0xa2ea380 id(MPEG2VIDEO) type (Video).
2009-10-01 22:32:25.669 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-01 22:32:25.669 AFD: Using ffmpeg for video decoding
2009-10-01 22:32:25.669 AFD: Looking for decoder for MPEG2VIDEO
2009-10-01 22:32:25.669 AFD: Opened codec 0xa2ea380, id(MPEG2VIDEO) type(Video)
2009-10-01 22:32:25.669 AFD: Stream #1, has id 0x2113 codec id AC3, type Audio, bitrate 384000 at 0x0xa2e7020
2009-10-01 22:32:25.669 AFD: codec AC3 has 6 channels
2009-10-01 22:32:25.669 AFD: Looking for decoder for AC3
2009-10-01 22:32:25.670 AFD: Opened codec 0xa2ea710, id(AC3) type(Audio)
2009-10-01 22:32:25.670 AFD: Stream #2, has id 0x2114 codec id AC3, type Audio, bitrate 192000 at 0x0xa2b7700
2009-10-01 22:32:25.670 AFD: codec AC3 has 1 channels
2009-10-01 22:32:25.670 AFD: Looking for decoder for AC3
2009-10-01 22:32:25.670 AFD: Opened codec 0xa358e30, id(AC3) type(Audio)
2009-10-01 22:32:25.671 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): CalcReadAheadThresh(3046579085 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-01 22:32:25.671 Dec: Trying to select track (w/lang)
2009-10-01 22:32:25.671 Dec: Selecting first track
2009-10-01 22:32:25.671 Dec: Selected track #1 in the Unknown language(0)
2009-10-01 22:32:25.671 AFD: Recording has no position -- using libavformat seeking.
2009-10-01 22:32:25.671 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1051_20090929195900.mpg". novideo(0)
2009-10-01 22:32:25.672 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:25.673 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:25.673 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:25.684 VideoOutputNull()
2009-10-01 22:32:25.684 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:25.684 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-01 22:32:25.684 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:25.684 Created data @0xac9a9020->0xacafa822
2009-10-01 22:32:25.684 Created data @0xac857020->0xac9a8822
2009-10-01 22:32:25.684 Created data @0xac705020->0xac856822
2009-10-01 22:32:25.684 Created data @0xac5b3020->0xac704822
2009-10-01 22:32:25.685 Created data @0xac461020->0xac5b2822
2009-10-01 22:32:25.685 Created data @0xac30f020->0xac460822
2009-10-01 22:32:25.685 Created data @0xac1bd020->0xac30e822
2009-10-01 22:32:25.685 Created data @0xac06b020->0xac1bc822
2009-10-01 22:32:25.685 Created data @0xabf19020->0xac06a822
2009-10-01 22:32:25.685 Created data @0xabdc7020->0xabf18822
2009-10-01 22:32:25.685 Created data @0xabc75020->0xabdc6822
2009-10-01 22:32:25.685 Created data @0xabb23020->0xabc74822
2009-10-01 22:32:25.685 Created data @0xab9d1020->0xabb22822
2009-10-01 22:32:25.685 Created data @0xab87f020->0xab9d0822
2009-10-01 22:32:25.685 Created data @0xab72d020->0xab87e822
2009-10-01 22:32:25.685 Created data @0xab5db020->0xab72c822
2009-10-01 22:32:25.685 Created data @0xab489020->0xab5da822
2009-10-01 22:32:25.685 Created data @0xab337020->0xab488822
2009-10-01 22:32:25.685 Created data @0xab1e5020->0xab336822
2009-10-01 22:32:25.686 Created data @0xab093020->0xab1e4822
2009-10-01 22:32:25.686 Created data @0xaaf41020->0xab092822
2009-10-01 22:32:25.686 Created data @0xaadef020->0xaaf40822
2009-10-01 22:32:25.686 Created data @0xaac9d020->0xaadee822
2009-10-01 22:32:25.686 Created data @0xaab4b020->0xaac9c822
2009-10-01 22:32:25.686 Created data @0xaa9f9020->0xaab4a822
2009-10-01 22:32:25.686 Created data @0xaa8a7020->0xaa9f8822
2009-10-01 22:32:25.686 Created data @0xaa755020->0xaa8a6822
2009-10-01 22:32:25.686 Created data @0xaa603020->0xaa754822
2009-10-01 22:32:25.686 Created data @0xaa4b1020->0xaa602822
2009-10-01 22:32:25.686 Created data @0xaa35f020->0xaa4b0822
2009-10-01 22:32:25.686 Created data @0xaa20d020->0xaa35e822
2009-10-01 22:32:25.686 Created data @0xaa0bb020->0xaa20c822
2009-10-01 22:32:25.751 VDP: SetVideoRenderer(null)
2009-10-01 22:32:25.751 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:25.751 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-01 22:32:25.751 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-01 22:32:25.751 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:25.752 NVP: LoadFilters(''..) -> 0
2009-10-01 22:32:25.752 NVP: ClearAfterSeek(1)
2009-10-01 22:32:25.754 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:25.823 NVP: Waiting for prebuffer..  1 UuUULLAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:25.847 Dec: Selected track #1 in the Unknown language(0)
2009-10-01 22:32:25.893 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-10-01 22:32:25.894 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-01 22:32:25.894 AFD: HandleGopStart: Initial key frame distance: 15.
2009-10-01 22:32:25.900 NVP: Waiting for prebuffer..  2 UUUUUUULUULAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:25.927 NVP: Exited decoder loop.
2009-10-01 22:32:25.928 TV: Attempting to change from None to WatchingPreRecorded
2009-10-01 22:32:25.929 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): OpenFile(/Storage/mythTVRecordings/1051_20090929195900.mpg, 12)
2009-10-01 22:32:25.930 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): CalcReadAheadThresh(3046578769 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-01 22:32:25.931 DPMS Deactivated 
2009-10-01 22:32:25.967 ~VideoOutputNull()
2009-10-01 22:32:26.138 AFD: Stream #0, has id 0x2112 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa4753e0
2009-10-01 22:32:26.139 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:26.139 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:26.139 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:26.140 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:26.442 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): OpenFile(/Storage/mythTVRecordings/1051_20090929195900.mpg, 1)
2009-10-01 22:32:26.442 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): CalcReadAheadThresh(3011126224 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-01 22:32:26.471 VDPAU: Version 0
2009-10-01 22:32:26.472 VDPAU: Information NVIDIA VDPAU Driver Shared Library  185.18.36  Fri Aug 14 17:50:51 PDT 2009
2009-10-01 22:32:26.525 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:26.525 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:26.525 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:26.525 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:26.525 Using 1 CPUs for decoding
2009-10-01 22:32:26.525 AFD: InitVideoCodec() 0xa475580 id(MPEGVIDEO_VDPAU) type (Video).
2009-10-01 22:32:26.525 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-01 22:32:26.526 AFD: Using vdpau for video decoding
2009-10-01 22:32:26.526 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-01 22:32:26.526 AFD: Opened codec 0xa475580, id(MPEGVIDEO_VDPAU) type(Video)
2009-10-01 22:32:26.526 AFD: Stream #1, has id 0x2113 codec id AC3, type Audio, bitrate 384000 at 0x0xa475ad0
2009-10-01 22:32:26.526 AFD: codec AC3 has 6 channels
2009-10-01 22:32:26.526 AFD: Looking for decoder for AC3
2009-10-01 22:32:26.526 AFD: Opened codec 0xa475c70, id(AC3) type(Audio)
2009-10-01 22:32:26.526 AFD: Stream #2, has id 0x2114 codec id AC3, type Audio, bitrate 192000 at 0x0xa4761c0
2009-10-01 22:32:26.527 AFD: codec AC3 has 1 channels
2009-10-01 22:32:26.527 AFD: Looking for decoder for AC3
2009-10-01 22:32:26.527 AFD: Opened codec 0xa476360, id(AC3) type(Audio)
2009-10-01 22:32:26.527 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): CalcReadAheadThresh(3046579085 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-01 22:32:26.532 Opening audio device 'default'. ch 2(2) sr 48000
2009-10-01 22:32:26.532 Opening ALSA audio device 'default'.
2009-10-01 22:32:26.547 Mixer unable to find control Master
2009-10-01 22:32:26.547 Mixer unable to find control Master
2009-10-01 22:32:26.548 Mixer unable to find control PCM
2009-10-01 22:32:26.548 Mixer unable to find control PCM
2009-10-01 22:32:26.548 Mixer unable to find control PCM
2009-10-01 22:32:26.548 Dec: Trying to select track (w/lang)
2009-10-01 22:32:26.549 Dec: Selecting first track
2009-10-01 22:32:26.549 Dec: Selected track #1 in the Unknown language(0)
2009-10-01 22:32:26.549 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-01 22:32:26.616 AFD: Stream #0, has id 0x2112 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xaf3f69c0
2009-10-01 22:32:26.618 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:26.618 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:26.618 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:26.618 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:26.618 Using 4 CPUs for decoding
2009-10-01 22:32:26.623 AFD: InitVideoCodec() 0xaf3f6b50 id(MPEG2VIDEO) type (Video).
2009-10-01 22:32:26.623 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-01 22:32:26.623 AFD: Using ffmpeg for video decoding
2009-10-01 22:32:26.623 AFD: Looking for decoder for MPEG2VIDEO
2009-10-01 22:32:26.623 AFD: Opened codec 0xaf3f6b50, id(MPEG2VIDEO) type(Video)
2009-10-01 22:32:26.623 AFD: Stream #1, has id 0x2113 codec id AC3, type Audio, bitrate 384000 at 0x0xb377d710
2009-10-01 22:32:26.623 AFD: codec AC3 has 6 channels
2009-10-01 22:32:26.623 AFD: Looking for decoder for AC3
2009-10-01 22:32:26.624 AFD: Opened codec 0xb377d8b0, id(AC3) type(Audio)
2009-10-01 22:32:26.624 AFD: Stream #2, has id 0x2114 codec id AC3, type Audio, bitrate 192000 at 0x0xb137be60
2009-10-01 22:32:26.624 AFD: codec AC3 has 1 channels
2009-10-01 22:32:26.624 AFD: Looking for decoder for AC3
2009-10-01 22:32:26.625 AFD: Opened codec 0xb137bff0, id(AC3) type(Audio)
2009-10-01 22:32:26.625 RingBuf(/Storage/mythTVRecordings/1051_20090929195900.mpg): CalcReadAheadThresh(3046579085 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-01 22:32:26.625 Dec: Trying to select track (w/lang)
2009-10-01 22:32:26.625 Dec: Selecting first track
2009-10-01 22:32:26.625 Dec: Selected track #1 in the Unknown language(0)
2009-10-01 22:32:26.625 AFD: Recording has no position -- using libavformat seeking.
2009-10-01 22:32:26.625 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1051_20090929195900.mpg". novideo(0)
2009-10-01 22:32:26.627 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:26.627 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:26.627 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:26.637 VideoOutputNull()
2009-10-01 22:32:26.638 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:26.638 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-01 22:32:26.638 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:26.638 Created data @0xac1a8020->0xac2f9822
2009-10-01 22:32:26.638 Created data @0xac056020->0xac1a7822
2009-10-01 22:32:26.638 Created data @0xabf04020->0xac055822
2009-10-01 22:32:26.639 Created data @0xabdb2020->0xabf03822
2009-10-01 22:32:26.639 Created data @0xabc60020->0xabdb1822
2009-10-01 22:32:26.639 Created data @0xabb0e020->0xabc5f822
2009-10-01 22:32:26.639 Created data @0xab9bc020->0xabb0d822
2009-10-01 22:32:26.639 Created data @0xab86a020->0xab9bb822
2009-10-01 22:32:26.639 Created data @0xab718020->0xab869822
2009-10-01 22:32:26.639 Created data @0xab5c6020->0xab717822
2009-10-01 22:32:26.639 Created data @0xab474020->0xab5c5822
2009-10-01 22:32:26.639 Created data @0xab322020->0xab473822
2009-10-01 22:32:26.640 Created data @0xab1d0020->0xab321822
2009-10-01 22:32:26.640 Created data @0xab07e020->0xab1cf822
2009-10-01 22:32:26.640 Created data @0xaaf2c020->0xab07d822
2009-10-01 22:32:26.640 Created data @0xaadda020->0xaaf2b822
2009-10-01 22:32:26.640 Created data @0xaac88020->0xaadd9822
2009-10-01 22:32:26.640 Created data @0xaab36020->0xaac87822
2009-10-01 22:32:26.640 Created data @0xaa9e4020->0xaab35822
2009-10-01 22:32:26.640 Created data @0xaa892020->0xaa9e3822
2009-10-01 22:32:26.641 Created data @0xaa740020->0xaa891822
2009-10-01 22:32:26.641 Created data @0xaa5ee020->0xaa73f822
2009-10-01 22:32:26.641 Created data @0xaa49c020->0xaa5ed822
2009-10-01 22:32:26.641 Created data @0xaa34a020->0xaa49b822
2009-10-01 22:32:26.641 Created data @0xaa1f8020->0xaa349822
2009-10-01 22:32:26.641 Created data @0xaa0a6020->0xaa1f7822
2009-10-01 22:32:26.641 Created data @0xa9f54020->0xaa0a5822
2009-10-01 22:32:26.641 Created data @0xa9e02020->0xa9f53822
2009-10-01 22:32:26.641 Created data @0xa9cb0020->0xa9e01822
2009-10-01 22:32:26.642 Created data @0xa9b5e020->0xa9caf822
2009-10-01 22:32:26.642 Created data @0xa9a0c020->0xa9b5d822
2009-10-01 22:32:26.642 Created data @0xa98ba020->0xa9a0b822
2009-10-01 22:32:26.729 VDP: SetVideoRenderer(null)
2009-10-01 22:32:26.730 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:26.730 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-01 22:32:26.730 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-01 22:32:26.730 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:26.730 NVP: LoadFilters(''..) -> 0
2009-10-01 22:32:26.730 NVP: ClearAfterSeek(1)
2009-10-01 22:32:26.731 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:26.777 Position map filled from DB to: 219177
2009-10-01 22:32:26.786 SyncPositionMap prerecorded, from DB: 18265 entries
2009-10-01 22:32:26.786 SyncPositionMap, new totframes: 219177, new length: 3656, posMap size: 18265
2009-10-01 22:32:26.787 AFD: Position map found
2009-10-01 22:32:26.787 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1051_20090929195900.mpg". novideo(0)
2009-10-01 22:32:26.797 NVP: Waiting for prebuffer..  1 uLULAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:26.863 NVP: Waiting for prebuffer..  2 UuUULULAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:26.864 Dec: Selected track #1 in the Unknown language(0)
2009-10-01 22:32:26.917 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-10-01 22:32:26.917 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-01 22:32:26.917 AFD: HandleGopStart: Initial key frame distance: 15.
2009-10-01 22:32:26.930 NVP: Waiting for prebuffer..  3 UUUUUUULUULAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:26.985 NVP: progressive frame seen after 2 interlaced  frames
2009-10-01 22:32:27.002 Disabled deinterlacing
2009-10-01 22:32:27.186 VideoOutput: Allowed renderers: vdpau
2009-10-01 22:32:27.186 VideoOutput: Allowed renderers (filt: vdpau): vdpau
2009-10-01 22:32:27.188 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:27.188 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:27.189 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:27.189 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:27.189 VideoOutput: Preferred renderer: vdpau
2009-10-01 22:32:27.189 VideoOutput: Trying video renderer: vdpau
2009-10-01 22:32:27.191 VDP: Accepting: cmp(< 1920 768,>= 0 704) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpauadvanced) filt()
2009-10-01 22:32:27.191 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-01 22:32:27.191 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-01 22:32:27.202 VideoOutputXv: ctor
2009-10-01 22:32:27.204 XOff: 0, YOff: 0
2009-10-01 22:32:27.204 VDP: LoadBestPreferences(1280x720, 60)
2009-10-01 22:32:27.204 Snapping width to avoid scaling: width: 1280, left: 0
2009-10-01 22:32:27.204 Display Rect  left: 0, top: 90, width: 1280, height: 540, aspect: 1.33333
2009-10-01 22:32:27.204 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:27.206 VideoOutputXv: Pixel dimensions: Screen 1280x720, window 1280x720
2009-10-01 22:32:27.208 VideoOutputXv: Estimated display dimensions: 325x183 mm  Aspect: 1.77596
2009-10-01 22:32:27.208 VideoOutputXv: Estimated window dimensions: 325x183 mm  Aspect: 1.77596
2009-10-01 22:32:27.582 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: vdpau
2009-10-01 22:32:27.824 VideoOutputXv: Created VDPAU context (GPU decode)
2009-10-01 22:32:27.824 VDP: SetVideoRenderer(vdpau)
2009-10-01 22:32:27.824 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-10-01 22:32:27.828 VDPAU: Created OSD (1280x720)
2009-10-01 22:32:27.828 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-01 22:32:27.828 Snapping height to avoid scaling: height: 720, top: 0
2009-10-01 22:32:27.829 Snapping width to avoid scaling: width: 1280, left: 0
2009-10-01 22:32:27.829 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:27.829 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:27.831 Over/underscan. V: 0, H: 0
2009-10-01 22:32:27.831 Snapping height to avoid scaling: height: 720, top: 0
2009-10-01 22:32:27.831 Snapping width to avoid scaling: width: 1280, left: 0
2009-10-01 22:32:27.831 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:27.831 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-01 22:32:27.832 VDP: LoadBestPreferences(1280x720, 59.9401)
2009-10-01 22:32:27.832 NVP: LoadFilters(''..) -> 0
2009-10-01 22:32:27.839 OSD Theme Dimensions W: 1280 H: 720
2009-10-01 22:32:28.086 NVP: prebuffering pause
2009-10-01 22:32:28.086 NVP: Waiting for prebuffer..  0 aLAAAAAAULAAAAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:28.154 NVP: Waiting for prebuffer..  1 AUAALAALUUAUUAAAAAAAAAAAAAAAAAA
2009-10-01 22:32:28.220 NVP: Waiting for prebuffer..  2 AUAAUAALUULUUAUUAAAAAAAAAAAAAAA
2009-10-01 22:32:28.376 TV: StartPlayer(): took 2436 ms to start player.
2009-10-01 22:32:28.376 NVP: ClearAfterSeek(1)
2009-10-01 22:32:28.377 TV: Changing from None to WatchingPreRecorded
2009-10-01 22:32:28.376 VideoOutputXv: ClearAfterSeek()
2009-10-01 22:32:28.378 VideoOutputXv: DiscardFrames(0)
2009-10-01 22:32:28.378 VideoBuffers::DiscardFrames(0): AAAAAAAA         
2009-10-01 22:32:28.378 VideoBuffers::DiscardFrames(0): AAAAAAAA          -- done
2009-10-01 22:32:28.378 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-01 22:32:28.379 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-01 22:32:28.383 New DB connection, total: 3
2009-10-01 22:32:28.383 Realtime priority would require SUID as root.
2009-10-01 22:32:28.384 Connected to database 'mythconverg' at host: localhost
2009-10-01 22:32:28.424 VDPAU: Created VDPAU decoder (2 ref frames)
2009-10-01 22:32:28.484 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-10-01 22:32:28.484 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-10-01 22:32:28.484 OpenGLVideoSync()
2009-10-01 22:32:28.490 OpenGLVideoSync: x,y -> 640, 360
2009-10-01 22:32:28.545 Using OpenGLVideoSync
2009-10-01 22:32:28.546 Set video sync frame interval to 16683
2009-10-01 22:32:28.546 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-10-01 22:32:28.546 Set video sync frame interval to 16683
2009-10-01 22:32:28.546 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-01 22:32:28.547 VDP: GetFilteredDeint(vdpauadvanced) : vdpau -> 'vdpauadvanced'
2009-10-01 22:32:28.553 Using audio as timebase
2009-10-01 22:32:28.553 Video timing method: SGI OpenGL
2009-10-01 22:32:28.554 Refresh rate: 16684, frame interval: 16683
2009-10-01 22:32:28.570 NVP: Waiting for prebuffer..  0 (AL)AAAAAAA         
2009-10-01 22:32:28.653 NVP: Waiting for prebuffer..  1 (AL)AAAAAAA         
2009-10-01 22:32:28.737 NVP: Waiting for prebuffer..  2 (AL)AAAAAAA         
2009-10-01 22:32:28.820 NVP: Waiting for prebuffer..  3 (AL)AAAAAAA         
'video_output' mean = '18465.11', std. dev. = '17892.36', fps = '54.16'
2009-10-01 22:32:28.904 NVP: Waiting for prebuffer..  4 (AL)AAAAAAA         
2009-10-01 22:32:28.954 VideoOutputXv: UpdatePauseFrame() (AL)AAAAAAA         
2009-10-01 22:32:28.960 AFD: DoFastForward(2821 (1), do discard frames)
2009-10-01 22:32:28.961 Dec: DoFastForward(2821 (1), do discard frames)
2009-10-01 22:32:28.961 AFD: SeekReset(2820, 1, do flush, do discard)
2009-10-01 22:32:28.961 AFD: SeekReset() flushing
2009-10-01 22:32:28.961 VideoOutputXv: DiscardFrames(1)
2009-10-01 22:32:28.961 VideoBuffers::DiscardFrames(1): AAAAAAAA         
2009-10-01 22:32:28.961 VideoBuffers::DiscardFrames(): AAAAAAAA          -- done()
2009-10-01 22:32:28.961 VideoBuffers::DiscardFrames(1): AAAAAAAA          -- done
2009-10-01 22:32:28.961 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-01 22:32:29.228 VDPAU: Using 4 output surfaces (max 4)
2009-10-01 22:32:29.717 NVP: ClearAfterSeek(0)
2009-10-01 22:32:29.756 NVP: Waiting for prebuffer..  5 Aa(AL)AAAAA         
2009-10-01 22:32:29.772 NVP: progressive frame seen after 2 interlaced  frames
2009-10-01 22:32:29.808 Disabled deinterlacing
2009-10-01 22:32:29.839 NVP: prebuffering pause
2009-10-01 22:32:29.839 NVP: Waiting for prebuffer..  0 AAaAA(AL)Aa         
2009-10-01 22:32:29.959 NVP: prebuffering pause
2009-10-01 22:32:29.959 NVP: Waiting for prebuffer..  0 AAAaAA(AL)A         
2009-10-01 22:32:30.040 NVP: prebuffering pause
2009-10-01 22:32:30.040 NVP: Waiting for prebuffer..  0 AaAAAAaA         
2009-10-01 22:32:30.141 NVP: prebuffering pause
2009-10-01 22:32:30.141 NVP: Waiting for prebuffer..  0 AAAaAAaA         
2009-10-01 22:32:30.443 NVP: prebuffering pause
2009-10-01 22:32:30.443 NVP: Waiting for prebuffer..  0 (AL)aAAAaAA         
2009-10-01 22:32:30.494 NVP: prebuffering pause
2009-10-01 22:32:30.494 NVP: Waiting for prebuffer..  0 aAa(AL)AAAA         
'video_output' mean = '16681.02', std. dev. = '1260.78', fps = '59.95'
2009-10-01 22:32:30.578 NVP: prebuffering pause
2009-10-01 22:32:30.578 NVP: Waiting for prebuffer..  0 AAAaaA(AL)A         
2009-10-01 22:32:30.661 NVP: prebuffering pause
2009-10-01 22:32:30.662 NVP: Waiting for prebuffer..  0 a(AL)AAAAaA         
2009-10-01 22:32:30.761 NVP: prebuffering pause
2009-10-01 22:32:30.761 NVP: Waiting for prebuffer..  0 AAAAaAA(AL)         
2009-10-01 22:32:30.795 NVP: prebuffering pause
2009-10-01 22:32:30.795 NVP: Waiting for prebuffer..  0 AAAAaAa(AL)         
2009-10-01 22:32:30.841 NVP: prebuffering pause
2009-10-01 22:32:30.843 NVP: Waiting for prebuffer..  0 A(AL)AAAAAa         
2009-10-01 22:32:30.942 NVP: prebuffering pause
2009-10-01 22:32:30.942 NVP: Waiting for prebuffer..  0 Aa(AL)aAAAA         
2009-10-01 22:32:30.978 NVP: prebuffering pause
2009-10-01 22:32:30.978 NVP: Waiting for prebuffer..  0 AAaAA(AL)aA         
2009-10-01 22:32:31.079 NVP: prebuffering pause
2009-10-01 22:32:31.079 NVP: Waiting for prebuffer..  0 (AL)AAAAaAA         
2009-10-01 22:32:31.160 NVP: prebuffering pause
2009-10-01 22:32:31.161 NVP: Waiting for prebuffer..  0 AAAaAA(AL)A         
2009-10-01 22:32:31.262 NVP: prebuffering pause
2009-10-01 22:32:31.262 NVP: Waiting for prebuffer..  0 AaAAAAaA         
2009-10-01 22:32:31.328 NVP: prebuffering pause
2009-10-01 22:32:31.328 NVP: Waiting for prebuffer..  0 AAAA(AL)AaA         
2009-10-01 22:32:31.445 NVP: prebuffering pause
2009-10-01 22:32:31.446 NVP: Waiting for prebuffer..  0 AAaAA(AL)AA         
2009-10-01 22:32:31.496 NVP: prebuffering pause
2009-10-01 22:32:31.496 NVP: Waiting for prebuffer..  0 (AL)AAAAaAA         
2009-10-01 22:32:31.781 NVP: prebuffering pause
2009-10-01 22:32:31.781 NVP: Waiting for prebuffer..  0 AAAAaaA(AL)         
'video_output' mean = '20639.96', std. dev. = '21985.74', fps = '48.45'
2009-10-01 22:32:31.846 NVP: prebuffering pause
2009-10-01 22:32:31.846 NVP: Waiting for prebuffer..  0 A(AL)AAAAAa         
2009-10-01 22:32:31.947 NVP: prebuffering pause
2009-10-01 22:32:31.947 NVP: Waiting for prebuffer..  0 AAaAA(AL)AA         
'video_output' mean = '16681.28', std. dev. = '967.50', fps = '59.95'
2009-10-01 22:32:32.315 NVP: Changing speed to 0
2009-10-01 22:32:32.315 rate: 59.9401 speed: 1 skip: 1 = interval 16683
2009-10-01 22:32:32.315 Set video sync frame interval to 16683
2009-10-01 22:32:32.348 VideoOutputXv: UpdatePauseFrame() (au)(AU)(AU)(UL)(AU)(AU)(AU)(AU)         
2009-10-01 22:32:32.392 DPMS Reactivated.
2009-10-01 22:32:33.498 TV: Attempting to change from WatchingPreRecorded to None
2009-10-01 22:32:33.498 TV: StopStuff() -- begin
2009-10-01 22:32:33.498 TV: StopStuff(): stopping ring buffer[s]
2009-10-01 22:32:33.498 TV: StopStuff(): stopping player[s] (1/2)
2009-10-01 22:32:33.498 TV: StopStuff(): stopping player[s] (2/2)
2009-10-01 22:32:33.498 NVP: Exited decoder loop.
2009-10-01 22:32:33.513 ~OpenGLVideoSync() -- begin
2009-10-01 22:32:33.514 ~OpenGLVideoSync() -- middle
2009-10-01 22:32:33.514 ~OpenGLVideoSync() -- end
2009-10-01 22:32:33.514 VideoOutputXv: dtor
2009-10-01 22:32:33.514 VideoOutputXv: DiscardFrames(1)
2009-10-01 22:32:33.514 VideoBuffers::DiscardFrames(1): (au)(AU)(AU)(UL)(AU)(AU)(AU)(AU)         
2009-10-01 22:32:33.515 VideoBuffers::DiscardFrames(): AAAAAAAA          -- done()
2009-10-01 22:32:33.515 VideoBuffers::DiscardFrames(1): AAAAAAAA          -- done
2009-10-01 22:32:33.515 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-01 22:32:33.560 VideoOutputXv: DiscardFrames(1)
2009-10-01 22:32:33.560 VideoBuffers::DiscardFrames(1): AAAAAAAA         
2009-10-01 22:32:33.561 VideoBuffers::DiscardFrames(): AAAAAAAA          -- done()
2009-10-01 22:32:33.561 VideoBuffers::DiscardFrames(1): AAAAAAAA          -- done
2009-10-01 22:32:33.561 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-01 22:32:33.670 TV: StopStuff() -- end
2009-10-01 22:32:33.670 TV: Changing from WatchingPreRecorded to None
2009-10-01 22:32:33.755 NVP: Exited decoder loop.
2009-10-01 22:32:33.755 ~VideoOutputNull()
2009-10-01 22:32:37.367 Deleting UPnP client...


```

So it appears that VDPAU might be getting invoked .. but my CPU is still very high (I even saw 154%) when playing recorded shows, but nice and low (27%ish) watching live TV.

Ideas?

---

### Post by Crash87ss on 2009-10-02
klc5555, 
     The drive speed jumper was the first thing I checked. No jumpers so I believe that means full speed (WD documentation seems to elude but not clearly state that)

     My 8.04 setup does work, but was having trouble before the summer..frontend freezes, lirc freezes, sluggish response. But while researching this i might need to run optimze SQL to clean that up.


zymurgist,

Good to hear I'm not the only one with this issue (sorry your having this problem too zymurgist).

You point about CPU usage is interesting... I've been using mpstat to report mine at 50-60% (recorded playback), but I'm wondering if that is total or per-core?

I tried XvMC last night, at least i think i did - will have to check logs - not much effect, CPU seemed to stick to low 50% though. 

I did find that extra audio buffer & aggresive buffering do help (cuts pause frequency by about half) still get pause every 3-4 seconds

It really bugs me that this problem doesn't occur in live TV...even when time shifting. What might be different between live TV and recording playback?
My assumption was that live TV was recorded to the HDD and playback from there.. Any insight?

---

### Post by klc5555 on 2009-10-02
> **Crash87ss said:**
> klc5555, 
     The drive speed jumper was the first thing I checked. No jumpers so I believe that means full speed (WD documentation seems to elude but not clearly state that)

     My 8.04 setup does work, but was having trouble before the summer..frontend freezes, lirc freezes, sluggish response. But while researching this i might need to run optimze SQL to clean that up.


zymurgist,

Good to hear I'm not the only one with this issue (sorry your having this problem too zymurgist).

You point about CPU usage is interesting... I've been using mpstat to report mine at 50-60% (recorded playback), but I'm wondering if that is total or per-core?

I tried XvMC last night, at least i think i did - will have to check logs - not much effect, CPU seemed to stick to low 50% though. 

I did find that extra audio buffer & aggresive buffering do help (cuts pause frequency by about half) still get pause every 3-4 seconds

It really bugs me that this problem doesn't occur in live TV...even when time shifting. What might be different between live TV and recording playback?
My assumption was that live TV was recorded to the HDD and playback from there.. Any insight?

Well, it certainly looks like some kind of frontend-only problem. The main difference between watching livetv and a prerecorded show is that in the first case you're watching something that was prerecorded 5 seconds ago, rather than, say, yesterday. If you record something while watching, you could compare the frontend log from the period you're watching while recording and compare this with the frontend log from when you later watch it as a prerecorded show.

But in case your recording or playback profile is introducing something that the internal player is later finding troublesome, as an experient you might select a troublesome recording and run a lossless transcode on it. mythtranscode --mpeg2 -c  -s  (or -i) The original recording is moved to .bak, the .tmp file that mythtranscode produced (which should be a few bytes smaller than the original) is moved to the name of the original recording file, and then you see if myth's internal player has an easier time with the new transcoded copy. If the transcoded version plays correctly, then you begin to track down the offending setting in the recording/playback profiles. 

I had this happen in 7.10 (0.21 backports), where I could watch one channel in livetv, but recordings (even ones I had watched in livetv) wouldn't play at all until transcoded. In my case (yours is clearly different) I had a profile set that required XvMC, which wouldn't run on my hardware. Fixed the profile and the internal player was happy again.

If, however, your transcoded recording doesn't play any better on the internal player than the original did, then it's back to square one again looking at logs.

---

### Post by zymurgist on 2009-10-03
I agree, it appears to be front-end only.

I am playing with it more and reading the logs. 

Transcoding did not help. Here's the log:

```

:~/Desktop$ mythfrontend.real -v playback
2009-10-03 09:20:56.218 Using runtime prefix = /usr
2009-10-03 09:20:56.903 XScreenSaver support enabled
2009-10-03 09:20:56.904 DPMS is active.
2009-10-03 09:20:56.938 Empty LocalHostName.
2009-10-03 09:20:56.939 Using localhost value of MythBuntuServer
2009-10-03 09:20:57.011 New DB connection, total: 1
2009-10-03 09:20:57.069 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:57.071 Closing DB connection named 'DBManager0'
2009-10-03 09:20:57.072 Primary screen 0.
2009-10-03 09:20:57.073 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:57.074 Using screen 0, 1280x720 at 0,0
2009-10-03 09:20:57.196 user: 1000 effective user: 1000 before privileged thread
2009-10-03 09:20:57.196 user: 1000 effective user: 1000 after privileged thread
2009-10-03 09:20:57.196 user: 1000 effective user: 1000 run_priv_thread
2009-10-03 09:20:57.237 New DB connection, total: 2
2009-10-03 09:20:57.238 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:20:57.240 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-10-03 09:20:57.240 Enabled verbose msgs:  important general playback
2009-10-03 09:20:58.417 max_width: 1280 max_height: 720
2009-10-03 09:20:58.495 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-03 09:20:58.497 Primary screen 0.
2009-10-03 09:20:58.497 Using screen 0, 1280x720 at 0,0
2009-10-03 09:20:58.497 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-03 09:20:58.498 Switching to wide mode (metallurgy-wide)
2009-10-03 09:20:58.559 Using the Qt painter
2009-10-03 09:20:58.559 JoystickMenuClient Error: Joystick disabled - Failed to read /home/aasland/.mythtv/joystickmenurc
2009-10-03 09:20:58.608 lirc init success using configuration file: /home/aasland/.mythtv/lircrc
2009-10-03 09:20:59.047 Loading from: /usr/share/mythtv/themes/metallurgy-wide/base.xml
2009-10-03 09:20:59.117 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-03 09:20:59.175 Registering Internal as a media playback plugin.
2009-10-03 09:20:59.411 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-03 09:20:59.666 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-03 09:20:59.762 Starting update of NWS-XML
2009-10-03 09:20:59.770 Starting update of NDFD-6_day
2009-10-03 09:20:59.780 Starting update of NDFD-18_Hour
2009-10-03 09:20:59.794 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-03 09:21:01.809 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NWS-XML KRGK has exited
2009-10-03 09:21:01.810 wind_gust::
2009-10-03 09:21:01.810 nrecoverable error parsing script output 
2009-10-03 09:21:05.729 XMLParse::LoadTheme using /usr/share/mythtv/themes/metallurgy-wide/ui.xml
2009-10-03 09:21:06.089 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-03 09:21:06.090 Using protocol version 40
2009-10-03 09:21:07.141 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): OpenFile(/Storage/mythLiveRecordings/1091_20091002210318.mpg, 1)
2009-10-03 09:21:07.153 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046832721 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:07.459 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa0a1a00
2009-10-03 09:21:07.478 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:07.478 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:07.478 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:07.478 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 09:21:07.479 Using 4 CPUs for decoding
2009-10-03 09:21:07.479 AFD: InitVideoCodec() 0xa0b5820 id(MPEG2VIDEO) type (Video).
2009-10-03 09:21:07.479 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-03 09:21:07.479 AFD: Using ffmpeg for video decoding
2009-10-03 09:21:07.479 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 09:21:07.479 AFD: Opened codec 0xa0b5820, id(MPEG2VIDEO) type(Video)
2009-10-03 09:21:07.479 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 448000 at 0x0xa0a1c00
2009-10-03 09:21:07.481 AFD: codec AC3 has 2 channels
2009-10-03 09:21:07.481 AFD: Looking for decoder for AC3
2009-10-03 09:21:07.489 AFD: Opened codec 0xa0b5bb0, id(AC3) type(Audio)
2009-10-03 09:21:07.489 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0xa0111e0
2009-10-03 09:21:07.489 AFD: codec AC3 has 1 channels
2009-10-03 09:21:07.490 AFD: Looking for decoder for AC3
2009-10-03 09:21:07.490 AFD: Opened codec 0xa0b5f40, id(AC3) type(Audio)
2009-10-03 09:21:07.490 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:07.490 Dec: Trying to select track (w/lang)
2009-10-03 09:21:07.490 Dec: Selecting first track
2009-10-03 09:21:07.490 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:07.503 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 09:21:07.503 AFD: Successfully opened decoder for file: "/Storage/mythLiveRecordings/1091_20091002210318.mpg". novideo(0)
2009-10-03 09:21:07.505 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:07.505 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:07.505 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:07.516 VideoOutputNull()
2009-10-03 09:21:07.517 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 09:21:07.517 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:07.517 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 09:21:07.517 Created data @0xb14f7020->0xb1648822
2009-10-03 09:21:07.517 Created data @0xb13a5020->0xb14f6822
2009-10-03 09:21:07.517 Created data @0xb1253020->0xb13a4822
2009-10-03 09:21:07.517 Created data @0xb1101020->0xb1252822
2009-10-03 09:21:07.517 Created data @0xb0faf020->0xb1100822
2009-10-03 09:21:07.517 Created data @0xab9a9020->0xabafa822
2009-10-03 09:21:07.517 Created data @0xab857020->0xab9a8822
2009-10-03 09:21:07.517 Created data @0xab705020->0xab856822
2009-10-03 09:21:07.518 Created data @0xab5b3020->0xab704822
2009-10-03 09:21:07.518 Created data @0xab461020->0xab5b2822
2009-10-03 09:21:07.518 Created data @0xab30f020->0xab460822
2009-10-03 09:21:07.518 Created data @0xab1bd020->0xab30e822
2009-10-03 09:21:07.518 Created data @0xab06b020->0xab1bc822
2009-10-03 09:21:07.518 Created data @0xaaf19020->0xab06a822
2009-10-03 09:21:07.518 Created data @0xaadc7020->0xaaf18822
2009-10-03 09:21:07.518 Created data @0xaac75020->0xaadc6822
2009-10-03 09:21:07.518 Created data @0xaab23020->0xaac74822
2009-10-03 09:21:07.518 Created data @0xaa9d1020->0xaab22822
2009-10-03 09:21:07.518 Created data @0xaa87f020->0xaa9d0822
2009-10-03 09:21:07.518 Created data @0xaa72d020->0xaa87e822
2009-10-03 09:21:07.518 Created data @0xaa5db020->0xaa72c822
2009-10-03 09:21:07.518 Created data @0xaa489020->0xaa5da822
2009-10-03 09:21:07.518 Created data @0xaa337020->0xaa488822
2009-10-03 09:21:07.519 Created data @0xaa1e5020->0xaa336822
2009-10-03 09:21:07.519 Created data @0xaa093020->0xaa1e4822
2009-10-03 09:21:07.519 Created data @0xa9f41020->0xaa092822
2009-10-03 09:21:07.519 Created data @0xa9def020->0xa9f40822
2009-10-03 09:21:07.519 Created data @0xa9c9d020->0xa9dee822
2009-10-03 09:21:07.519 Created data @0xa9b4b020->0xa9c9c822
2009-10-03 09:21:07.519 Created data @0xa99f9020->0xa9b4a822
2009-10-03 09:21:07.519 Created data @0xa98a7020->0xa99f8822
2009-10-03 09:21:07.519 Created data @0xa9755020->0xa98a6822
[COLOR="Red"][B]2009-10-03 09:21:07.586 VDP: SetVideoRenderer(null)
2009-10-03 09:21:07.586 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:07.586 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
[/B][/COLOR]2009-10-03 09:21:07.587 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:07.587 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 09:21:07.588 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:07.588 NVP: ClearAfterSeek(1)
2009-10-03 09:21:07.589 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:07.630 NVP: Exited decoder loop.
2009-10-03 09:21:07.655 ~VideoOutputNull()
2009-10-03 09:21:07.914 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): OpenFile(/Storage/mythLiveRecordings/1091_20091002210318.mpg, 1)
2009-10-03 09:21:07.914 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(2985354376 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:08.073 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa1199c0
[COLOR="Red"][B]2009-10-03 09:21:08.074 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:08.074 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:08.074 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:08.075 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 09:21:08.075 Using 4 CPUs for decoding
2009-10-03 09:21:08.075 AFD: InitVideoCodec() 0xa0bb400 id(MPEG2VIDEO) type (Video).
2009-10-03 09:21:08.075 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-03 09:21:08.075 AFD: Using ffmpeg for video decoding
2009-10-03 09:21:08.075 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 09:21:08.075 AFD: Opened codec 0xa0bb400, id(MPEG2VIDEO) type(Video)
[/B][/COLOR]2009-10-03 09:21:08.075 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 448000 at 0x0xa114bd0
2009-10-03 09:21:08.075 AFD: codec AC3 has 2 channels
2009-10-03 09:21:08.075 AFD: Looking for decoder for AC3
2009-10-03 09:21:08.076 AFD: Opened codec 0xa0b9f20, id(AC3) type(Audio)
2009-10-03 09:21:08.076 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0xa114920
2009-10-03 09:21:08.076 AFD: codec AC3 has 1 channels
2009-10-03 09:21:08.076 AFD: Looking for decoder for AC3
2009-10-03 09:21:08.076 AFD: Opened codec 0xa119bf0, id(AC3) type(Audio)
2009-10-03 09:21:08.076 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:08.077 Dec: Trying to select track (w/lang)
2009-10-03 09:21:08.077 Dec: Selecting first track
2009-10-03 09:21:08.077 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:08.077 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 09:21:08.077 AFD: Successfully opened decoder for file: "/Storage/mythLiveRecordings/1091_20091002210318.mpg". novideo(0)
2009-10-03 09:21:08.078 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:08.078 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:08.078 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:08.082 VideoOutputNull()
2009-10-03 09:21:08.082 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 09:21:08.082 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:08.082 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 09:21:08.082 Created data @0xb14f7020->0xb1648822
2009-10-03 09:21:08.082 Created data @0xb13a5020->0xb14f6822
2009-10-03 09:21:08.082 Created data @0xb1253020->0xb13a4822
2009-10-03 09:21:08.082 Created data @0xb1101020->0xb1252822
2009-10-03 09:21:08.082 Created data @0xb0faf020->0xb1100822
2009-10-03 09:21:08.082 Created data @0xab9a9020->0xabafa822
2009-10-03 09:21:08.082 Created data @0xab857020->0xab9a8822
2009-10-03 09:21:08.082 Created data @0xab705020->0xab856822
2009-10-03 09:21:08.083 Created data @0xab5b3020->0xab704822
2009-10-03 09:21:08.083 Created data @0xab461020->0xab5b2822
2009-10-03 09:21:08.083 Created data @0xab30f020->0xab460822
2009-10-03 09:21:08.083 Created data @0xab1bd020->0xab30e822
2009-10-03 09:21:08.083 Created data @0xab06b020->0xab1bc822
2009-10-03 09:21:08.083 Created data @0xaaf19020->0xab06a822
2009-10-03 09:21:08.083 Created data @0xaadc7020->0xaaf18822
2009-10-03 09:21:08.083 Created data @0xaac75020->0xaadc6822
2009-10-03 09:21:08.083 Created data @0xaab23020->0xaac74822
2009-10-03 09:21:08.083 Created data @0xaa9d1020->0xaab22822
2009-10-03 09:21:08.083 Created data @0xaa87f020->0xaa9d0822
2009-10-03 09:21:08.083 Created data @0xaa72d020->0xaa87e822
2009-10-03 09:21:08.083 Created data @0xaa5db020->0xaa72c822
2009-10-03 09:21:08.083 Created data @0xaa489020->0xaa5da822
2009-10-03 09:21:08.084 Created data @0xaa337020->0xaa488822
2009-10-03 09:21:08.084 Created data @0xaa1e5020->0xaa336822
2009-10-03 09:21:08.084 Created data @0xaa093020->0xaa1e4822
2009-10-03 09:21:08.084 Created data @0xa9f41020->0xaa092822
2009-10-03 09:21:08.084 Created data @0xa9def020->0xa9f40822
2009-10-03 09:21:08.084 Created data @0xa9c9d020->0xa9dee822
2009-10-03 09:21:08.084 Created data @0xa9b4b020->0xa9c9c822
2009-10-03 09:21:08.084 Created data @0xa99f9020->0xa9b4a822
2009-10-03 09:21:08.084 Created data @0xa98a7020->0xa99f8822
2009-10-03 09:21:08.084 Created data @0xa9755020->0xa98a6822
[COLOR="Red"][B]2009-10-03 09:21:08.147 VDP: SetVideoRenderer(null)
2009-10-03 09:21:08.147 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:08.147 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
[/B][/COLOR]2009-10-03 09:21:08.147 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:08.147 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 09:21:08.147 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:08.147 NVP: ClearAfterSeek(1)
2009-10-03 09:21:08.148 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:08.168 NVP: Exited decoder loop.
2009-10-03 09:21:08.214 ~VideoOutputNull()
2009-10-03 09:21:08.523 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NDFD-18_Hour +44.35,-092.29 has exited
2009-10-03 09:21:10.440 Starting preview generator 1 && (0 || ((2009-09-26T14:50:57<2009-10-03T09:12:55)->1 && (2009-09-26T14:50:57>=2009-09-26T14:00:00)->1)) && 1 && 1 && 1
2009-10-03 09:21:10.677 Using runtime prefix = /usr
2009-10-03 09:21:10.678 Empty LocalHostName.
2009-10-03 09:21:10.678 Using localhost value of MythBuntuServer
2009-10-03 09:21:10.691 New DB connection, total: 1
2009-10-03 09:21:10.697 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:21:10.698 Closing DB connection named 'DBManager0'
2009-10-03 09:21:10.699 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:21:10.700 New DB connection, total: 2
2009-10-03 09:21:10.701 Connected to database 'mythconverg' at host: localhost
2009-10-03 09:21:10.712 Current Schema Version: 1214
2009-10-03 09:21:10.861 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NDFD-6_day +44.35,-092.29 has exited
2009-10-03 09:21:10.947 RingBuf(myth://127.0.0.1:6543/1021_20090926133000.mpg): OpenFile(myth://127.0.0.1:6543/1021_20090926133000.mpg, 1)
2009-10-03 09:21:10.953 RingBuf(myth://127.0.0.1:6543/1021_20090926133000.mpg): CalcReadAheadThresh(3046832721 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:13.282 AFD: Opened codec 0x9737530, id(MPEG2VIDEO) type(Video)
2009-10-03 09:21:13.282 AFD: codec AC3 has 2 channels
2009-10-03 09:21:13.283 AFD: Opened codec 0x97378c0, id(AC3) type(Audio)
2009-10-03 09:21:13.283 AFD: codec AC3 has 6 channels
2009-10-03 09:21:13.283 AFD: Opened codec 0x97384d0, id(AC3) type(Audio)
2009-10-03 09:21:13.684 Preview: Grabbed preview '/Storage/mythTVRecordings/1021_20090926133000.mpg' 1920x1088@124s
2009-10-03 09:21:13.744 AFD: Stream #0, has id 0x480 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa1199c0
[COLOR="Red"][B]2009-10-03 09:21:13.745 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:13.745 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:13.745 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:13.745 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:13.745 Using 4 CPUs for decoding
2009-10-03 09:21:13.745 AFD: InitVideoCodec() 0xa0bb400 id(MPEG2VIDEO) type (Video).
2009-10-03 09:21:13.746 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 09:21:13.746 AFD: Using ffmpeg for video decoding
2009-10-03 09:21:13.746 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 09:21:13.746 AFD: Opened codec 0xa0bb400, id(MPEG2VIDEO) type(Video)
[/B][/COLOR]2009-10-03 09:21:13.746 AFD: Stream #1, has id 0x129 codec id AC3, type Audio, bitrate 192000 at 0x0xa114bd0
2009-10-03 09:21:13.746 AFD: codec AC3 has 2 channels
2009-10-03 09:21:13.746 AFD: Looking for decoder for AC3
2009-10-03 09:21:13.746 AFD: Opened codec 0xa0b9f20, id(AC3) type(Audio)
2009-10-03 09:21:13.747 AFD: Stream #2, has id 0x128 codec id AC3, type Audio, bitrate 384000 at 0x0xa0ec350
2009-10-03 09:21:13.747 AFD: codec AC3 has 6 channels
2009-10-03 09:21:13.747 AFD: Looking for decoder for AC3
2009-10-03 09:21:13.747 AFD: Opened codec 0xa119bf0, id(AC3) type(Audio)
2009-10-03 09:21:13.747 RingBuf(myth://127.0.0.1:6543/1021_20090926133000.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:13.747 Dec: Trying to select track (w/lang)
2009-10-03 09:21:13.747 Dec: Selecting first track
2009-10-03 09:21:13.747 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:13.747 AFD: Recording has no position -- using libavformat seeking.
[COLOR="Red"][B]2009-10-03 09:21:13.748 AFD: Successfully opened decoder for file: "myth://127.0.0.1:6543/1021_20090926133000.mpg". novideo(0)
2009-10-03 09:21:13.749 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:13.749 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:13.749 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:13.752 VideoOutputNull()
2009-10-03 09:21:13.752 VDP: LoadBestPreferences(1920x1088, 60)
[/B][/COLOR]2009-10-03 09:21:13.752 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:13.752 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:13.753 Created data @0xb1002020->0xb12ff022
2009-10-03 09:21:13.753 Created data @0xaaffc020->0xab2f9022
2009-10-03 09:21:13.753 Created data @0xaacfe020->0xaaffb022
2009-10-03 09:21:13.753 Created data @0xaaa00020->0xaacfd022
2009-10-03 09:21:13.753 Created data @0xaa702020->0xaa9ff022
2009-10-03 09:21:13.753 Created data @0xaa404020->0xaa701022
2009-10-03 09:21:13.753 Created data @0xaa106020->0xaa403022
2009-10-03 09:21:13.753 Created data @0xa9e08020->0xaa105022
2009-10-03 09:21:13.753 Created data @0xa9b0a020->0xa9e07022
2009-10-03 09:21:13.753 Created data @0xa980c020->0xa9b09022
2009-10-03 09:21:13.753 Created data @0xa950e020->0xa980b022
2009-10-03 09:21:13.753 Created data @0xa9210020->0xa950d022
2009-10-03 09:21:13.753 Created data @0xa8f12020->0xa920f022
2009-10-03 09:21:13.754 Created data @0xa8c14020->0xa8f11022
2009-10-03 09:21:13.754 Created data @0xa8916020->0xa8c13022
2009-10-03 09:21:13.754 Created data @0xa8618020->0xa8915022
2009-10-03 09:21:13.754 Created data @0xa831a020->0xa8617022
2009-10-03 09:21:13.754 Created data @0xa801c020->0xa8319022
2009-10-03 09:21:13.754 Created data @0xa7d1e020->0xa801b022
2009-10-03 09:21:13.754 Created data @0xa7a20020->0xa7d1d022
2009-10-03 09:21:13.754 Created data @0xa7722020->0xa7a1f022
2009-10-03 09:21:13.754 Created data @0xa7424020->0xa7721022
2009-10-03 09:21:13.754 Created data @0xa7126020->0xa7423022
2009-10-03 09:21:13.754 Created data @0xa6e28020->0xa7125022
2009-10-03 09:21:13.754 Created data @0xa6b2a020->0xa6e27022
2009-10-03 09:21:13.754 Created data @0xa682c020->0xa6b29022
2009-10-03 09:21:13.754 Created data @0xa652e020->0xa682b022
2009-10-03 09:21:13.754 Created data @0xa6230020->0xa652d022
2009-10-03 09:21:13.755 Created data @0xa5f32020->0xa622f022
2009-10-03 09:21:13.755 Created data @0xa5c34020->0xa5f31022
2009-10-03 09:21:13.755 Created data @0xa5936020->0xa5c33022
2009-10-03 09:21:13.755 Created data @0xa5638020->0xa5935022
2009-10-03 09:21:13.902 Preview: Preview process returned 0.
2009-10-03 09:21:13.903 Preview: Preview process ran ok.
2009-10-03 09:21:13.908 Preview: previewThreadDone took 5ms
[COLOR="Red"][B]2009-10-03 09:21:13.939 VDP: SetVideoRenderer(null)
2009-10-03 09:21:13.939 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:13.939 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
[/B][/COLOR]2009-10-03 09:21:13.939 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:13.940 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:13.940 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:13.940 NVP: ClearAfterSeek(1)
2009-10-03 09:21:13.940 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:14.074 NVP: Waiting for prebuffer..  1 UUuLAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:14.207 NVP: Waiting for prebuffer..  2 UUUUUUUULLAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:14.912 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-10-03 09:21:14.912 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-03 09:21:14.912 AFD: HandleGopStart: Initial key frame distance: 15.
2009-10-03 09:21:14.956 NVP: Exited decoder loop.
2009-10-03 09:21:14.983 ~VideoOutputNull()
2009-10-03 09:21:15.058 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): OpenFile(/Storage/mythTVRecordings/1021_20090926133000.mpg, 1)
2009-10-03 09:21:15.058 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(2985610456 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:16.054 TV: Attempting to change from None to WatchingPreRecorded
2009-10-03 09:21:16.055 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): OpenFile(/Storage/mythTVRecordings/1021_20090926133000.mpg, 12)
2009-10-03 09:21:16.055 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(168465904 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:16.148 DPMS Deactivated 
2009-10-03 09:21:17.542 AFD: Stream #0, has id 0x480 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa1199c0
2009-10-03 09:21:17.543 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:17.543 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:17.543 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:17.543 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:17.543 Using 4 CPUs for decoding
2009-10-03 09:21:17.543 AFD: InitVideoCodec() 0xa0b9f20 id(MPEG2VIDEO) type (Video).
2009-10-03 09:21:17.544 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 09:21:17.544 AFD: Using ffmpeg for video decoding
2009-10-03 09:21:17.544 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 09:21:17.544 AFD: Opened codec 0xa0b9f20, id(MPEG2VIDEO) type(Video)
2009-10-03 09:21:17.544 AFD: Stream #1, has id 0x129 codec id AC3, type Audio, bitrate 192000 at 0x0xa114bd0
2009-10-03 09:21:17.544 AFD: codec AC3 has 2 channels
2009-10-03 09:21:17.544 AFD: Looking for decoder for AC3
2009-10-03 09:21:17.544 AFD: Opened codec 0xa119bf0, id(AC3) type(Audio)
2009-10-03 09:21:17.544 AFD: Stream #2, has id 0x128 codec id AC3, type Audio, bitrate 384000 at 0x0xa0bac40
2009-10-03 09:21:17.544 AFD: codec AC3 has 6 channels
2009-10-03 09:21:17.545 AFD: Looking for decoder for AC3
2009-10-03 09:21:17.545 AFD: Opened codec 0xa10af80, id(AC3) type(Audio)
2009-10-03 09:21:17.545 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:17.545 Dec: Trying to select track (w/lang)
2009-10-03 09:21:17.545 Dec: Selecting first track
2009-10-03 09:21:17.545 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:17.545 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 09:21:17.545 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20090926133000.mpg". novideo(0)
2009-10-03 09:21:17.547 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:17.547 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:17.547 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:17.550 VideoOutputNull()
2009-10-03 09:21:17.550 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 09:21:17.550 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:17.550 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:17.550 Created data @0xa9ffa020->0xaa2f7022
2009-10-03 09:21:17.551 Created data @0xa9cfc020->0xa9ff9022
2009-10-03 09:21:17.551 Created data @0xa99fe020->0xa9cfb022
2009-10-03 09:21:17.551 Created data @0xa9700020->0xa99fd022
2009-10-03 09:21:17.551 Created data @0xa9402020->0xa96ff022
2009-10-03 09:21:17.551 Created data @0xa9104020->0xa9401022
2009-10-03 09:21:17.551 Created data @0xa8e06020->0xa9103022
2009-10-03 09:21:17.551 Created data @0xa8b08020->0xa8e05022
2009-10-03 09:21:17.551 Created data @0xa880a020->0xa8b07022
2009-10-03 09:21:17.551 Created data @0xa850c020->0xa8809022
2009-10-03 09:21:17.551 Created data @0xa820e020->0xa850b022
2009-10-03 09:21:17.551 Created data @0xa7f10020->0xa820d022
2009-10-03 09:21:17.551 Created data @0xa7c12020->0xa7f0f022
2009-10-03 09:21:17.551 Created data @0xa7914020->0xa7c11022
2009-10-03 09:21:17.551 Created data @0xa7616020->0xa7913022
2009-10-03 09:21:17.552 Created data @0xa7318020->0xa7615022
2009-10-03 09:21:17.552 Created data @0xa701a020->0xa7317022
2009-10-03 09:21:17.552 Created data @0xa6d1c020->0xa7019022
2009-10-03 09:21:17.552 Created data @0xa6a1e020->0xa6d1b022
2009-10-03 09:21:17.552 Created data @0xa6720020->0xa6a1d022
2009-10-03 09:21:17.552 Created data @0xa6422020->0xa671f022
2009-10-03 09:21:17.552 Created data @0xa6124020->0xa6421022
2009-10-03 09:21:17.552 Created data @0xa5e26020->0xa6123022
2009-10-03 09:21:17.552 Created data @0xa5b28020->0xa5e25022
2009-10-03 09:21:17.552 Created data @0xa582a020->0xa5b27022
2009-10-03 09:21:17.552 Created data @0xa552c020->0xa5829022
2009-10-03 09:21:17.552 Created data @0xa4d02020->0xa4fff022
2009-10-03 09:21:17.552 Created data @0xa4a04020->0xa4d01022
2009-10-03 09:21:17.552 Created data @0xa4706020->0xa4a03022
2009-10-03 09:21:17.552 Created data @0xa4408020->0xa4705022
2009-10-03 09:21:17.553 Created data @0xa410a020->0xa4407022
2009-10-03 09:21:17.553 Created data @0xa3e0c020->0xa4109022
2009-10-03 09:21:17.691 VDP: SetVideoRenderer(null)
2009-10-03 09:21:17.691 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:17.692 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 09:21:17.692 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:17.692 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:17.692 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:17.692 NVP: ClearAfterSeek(1)
2009-10-03 09:21:17.692 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:17.794 NVP: Exited decoder loop.
2009-10-03 09:21:17.825 ~VideoOutputNull()
2009-10-03 09:21:17.867 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): OpenFile(/Storage/mythTVRecordings/1021_20090926133000.mpg, 1)
2009-10-03 09:21:17.867 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(3047809488 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:18.570 AFD: Stream #0, has id 0x480 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa1089c0
2009-10-03 09:21:18.572 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:18.572 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:18.572 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:18.573 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:18.941 VDPAU: Version 0
2009-10-03 09:21:18.941 VDPAU: Information NVIDIA VDPAU Driver Shared Library  185.18.36  Fri Aug 14 17:50:51 PDT 2009
2009-10-03 09:21:18.986 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:18.986 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:18.986 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:18.986 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:18.987 Using 1 CPUs for decoding
2009-10-03 09:21:18.987 AFD: InitVideoCodec() 0xa108b50 id(MPEGVIDEO_VDPAU) type (Video).
2009-10-03 09:21:18.987 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 09:21:18.987 AFD: Using vdpau for video decoding
2009-10-03 09:21:18.987 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-03 09:21:18.987 AFD: Opened codec 0xa108b50, id(MPEGVIDEO_VDPAU) type(Video)
2009-10-03 09:21:18.987 AFD: Stream #1, has id 0x129 codec id AC3, type Audio, bitrate 192000 at 0x0xa108ee0
2009-10-03 09:21:18.987 AFD: codec AC3 has 2 channels
2009-10-03 09:21:18.987 AFD: Looking for decoder for AC3
2009-10-03 09:21:18.988 AFD: Opened codec 0xa109070, id(AC3) type(Audio)
2009-10-03 09:21:18.988 AFD: Stream #2, has id 0x128 codec id AC3, type Audio, bitrate 384000 at 0x0xa109890
2009-10-03 09:21:18.988 AFD: codec AC3 has 6 channels
2009-10-03 09:21:18.988 AFD: Looking for decoder for AC3
2009-10-03 09:21:18.988 AFD: Opened codec 0xa109a30, id(AC3) type(Audio)
2009-10-03 09:21:18.988 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:19.004 Opening audio device 'default'. ch 2(2) sr 48000
2009-10-03 09:21:19.004 Opening ALSA audio device 'default'.
2009-10-03 09:21:19.074 Mixer unable to find control Master
2009-10-03 09:21:19.074 Mixer unable to find control Master
2009-10-03 09:21:19.075 Mixer unable to find control PCM
2009-10-03 09:21:19.075 Mixer unable to find control PCM
2009-10-03 09:21:19.075 Mixer unable to find control PCM
2009-10-03 09:21:19.076 Dec: Trying to select track (w/lang)
2009-10-03 09:21:19.076 Dec: Selecting first track
2009-10-03 09:21:19.076 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:19.076 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-03 09:21:19.093 Position map filled from DB to: 53693
2009-10-03 09:21:19.094 SyncPositionMap prerecorded, from DB: 1677 entries
2009-10-03 09:21:19.094 SyncPositionMap, new totframes: 53693, new length: 1791, posMap size: 1677
2009-10-03 09:21:19.094 AFD: Position map found
2009-10-03 09:21:19.094 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20090926133000.mpg". novideo(0)
2009-10-03 09:21:19.446 VideoOutput: Allowed renderers: vdpau
2009-10-03 09:21:19.447 VideoOutput: Allowed renderers (filt: vdpau): vdpau
2009-10-03 09:21:19.448 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:19.448 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:19.448 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:19.448 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:19.448 VideoOutput: Preferred renderer: vdpau
2009-10-03 09:21:19.448 VideoOutput: Trying video renderer: vdpau
2009-10-03 09:21:19.450 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:19.450 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:19.450 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:19.453 VideoOutputXv: ctor
2009-10-03 09:21:19.474 XOff: 0, YOff: 0
2009-10-03 09:21:19.475 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 09:21:19.475 Display Rect  left: 0, top: 90, width: 1280, height: 540, aspect: 1.33333
2009-10-03 09:21:19.475 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:19.476 VideoOutputXv: Pixel dimensions: Screen 1280x720, window 1280x720
2009-10-03 09:21:19.477 VideoOutputXv: Estimated display dimensions: 325x183 mm  Aspect: 1.77596
2009-10-03 09:21:19.477 VideoOutputXv: Estimated window dimensions: 325x183 mm  Aspect: 1.77596
2009-10-03 09:21:19.817 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: vdpau
2009-10-03 09:21:20.086 VideoOutputXv: Created VDPAU context (GPU decode)
2009-10-03 09:21:20.086 VDP: SetVideoRenderer(vdpau)
2009-10-03 09:21:20.086 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-10-03 09:21:20.090 VDPAU: Created OSD (1280x720)
2009-10-03 09:21:20.090 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-03 09:21:20.091 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 09:21:20.091 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:20.093 Over/underscan. V: 0, H: 0
2009-10-03 09:21:20.093 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 09:21:20.093 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:20.094 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-10-03 09:21:20.094 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:20.098 OSD Theme Dimensions W: 1280 H: 720
2009-10-03 09:21:20.349 AFD: Stream #0, has id 0x480 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa406970
2009-10-03 09:21:20.351 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:20.351 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:20.351 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:20.351 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:20.351 Using 4 CPUs for decoding
2009-10-03 09:21:20.351 AFD: InitVideoCodec() 0xa406b00 id(MPEG2VIDEO) type (Video).
2009-10-03 09:21:20.352 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 09:21:20.352 AFD: Using ffmpeg for video decoding
2009-10-03 09:21:20.352 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 09:21:20.352 AFD: Opened codec 0xa406b00, id(MPEG2VIDEO) type(Video)
2009-10-03 09:21:20.352 AFD: Stream #1, has id 0x129 codec id AC3, type Audio, bitrate 192000 at 0x0xa406e90
2009-10-03 09:21:20.352 AFD: codec AC3 has 2 channels
2009-10-03 09:21:20.352 AFD: Looking for decoder for AC3
2009-10-03 09:21:20.353 AFD: Opened codec 0xa407030, id(AC3) type(Audio)
2009-10-03 09:21:20.353 AFD: Stream #2, has id 0x128 codec id AC3, type Audio, bitrate 384000 at 0x0xa407840
2009-10-03 09:21:20.353 AFD: codec AC3 has 6 channels
2009-10-03 09:21:20.353 AFD: Looking for decoder for AC3
2009-10-03 09:21:20.353 AFD: Opened codec 0xa4079e0, id(AC3) type(Audio)
2009-10-03 09:21:20.354 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:20.354 Dec: Trying to select track (w/lang)
2009-10-03 09:21:20.354 Dec: Selecting first track
2009-10-03 09:21:20.354 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:20.354 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 09:21:20.354 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20090926133000.mpg". novideo(0)
2009-10-03 09:21:20.356 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:20.356 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:20.356 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:20.362 VideoOutputNull()
2009-10-03 09:21:20.362 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 09:21:20.362 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:20.362 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:20.362 Created data @0xa868f020->0xa898c022
2009-10-03 09:21:20.364 Created data @0xa8391020->0xa868e022
2009-10-03 09:21:20.364 Created data @0xa8093020->0xa8390022
2009-10-03 09:21:20.364 Created data @0xa7d95020->0xa8092022
2009-10-03 09:21:20.365 Created data @0xa7a97020->0xa7d94022
2009-10-03 09:21:20.365 Created data @0xa7799020->0xa7a96022
2009-10-03 09:21:20.365 Created data @0xa749b020->0xa7798022
2009-10-03 09:21:20.365 Created data @0xa719d020->0xa749a022
2009-10-03 09:21:20.365 Created data @0xa6e9f020->0xa719c022
2009-10-03 09:21:20.365 Created data @0xa6ba1020->0xa6e9e022
2009-10-03 09:21:20.365 Created data @0xa68a3020->0xa6ba0022
2009-10-03 09:21:20.365 Created data @0xa65a5020->0xa68a2022
2009-10-03 09:21:20.366 Created data @0xa62a7020->0xa65a4022
2009-10-03 09:21:20.366 Created data @0xa5fa9020->0xa62a6022
2009-10-03 09:21:20.366 Created data @0xa5cab020->0xa5fa8022
2009-10-03 09:21:20.366 Created data @0xa59ad020->0xa5caa022
2009-10-03 09:21:20.366 Created data @0xa56af020->0xa59ac022
2009-10-03 09:21:20.366 Created data @0xa53b1020->0xa56ae022
2009-10-03 09:21:20.366 Created data @0xa4f02020->0xa51ff022
2009-10-03 09:21:20.367 Created data @0xa4c04020->0xa4f01022
2009-10-03 09:21:20.367 Created data @0xa4906020->0xa4c03022
2009-10-03 09:21:20.367 Created data @0xa4608020->0xa4905022
2009-10-03 09:21:20.367 Created data @0xa430a020->0xa4607022
2009-10-03 09:21:20.367 Created data @0xa400c020->0xa4309022
2009-10-03 09:21:20.367 Created data @0xa3d0e020->0xa400b022
2009-10-03 09:21:20.367 Created data @0xa3a10020->0xa3d0d022
2009-10-03 09:21:20.367 Created data @0xa3712020->0xa3a0f022
2009-10-03 09:21:20.368 Created data @0xa3414020->0xa3711022
2009-10-03 09:21:20.368 Created data @0xa3116020->0xa3413022
2009-10-03 09:21:20.368 Created data @0xa2e18020->0xa3115022
2009-10-03 09:21:20.368 Created data @0xa2b1a020->0xa2e17022
2009-10-03 09:21:20.368 Created data @0xa281c020->0xa2b19022
2009-10-03 09:21:20.660 VDP: SetVideoRenderer(null)
2009-10-03 09:21:20.660 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:20.661 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 09:21:20.661 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:20.661 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:20.661 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:20.661 NVP: ClearAfterSeek(1)
2009-10-03 09:21:20.664 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:20.753 TV: StartPlayer(): took 4687 ms to start player.
2009-10-03 09:21:20.755 TV: Changing from None to WatchingPreRecorded
2009-10-03 09:21:20.755 NVP: ClearAfterSeek(1)
2009-10-03 09:21:20.755 VideoOutputXv: ClearAfterSeek()
2009-10-03 09:21:20.755 VideoOutputXv: DiscardFrames(0)
2009-10-03 09:21:20.756 VideoBuffers::DiscardFrames(0): AAAAAAAA         
2009-10-03 09:21:20.756 VideoBuffers::DiscardFrames(0): AAAAAAAA          -- done
2009-10-03 09:21:20.756 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-03 09:21:20.757 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-03 09:21:20.759 Realtime priority would require SUID as root.
2009-10-03 09:21:20.797 NVP: Waiting for prebuffer..  1 ULLAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:20.860 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-10-03 09:21:20.860 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-10-03 09:21:20.860 OpenGLVideoSync()
2009-10-03 09:21:20.865 OpenGLVideoSync: x,y -> 640, 360
2009-10-03 09:21:20.882 VDPAU: Created VDPAU decoder (2 ref frames)
2009-10-03 09:21:20.931 NVP: Waiting for prebuffer..  2 UUULLAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:20.966 Using OpenGLVideoSync
2009-10-03 09:21:20.966 Set video sync frame interval to 33366
2009-10-03 09:21:20.971 Using audio as timebase
2009-10-03 09:21:20.971 Video timing method: SGI OpenGL
2009-10-03 09:21:20.972 Refresh rate: 16684, frame interval: 33366
2009-10-03 09:21:20.990 NVP: Waiting for prebuffer..  0 AAAAAAAA         
2009-10-03 09:21:21.064 NVP: Waiting for prebuffer..  3 UUUUUUULLAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:21.105 VideoOutputXv: UpdatePauseFrame() (AL)AAAAAAA         
2009-10-03 09:21:21.110 AFD: DoFastForward(1967 (1), do discard frames)
2009-10-03 09:21:21.110 Dec: DoFastForward(1967 (1), do discard frames)
2009-10-03 09:21:21.110 AFD: SeekReset(1946, 21, do flush, do discard)
2009-10-03 09:21:21.110 AFD: SeekReset() flushing
2009-10-03 09:21:21.110 VideoOutputXv: DiscardFrames(1)
2009-10-03 09:21:21.110 VideoBuffers::DiscardFrames(1): AAAAAAAA         
2009-10-03 09:21:21.111 VideoBuffers::DiscardFrames(): AAAAAAAA          -- done()
2009-10-03 09:21:21.111 VideoBuffers::DiscardFrames(1): AAAAAAAA          -- done
2009-10-03 09:21:21.111 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-03 09:21:21.197 NVP: Waiting for prebuffer..  4 UUUUUUUUULUULAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:21.479 VDPAU: Using 4 output surfaces (max 4)
2009-10-03 09:21:21.729 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-10-03 09:21:21.729 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-03 09:21:21.729 AFD: HandleGopStart: Initial key frame distance: 15.
2009-10-03 09:21:21.973 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:22.007 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:22.220 NVP: ClearAfterSeek(0)
2009-10-03 09:21:22.257 NVP: Waiting for prebuffer..  1 AAAAa(AL)AA         
2009-10-03 09:21:22.464 NVP: prebuffering pause
2009-10-03 09:21:22.464 NVP: Waiting for prebuffer..  0 A(ad)(AL)AAA(AD)(AD)         
2009-10-03 09:21:22.464 WriteAudio: buffer underrun
2009-10-03 09:21:22.467 AFD: HandleGopStart: Key frame distance changed from 37 to 25.
2009-10-03 09:21:22.560 AFD: HandleGopStart: Key frame distance changed from 25 to 4.
2009-10-03 09:21:22.616 NVP: Waiting for prebuffer..  1 (AL)(AD)(au)AAA(AD)(AD)         
2009-10-03 09:21:22.867 NVP: prebuffering pause
2009-10-03 09:21:22.867 NVP: Waiting for prebuffer..  0 (AD)AA(AL)(AD)(ad)AA         
2009-10-03 09:21:22.867 WriteAudio: buffer underrun
2009-10-03 09:21:23.011 NVP: Waiting for prebuffer..  1 (AD)AA(AL)(AD)(AD)A(AL)         
2009-10-03 09:21:23.092 NVP: prebuffering pause
2009-10-03 09:21:23.092 NVP: Waiting for prebuffer..  0 AAA(ad)(AD)(AD)A(AL)         
2009-10-03 09:21:23.404 AFD: HandleGopStart: Key frame distance changed from 4 to 27.
2009-10-03 09:21:23.505 NVP: Video is 4.31023 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:23.505 NVP: Video is 4.60382 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:23.505 NVP: Video is 4.57675 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:23.505 NVP: Video is 4.30171 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:23.628 WriteAudio: buffer underrun
2009-10-03 09:21:23.706 NVP: Video is 4.18027 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:23.706 NVP: Video is 4.07927 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:23.750 WriteAudio: buffer underrun
2009-10-03 09:21:23.850 WriteAudio: buffer underrun
2009-10-03 09:21:23.921 WriteAudio: buffer underrun
2009-10-03 09:21:23.990 WriteAudio: buffer underrun
2009-10-03 09:21:24.054 NVP: Video is 4.15579 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:24.054 NVP: Video is 4.12084 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:24.132 WriteAudio: buffer underrun
2009-10-03 09:21:24.192 NVP: Video is 4.08976 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:24.193 NVP: prebuffering pause
2009-10-03 09:21:24.193 NVP: Waiting for prebuffer..  0 A(AL)AAA(AD)DA         
2009-10-03 09:21:24.200 AFD: HandleGopStart: Key frame distance changed from 27 to 15.
2009-10-03 09:21:24.245 NVP: Video is 4.0039 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:24.245 NVP: prebuffering pause
2009-10-03 09:21:24.245 NVP: Waiting for prebuffer..  0 (AL)A(AL)AA(AD)DA         
'video_output' mean = '33364.06', std. dev. = '1224.18', fps = '29.97'
2009-10-03 09:21:24.554 AFD: HandleGopStart: Key frame distance changed from 15 to 9.
2009-10-03 09:21:24.650 WriteAudio: buffer underrun
2009-10-03 09:21:24.699 WriteAudio: buffer underrun
2009-10-03 09:21:24.859 NVP: prebuffering pause
2009-10-03 09:21:24.859 NVP: Waiting for prebuffer..  0 AA(AD)(dl)A(AD)AA         
2009-10-03 09:21:24.861 WriteAudio: buffer underrun
2009-10-03 09:21:24.996 NVP: Waiting for prebuffer..  1 AA(AD)(dl)A(AD)AA         
2009-10-03 09:21:25.479 AFD: HandleGopStart: Key frame distance changed from 9 to 29.
2009-10-03 09:21:25.496 NVP: prebuffering pause
2009-10-03 09:21:25.496 NVP: Waiting for prebuffer..  0 (AD)(ad)AAAA(AL)A         
2009-10-03 09:21:25.496 WriteAudio: buffer underrun
2009-10-03 09:21:25.649 NVP: Waiting for prebuffer..  1 (AD)(AD)AAA(AL)(au)A         
2009-10-03 09:21:25.976 NVP: prebuffering pause
2009-10-03 09:21:25.976 NVP: Waiting for prebuffer..  0 (ad)A(AD)A(AL)A(AD)A         
2009-10-03 09:21:25.978 WriteAudio: buffer underrun
2009-10-03 09:21:26.472 NVP: Video is 4.05554 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:26.473 NVP: Video is 4.3004 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:26.473 NVP: Video is 4.2368 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:26.541 NVP: prebuffering pause
2009-10-03 09:21:26.542 NVP: Waiting for prebuffer..  0 A(AL)ADAAAA         
2009-10-03 09:21:26.543 WriteAudio: buffer underrun
2009-10-03 09:21:26.696 AFD: HandleGopStart: Key frame distance changed from 29 to 30.
2009-10-03 09:21:26.933 NVP: Video is 4.0348 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:26.933 NVP: Video is 4.1275 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:27.028 WriteAudio: buffer underrun
2009-10-03 09:21:27.224 NVP: prebuffering pause
2009-10-03 09:21:27.224 NVP: Waiting for prebuffer..  0 A(AD)(AD)A(ad)AA(AL)         
2009-10-03 09:21:27.225 WriteAudio: buffer underrun
2009-10-03 09:21:27.367 NVP: Waiting for prebuffer..  1 A(AD)(AD)A(ad)AA(AL)         
2009-10-03 09:21:27.518 NVP: Waiting for prebuffer..  2 A(AD)(AD)A(ad)AA(AL)         
2009-10-03 09:21:27.668 NVP: Waiting for prebuffer..  3 A(AD)(AD)A(ad)AA(AL)         
2009-10-03 09:21:27.818 NVP: Waiting for prebuffer..  4 A(AD)(AD)A(ad)AA(AL)         
'video_output' mean = '33363.06', std. dev. = '4972.72', fps = '29.97'
2009-10-03 09:21:28.149 AFD: HandleGopStart: Key frame distance changed from 30 to 42.
2009-10-03 09:21:28.305 WriteAudio: buffer underrun
2009-10-03 09:21:28.337 WriteAudio: buffer underrun
2009-10-03 09:21:28.362 NVP: Video is 4.4403 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:28.362 NVP: Video is 4.67889 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:28.362 NVP: Video is 4.6031 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:28.362 NVP: Video is 4.30648 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:28.362 NVP: prebuffering pause
2009-10-03 09:21:28.363 NVP: Waiting for prebuffer..  0 A(AD)(AL)AAA(ad)A         
2009-10-03 09:21:28.503 NVP: Waiting for prebuffer..  1 A(AD)(au)AAA(AD)(AL)         
2009-10-03 09:21:28.592 AFD: HandleGopStart: Key frame distance changed from 42 to 8.
2009-10-03 09:21:28.653 NVP: Waiting for prebuffer..  2 A(AD)(au)AAA(AD)(AL)         
2009-10-03 09:21:28.973 AFD: HandleGopStart: Key frame distance changed from 8 to 29.
2009-10-03 09:21:29.145 NVP: Video is 4.08473 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:29.145 NVP: Video is 4.17994 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:29.146 NVP: Video is 4.00411 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 09:21:29.280 NVP: prebuffering pause
2009-10-03 09:21:29.280 NVP: Waiting for prebuffer..  0 (ad)AA(AD)(AL)AA(AD)         
2009-10-03 09:21:29.281 WriteAudio: buffer underrun
2009-10-03 09:21:29.422 NVP: Waiting for prebuffer..  1 (ad)AA(AD)(AL)AA(AD)         
'video_output' mean = '72496.76', std. dev. = '91683.15', fps = '13.79'
2009-10-03 09:21:29.685 AFD: HandleGopStart: Key frame distance changed from 29 to 28.
2009-10-03 09:21:29.900 NVP: prebuffering pause
2009-10-03 09:21:29.900 NVP: Waiting for prebuffer..  0 A(AD)(ad)AAA(AD)(AL)         
2009-10-03 09:21:29.900 WriteAudio: buffer underrun
2009-10-03 09:21:30.039 NVP: Waiting for prebuffer..  1 A(AD)(ad)AAA(AD)(AL)         
2009-10-03 09:21:30.166 NVP: Changing speed to 0
2009-10-03 09:21:30.167 rate: 29.97 speed: 1 skip: 1 = interval 33366
2009-10-03 09:21:30.167 Set video sync frame interval to 33366
2009-10-03 09:21:30.223 VideoOutputXv: UpdatePauseFrame() A(AD)(ad)AAA(AD)(AL)         
2009-10-03 09:21:30.354 DPMS Reactivated.
2009-10-03 09:21:30.779 AFD: HandleGopStart: Key frame distance changed from 28 to 35.
'video_output' mean = '33364.26', std. dev. = '834.02', fps = '29.97'
2009-10-03 09:21:31.913 AFD: HandleGopStart: Key frame distance changed from 35 to 34.
2009-10-03 09:21:31.995 TV: Attempting to change from WatchingPreRecorded to None
2009-10-03 09:21:31.995 TV: StopStuff() -- begin
2009-10-03 09:21:31.995 TV: StopStuff(): stopping ring buffer[s]
2009-10-03 09:21:31.995 TV: StopStuff(): stopping player[s] (1/2)
2009-10-03 09:21:31.995 TV: StopStuff(): stopping player[s] (2/2)
2009-10-03 09:21:31.996 NVP: Exited decoder loop.
2009-10-03 09:21:32.010 ~OpenGLVideoSync() -- begin
2009-10-03 09:21:32.010 ~OpenGLVideoSync() -- middle
2009-10-03 09:21:32.011 ~OpenGLVideoSync() -- end
2009-10-03 09:21:32.011 VideoOutputXv: dtor
2009-10-03 09:21:32.011 VideoOutputXv: DiscardFrames(1)
2009-10-03 09:21:32.011 VideoBuffers::DiscardFrames(1): A(AD)(ad)AAA(AD)(AL)         
2009-10-03 09:21:32.011 VideoBuffers::DiscardFrames(): A(AD)AAAA(AD)A          -- done()
2009-10-03 09:21:32.011 VideoBuffers::DiscardFrames(1): A(AD)AAAA(AD)A          -- done
2009-10-03 09:21:32.011 VideoOutputXv: DiscardFrames() 3: A(AD)AAAA(AD)A          -- done()
2009-10-03 09:21:32.060 VideoOutputXv: DiscardFrames(1)
2009-10-03 09:21:32.060 VideoBuffers::DiscardFrames(1): A(AD)AAAA(AD)A         
2009-10-03 09:21:32.060 VideoBuffers::DiscardFrames(): A(AD)AAAA(AD)A          -- done()
2009-10-03 09:21:32.060 VideoBuffers::DiscardFrames(1): A(AD)AAAA(AD)A          -- done
2009-10-03 09:21:32.061 VideoOutputXv: DiscardFrames() 3: A(AD)AAAA(AD)A          -- done()
2009-10-03 09:21:32.139 TV: StopStuff() -- end
2009-10-03 09:21:32.140 TV: Changing from WatchingPreRecorded to None
2009-10-03 09:21:32.248 NVP: Exited decoder loop.
2009-10-03 09:21:32.280 ~VideoOutputNull()
2009-10-03 09:21:32.759 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): OpenFile(/Storage/mythTVRecordings/1021_20090926133000.mpg, 1)
2009-10-03 09:21:32.759 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(3046832721 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:34.876 AFD: Stream #0, has id 0x480 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0xa3f0020
2009-10-03 09:21:34.877 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:34.877 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:34.877 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:34.877 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 09:21:34.877 Using 4 CPUs for decoding
2009-10-03 09:21:34.878 AFD: InitVideoCodec() 0xa7330b0 id(MPEG2VIDEO) type (Video).
2009-10-03 09:21:34.878 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 09:21:34.878 AFD: Using ffmpeg for video decoding
2009-10-03 09:21:34.878 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 09:21:34.878 AFD: Opened codec 0xa7330b0, id(MPEG2VIDEO) type(Video)
2009-10-03 09:21:34.878 AFD: Stream #1, has id 0x129 codec id AC3, type Audio, bitrate 192000 at 0x0xa0a2cb0
2009-10-03 09:21:34.878 AFD: codec AC3 has 2 channels
2009-10-03 09:21:34.878 AFD: Looking for decoder for AC3
2009-10-03 09:21:34.879 AFD: Opened codec 0xa7b7b20, id(AC3) type(Audio)
2009-10-03 09:21:34.879 AFD: Stream #2, has id 0x128 codec id AC3, type Audio, bitrate 384000 at 0x0xa3e8750
2009-10-03 09:21:34.879 AFD: codec AC3 has 6 channels
2009-10-03 09:21:34.879 AFD: Looking for decoder for AC3
2009-10-03 09:21:34.879 AFD: Opened codec 0xa8af1c0, id(AC3) type(Audio)
2009-10-03 09:21:34.880 RingBuf(/Storage/mythTVRecordings/1021_20090926133000.mpg): CalcReadAheadThresh(3046833037 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 09:21:34.880 Dec: Trying to select track (w/lang)
2009-10-03 09:21:34.880 Dec: Selecting first track
2009-10-03 09:21:34.880 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 09:21:34.880 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 09:21:34.880 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20090926133000.mpg". novideo(0)
2009-10-03 09:21:34.881 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:34.881 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 09:21:34.881 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 09:21:34.885 VideoOutputNull()
2009-10-03 09:21:34.885 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 09:21:34.885 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:34.885 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:34.885 Created data @0xb1002020->0xb12ff022
2009-10-03 09:21:34.885 Created data @0xac7ff020->0xacafc022
2009-10-03 09:21:34.885 Created data @0xac501020->0xac7fe022
2009-10-03 09:21:34.885 Created data @0xac203020->0xac500022
2009-10-03 09:21:34.885 Created data @0xabf05020->0xac202022
2009-10-03 09:21:34.885 Created data @0xabc07020->0xabf04022
2009-10-03 09:21:34.885 Created data @0xab68b020->0xab988022
2009-10-03 09:21:34.885 Created data @0xab38d020->0xab68a022
2009-10-03 09:21:34.886 Created data @0xab00f020->0xab30c022
2009-10-03 09:21:34.886 Created data @0xaad11020->0xab00e022
2009-10-03 09:21:34.886 Created data @0xaaa13020->0xaad10022
2009-10-03 09:21:34.886 Created data @0xaa715020->0xaaa12022
2009-10-03 09:21:34.886 Created data @0xaa417020->0xaa714022
2009-10-03 09:21:34.886 Created data @0xaa119020->0xaa416022
2009-10-03 09:21:34.886 Created data @0xa9e1b020->0xaa118022
2009-10-03 09:21:34.886 Created data @0xa9b1d020->0xa9e1a022
2009-10-03 09:21:34.886 Created data @0xa868f020->0xa898c022
2009-10-03 09:21:34.886 Created data @0xa8391020->0xa868e022
2009-10-03 09:21:34.886 Created data @0xa8093020->0xa8390022
2009-10-03 09:21:34.886 Created data @0xa7d95020->0xa8092022
2009-10-03 09:21:34.886 Created data @0xa7a97020->0xa7d94022
2009-10-03 09:21:34.886 Created data @0xa7799020->0xa7a96022
2009-10-03 09:21:34.887 Created data @0xa749b020->0xa7798022
2009-10-03 09:21:34.887 Created data @0xa719d020->0xa749a022
2009-10-03 09:21:34.887 Created data @0xa6e9f020->0xa719c022
2009-10-03 09:21:34.887 Created data @0xa6ba1020->0xa6e9e022
2009-10-03 09:21:34.887 Created data @0xa68a3020->0xa6ba0022
2009-10-03 09:21:34.887 Created data @0xa65a5020->0xa68a2022
2009-10-03 09:21:34.887 Created data @0xa62a7020->0xa65a4022
2009-10-03 09:21:34.887 Created data @0xa5fa9020->0xa62a6022
2009-10-03 09:21:34.887 Created data @0xa5cab020->0xa5fa8022
2009-10-03 09:21:34.887 Created data @0xa59ad020->0xa5caa022
2009-10-03 09:21:35.033 VDP: SetVideoRenderer(null)
2009-10-03 09:21:35.033 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 09:21:35.033 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 09:21:35.033 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 09:21:35.033 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 09:21:35.033 NVP: LoadFilters(''..) -> 0
2009-10-03 09:21:35.034 NVP: ClearAfterSeek(1)
2009-10-03 09:21:35.034 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 09:21:35.034 NVP: Exited decoder loop.
2009-10-03 09:21:35.167 ~VideoOutputNull()
2009-10-03 09:21:38.242 Deleting UPnP client...
aasland@MythBuntuServer:~/Desktop$ 

```

The file in question works great on a different computer (Thinkpad with built-in Intel graphics outputting to 1920x1200). By all means, I would expect the Geforce 9400GT w/VDPAU to completely blow away the laptop+intel, so something ain't right.

For the run above, I have set the playback profile to always use VDPAU, yet it is clear it is dropping back to ffmpeg. I have [COLOR="Red"]**highlighted**[/COLOR] some of those sections in the log above. 

Now the wierd thing, which really confuses me, is that I have some recorded shows which play ok ... they are rare, but they are ok. When I play one of them, I get this log:

```

mythfrontend.real -v playback
2009-10-03 08:25:53.974 Using runtime prefix = /usr
2009-10-03 08:25:54.625 XScreenSaver support enabled
2009-10-03 08:25:54.626 DPMS is active.
2009-10-03 08:25:54.626 Empty LocalHostName.
2009-10-03 08:25:54.626 Using localhost value of MythBuntuServer
2009-10-03 08:25:54.634 New DB connection, total: 1
2009-10-03 08:25:54.638 Connected to database 'mythconverg' at host: localhost
2009-10-03 08:25:54.640 Closing DB connection named 'DBManager0'
2009-10-03 08:25:54.642 Primary screen 0.
2009-10-03 08:25:54.642 Connected to database 'mythconverg' at host: localhost
2009-10-03 08:25:54.643 Using screen 0, 1280x720 at 0,0
2009-10-03 08:25:54.671 user: 1000 effective user: 1000 before privileged thread
2009-10-03 08:25:54.671 user: 1000 effective user: 1000 after privileged thread
2009-10-03 08:25:54.671 user: 1000 effective user: 1000 run_priv_thread
2009-10-03 08:25:54.673 New DB connection, total: 2
2009-10-03 08:25:54.673 Connected to database 'mythconverg' at host: localhost
2009-10-03 08:25:54.675 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-10-03 08:25:54.675 Enabled verbose msgs:  important general playback
2009-10-03 08:25:55.086 max_width: 1280 max_height: 720
2009-10-03 08:25:55.168 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-03 08:25:55.170 Primary screen 0.
2009-10-03 08:25:55.170 Using screen 0, 1280x720 at 0,0
2009-10-03 08:25:55.171 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-03 08:25:55.171 Switching to wide mode (metallurgy-wide)
2009-10-03 08:25:55.197 Using the Qt painter
2009-10-03 08:25:55.197 JoystickMenuClient Error: Joystick disabled - Failed to read /home/aasland/.mythtv/joystickmenurc
2009-10-03 08:25:55.199 lirc init success using configuration file: /home/aasland/.mythtv/lircrc
2009-10-03 08:25:55.528 Loading from: /usr/share/mythtv/themes/metallurgy-wide/base.xml
2009-10-03 08:25:55.536 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-10-03 08:25:55.573 Registering Internal as a media playback plugin.
2009-10-03 08:25:55.647 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-10-03 08:25:55.694 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-10-03 08:25:55.743 Starting update of NWS-XML
2009-10-03 08:25:55.752 Starting update of NDFD-6_day
2009-10-03 08:25:55.765 Starting update of NDFD-18_Hour
2009-10-03 08:25:55.790 No theme dir: /home/aasland/.mythtv/themes/metallurgy-wide
2009-10-03 08:25:56.739 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NWS-XML KRGK has exited
2009-10-03 08:25:56.740 wind_gust::
2009-10-03 08:25:56.740 nrecoverable error parsing script output 
2009-10-03 08:26:01.048 XMLParse::LoadTheme using /usr/share/mythtv/themes/metallurgy-wide/ui.xml
2009-10-03 08:26:01.323 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-10-03 08:26:01.325 Using protocol version 40
2009-10-03 08:26:01.421 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NDFD-18_Hour +44.35,-092.29 has exited
2009-10-03 08:26:01.592 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd.pl -u ENG -d /home/aasland/.mythtv/MythWeather/NDFD-6_day +44.35,-092.29 has exited
2009-10-03 08:26:02.361 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): OpenFile(/Storage/mythLiveRecordings/1091_20091002210318.mpg, 1)
2009-10-03 08:26:02.362 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046939217 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:02.539 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x904c560
2009-10-03 08:26:02.541 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:02.542 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:02.542 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:02.542 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 08:26:02.542 Using 4 CPUs for decoding
2009-10-03 08:26:02.542 AFD: InitVideoCodec() 0x8fc9f20 id(MPEG2VIDEO) type (Video).
2009-10-03 08:26:02.542 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-03 08:26:02.543 AFD: Using ffmpeg for video decoding
2009-10-03 08:26:02.543 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 08:26:02.543 AFD: Opened codec 0x8fc9f20, id(MPEG2VIDEO) type(Video)
2009-10-03 08:26:02.543 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 448000 at 0x0x8f73e00
2009-10-03 08:26:02.543 AFD: codec AC3 has 2 channels
2009-10-03 08:26:02.543 AFD: Looking for decoder for AC3
2009-10-03 08:26:02.543 AFD: Opened codec 0x8fa47f0, id(AC3) type(Audio)
2009-10-03 08:26:02.544 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x902a280
2009-10-03 08:26:02.544 AFD: codec AC3 has 1 channels
2009-10-03 08:26:02.544 AFD: Looking for decoder for AC3
2009-10-03 08:26:02.544 AFD: Opened codec 0x9043500, id(AC3) type(Audio)
2009-10-03 08:26:02.544 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:02.544 Dec: Trying to select track (w/lang)
2009-10-03 08:26:02.545 Dec: Selecting first track
2009-10-03 08:26:02.545 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:02.545 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 08:26:02.545 AFD: Successfully opened decoder for file: "/Storage/mythLiveRecordings/1091_20091002210318.mpg". novideo(0)
2009-10-03 08:26:02.546 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:02.546 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:02.546 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:02.563 VideoOutputNull()
2009-10-03 08:26:02.566 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 08:26:02.566 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:02.566 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 08:26:02.566 Created data @0xb1504020->0xb1655822
2009-10-03 08:26:02.567 Created data @0xb13b2020->0xb1503822
2009-10-03 08:26:02.567 Created data @0xb1260020->0xb13b1822
2009-10-03 08:26:02.567 Created data @0xb110e020->0xb125f822
2009-10-03 08:26:02.567 Created data @0xb0fbc020->0xb110d822
2009-10-03 08:26:02.567 Created data @0xabaa9020->0xabbfa822
2009-10-03 08:26:02.567 Created data @0xab957020->0xabaa8822
2009-10-03 08:26:02.567 Created data @0xab805020->0xab956822
2009-10-03 08:26:02.567 Created data @0xab6b3020->0xab804822
2009-10-03 08:26:02.567 Created data @0xab561020->0xab6b2822
2009-10-03 08:26:02.567 Created data @0xab40f020->0xab560822
2009-10-03 08:26:02.567 Created data @0xab2bd020->0xab40e822
2009-10-03 08:26:02.567 Created data @0xab16b020->0xab2bc822
2009-10-03 08:26:02.567 Created data @0xab019020->0xab16a822
2009-10-03 08:26:02.567 Created data @0xaaec7020->0xab018822
2009-10-03 08:26:02.568 Created data @0xaad75020->0xaaec6822
2009-10-03 08:26:02.568 Created data @0xaac23020->0xaad74822
2009-10-03 08:26:02.568 Created data @0xaaad1020->0xaac22822
2009-10-03 08:26:02.568 Created data @0xaa97f020->0xaaad0822
2009-10-03 08:26:02.568 Created data @0xaa82d020->0xaa97e822
2009-10-03 08:26:02.568 Created data @0xaa6db020->0xaa82c822
2009-10-03 08:26:02.568 Created data @0xaa589020->0xaa6da822
2009-10-03 08:26:02.568 Created data @0xaa437020->0xaa588822
2009-10-03 08:26:02.568 Created data @0xaa2e5020->0xaa436822
2009-10-03 08:26:02.568 Created data @0xaa193020->0xaa2e4822
2009-10-03 08:26:02.568 Created data @0xaa041020->0xaa192822
2009-10-03 08:26:02.568 Created data @0xa9eef020->0xaa040822
2009-10-03 08:26:02.568 Created data @0xa9d9d020->0xa9eee822
2009-10-03 08:26:02.568 Created data @0xa9c4b020->0xa9d9c822
2009-10-03 08:26:02.568 Created data @0xa9af9020->0xa9c4a822
2009-10-03 08:26:02.569 Created data @0xa99a7020->0xa9af8822
2009-10-03 08:26:02.569 Created data @0xa9855020->0xa99a6822
2009-10-03 08:26:02.633 VDP: SetVideoRenderer(null)
2009-10-03 08:26:02.633 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:02.634 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 08:26:02.634 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:02.634 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 08:26:02.635 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:02.635 NVP: ClearAfterSeek(1)
2009-10-03 08:26:02.636 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:02.656 NVP: Exited decoder loop.
2009-10-03 08:26:02.702 ~VideoOutputNull()
2009-10-03 08:26:02.936 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): OpenFile(/Storage/mythLiveRecordings/1091_20091002210318.mpg, 1)
2009-10-03 08:26:02.936 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046939217 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:03.099 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x9045ea0
2009-10-03 08:26:03.100 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:03.100 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:03.100 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:03.100 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 08:26:03.101 Using 4 CPUs for decoding
2009-10-03 08:26:03.101 AFD: InitVideoCodec() 0x8fc8c80 id(MPEG2VIDEO) type (Video).
2009-10-03 08:26:03.101 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-03 08:26:03.101 AFD: Using ffmpeg for video decoding
2009-10-03 08:26:03.101 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 08:26:03.101 AFD: Opened codec 0x8fc8c80, id(MPEG2VIDEO) type(Video)
2009-10-03 08:26:03.101 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 448000 at 0x0x8ff2c20
2009-10-03 08:26:03.101 AFD: codec AC3 has 2 channels
2009-10-03 08:26:03.101 AFD: Looking for decoder for AC3
2009-10-03 08:26:03.102 AFD: Opened codec 0x9043d20, id(AC3) type(Audio)
2009-10-03 08:26:03.102 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x8ff56f0
2009-10-03 08:26:03.102 AFD: codec AC3 has 1 channels
2009-10-03 08:26:03.102 AFD: Looking for decoder for AC3
2009-10-03 08:26:03.102 AFD: Opened codec 0x8fd3960, id(AC3) type(Audio)
2009-10-03 08:26:03.102 RingBuf(/Storage/mythLiveRecordings/1091_20091002210318.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:03.103 Dec: Trying to select track (w/lang)
2009-10-03 08:26:03.103 Dec: Selecting first track
2009-10-03 08:26:03.103 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:03.103 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 08:26:03.103 AFD: Successfully opened decoder for file: "/Storage/mythLiveRecordings/1091_20091002210318.mpg". novideo(0)
2009-10-03 08:26:03.104 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:03.104 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:03.105 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:03.108 VideoOutputNull()
2009-10-03 08:26:03.108 VDP: LoadBestPreferences(1280x720, 60)
2009-10-03 08:26:03.108 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:03.108 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 08:26:03.108 Created data @0xb1504020->0xb1655822
2009-10-03 08:26:03.108 Created data @0xb13b2020->0xb1503822
2009-10-03 08:26:03.109 Created data @0xb1260020->0xb13b1822
2009-10-03 08:26:03.109 Created data @0xb110e020->0xb125f822
2009-10-03 08:26:03.109 Created data @0xb0fbc020->0xb110d822
2009-10-03 08:26:03.109 Created data @0xabaa9020->0xabbfa822
2009-10-03 08:26:03.109 Created data @0xab957020->0xabaa8822
2009-10-03 08:26:03.109 Created data @0xab805020->0xab956822
2009-10-03 08:26:03.109 Created data @0xab6b3020->0xab804822
2009-10-03 08:26:03.109 Created data @0xab561020->0xab6b2822
2009-10-03 08:26:03.109 Created data @0xab40f020->0xab560822
2009-10-03 08:26:03.109 Created data @0xab2bd020->0xab40e822
2009-10-03 08:26:03.109 Created data @0xab16b020->0xab2bc822
2009-10-03 08:26:03.109 Created data @0xab019020->0xab16a822
2009-10-03 08:26:03.109 Created data @0xaaec7020->0xab018822
2009-10-03 08:26:03.109 Created data @0xaad75020->0xaaec6822
2009-10-03 08:26:03.109 Created data @0xaac23020->0xaad74822
2009-10-03 08:26:03.110 Created data @0xaaad1020->0xaac22822
2009-10-03 08:26:03.110 Created data @0xaa97f020->0xaaad0822
2009-10-03 08:26:03.110 Created data @0xaa82d020->0xaa97e822
2009-10-03 08:26:03.110 Created data @0xaa6db020->0xaa82c822
2009-10-03 08:26:03.110 Created data @0xaa589020->0xaa6da822
2009-10-03 08:26:03.110 Created data @0xaa437020->0xaa588822
2009-10-03 08:26:03.110 Created data @0xaa2e5020->0xaa436822
2009-10-03 08:26:03.110 Created data @0xaa193020->0xaa2e4822
2009-10-03 08:26:03.110 Created data @0xaa041020->0xaa192822
2009-10-03 08:26:03.110 Created data @0xa9eef020->0xaa040822
2009-10-03 08:26:03.110 Created data @0xa9d9d020->0xa9eee822
2009-10-03 08:26:03.110 Created data @0xa9c4b020->0xa9d9c822
2009-10-03 08:26:03.111 Created data @0xa9af9020->0xa9c4a822
2009-10-03 08:26:03.111 Created data @0xa99a7020->0xa9af8822
2009-10-03 08:26:03.111 Created data @0xa9855020->0xa99a6822
2009-10-03 08:26:03.175 VDP: SetVideoRenderer(null)
2009-10-03 08:26:03.175 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:03.176 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 08:26:03.176 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:03.176 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 08:26:03.176 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:03.176 NVP: ClearAfterSeek(1)
2009-10-03 08:26:03.176 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:03.243 NVP: Waiting for prebuffer..  1 uLLAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:03.246 NVP: Exited decoder loop.
2009-10-03 08:26:03.309 ~VideoOutputNull()
2009-10-03 08:26:03.732 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): OpenFile(/Storage/mythTVRecordings/1021_20091002195900.mpg, 1)
2009-10-03 08:26:03.732 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3046939217 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:03.920 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x9004280
2009-10-03 08:26:03.921 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:03.921 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:03.921 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:03.921 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:03.922 Using 4 CPUs for decoding
2009-10-03 08:26:03.922 AFD: InitVideoCodec() 0x8fe1370 id(MPEG2VIDEO) type (Video).
2009-10-03 08:26:03.922 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 08:26:03.922 AFD: Using ffmpeg for video decoding
2009-10-03 08:26:03.922 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 08:26:03.922 AFD: Opened codec 0x8fe1370, id(MPEG2VIDEO) type(Video)
2009-10-03 08:26:03.922 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 384000 at 0x0x9004420
2009-10-03 08:26:03.922 AFD: codec AC3 has 6 channels
2009-10-03 08:26:03.922 AFD: Looking for decoder for AC3
2009-10-03 08:26:03.923 AFD: Opened codec 0x8fce220, id(AC3) type(Audio)
2009-10-03 08:26:03.923 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x9057b40
2009-10-03 08:26:03.923 AFD: codec AC3 has 2 channels
2009-10-03 08:26:03.923 AFD: Looking for decoder for AC3
2009-10-03 08:26:03.924 AFD: Opened codec 0x9057ce0, id(AC3) type(Audio)
2009-10-03 08:26:03.924 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:03.924 Dec: Trying to select track (w/lang)
2009-10-03 08:26:03.924 Dec: Selecting first track
2009-10-03 08:26:03.924 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:03.924 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 08:26:03.924 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20091002195900.mpg". novideo(0)
2009-10-03 08:26:03.925 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:03.926 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:03.926 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:03.929 VideoOutputNull()
2009-10-03 08:26:03.933 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 08:26:03.933 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:03.933 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:03.933 Created data @0xb1358020->0xb1655022
2009-10-03 08:26:03.933 Created data @0xb105a020->0xb1357022
2009-10-03 08:26:03.933 Created data @0xab8fd020->0xabbfa022
2009-10-03 08:26:03.933 Created data @0xab5ff020->0xab8fc022
2009-10-03 08:26:03.934 Created data @0xab301020->0xab5fe022
2009-10-03 08:26:03.934 Created data @0xab003020->0xab300022
2009-10-03 08:26:03.934 Created data @0xaad05020->0xab002022
2009-10-03 08:26:03.934 Created data @0xaaa07020->0xaad04022
2009-10-03 08:26:03.934 Created data @0xaa709020->0xaaa06022
2009-10-03 08:26:03.934 Created data @0xaa40b020->0xaa708022
2009-10-03 08:26:03.934 Created data @0xaa10d020->0xaa40a022
2009-10-03 08:26:03.934 Created data @0xa9e0f020->0xaa10c022
2009-10-03 08:26:03.934 Created data @0xa9b11020->0xa9e0e022
2009-10-03 08:26:03.934 Created data @0xa9813020->0xa9b10022
2009-10-03 08:26:03.934 Created data @0xa9515020->0xa9812022
2009-10-03 08:26:03.934 Created data @0xa9217020->0xa9514022
2009-10-03 08:26:03.934 Created data @0xa8f19020->0xa9216022
2009-10-03 08:26:03.934 Created data @0xa8b02020->0xa8dff022
2009-10-03 08:26:03.934 Created data @0xa8804020->0xa8b01022
2009-10-03 08:26:03.935 Created data @0xa8506020->0xa8803022
2009-10-03 08:26:03.935 Created data @0xa8208020->0xa8505022
2009-10-03 08:26:03.935 Created data @0xa7f0a020->0xa8207022
2009-10-03 08:26:03.935 Created data @0xa7c0c020->0xa7f09022
2009-10-03 08:26:03.935 Created data @0xa790e020->0xa7c0b022
2009-10-03 08:26:03.935 Created data @0xa7610020->0xa790d022
2009-10-03 08:26:03.935 Created data @0xa7312020->0xa760f022
2009-10-03 08:26:03.935 Created data @0xa7014020->0xa7311022
2009-10-03 08:26:03.935 Created data @0xa6d16020->0xa7013022
2009-10-03 08:26:03.935 Created data @0xa6a18020->0xa6d15022
2009-10-03 08:26:03.935 Created data @0xa671a020->0xa6a17022
2009-10-03 08:26:03.935 Created data @0xa641c020->0xa6719022
2009-10-03 08:26:03.935 Created data @0xa611e020->0xa641b022
2009-10-03 08:26:04.078 VDP: SetVideoRenderer(null)
2009-10-03 08:26:04.078 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:04.079 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 08:26:04.079 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:04.079 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:04.079 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:04.079 NVP: ClearAfterSeek(1)
2009-10-03 08:26:04.079 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:04.212 NVP: Waiting for prebuffer..  1 UuUULULAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:04.346 NVP: Waiting for prebuffer..  2 UUUUUUUuUULULAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:04.737 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-10-03 08:26:04.737 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-03 08:26:04.737 AFD: HandleGopStart: Initial key frame distance: 15.
2009-10-03 08:26:05.377 NVP: Exited decoder loop.
2009-10-03 08:26:05.402 ~VideoOutputNull()
2009-10-03 08:26:05.459 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): OpenFile(/Storage/mythTVRecordings/1021_20091002195900.mpg, 1)
2009-10-03 08:26:05.459 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3047915904 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:05.648 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x8fa3ae0
2009-10-03 08:26:05.649 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:05.649 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:05.649 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:05.649 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:05.649 Using 4 CPUs for decoding
2009-10-03 08:26:05.650 AFD: InitVideoCodec() 0x8feda10 id(MPEG2VIDEO) type (Video).
2009-10-03 08:26:05.650 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 08:26:05.650 AFD: Using ffmpeg for video decoding
2009-10-03 08:26:05.650 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 08:26:05.650 AFD: Opened codec 0x8feda10, id(MPEG2VIDEO) type(Video)
2009-10-03 08:26:05.650 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 384000 at 0x0x8fedf60
2009-10-03 08:26:05.650 AFD: codec AC3 has 6 channels
2009-10-03 08:26:05.650 AFD: Looking for decoder for AC3
2009-10-03 08:26:05.651 AFD: Opened codec 0x8fee100, id(AC3) type(Audio)
2009-10-03 08:26:05.651 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x90393a0
2009-10-03 08:26:05.651 AFD: codec AC3 has 2 channels
2009-10-03 08:26:05.651 AFD: Looking for decoder for AC3
2009-10-03 08:26:05.651 AFD: Opened codec 0x9039540, id(AC3) type(Audio)
2009-10-03 08:26:05.651 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:05.652 Dec: Trying to select track (w/lang)
2009-10-03 08:26:05.652 Dec: Selecting first track
2009-10-03 08:26:05.652 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:05.652 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 08:26:05.652 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20091002195900.mpg". novideo(0)
2009-10-03 08:26:05.653 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:05.653 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:05.653 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:05.656 VideoOutputNull()
2009-10-03 08:26:05.657 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 08:26:05.657 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:05.657 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:05.657 Created data @0xb1312020->0xb160f022
2009-10-03 08:26:05.657 Created data @0xb1014020->0xb1311022
2009-10-03 08:26:05.657 Created data @0xab8fd020->0xabbfa022
2009-10-03 08:26:05.657 Created data @0xab5ff020->0xab8fc022
2009-10-03 08:26:05.657 Created data @0xab301020->0xab5fe022
2009-10-03 08:26:05.657 Created data @0xab003020->0xab300022
2009-10-03 08:26:05.657 Created data @0xaad05020->0xab002022
2009-10-03 08:26:05.657 Created data @0xaaa07020->0xaad04022
2009-10-03 08:26:05.657 Created data @0xaa709020->0xaaa06022
2009-10-03 08:26:05.658 Created data @0xaa40b020->0xaa708022
2009-10-03 08:26:05.658 Created data @0xaa10d020->0xaa40a022
2009-10-03 08:26:05.658 Created data @0xa9e0f020->0xaa10c022
2009-10-03 08:26:05.658 Created data @0xa9b11020->0xa9e0e022
2009-10-03 08:26:05.658 Created data @0xa9813020->0xa9b10022
2009-10-03 08:26:05.658 Created data @0xa9515020->0xa9812022
2009-10-03 08:26:05.658 Created data @0xa9217020->0xa9514022
2009-10-03 08:26:05.658 Created data @0xa8f19020->0xa9216022
2009-10-03 08:26:05.658 Created data @0xa8b02020->0xa8dff022
2009-10-03 08:26:05.658 Created data @0xa8804020->0xa8b01022
2009-10-03 08:26:05.658 Created data @0xa8506020->0xa8803022
2009-10-03 08:26:05.658 Created data @0xa8208020->0xa8505022
2009-10-03 08:26:05.658 Created data @0xa7f0a020->0xa8207022
2009-10-03 08:26:05.658 Created data @0xa7c0c020->0xa7f09022
2009-10-03 08:26:05.658 Created data @0xa790e020->0xa7c0b022
2009-10-03 08:26:05.659 Created data @0xa7610020->0xa790d022
2009-10-03 08:26:05.659 Created data @0xa7312020->0xa760f022
2009-10-03 08:26:05.659 Created data @0xa7014020->0xa7311022
2009-10-03 08:26:05.659 Created data @0xa6d16020->0xa7013022
2009-10-03 08:26:05.659 Created data @0xa6a18020->0xa6d15022
2009-10-03 08:26:05.659 Created data @0xa671a020->0xa6a17022
2009-10-03 08:26:05.659 Created data @0xa641c020->0xa6719022
2009-10-03 08:26:05.659 Created data @0xa611e020->0xa641b022
2009-10-03 08:26:05.799 VDP: SetVideoRenderer(null)
2009-10-03 08:26:05.799 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:05.799 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 08:26:05.799 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:05.800 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:05.800 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:05.800 NVP: ClearAfterSeek(1)
2009-10-03 08:26:05.800 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:05.933 NVP: Waiting for prebuffer..  1 UuUULULAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:06.067 NVP: Waiting for prebuffer..  2 UUUUUUUuUULULAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:06.461 NVP: Exited decoder loop.
2009-10-03 08:26:06.461 TV: Attempting to change from None to WatchingPreRecorded
2009-10-03 08:26:06.462 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): OpenFile(/Storage/mythTVRecordings/1021_20091002195900.mpg, 12)
2009-10-03 08:26:06.462 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(150419072 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:06.466 DPMS Deactivated 
2009-10-03 08:26:06.490 ~VideoOutputNull()
2009-10-03 08:26:06.717 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x90cf020
2009-10-03 08:26:06.719 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:06.719 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:06.719 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:06.719 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:06.971 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): OpenFile(/Storage/mythTVRecordings/1021_20091002195900.mpg, 1)
2009-10-03 08:26:06.972 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(2985296032 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:07.042 VDPAU: Version 0
2009-10-03 08:26:07.042 VDPAU: Information NVIDIA VDPAU Driver Shared Library  185.18.36  Fri Aug 14 17:50:51 PDT 2009
2009-10-03 08:26:07.094 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:07.094 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:07.094 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:07.094 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:07.094 Using 1 CPUs for decoding
2009-10-03 08:26:07.094 AFD: InitVideoCodec() 0x90e0180 id(MPEGVIDEO_VDPAU) type (Video).
2009-10-03 08:26:07.095 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 08:26:07.095 AFD: Using vdpau for video decoding
2009-10-03 08:26:07.095 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-03 08:26:07.095 AFD: Opened codec 0x90e0180, id(MPEGVIDEO_VDPAU) type(Video)
2009-10-03 08:26:07.095 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 384000 at 0x0x90e06d0
2009-10-03 08:26:07.095 AFD: codec AC3 has 6 channels
2009-10-03 08:26:07.095 AFD: Looking for decoder for AC3
2009-10-03 08:26:07.095 AFD: Opened codec 0x90e0870, id(AC3) type(Audio)
2009-10-03 08:26:07.095 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x90e0dc0
2009-10-03 08:26:07.096 AFD: codec AC3 has 2 channels
2009-10-03 08:26:07.096 AFD: Looking for decoder for AC3
2009-10-03 08:26:07.096 AFD: Opened codec 0x90e0f60, id(AC3) type(Audio)
2009-10-03 08:26:07.096 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:07.101 Opening audio device 'default'. ch 2(2) sr 48000
2009-10-03 08:26:07.101 Opening ALSA audio device 'default'.
2009-10-03 08:26:07.114 Mixer unable to find control Master
2009-10-03 08:26:07.115 Mixer unable to find control Master
2009-10-03 08:26:07.115 Mixer unable to find control PCM
2009-10-03 08:26:07.115 Mixer unable to find control PCM
2009-10-03 08:26:07.115 Mixer unable to find control PCM
2009-10-03 08:26:07.116 Dec: Trying to select track (w/lang)
2009-10-03 08:26:07.116 Dec: Selecting first track
2009-10-03 08:26:07.116 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:07.116 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-03 08:26:07.172 Position map filled from DB to: 214107
2009-10-03 08:26:07.173 SyncPositionMap prerecorded, from DB: 6685 entries
2009-10-03 08:26:07.173 SyncPositionMap, new totframes: 214107, new length: 7144, posMap size: 6685
2009-10-03 08:26:07.173 AFD: Position map found
2009-10-03 08:26:07.174 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20091002195900.mpg". novideo(0)
2009-10-03 08:26:07.202 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x9045ea0
2009-10-03 08:26:07.207 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:07.207 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:07.207 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:07.208 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:07.208 Using 4 CPUs for decoding
2009-10-03 08:26:07.211 AFD: InitVideoCodec() 0x8fc8c80 id(MPEG2VIDEO) type (Video).
2009-10-03 08:26:07.211 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 08:26:07.211 AFD: Using ffmpeg for video decoding
2009-10-03 08:26:07.211 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 08:26:07.211 AFD: Opened codec 0x8fc8c80, id(MPEG2VIDEO) type(Video)
2009-10-03 08:26:07.211 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 384000 at 0x0x8ff56f0
2009-10-03 08:26:07.211 AFD: codec AC3 has 6 channels
2009-10-03 08:26:07.211 AFD: Looking for decoder for AC3
2009-10-03 08:26:07.212 AFD: Opened codec 0x8fe60d0, id(AC3) type(Audio)
2009-10-03 08:26:07.212 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x8ff2c20
2009-10-03 08:26:07.212 AFD: codec AC3 has 2 channels
2009-10-03 08:26:07.212 AFD: Looking for decoder for AC3
2009-10-03 08:26:07.213 AFD: Opened codec 0x904a610, id(AC3) type(Audio)
2009-10-03 08:26:07.213 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:07.213 Dec: Trying to select track (w/lang)
2009-10-03 08:26:07.213 Dec: Selecting first track
2009-10-03 08:26:07.213 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:07.213 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 08:26:07.213 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20091002195900.mpg". novideo(0)
2009-10-03 08:26:07.214 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:07.214 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:07.215 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:07.218 VideoOutputNull()
2009-10-03 08:26:07.219 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 08:26:07.219 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:07.219 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:07.219 Created data @0xb0f57020->0xb1254022
2009-10-03 08:26:07.219 Created data @0xab0fc020->0xab3f9022
2009-10-03 08:26:07.219 Created data @0xaadfe020->0xab0fb022
2009-10-03 08:26:07.219 Created data @0xaab00020->0xaadfd022
2009-10-03 08:26:07.219 Created data @0xaa802020->0xaaaff022
2009-10-03 08:26:07.219 Created data @0xaa504020->0xaa801022
2009-10-03 08:26:07.219 Created data @0xaa206020->0xaa503022
2009-10-03 08:26:07.219 Created data @0xa9f08020->0xaa205022
2009-10-03 08:26:07.219 Created data @0xa9c0a020->0xa9f07022
2009-10-03 08:26:07.219 Created data @0xa990c020->0xa9c09022
2009-10-03 08:26:07.220 Created data @0xa960e020->0xa990b022
2009-10-03 08:26:07.220 Created data @0xa9310020->0xa960d022
2009-10-03 08:26:07.220 Created data @0xa9012020->0xa930f022
2009-10-03 08:26:07.220 Created data @0xa8b02020->0xa8dff022
2009-10-03 08:26:07.220 Created data @0xa8804020->0xa8b01022
2009-10-03 08:26:07.220 Created data @0xa8506020->0xa8803022
2009-10-03 08:26:07.220 Created data @0xa8208020->0xa8505022
2009-10-03 08:26:07.220 Created data @0xa7f0a020->0xa8207022
2009-10-03 08:26:07.220 Created data @0xa7c0c020->0xa7f09022
2009-10-03 08:26:07.220 Created data @0xa790e020->0xa7c0b022
2009-10-03 08:26:07.220 Created data @0xa7610020->0xa790d022
2009-10-03 08:26:07.220 Created data @0xa7312020->0xa760f022
2009-10-03 08:26:07.220 Created data @0xa7014020->0xa7311022
2009-10-03 08:26:07.220 Created data @0xa6d16020->0xa7013022
2009-10-03 08:26:07.220 Created data @0xa6a18020->0xa6d15022
2009-10-03 08:26:07.220 Created data @0xa671a020->0xa6a17022
2009-10-03 08:26:07.220 Created data @0xa641c020->0xa6719022
2009-10-03 08:26:07.221 Created data @0xa611e020->0xa641b022
2009-10-03 08:26:07.221 Created data @0xa5e20020->0xa611d022
2009-10-03 08:26:07.221 Created data @0xa5b22020->0xa5e1f022
2009-10-03 08:26:07.221 Created data @0xa5824020->0xa5b21022
2009-10-03 08:26:07.221 Created data @0xa365e020->0xa395b022
2009-10-03 08:26:07.418 VDP: SetVideoRenderer(null)
2009-10-03 08:26:07.418 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:07.418 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 08:26:07.418 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:07.418 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:07.419 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:07.419 NVP: ClearAfterSeek(1)
2009-10-03 08:26:07.419 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:07.552 NVP: Waiting for prebuffer..  1 uLULAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:07.563 VideoOutput: Allowed renderers: vdpau
2009-10-03 08:26:07.563 VideoOutput: Allowed renderers (filt: vdpau): vdpau
2009-10-03 08:26:07.567 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:07.568 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:07.568 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:07.568 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:07.568 VideoOutput: Preferred renderer: vdpau
2009-10-03 08:26:07.568 VideoOutput: Trying video renderer: vdpau
2009-10-03 08:26:07.570 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:07.570 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:07.570 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:07.584 VideoOutputXv: ctor
2009-10-03 08:26:07.586 XOff: 0, YOff: 0
2009-10-03 08:26:07.586 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 08:26:07.587 Display Rect  left: 0, top: 90, width: 1280, height: 540, aspect: 1.33333
2009-10-03 08:26:07.587 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:07.588 VideoOutputXv: Pixel dimensions: Screen 1280x720, window 1280x720
2009-10-03 08:26:07.590 VideoOutputXv: Estimated display dimensions: 325x183 mm  Aspect: 1.77596
2009-10-03 08:26:07.590 VideoOutputXv: Estimated window dimensions: 325x183 mm  Aspect: 1.77596
2009-10-03 08:26:07.685 NVP: Waiting for prebuffer..  2 UUUULUULAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:07.819 NVP: Waiting for prebuffer..  3 UUUUUUULUULAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:07.968 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: vdpau
2009-10-03 08:26:08.361 AFD: HandleGopStart: gopset not set, syncing positionMap
2009-10-03 08:26:08.361 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2009-10-03 08:26:08.361 AFD: HandleGopStart: Initial key frame distance: 15.
2009-10-03 08:26:08.468 VideoOutputXv: Created VDPAU context (GPU decode)
2009-10-03 08:26:08.468 VDP: SetVideoRenderer(vdpau)
2009-10-03 08:26:08.469 VDP: SetVideoRender(vdpau) == GetVideoRenderer()
2009-10-03 08:26:08.472 VDPAU: Created OSD (1280x720)
2009-10-03 08:26:08.473 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-03 08:26:08.473 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 08:26:08.473 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:08.475 Over/underscan. V: 0, H: 0
2009-10-03 08:26:08.476 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-03 08:26:08.476 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:08.476 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-10-03 08:26:08.476 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:08.489 OSD Theme Dimensions W: 1280 H: 720
2009-10-03 08:26:09.199 TV: StartPlayer(): took 2724 ms to start player.
2009-10-03 08:26:09.199 TV: Changing from None to WatchingPreRecorded
2009-10-03 08:26:09.200 NVP: ClearAfterSeek(1)
2009-10-03 08:26:09.200 VideoOutputXv: ClearAfterSeek()
2009-10-03 08:26:09.201 VideoOutputXv: DiscardFrames(0)
2009-10-03 08:26:09.201 VideoBuffers::DiscardFrames(0): AAAAAAAA         
2009-10-03 08:26:09.201 VideoBuffers::DiscardFrames(0): AAAAAAAA          -- done
2009-10-03 08:26:09.201 VideoOutputXv: DiscardFrames() 3: AAAAAAAA          -- done()
2009-10-03 08:26:09.202 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-03 08:26:09.205 Realtime priority would require SUID as root.
2009-10-03 08:26:09.280 VDPAU: Created VDPAU decoder (2 ref frames)
2009-10-03 08:26:09.309 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-10-03 08:26:09.309 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-10-03 08:26:09.309 OpenGLVideoSync()
2009-10-03 08:26:09.315 OpenGLVideoSync: x,y -> 640, 360
2009-10-03 08:26:09.373 Using OpenGLVideoSync
2009-10-03 08:26:09.374 Set video sync frame interval to 33366
2009-10-03 08:26:09.375 Using audio as timebase
2009-10-03 08:26:09.375 Video timing method: SGI OpenGL
2009-10-03 08:26:09.375 Refresh rate: 16684, frame interval: 33366
2009-10-03 08:26:09.398 NVP: Waiting for prebuffer..  0 AAAAAAAA         
2009-10-03 08:26:09.541 NVP: Waiting for prebuffer..  1 (AL)AAAAAAA         
2009-10-03 08:26:09.672 AFD: HandleGopStart: Key frame distance changed from 30 to 16.
2009-10-03 08:26:09.692 NVP: Waiting for prebuffer..  2 (AL)AAAAAAA         
2009-10-03 08:26:10.014 VDPAU: Using 4 output surfaces (max 4)
2009-10-03 08:26:10.300 NVP: Video is 4.32284 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:10.300 NVP: Video is 4.67323 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:10.301 NVP: Video is 4.68126 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:10.301 NVP: Video is 4.44003 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:10.301 NVP: Video is 4.01184 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:10.301 NVP: prebuffering pause
2009-10-03 08:26:10.301 NVP: Waiting for prebuffer..  0 (AD)aA(AD)(AL)aA(AD)         
2009-10-03 08:26:10.308 AFD: HandleGopStart: Key frame distance changed from 16 to 10.
2009-10-03 08:26:10.890 NVP: prebuffering pause
2009-10-03 08:26:10.890 NVP: Waiting for prebuffer..  0 AA(ad)A(AD)(AL)(ad)A         
2009-10-03 08:26:10.890 WriteAudio: buffer underrun
'video_output' mean = '33365.23', std. dev. = '2920.69', fps = '29.97'
2009-10-03 08:26:11.270 AFD: HandleGopStart: Key frame distance changed from 10 to 34.
2009-10-03 08:26:11.360 NVP: prebuffering pause
2009-10-03 08:26:11.360 NVP: Waiting for prebuffer..  0 AAA(dl)A(AD)A(ad)         
2009-10-03 08:26:11.362 WriteAudio: buffer underrun
2009-10-03 08:26:11.495 NVP: Waiting for prebuffer..  1 (au)AA(dl)A(AD)A(AD)         
2009-10-03 08:26:11.801 WriteAudio: buffer underrun
2009-10-03 08:26:11.862 WriteAudio: buffer underrun
2009-10-03 08:26:11.901 WriteAudio: buffer underrun
2009-10-03 08:26:12.039 WriteAudio: buffer underrun
2009-10-03 08:26:12.083 NVP: prebuffering pause
2009-10-03 08:26:12.084 NVP: Waiting for prebuffer..  0 (AD)(ad)(ad)A(AL)AAA         
2009-10-03 08:26:12.084 WriteAudio: buffer underrun
2009-10-03 08:26:12.390 AFD: HandleGopStart: Key frame distance changed from 34 to 30.
2009-10-03 08:26:12.612 NVP: prebuffering pause
2009-10-03 08:26:12.612 NVP: Waiting for prebuffer..  0 (AL)AA(AD)A(ad)A(AD)         
2009-10-03 08:26:12.614 WriteAudio: buffer underrun
2009-10-03 08:26:12.748 NVP: Waiting for prebuffer..  1 (AL)AA(AD)A(ad)A(AD)         
2009-10-03 08:26:12.898 NVP: Waiting for prebuffer..  2 (AL)AA(AD)A(ad)A(AD)         
2009-10-03 08:26:13.209 WriteAudio: buffer underrun
2009-10-03 08:26:13.277 WriteAudio: buffer underrun
2009-10-03 08:26:13.354 WriteAudio: buffer underrun
2009-10-03 08:26:13.439 WriteAudio: buffer underrun
2009-10-03 08:26:13.472 NVP: Video is 4.00788 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:13.503 WriteAudio: buffer underrun
2009-10-03 08:26:13.549 WriteAudio: buffer underrun
2009-10-03 08:26:13.592 WriteAudio: buffer underrun
2009-10-03 08:26:13.673 WriteAudio: buffer underrun
2009-10-03 08:26:13.749 WriteAudio: buffer underrun
2009-10-03 08:26:13.783 WriteAudio: buffer underrun
2009-10-03 08:26:13.932 WriteAudio: buffer underrun
2009-10-03 08:26:13.943 NVP: prebuffering pause
2009-10-03 08:26:13.943 NVP: Waiting for prebuffer..  0 A(ad)A(AD)A(ad)A(AL)         
2009-10-03 08:26:14.001 NVP: prebuffering pause
2009-10-03 08:26:14.001 NVP: Waiting for prebuffer..  0 A(ad)A(ad)A(AD)A(AL)         
2009-10-03 08:26:14.302 NVP: prebuffering pause
2009-10-03 08:26:14.302 NVP: Waiting for prebuffer..  0 AAAAAAAUAAAAAALAAAAAAAAAAaAALAA
2009-10-03 08:26:14.382 WriteAudio: buffer underrun
2009-10-03 08:26:14.432 WriteAudio: buffer underrun
2009-10-03 08:26:14.435 NVP: Waiting for prebuffer..  1 LAAAAAAUAALAAAUAAAAAAAAAAAAAuAA
2009-10-03 08:26:14.436 NVP: Video is 4.51951 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:14.436 NVP: Video is 4.79824 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:14.436 NVP: Video is 4.75253 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:14.436 NVP: Video is 4.47848 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:14.436 NVP: prebuffering pause
2009-10-03 08:26:14.436 NVP: Waiting for prebuffer..  0 (AD)AAA(ad)(AL)AA         
2009-10-03 08:26:14.518 NVP: Video is 4.02568 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:14.568 NVP: Waiting for prebuffer..  2 uLAAAAAUAAUAALUAAUAAAAAAAAAAUAA
2009-10-03 08:26:14.694 NVP: prebuffering pause
2009-10-03 08:26:14.694 NVP: Waiting for prebuffer..  0 A(AL)(AD)(ad)AA(AD)A         
2009-10-03 08:26:14.696 WriteAudio: buffer underrun
2009-10-03 08:26:14.702 NVP: Waiting for prebuffer..  3 UuAAAAAUAAUALUUAUUAAUAALAAAAUAA
2009-10-03 08:26:14.867 AFD: HandleGopStart: Key frame distance changed from 30 to 31.
'video_output' mean = '37552.76', std. dev. = '41909.33', fps = '26.63'
2009-10-03 08:26:15.075 WriteAudio: buffer underrun
2009-10-03 08:26:15.112 WriteAudio: buffer underrun
2009-10-03 08:26:15.192 NVP: prebuffering pause
2009-10-03 08:26:15.192 NVP: Waiting for prebuffer..  0 (AD)AAAAA(ad)(DL)         
2009-10-03 08:26:15.193 WriteAudio: buffer underrun
2009-10-03 08:26:15.580 WriteAudio: buffer underrun
2009-10-03 08:26:15.632 NVP: Video is 4.47491 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:15.633 NVP: Video is 4.68237 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:15.633 NVP: Video is 4.59072 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:15.633 NVP: Video is 4.27471 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:15.702 NVP: prebuffering pause
2009-10-03 08:26:15.703 NVP: Waiting for prebuffer..  0 (AD)(AL)(AD)AAA(ad)A         
2009-10-03 08:26:15.703 WriteAudio: buffer underrun
2009-10-03 08:26:15.838 NVP: Waiting for prebuffer..  1 (AD)(AL)(AD)AAA(ad)A         
2009-10-03 08:26:15.988 NVP: Waiting for prebuffer..  2 (AD)(AL)(AD)AAA(ad)A         
2009-10-03 08:26:16.436 AFD: HandleGopStart: Key frame distance changed from 31 to 41.
2009-10-03 08:26:16.450 WriteAudio: buffer underrun
'video_output' mean = '67056.87', std. dev. = '61482.33', fps = '14.91'
2009-10-03 08:26:16.616 WriteAudio: buffer underrun
2009-10-03 08:26:16.672 WriteAudio: buffer underrun
2009-10-03 08:26:16.756 WriteAudio: buffer underrun
2009-10-03 08:26:16.800 WriteAudio: buffer underrun
2009-10-03 08:26:16.838 WriteAudio: buffer underrun
2009-10-03 08:26:16.843 NVP: Video is 4.04562 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:16.843 NVP: Video is 4.08317 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:17.014 NVP: prebuffering pause
2009-10-03 08:26:17.014 NVP: Waiting for prebuffer..  0 (AL)A(AD)(ad)AA(ad)A         
2009-10-03 08:26:17.015 WriteAudio: buffer underrun
2009-10-03 08:26:17.157 NVP: Waiting for prebuffer..  1 (AL)A(AD)(ad)A(au)(AD)A         
2009-10-03 08:26:17.501 WriteAudio: buffer underrun
2009-10-03 08:26:17.501 NVP: Video is 4.07106 frames behind audio (too slow), dropping frame to catch up.
2009-10-03 08:26:17.558 AFD: HandleGopStart: Key frame distance changed from 41 to 33.
2009-10-03 08:26:17.638 WriteAudio: buffer underrun
2009-10-03 08:26:17.711 NVP: prebuffering pause
2009-10-03 08:26:17.712 NVP: Waiting for prebuffer..  0 A(AD)AA(AL)A(ad)A         
2009-10-03 08:26:17.713 WriteAudio: buffer underrun
2009-10-03 08:26:17.858 NVP: Waiting for prebuffer..  1 A(AD)AA(AL)A(ad)A         
2009-10-03 08:26:18.009 NVP: Waiting for prebuffer..  2 A(AD)AA(AL)A(ad)A         
2009-10-03 08:26:18.159 NVP: Waiting for prebuffer..  3 A(AD)AA(AL)A(ad)A         
2009-10-03 08:26:18.174 NVP: Changing speed to 0
2009-10-03 08:26:18.174 rate: 29.97 speed: 1 skip: 1 = interval 33366
2009-10-03 08:26:18.175 Set video sync frame interval to 33366
'video_output' mean = '33364.22', std. dev. = '2018.28', fps = '29.97'
2009-10-03 08:26:18.343 VideoOutputXv: UpdatePauseFrame() A(AD)AA(AL)A(ad)A         
2009-10-03 08:26:18.466 DPMS Reactivated.
2009-10-03 08:26:19.301 AFD: HandleGopStart: Key frame distance changed from 33 to 30.
2009-10-03 08:26:20.191 AFD: HandleGopStart: Key frame distance changed from 30 to 33.
2009-10-03 08:26:20.398 TV: Attempting to change from WatchingPreRecorded to None
2009-10-03 08:26:20.398 TV: StopStuff() -- begin
2009-10-03 08:26:20.398 TV: StopStuff(): stopping ring buffer[s]
2009-10-03 08:26:20.399 TV: StopStuff(): stopping player[s] (1/2)
2009-10-03 08:26:20.399 TV: StopStuff(): stopping player[s] (2/2)
2009-10-03 08:26:20.399 NVP: Exited decoder loop.
2009-10-03 08:26:20.414 ~OpenGLVideoSync() -- begin
2009-10-03 08:26:20.414 ~OpenGLVideoSync() -- middle
2009-10-03 08:26:20.414 ~OpenGLVideoSync() -- end
2009-10-03 08:26:20.415 VideoOutputXv: dtor
2009-10-03 08:26:20.415 VideoOutputXv: DiscardFrames(1)
2009-10-03 08:26:20.415 VideoBuffers::DiscardFrames(1): A(AD)AA(AL)A(ad)A         
2009-10-03 08:26:20.415 VideoBuffers::DiscardFrames(): A(AD)AAAAAA          -- done()
2009-10-03 08:26:20.415 VideoBuffers::DiscardFrames(1): A(AD)AAAAAA          -- done
2009-10-03 08:26:20.415 VideoOutputXv: DiscardFrames() 3: A(AD)AAAAAA          -- done()
2009-10-03 08:26:20.461 VideoOutputXv: DiscardFrames(1)
2009-10-03 08:26:20.461 VideoBuffers::DiscardFrames(1): A(AD)AAAAAA         
2009-10-03 08:26:20.461 VideoBuffers::DiscardFrames(): A(AD)AAAAAA          -- done()
2009-10-03 08:26:20.461 VideoBuffers::DiscardFrames(1): A(AD)AAAAAA          -- done
2009-10-03 08:26:20.462 VideoOutputXv: DiscardFrames() 3: A(AD)AAAAAA          -- done()
2009-10-03 08:26:20.527 TV: StopStuff() -- end
2009-10-03 08:26:20.528 TV: Changing from WatchingPreRecorded to None
2009-10-03 08:26:20.725 NVP: Exited decoder loop.
2009-10-03 08:26:20.726 ~VideoOutputNull()
2009-10-03 08:26:21.232 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): OpenFile(/Storage/mythTVRecordings/1021_20091002195900.mpg, 1)
2009-10-03 08:26:21.232 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(150624568 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:21.419 AFD: Stream #0, has id 0x1984 codec id MPEG2VIDEO, type Video, bitrate 38810400 at 0x0x90f4900
2009-10-03 08:26:21.421 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:21.421 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:21.421 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:21.421 VDP: LoadBestPreferences(1920x1080, 60)
2009-10-03 08:26:21.421 Using 4 CPUs for decoding
2009-10-03 08:26:21.421 AFD: InitVideoCodec() 0x9089720 id(MPEG2VIDEO) type (Video).
2009-10-03 08:26:21.422 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-03 08:26:21.422 AFD: Using ffmpeg for video decoding
2009-10-03 08:26:21.422 AFD: Looking for decoder for MPEG2VIDEO
2009-10-03 08:26:21.422 AFD: Opened codec 0x9089720, id(MPEG2VIDEO) type(Video)
2009-10-03 08:26:21.422 AFD: Stream #1, has id 0x1985 codec id AC3, type Audio, bitrate 384000 at 0x0x9089c70
2009-10-03 08:26:21.422 AFD: codec AC3 has 6 channels
2009-10-03 08:26:21.422 AFD: Looking for decoder for AC3
2009-10-03 08:26:21.422 AFD: Opened codec 0x9089e10, id(AC3) type(Audio)
2009-10-03 08:26:21.423 AFD: Stream #2, has id 0x1986 codec id AC3, type Audio, bitrate 192000 at 0x0x908a360
2009-10-03 08:26:21.423 AFD: codec AC3 has 2 channels
2009-10-03 08:26:21.423 AFD: Looking for decoder for AC3
2009-10-03 08:26:21.423 AFD: Opened codec 0x9438080, id(AC3) type(Audio)
2009-10-03 08:26:21.423 RingBuf(/Storage/mythTVRecordings/1021_20091002195900.mpg): CalcReadAheadThresh(3046939533 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-10-03 08:26:21.423 Dec: Trying to select track (w/lang)
2009-10-03 08:26:21.423 Dec: Selecting first track
2009-10-03 08:26:21.423 Dec: Selected track #1 in the Unknown language(0)
2009-10-03 08:26:21.423 AFD: Recording has no position -- using libavformat seeking.
2009-10-03 08:26:21.424 AFD: Successfully opened decoder for file: "/Storage/mythTVRecordings/1021_20091002195900.mpg". novideo(0)
2009-10-03 08:26:21.425 VDP: Accepting: cmp(> 0 0) dec(vdpau) cpus(4) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:21.425 VDP: LoadBestPreferences(2048x2048, 0)
2009-10-03 08:26:21.425 VDP: LoadBestPreferences(2048x2048, 60)
2009-10-03 08:26:21.428 VideoOutputNull()
2009-10-03 08:26:21.428 VDP: LoadBestPreferences(1920x1088, 60)
2009-10-03 08:26:21.428 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:21.428 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:21.429 Created data @0xad901020->0xadbfe022
2009-10-03 08:26:21.429 Created data @0xad603020->0xad900022
2009-10-03 08:26:21.429 Created data @0xb11a0020->0xb149d022
2009-10-03 08:26:21.429 Created data @0xb0ea2020->0xb119f022
2009-10-03 08:26:21.429 Created data @0xab0fc020->0xab3f9022
2009-10-03 08:26:21.429 Created data @0xaadfe020->0xab0fb022
2009-10-03 08:26:21.429 Created data @0xaab00020->0xaadfd022
2009-10-03 08:26:21.429 Created data @0xaa802020->0xaaaff022
2009-10-03 08:26:21.429 Created data @0xaa504020->0xaa801022
2009-10-03 08:26:21.429 Created data @0xaa206020->0xaa503022
2009-10-03 08:26:21.429 Created data @0xa9f08020->0xaa205022
2009-10-03 08:26:21.429 Created data @0xa9c0a020->0xa9f07022
2009-10-03 08:26:21.430 Created data @0xa990c020->0xa9c09022
2009-10-03 08:26:21.430 Created data @0xa960e020->0xa990b022
2009-10-03 08:26:21.430 Created data @0xa9310020->0xa960d022
2009-10-03 08:26:21.430 Created data @0xa9012020->0xa930f022
2009-10-03 08:26:21.430 Created data @0xa8b02020->0xa8dff022
2009-10-03 08:26:21.430 Created data @0xa8804020->0xa8b01022
2009-10-03 08:26:21.430 Created data @0xa8506020->0xa8803022
2009-10-03 08:26:21.430 Created data @0xa8208020->0xa8505022
2009-10-03 08:26:21.430 Created data @0xa7f0a020->0xa8207022
2009-10-03 08:26:21.430 Created data @0xa7c0c020->0xa7f09022
2009-10-03 08:26:21.430 Created data @0xa790e020->0xa7c0b022
2009-10-03 08:26:21.430 Created data @0xa7610020->0xa790d022
2009-10-03 08:26:21.430 Created data @0xa7312020->0xa760f022
2009-10-03 08:26:21.430 Created data @0xa7014020->0xa7311022
2009-10-03 08:26:21.430 Created data @0xa6d16020->0xa7013022
2009-10-03 08:26:21.431 Created data @0xa6a18020->0xa6d15022
2009-10-03 08:26:21.431 Created data @0xa671a020->0xa6a17022
2009-10-03 08:26:21.431 Created data @0xa641c020->0xa6719022
2009-10-03 08:26:21.431 Created data @0xa611e020->0xa641b022
2009-10-03 08:26:21.431 Created data @0xa5e20020->0xa611d022
2009-10-03 08:26:21.573 VDP: SetVideoRenderer(null)
2009-10-03 08:26:21.573 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,vdpaubasic) filt()
2009-10-03 08:26:21.573 VDP: New preferences: rend(null) osd(softblend) deint(linearblend,linearblend) filt()
2009-10-03 08:26:21.574 Display Rect  left: 0, top: 0, width: 0, height: 0, aspect: 1.33333
2009-10-03 08:26:21.574 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-03 08:26:21.574 NVP: LoadFilters(''..) -> 0
2009-10-03 08:26:21.574 NVP: ClearAfterSeek(1)
2009-10-03 08:26:21.574 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-10-03 08:26:21.696 NVP: Exited decoder loop.
2009-10-03 08:26:21.708 ~VideoOutputNull()
2009-10-03 08:26:24.857 Deleting UPnP client...
aasland@MythBuntuServer:~/Desktop$ 

```

Note the exact same sections which imply it's not using VDPAU either.:confused:

---

### Post by zymurgist on 2009-10-03
I solved my problem:

I reinstalled everything, from bare metal.

---

### Post by Crash87ss on 2009-10-06
zymurgist, 

glad you solved it ..but a full re-install doesn't sounds like much fun. Would be nice to know what the offending setting/application is. 
I assume you were running mythbuntu, did you have Ubuntu desktop installed? (I don’t)

Is there anything you might have done differently between installs?

Klc5555,

I haven’t tried to transcode with your method – will try tonight – but I have tried transcoding in myth. Now this is something I found very odd. When I run a transcode job on a recording playback is great. When the transcode job is done (or sometime after) back to the pauses. 

In searching for a solution I happened to fix another problem and was able to get audio to work outside myth. Oddly it required running the following commands in terminal:

```
speaker-test -c2 --device cards.pcm.iec958 --rate 44100
speaker-test -c2 --device cards.pcm.iec958 --rate 48000 
```

This is documented on this wiki: [http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound) 

Now that audio works outside Myth, I tested the recordings in mplayer and VLC. They both play with no issues. 

I’ve also tried (from the above wiki) forcing all sound directly to SPDIF (bypassing all mixing). This had no apparent effect. 


In a previous post I mention trying to us XvMC, but I found out it does not work on 8000 series Nvidia cards (earlier I mentioned a 6400 that is in error, it is actually a 8400). 

I will try transcoding the way klc5555 mentioned and post the results. I will also post any relevant portion of the frontend log.

---

### Post by zymurgist on 2009-10-06
I was running on Mythbuntu, this time I reinstalled from Ubuntu then added Myth. 

No kidding it's irritating. The worst part is that while myth is now working well, other things aren't. Like a ndiswrapper for my wlan that locks up hard a couple times a day, and a vncserver that lets me see the desktop but then freezes.

The closer I we get to 10.22.09 and I don't have this functioning as a wife-proof and reliable PVR, the more likely I'm going to give Myth and Ubuntu a solid boot in the rear and install win7 - provided my buddy [who has kids and doesn't have two weeks to fiddle with getting Ubuntu working] does his first and it lives up to its hype. 

But at least I'll end on the note that I am very impressed with what the Linux community has acheived with Myth and Ubuntu .. and I hope to give it one more shot before throwing in the towel.

---

### Post by Crash87ss on 2009-10-06
> The closer I we get to 10.22.09 and I don't have this functioning as a wife-proof and reliable PVR

something thats wife-proof? now thats funny :)

---

### Post by Crash87ss on 2009-10-06
I tired mythtrancode in terminal on a recording that was skipping. Here is my output:

```
james@MythTv:~/Desktop$ mythtranscode --mpeg2 -c 2311 -s 20091004210000
2009-10-06 
17:33:44.704 Using runtime prefix = /usr
2009-10-06 
17:33:44.705 Empty LocalHostName.
2009-10-06 
17:33:44.740 New DB connection, total: 1
2009-10-06 
17:33:44.750 Closing DB connection named 'DBManager0'
2009-10-06 
17:33:44.751 Enabled verbose msgs: important
2009-10-06 
17:33:44.755 New DB connection, total: 2

Mux rate: 19.77 Mbit/s
2009-10-06 
17:35:46.707 Frame 3 > 2. Corruption likely at pos: 2224356780
2009-10-06 
17:35:47.011 Frame 3 > 2. Corruption likely at pos: 2225219512
2009-10-06 
17:35:47.154 Frame 3 > 2. Corruption likely at pos: 2225610176
2009-10-06 
17:35:47.368 Frame 17 > 8. Corruption likely at pos: 2226217980

ICE default IO error handler doing an exit(), pid = 4916, errno = 32

james@MythTv:~/Desktop$ 
```

Looks to me like it didn't finish... did seem to want to transcode inside myth either. 

Another recording (The Simpsons :)), which I had myth transcode while I watched (no errors) now has no sound. The transcode worked as it is now a .nuv file. Any idea where the sound went?

I do now have a recording with minimal errors ( ~6 times over 30 minutes) ...not sure how i got it exactly. I did set the recoding profile to Live TV (which i changed from normal to TV only). I'm trying it again now, but i'm not too confident.

---

### Post by klc5555 on 2009-10-07
> **Crash87ss said:**
> I tired mythtrancode in terminal on a recording that was skipping. Here is my output:

```
james@MythTv:~/Desktop$ mythtranscode --mpeg2 -c 2311 -s 20091004210000
2009-10-06 
17:33:44.704 Using runtime prefix = /usr
2009-10-06 
17:33:44.705 Empty LocalHostName.
2009-10-06 
17:33:44.740 New DB connection, total: 1
2009-10-06 
17:33:44.750 Closing DB connection named 'DBManager0'
2009-10-06 
17:33:44.751 Enabled verbose msgs: important
2009-10-06 
17:33:44.755 New DB connection, total: 2

Mux rate: 19.77 Mbit/s
2009-10-06 
17:35:46.707 Frame 3 > 2. Corruption likely at pos: 2224356780
2009-10-06 
17:35:47.011 Frame 3 > 2. Corruption likely at pos: 2225219512
2009-10-06 
17:35:47.154 Frame 3 > 2. Corruption likely at pos: 2225610176
2009-10-06 
17:35:47.368 Frame 17 > 8. Corruption likely at pos: 2226217980

ICE default IO error handler doing an exit(), pid = 4916, errno = 32

james@MythTv:~/Desktop$ 
```

Looks to me like it didn't finish... did seem to want to transcode inside myth either. 

Another recording (The Simpsons :)), which I had myth transcode while I watched (no errors) now has no sound. The transcode worked as it is now a .nuv file. Any idea where the sound went?

I do now have a recording with minimal errors ( ~6 times over 30 minutes) ...not sure how i got it exactly. I did set the recoding profile to Live TV (which i changed from normal to TV only). I'm trying it again now, but i'm not too confident.

The recording that errored out exhibits the type of severe error that mythtranscode has a hard time recovering from. Though the version of mythtranscode in 0.21 does seem much more tolerant of this sort of thing than it was in 0.20.2. 

The Simpson's episode is stranger. Mythtranscode as run from the command line should not have produced a *.nuv (unless it was originally a *.nuv). Your *.mpg should have produced a *.mpg.tmp that had the same container and was in the same format as the original file. 

At any rate, when mythtranscode encounters severe errors in a recording, it sometimes will strip sound rather than simply error out (sometimes it may just introduce severe audio-sync mismatch). Sometimes a second attempt at transcoding the original (with no other changes) will produce a usable transcoded file, rather than an error or a silent movie. You'll have noticed that the file size of the silent transcode in this case is not just a little smaller than the original, but is much smaller (maybe only 2/3rds-3/4ths  the size of the original). This is why one should always keep the original recording around.

The first thing to figure out will be how are these errors are being introduced into the encoding of the original recording. Bad signal strength, not-quite-tight cabling, tuner trouble, cable-company-introduced noise, too much hard disk activity or cpu while recording, etc. Maybe a wonky recording profile too.

For the recordings you already have that have errors which mythtranscode can't handle, the only tool I've found that can do much of anything with them is nuvexport (either the default with ffmpeg, or using transcode).

---

### Post by Crash87ss on 2009-10-07
My previous post may have been confusing. The Simpsons episode was transcoded from mythfrontend. (job options > begin trancode > high quality). I watched the episode while this job was running (no issues while watching).

When a transcode is run I assume the old file is changed to *.mpg.tmp and the new transcoded file is now .mpg and myth fontend will ignore the *.mpg.tmp. Is this true?

---

### Post by klc5555 on 2009-10-07
> **Crash87ss said:**
> My previous post may have been confusing. The Simpsons episode was transcoded from mythfrontend. (job options > begin trancode > high quality). I watched the episode while this job was running (no issues while watching).

When a transcode is run I assume the old file is changed to *.mpg.tmp and the new transcoded file is now .mpg and myth fontend will ignore the *.mpg.tmp. Is this true?

I wrongly assumed you had run mythtranscode --mpeg2 -c <channel> -s <startdatetime> (or -i <inputfilename>) from a prompt Lets you keep total control of the process so you can better see what may be happening. I should have described it better. So:

The output of a lossless ( --mpeg2) mythtranscode on file *.mpg is *.mpg.tmp The .tmp file is the new transcode. It should be just a few Mbytes shorter than the original, as small sound/recording errors will have been corrected. The original is left unchanged. 

What happens now can be set up in various ways. The *.mpg.tmp can be moved to the name of the original file, without renaming the original file. In this case the original recording ceases to exist --replaced by the transcode version. Or, the original file can itself be renamed to (usually) *.mpg.old, before the *.mpg.tmp file is moved to the original *.mpg filename. In this case, the original recording survives as a backup. I don't know how transcoding is set up on your particular backend.

If you were watching _while_ transcoding, you were still watching the original recording. If the file is in use when the 'mv' commands are operating, the effect is seen when the file is closed.

So the sequence of steps involved in checking one of these wonky recordings would have been:

1) Transcode the wonky recording.

mythtranscode --mpeg2 -c -s (or -i)

produces *.mpg.tmp

2) Keep the original:

mv <recordingfilename>.mpg   <recordingfilename>.mpg.old

3) Stick the (very slightly smaller) transcode in the place formerly held by the original recording.

mv <recordingfilename>.mpg.tmp   <recordingfilename>.mpg

4) See if the Myth internal player plays the new version. If it does, great. If not, then restore the .old file to its place as the original recording.

mv <recordingfilename>.mpg.old <recordingfilename>.mpg

and all should be as it was originally.


If the new transcoded recording plays fine but jumping forward/backward in it is a bit mushy, then you need to rebuild the index in it with mythtranscode:

mythtranscode --mpeg2 --buildindex -c -s (or -i)

If errors were being introduced that this sort of transcoding process could whisk away, my thought was that something set up amiss in your recording or playback profile would be likely to cause it. In my own case a year ago, the cause was using 'CPU+' playback profile which on one station at certain resolutions invoked XvMC which my hardware couldn't handle. Until I figured out that I had to use the 'Slim' profile, everything I recorded on the one station had to be transcoded by a script that did mostly what I described above as an automatic user job before I could watch it.  Unless I happened to be watching it in Livetv, where it was OK.

---

### Post by Crash87ss on 2009-10-09
2nd time writing this cause I accidently refreshed my browser and lost what I typed&#8230;grr

Now the short and sweet version. 

I followed klc5555&#8217;s instructions and used mythtrancode on a &#8220;wonky :)&#8221; recording. It made it to 99% and spit out this:

```
ICE default IO error handler doing an exit(), pid = 4916, errno = 32
```

It still created a .mpg.tmp so I tried it anyway, backed up the old and changed the extension on the new. The video played (in myth) with no apperent errors, but there was no sound. I them swapped files again so I could use the original. I did need to do a buildindex on the original because skipping forward and back was not working. Am still have the prebuffer pause issues. I&#8217;d like to try this again on a fresh recoding though. 

While doing all that I thought of trying to play the recordings with mythvideo to see what would happen. I pointed  mythvideo to my recordings directory.
Leaving mplayer as the default the recording played but with no sound. 
Changed the player to Internal, again video played with no sound. 
Had to change my sound setting from ALSA:cards.pcm.ie958 (or something like that) to ALSA:spif

Now here is the kicker. Recording played with no pausing issues. Everything was nice & smooth. But I couldn&#8217;t skip forward or back (it would just restart the recording). In an earlier post I mentioned a file the was trancoded to a .nuv format, which when played through the watch recordings menu had no sound &#8211; it played flawlessly in mythvideo, I was even able to skip forward and back. Recording still play poorly through watch recordings.  

I understand that it doesn&#8217;t make any sense for recording to play through one menu and not the other while using the same player, and while writing this realized the missing sound could have been my config settings.So I want to repeat this experiment to confirm my results. 

I&#8217;ll be pretty busy this weekend, but will post back first thing next week. I will be checking the forum, so any comments, questions concerns? I am determined to figure out the cause of this.

P.S. Thank you for all you help so far klc5555, I really appreciate it!

---

### Post by Crash87ss on 2009-10-09
I also found this post in the archives, seems to apply to my situation

[http://ubuntuforums.org/archive/index.php/t-1240159.html](http://ubuntuforums.org/archive/index.php/t-1240159.html)

---

### Post by zymurgist on 2009-10-09
I'm back! For various reasons I had to reinstall everything - had non-video-issues and broken kernels and I'm not getting into that.

But I'm back on Ubuntu, 185 nVidia drivers, the latest VDPAU, and things are choppy again.

This time I managed to nail it down more - SOME channels are choppy, and from those I get choppy recordings.

So .. now I have logs from non-choppy and logs from choppy channels. I did a compare .. and found these.

First .. not choppy section:

```

2009-10-09 11:34:20.210 VDPAU: Created OSD (1280x720)
2009-10-09 11:34:20.210 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-09 11:34:20.210 Snapping height to avoid scaling: height: 720, top: 0
2009-10-09 11:34:20.210 Snapping width to avoid scaling: width: 1280, left: 0
2009-10-09 11:34:20.210 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-09 11:34:20.211 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-09 11:34:20.211 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:34:20.211 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:34:20.211 VDP: LoadBestPreferences(1280x720, 59.9401)
2009-10-09 11:34:20.212 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-10-09 11:34:20.356 NVP: ClearAfterSeek(1)
2009-10-09 11:34:20.356 VideoOutputXv: ClearAfterSeek()
2009-10-09 11:34:20.356 VideoOutputXv: DiscardFrames(0)
2009-10-09 11:34:20.356 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-10-09 11:34:20.356 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-10-09 11:34:20.356 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-10-09 11:34:20.356 NVP: LoadFilters(''..) -> 0
2009-10-09 11:34:20.357 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-09 11:34:20.357 Set video sync frame interval to 16683
2009-10-09 11:34:20.362 Disabled deinterlacing
2009-10-09 11:34:20.362 AFD: Using vdpau for video decoding
2009-10-09 11:34:20.362 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-09 11:34:20.362 AFD: Opened codec 0x9684a30, id(MPEGVIDEO_VDPAU) type(Video)

```

and here is the CHOPPY log:

```

2009-10-09 11:27:51.719 VDPAU: Created OSD (1280x720)
2009-10-09 11:27:51.719 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-09 11:27:51.719 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-09 11:27:51.719 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-09 11:27:51.719 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:27:51.719 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:27:51.720 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-10-09 11:27:51.720 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-10-09 11:27:51.895 NVP: ClearAfterSeek(1)
2009-10-09 11:27:51.895 VideoOutputXv: ClearAfterSeek()
2009-10-09 11:27:51.896 VideoOutputXv: DiscardFrames(0)
2009-10-09 11:27:51.896 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-10-09 11:27:51.896 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-10-09 11:27:51.896 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-10-09 11:27:51.896 NVP: LoadFilters(''..) -> 0
2009-10-09 11:27:51.896 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-09 11:27:51.896 AFD: Using vdpau for video decoding
2009-10-09 11:27:51.896 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-09 11:27:51.896 AFD: Opened codec 0xb1f91d70, id(MPEGVIDEO_VDPAU) type(Video)

```

TO summarize:

non-choppy: 1280x720, progressive scan.
choppy:     1920x1088, interlaced scan.

Is there a way to force everything 'down' to 1280x720, or am I stuck with what comes in on the cable?

---

### Post by klc5555 on 2009-10-09
> **Crash87ss said:**
> I also found this post in the archives, seems to apply to my situation

[http://ubuntuforums.org/archive/index.php/t-1240159.html](http://ubuntuforums.org/archive/index.php/t-1240159.html)

The link does indeed seem to apply to your situation, and if you're using vdpau might be worth testing to see if it fixes the playback issue.

Perhaps playback of these recordings should also be tested with VDPAU disabled.

---

### Post by Crash87ss on 2009-10-15
> **zymurgist said:**
> I'm back! For various reasons I had to reinstall everything - had non-video-issues and broken kernels and I'm not getting into that.

But I'm back on Ubuntu, 185 nVidia drivers, the latest VDPAU, and things are choppy again.

This time I managed to nail it down more - SOME channels are choppy, and from those I get choppy recordings.

So .. now I have logs from non-choppy and logs from choppy channels. I did a compare .. and found these.

First .. not choppy section:

```

2009-10-09 11:34:20.210 VDPAU: Created OSD (1280x720)
2009-10-09 11:34:20.210 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-09 11:34:20.210 Snapping height to avoid scaling: height: 720, top: 0
2009-10-09 11:34:20.210 Snapping width to avoid scaling: width: 1280, left: 0
2009-10-09 11:34:20.210 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-09 11:34:20.211 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-09 11:34:20.211 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:34:20.211 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:34:20.211 VDP: LoadBestPreferences(1280x720, 59.9401)
2009-10-09 11:34:20.212 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-10-09 11:34:20.356 NVP: ClearAfterSeek(1)
2009-10-09 11:34:20.356 VideoOutputXv: ClearAfterSeek()
2009-10-09 11:34:20.356 VideoOutputXv: DiscardFrames(0)
2009-10-09 11:34:20.356 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-10-09 11:34:20.356 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-10-09 11:34:20.356 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-10-09 11:34:20.356 NVP: LoadFilters(''..) -> 0
2009-10-09 11:34:20.357 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2009-10-09 11:34:20.357 Set video sync frame interval to 16683
2009-10-09 11:34:20.362 Disabled deinterlacing
2009-10-09 11:34:20.362 AFD: Using vdpau for video decoding
2009-10-09 11:34:20.362 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-09 11:34:20.362 AFD: Opened codec 0x9684a30, id(MPEGVIDEO_VDPAU) type(Video)

```

and here is the CHOPPY log:

```

2009-10-09 11:27:51.719 VDPAU: Created OSD (1280x720)
2009-10-09 11:27:51.719 VideoOutputXv: VDPAU Colorkey: 0x20202 (depth 24)
2009-10-09 11:27:51.719 Display Rect  left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2009-10-09 11:27:51.719 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2009-10-09 11:27:51.719 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:27:51.719 VDP: GetFilteredDeint() : vdpau -> 'vdpauadvanceddoublerate'
2009-10-09 11:27:51.720 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAA
2009-10-09 11:27:51.720 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-10-09 11:27:51.895 NVP: ClearAfterSeek(1)
2009-10-09 11:27:51.895 VideoOutputXv: ClearAfterSeek()
2009-10-09 11:27:51.896 VideoOutputXv: DiscardFrames(0)
2009-10-09 11:27:51.896 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA
2009-10-09 11:27:51.896 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAA -- done
2009-10-09 11:27:51.896 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAA -- done()
2009-10-09 11:27:51.896 NVP: LoadFilters(''..) -> 0
2009-10-09 11:27:51.896 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1080) ->Interlaced Scan
2009-10-09 11:27:51.896 AFD: Using vdpau for video decoding
2009-10-09 11:27:51.896 AFD: Looking for decoder for MPEGVIDEO_VDPAU
2009-10-09 11:27:51.896 AFD: Opened codec 0xb1f91d70, id(MPEGVIDEO_VDPAU) type(Video)

```

TO summarize:

non-choppy: 1280x720, progressive scan.
choppy:     1920x1088, interlaced scan.

Is there a way to force everything 'down' to 1280x720, or am I stuck with what comes in on the cable?

Sorry, been busy this week. Is there something in you playback profile cause choppy HD? Set your profile so whatever it is using for the lower rez its the same for higher rez.
 
Also check you CPU usage during each instance.

I came across another thread (maybe another forum) where someones cable signal was too strong.. I'll post a link if I find it. 

BTW - havn't given up on my issue, just been busy this week. the "watch recordings" interface does something different than "watch tv" or "watch videos" ...just need to figure out what

---

### Post by zymurgist on 2009-10-17
> **Crash87ss said:**
> Sorry, been busy this week. Is there something in you playback profile cause choppy HD? Set your profile so whatever it is using for the lower rez its the same for higher rez.
 
Also check you CPU usage during each instance.

I came across another thread (maybe another forum) where someones cable signal was too strong.. I'll post a link if I find it. 

BTW - havn't given up on my issue, just been busy this week. the "watch recordings" interface does something different than "watch tv" or "watch videos" ...just need to figure out what

I am using VDPAU for all resolutions - no change in settings as far as I can tell.

CPU usage on 'low' rez (1280x720) = 35% 
CPU usage on 'high' rez (1920x1080) = 155%

(two cores .. so 17% and 75%). The PC is definitely working harder on the higher resolutions, but not maxed out.

---

### Post by zymurgist on 2009-10-19
Made some progress: I can now play recorded programs and videos without jerkiness.

I tried vlc outside of Myth, and it was smooth. Then I tried mplayer outside of Myth, and it was choppy. So I went here: 

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

and built mplayer with vdpau, and then it worked - nice and smooth at 1920x1080. I went into the video settings and setup Myth to use the mplayer vdpau settings:

```

mplayer -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau <filename>

``` 

and that had no effect - odd. 

Then went into the playback settings, set VDPAU for <= 1280x720, and Xvmc for anything bigger. 

Now I can play video and watch recordings of 1920x1080 rez nice and smooth, but uses lots of CPU. But live TV is still choppy in all cases >= 1280x720 ... and the logs show it is using xvmc.

To summarize:

1. In Myth, Xvmc is faster than VDPAU but uses more CPU.
2. External mplayer plays big (1920+) rez with vdpau just fine.
3. Internal player plays big rez with vdpau but is choppy.
4. All this proves my hardware can do it.

Conclusion: 

Something in Myth|VDPAU isn't working right.

Any ideas?

---

### Post by Crash87ss on 2009-10-19
> **zymurgist said:**
> 

Now I can play video and watch recordings of 1920x1080 rez nice and smooth, but uses lots of CPU. But live TV is still choppy in all cases >= 1280x720 ... and the logs show it is using xvmc.

To summarize:

1. In Myth, Xvmc is faster than VDPAU but uses more CPU.
2. External mplayer plays big (1920+) rez with vdpau just fine.
3. Internal player plays big rez with vdpau but is choppy.
4. All this proves my hardware can do it.

Conclusion: 

Something in Myth|VDPAU isn't working right.

Any ideas?

Ok.. so live TV is choppy with VDPAU or XVMC? Logs are still showing prebuffer pause?
 
What if you set a show to record, then played back from the "watch recordings" menu? I think the key is to figure out what is different about "watch tv".

Could the OSD be hogging some resources? Maybe set it to something simpler and turn off fade.

---

### Post by zymurgist on 2009-10-19
LiveTV is choppy with vdpau, but only at higher rez (1920x720). 

WIth vdpau, logs show prebuffer pauses.

Watching recorded shows are also choppy. If the original was choppy .. the recorded show is choppy.

I agree .. need to find out why myth's player is choppy when playing back high rez with vdpau (I thought it was mplayer .. but since mplayer plays the vid's smoothly outside myth, something else is going on).

---

### Post by Crash87ss on 2009-10-20
Looks like I solved my problem!

Recordings seemed to work everywhere except when accessed through "watch recordings". The only thing that I could think of being different is the preview for watch recordings. So I turned it off... and so far so good. Hopefully I didn't just jinx myself.

Now... Any idea why that might be a problem?

Zymurgist, 

Looks like you having the opposite problem than what I was having.
What capture card are you using? This may be a silly comment, but could there be a bandwitdh issue when HD is playing?

---

### Post by zymurgist on 2009-10-20
I am using the Hauppage 2250 capture card. Being a new card, there is very poor Linux support for it - HD only. 

Since video plays fine in mplayer outside of Myth, I doubt there is a bandwidth issue.

---

