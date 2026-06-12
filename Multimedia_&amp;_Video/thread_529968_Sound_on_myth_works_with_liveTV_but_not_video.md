---
title: "Sound on myth: works with liveTV but not video"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by pgcudahy on 2007-08-19
I've got a problem with no sound when I try to play videos with MythVideo but live tv and TV recordings with MythTV do have sound. I'm pretty sure the video sound was working before I started messing around with getting TV-out working with my PVR-350. Anyone got any ideas on what could have gone wrong? Thanks
-Patrick

---

### Post by newlinux on 2007-08-20
A bit more information would be helpful. Are you using analog or digital out? What is the format of the mythvideo files and what type of audio do they have? I've had similar problems which dealt with playing analog sources over the digital output. The best way to find out what is going on is to run mythfrontend from a terminal, and then see what the output is on a file you try to play that doesn't have sound. I recommend running

```

mythfrontend -v playback

```
to get more information about what is going on, and post back.

---

### Post by pgcudahy on 2007-09-07
This is going to sound dumb but how do I launch mythtv from the command line? When I try it from my normal user I run into a whole pile of errors that I've tried working through. Normally my box boots into user "mythtv" and launches myth from there but "mythtv" was set up by the Ubuntu installer and I don't know its password. Is there a default?

---

### Post by pgcudahy on 2007-09-08
Okay, scratch that last bit. Here's mythfrontend's output. I've narrowed it down and my problem is that audio works with liveTV and even MPlayer, but not with mythtv's internal DVD player.


```

2007-09-08 16:26:01.722 Using runtime prefix = /usr
2007-09-08 16:26:01.786 DPMS is active.
2007-09-08 16:26:01.801 New DB connection, total: 1
2007-09-08 16:26:01.807 Connected to database 'mythconverg' at host: localhost
2007-09-08 16:26:01.809 Total desktop dim: 720x480, with 1 screen[s].
2007-09-08 16:26:01.812 Using screen 0, 720x480 at 0,0
2007-09-08 16:26:01.822 user: 1000 effective user: 1000 before privileged thread
2007-09-08 16:26:01.822 user: 1000 effective user: 1000 run_priv_thread
2007-09-08 16:26:01.822 user: 1000 effective user: 1000 after privileged thread
2007-09-08 16:26:01.825 Current Schema Version: 1160
2007-09-08 16:26:01.825 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-09-08 16:26:01.825 Enabled verbose msgs:  important general playback
2007-09-08 16:26:02.009 max_width: 720 max_height: 480
2007-09-08 16:26:02.236 Total desktop dim: 720x480, with 1 screen[s].
2007-09-08 16:26:02.238 Using screen 0, 720x480 at 0,0
2007-09-08 16:26:02.239 Switching to square mode (G.A.N.T.)
2007-09-08 16:26:02.253 Using the Qt painter
2007-09-08 16:26:02.581 Joystick disabled.
2007-09-08 16:26:02.944 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-09-08 16:26:02.969 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-09-08 16:26:03.046 Registering Internal as a media playback plugin.
2007-09-08 16:26:03.075 Registering MythDVD DVD Media Handler as a media handler ext()
2007-09-08 16:26:03.077 Registering MythDVD VCD Media Handler as a media handler ext()
2007-09-08 16:26:08.499 New DB connection, total: 2
2007-09-08 16:26:08.500 Connected to database 'mythconverg' at host: localhost
2007-09-08 16:26:08.558 TV: Attempting to change from None to WatchingPreRecorded
2007-09-08 16:26:08.558 RingBuf(dvd://dev/dvd): OpenFile(dvd://dev/dvd, 12)
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: MIAMI_VICE
libdvdnav: DVD Serial Number: 355e79f2
libdvdnav: DVD Title (Alternative): UNRATED_WS_R1
libdvdnav: Unable to find map file '/home/pgcudahy/.dvdnav/MIAMI_VICE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2007-09-08 16:26:09.222 Opened DVD device at //dev/dvd
2007-09-08 16:26:09.222 There are 11 titles on the disk
2007-09-08 16:26:09.222 Title 0 has 0 parts.
2007-09-08 16:26:09.222 Title 1 has 21 parts.
2007-09-08 16:26:09.223 Title 2 has 2 parts.
2007-09-08 16:26:09.223 Title 3 has 2 parts.
2007-09-08 16:26:09.223 Title 4 has 2 parts.
2007-09-08 16:26:09.223 Title 5 has 2 parts.
2007-09-08 16:26:09.223 Title 6 has 2 parts.
2007-09-08 16:26:09.223 Title 7 has 2 parts.
2007-09-08 16:26:09.223 Title 8 has 2 parts.
2007-09-08 16:26:09.223 Title 9 has 7 parts.
2007-09-08 16:26:09.223 Title 10 has 2 parts.
2007-09-08 16:26:09.223 RingBuf(//dev/dvd): CalcReadAheadThresh(4000 KB)
                         -> threshhold(146 KB) min read(32 KB) blk size(64 KB)
2007-09-08 16:26:09.227 DPMS Deactivated 
2007-09-08 16:26:09.265 DVDNAV_HIGHLIGHT: display==1, palette==0, sx==0, sy==0, ex==55848, ey==2190, pts==0, buttonN==1
2007-09-08 16:26:09.266 DVDNAV_VTS_CHANGE: old_vtsN==0, new_vtsN==-1, aspect: 3, perm: 1
2007-09-08 16:26:09.266 DVDNAV_CELL_CHANGE: pg_length == 270000, pgc_length == 270000, cell_start == 0, pg_start == 0, title == 0, part == 0 titleParts 0
2007-09-08 16:26:09.266 DVDNAV_SPU_CLUT_CHANGE happened.
2007-09-08 16:26:09.266 DVDNAV_SPU_STREAM_CHANGE: physical_wide==-1, physical_letterbox==-1, physical_pan_scan==-1, logical==15368320
2007-09-08 16:26:09.266 DVDNAV_AUDIO_STREAM_CHANGE: physical==0, logical==-1
2007-09-08 16:26:09.426 detectInterlace(Ignore Scan, Interlaced Scan, 29.97, 480) ->Interlaced Scan
2007-09-08 16:26:09.426 RingBuf(//dev/dvd): CalcReadAheadThresh(8000 KB)
                         -> threshhold(292 KB) min read(32 KB) blk size(128 KB)
2007-09-08 16:26:09.426 Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2007-09-08 16:26:09.426 Position map filled from DB to: 89
2007-09-08 16:26:09.426 SyncPositionMap prerecorded, from DB: 1 entries
2007-09-08 16:26:09.426 SyncPositionMap, new totframes: 89, new length: 3, posMap size: 1
2007-09-08 16:26:09.427 Position map found
2007-09-08 16:26:09.436 Opening ALSA audio device 'default'.
2007-09-08 16:26:09.453 mixer unable to find control Master 1
2007-09-08 16:26:09.457 NVP: Enabling Audio
2007-09-08 16:26:09.489 IVD: Init() -- begin
2007-09-08 16:26:09.490 Over/underscan. V: -0.05, H: -0.1, XOff: 0, YOff: 0
2007-09-08 16:26:09.490 Display Rect  left: 72, top: 24, width: 576, height: 432, aspect: 1.33333
2007-09-08 16:26:09.490 Video Rect    left: 0, top: 0, width: 720, height: 480, aspect: 1.33
2007-09-08 16:26:09.490 Display Rect  left: 72, top: 24, width: 576, height: 432, aspect: 1.33333
2007-09-08 16:26:09.490 Video Rect    left: 0, top: 0, width: 720, height: 480, aspect: 1.33
2007-09-08 16:26:09.491 IVD: Open() -- begin
2007-09-08 16:26:09.491 IVD: Open() -- end
2007-09-08 16:26:09.495 IVD: ClearOSD
2007-09-08 16:26:09.532 Using the PVR-350 decoder/TV-out
2007-09-08 16:26:09.532 IVD: Init() -- end
2007-09-08 16:26:10.048 NVP: ClearAfterSeek(1)
2007-09-08 16:26:10.050 TV: StartPlayer(): took 785 ms to start player.
2007-09-08 16:26:10.050 TV: Changing from None to WatchingPreRecorded
2007-09-08 16:26:10.066 DVDNAV_HOP_CHANNEL happened.
2007-09-08 16:26:10.067 DVDNAV_CELL_CHANGE: pg_length == 270000, pgc_length == 270000, cell_start == 0, pg_start == 0, title == 0, part == 0 titleParts 0
2007-09-08 16:26:10.067 DVDNAV_SPU_CLUT_CHANGE happened.
2007-09-08 16:26:10.067 DVDNAV_SPU_STREAM_CHANGE: physical_wide==-1, physical_letterbox==-1, physical_pan_scan==-1, logical==15368320
2007-09-08 16:26:10.067 DVDNAV_AUDIO_STREAM_CHANGE: physical==0, logical==-1
2007-09-08 16:26:10.082 DVDNAV_CELL_CHANGE: pg_length == 630000, pgc_length == 720000, cell_start == 0, pg_start == 0, title == 0, part == 0 titleParts 0
2007-09-08 16:26:10.082 DVDNAV_SPU_CLUT_CHANGE happened.
2007-09-08 16:26:10.083 DVDNAV_SPU_STREAM_CHANGE: physical_wide==-1, physical_letterbox==-1, physical_pan_scan==-1, logical==15368320
2007-09-08 16:26:10.083 DVDNAV_AUDIO_STREAM_CHANGE: physical==0, logical==-1
2007-09-08 16:26:10.488 DVDNAV_VTS_CHANGE: old_vtsN==-1, new_vtsN==2, aspect: 0, perm: 3
2007-09-08 16:26:10.488 DVDNAV_CELL_CHANGE: pg_length == 15405000, pgc_length == 15495000, cell_start == 0, pg_start == 0, title == 2, part == 1 titleParts 2
2007-09-08 16:26:10.488 DVDNAV_SPU_CLUT_CHANGE happened.
2007-09-08 16:26:10.489 DVDNAV_SPU_STREAM_CHANGE: physical_wide==-1, physical_letterbox==-1, physical_pan_scan==-1, logical==15368320
2007-09-08 16:26:10.489 DVDNAV_AUDIO_STREAM_CHANGE: physical==0, logical==-1
2007-09-08 16:26:11.078 IVD: write0 !canwrite
2007-09-08 16:26:11.138 IVD: write0 !canwrite
2007-09-08 16:26:11.198 IVD: write0 !canwrite

etc, etc.

2007-09-08 16:26:21.122 IVD: write0 !canwrite
2007-09-08 16:26:21.153 TV: Attempting to change from WatchingPreRecorded to None
2007-09-08 16:26:21.153 TV: StopStuff() -- begin
2007-09-08 16:26:21.153 TV:  StopStuff() -- get dvd player out of still frame or wait status
2007-09-08 16:26:21.153 TV: StopStuff(): stopping ring buffer[s]
2007-09-08 16:26:21.153 TV: StopStuff(): stopping player[s] (1/2)
2007-09-08 16:26:21.153 TV: StopStuff(): stopping player[s] (2/2)
2007-09-08 16:26:21.194 IVD: write0 !canwrite
2007-09-08 16:26:21.202 NVP: Exited decoder loop.
2007-09-08 16:26:21.239 IVD: Close() -- begin
2007-09-08 16:26:21.239 IVD: Stop(1) -- begin
2007-09-08 16:26:21.255 IVD: Stop(1) -- end
2007-09-08 16:26:21.255 IVD: Close() -- end
2007-09-08 16:26:21.255 IVD: ClearOSD
2007-09-08 16:26:21.339 TV: StopStuff() -- end
2007-09-08 16:26:21.339 TV: Changing from WatchingPreRecorded to None
2007-09-08 16:26:22.355 DPMS Reactivated.
2007-09-08 16:26:23.305 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-09-08 16:26:23.306 Using protocol version 31
```

---

### Post by frankb on 2007-09-09
My setup is very similar to yours, and I have the same problem: no sound when playing DVDs with the mythdvd internal player. I can't tell you how to fix the  sound with the internal player, but I solved my problem by changing the player to xine. Try setting your DVD player command to "xine -phfg --no-splash dvd://dev/dvd".

---

### Post by pgcudahy on 2007-09-12
Are you using a pvr-350 for your TV out? I found out according to [this thread]("http://www.gossamer-threads.com/lists/mythtv/users/95788?search_string=internal%20dvd%20pvr-350;#95788") that pvr-350s won't do DVD audio output with the internal player.

---

### Post by dsauter on 2007-09-14
I have a PVR250 and can confirm that MythDVD sound doesn't work for me.  I have been using the XINE workaround with great success.

---

### Post by pvrbyrich on 2007-09-22
Me too.  Two-week-old feisty, MythTV 0.20.2, with just-installed MythDVD.  Sound was ok when DVD was played with Ogle, but no sound at all with MythDVD.  Using nVidia card's DVI out for video, on-board SoundMax ADI1988 for audio.  Does anyone have an answer other than "don't use MythDVD"?

---

### Post by newlinux on 2007-09-29
Everyone's problem is probably a little bit different. So for each person that wants help you should post your sound card model, which sound output you are using (digital/analog), your mythtv sound settings (which device you are telling it to use, something such as ALSA:default of /dev/dsp) and you .asoundrc file. I had a problem where my sound wouldn't work through digital for some videos (in mythvideo, not Mythdvd) through SPDIF which I was able to fix through changes in my .asoundrc file. There are a lot of variables.

---

