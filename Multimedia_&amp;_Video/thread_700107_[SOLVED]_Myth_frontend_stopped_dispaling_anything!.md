---
title: "[SOLVED] Myth frontend stopped dispaling anything!"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by tps on 2008-02-18
I have a Gateway MX8739 laptop, Widescreen, Intel 945 video. I had installed Gutsy on it right when it came out, and everyhing was fine. I could run the laptop as one of my frontends. I have been using Mythtv for a few years, and have quite a bit of experience working out the bugs. However, this one has me stumped. Sometime in the last 2 months, something broke myth-frontend. When I start it up, the screen goes black, and I get a blue bordered box (looks like the graphic from a beveled outline) and it will just sit like that until I press a key. After a while, I get a square blue filled box the height of my screen, and there it'll sit. I can still changes screens, etc, it's like Myth forgot how to write to the screen.  Hitting escape a couple of times will give me another box at the bottom of the screen, and if I hit the up/down cursor buttons, I see a hilited bar move up and down. That's the normal 3 exit messages. I just can't see them!

Is a X11 lib fubared? Has anyone seen anything like this?

the log looks like:

Starting mythfrontend.real..
2008-02-11 20:24:33.521 Current Schema Version: 1160
2008-02-11 20:24:33.522 mythfrontend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-02-11 20:24:33.523 Enabled verbose msgs:  important general
2008-02-11 20:24:33.876 Total desktop dim: 1440x900, with 1 screen[s].
2008-02-11 20:24:34.609 Using screen 0, 1440x900 at 0,0
2008-02-11 20:24:34.610 Switching to wide mode (MythCenter-wide)
2008-02-11 20:24:34.633 Using the Qt painter
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200008
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2008-02-11 20:24:34.895 Joystick disabled.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200016
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200017
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200018
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x420001a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200016
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200017
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x4200018
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x420001a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  154
  Minor opcode:  4
  Resource id:  0x420001e
X Error: RenderBadPicture (invalid Picture parameter) 169
  Major opcode:  154
  Minor opcode:  6
  Resource id:  0x420001f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x0
X Error: RenderBadPicture (invalid Picture parameter) 169
  Major opcode:  154
  Minor opcode:  5
  Resource id:  0x420001f
X Error: RenderBadPicture (invalid Picture parameter) 169
  Major opcode:  154
  Minor opcode:  6
  Resource id:  0x420001f

[hundreds of similar not pasted]

2008-02-11 20:24:35.553 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2008-02-11 20:24:35.573 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-02-11 20:24:35.646 Registering Internal as a media playback plugin.
libpng error: Read Error
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x4200008
2008-02-11 20:24:37.459 New DB connection, total: 2
2008-02-11 20:24:37.462 Connected to database 'mythconverg' at host: 10.0.0.51
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x420040d
2008-02-11 20:24:37.535 Connecting to backend server: 10.0.0.51:6543 (try 1 of 5)
2008-02-11 20:24:37.536 Using protocol version 31
2008-02-11 20:24:37.592 TV: Attempting to change from None to WatchingLiveTV
2008-02-11 20:24:37.593 Using protocol version 31
2008-02-11 20:24:41.103 DPMS Deactivated 
[mpeg @ 0xb74398b0]Parser not found for Codec Id: 94210 !
2008-02-11 20:24:41.234 AFD: Opened codec 0x863e780, id(MPEG2VIDEO) type(Video)
2008-02-11 20:24:41.251 AFD: Opened codec 0x863f410, id(MP2) type(Audio)
2008-02-11 20:24:41.369 Opening ALSA audio device 'default'.
2008-02-11 20:24:41.465 VideoOutputXv: XvMCTex: Init failed
2008-02-11 20:24:41.465 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Video Overlay'
2008-02-11 20:24:42.324 TV: Changing from None to WatchingLiveTV
Unable to launch application
2008-02-11 20:24:42.362 New DB connection, total: 3
2008-02-11 20:24:42.373 Using realtime priority.
2008-02-11 20:24:42.374 Connected to database 'mythconverg' at host: 10.0.0.51
2008-02-11 20:24:45.431 Video timing method: USleep with busy wait
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  19
  Resource id:  0x0


and it goes on from there.

---

### Post by tps on 2008-02-23
Success! For the record, glut3 seems to be non-compatable with at least my video setup. One of the versions of libgl1 that were installed to support glut3 seems to have been the problem. Myth is now back working. However, Second Life is not working as the full GL extentions are needed, which seem to have been provided by glut3 and associated libs.

Oh well...

---

