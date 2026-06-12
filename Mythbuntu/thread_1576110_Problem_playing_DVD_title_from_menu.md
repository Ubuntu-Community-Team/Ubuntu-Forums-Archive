---
title: "Problem playing DVD title from menu"
date: 2010-09-16
forum: Mythbuntu
---

### Post by bcg30506 on 2010-09-16
I've got mythbuntu 10.04 setup with 3 menu items under Optical Disks to play DVDs.  I have one that uses the Internal player, one that uses mplayer, and one that uses VLC.  My preferred one is mplayer as it seems to play most discs the best and with dvdnav:// supports menus.

Today though, I was playing disc 2 of the Battlestar Galactica series and none of them would work. Disc 1 played fine.  On all 3 programs I get the DVD menu and can select Episodes to get the submenu.  But when I choose Play to watch an episode, all 3 players crash back to the MythTV menu.

If I use mplayer dvd://1 or mplayer dvd://2 from the command line, the titles play fine with no issues whatsoever.  I'm pasting the mplayer output from the menu crash as well as the log entries from the Internal player below.  Does anyone know what can cause this while the disc still plays from the command line if you bypass the disc menu?

Mplayer output:
```
VO: [vdpau] 720x480 => 854x480 MPEG2 VDPAU acceleration  [fs]
[ac3 @ 0x89a61c0]incomplete frame  0.065  87/ 87  5% 12%  0.4% 6 0 
[ac3 @ 0x89a61c0]incomplete frame  0.202  44/ 44 11% 44%  1.3% 6 0 
libdvdread: Can't seek to block 32508537   1/  1  9% 58%  1.1% 6 0 
libdvdread: Invalid IFO for title 3 (VTS_03_0.IFO).
libdvdnav: ifoOpenVTSI failed
A:   2.0 V:   1.8 A-V:  0.173 ct:  0.294   1/  1  9% 58%  1.1% 6 0 

Exiting... (End of file)

```

MythTV Internal player log:
```
2010-09-16 14:39:33.487 AFD: Warning, video codec 0xa49c0b0 id(MPEG2VIDEO) type (Video) already open.
2010-09-16 14:39:33.488 AFD: Opened codec 0xa62d1710, id(DVD_SUBTITLE) type(Subtitle)
2010-09-16 14:39:33.488 NVP(0): Disabling Audio, params(-1,-1,-1)
2010-09-16 14:39:33.495 AFD: Warning, video codec 0xa49c0b0 id(MPEG2VIDEO) type (Video) already open.
2010-09-16 14:39:33.495 AFD: Opened codec 0xa7871ba0, id(DVD_SUBTITLE) type(Subtitle)
2010-09-16 14:39:33.498 AFD: Warning, video codec 0xa49c0b0 id(MPEG2VIDEO) type (Video) already open.
2010-09-16 14:39:33.498 AFD: codec AC3 has 0 channels
2010-09-16 14:39:33.499 AFD: Opened codec 0xa7871290, id(AC3) type(Audio)
2010-09-16 14:39:33.539 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-09-16 14:39:33.540 Opening ALSA audio device 'default'.
2010-09-16 14:39:33.580 Mixer unable to find control Master 1
2010-09-16 14:39:33.580 mixer unable to find control Master 1
2010-09-16 14:39:33.580 Mixer unable to find control Master 1
2010-09-16 14:39:33.580 mixer unable to find control Master 1
2010-09-16 14:39:33.581 NVP(0): Enabling Audio
libdvdnav: ifoOpenVTSI failed
2010-09-16 14:39:46.174 DVDNAV_STOP
2010-09-16 14:39:46.174 [ac3 @ 0x1cbe960]incomplete frame
2010-09-16 14:39:46.174 DVDRB: safe_read: called after DVDNAV_STOP
2010-09-16 14:39:46.175 WriteAudio: buffer underrun
2010-09-16 14:39:46.215 ~OpenGLVideoSync() -- closing opengl vsync
2010-09-16 14:39:46.270 TV: Attempting to change from WatchingDVD to None
2010-09-16 14:39:46.270 TV: Changing from WatchingDVD to None

```

---

### Post by bcg30506 on 2010-09-17
Okay, this is bizarre.  After eject the disc and watching another movie, then putting this disc back in the next day, I can now get to the titles from the episode menu using mplayer.  Strange.

---

