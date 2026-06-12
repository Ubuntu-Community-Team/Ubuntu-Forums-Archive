---
title: "Totem and VLC Stopped Working"
date: 2009-11-07
forum: Multimedia Software
---

### Post by bcerge on 2009-11-07
I was watching some avi files through totem, and wanted to display them on my television, so I did the mirrored monitor and hooked my sound up through my stereo, after I did this, totem movie player and vlc do not play my avi files, or any video files at all. when i load the movie, it shows up for a split second and just closes, no clue why it does that, but i cant watch anything now =(

anyone have a thought?

---

### Post by Mac_D83 on 2009-11-20
Totem and vlc stopped working for me too after updating my 9.10 system :-(

I found a fix at [http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html](http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html)

I installed the libavcodec52 which removed a lot of my codecs in the process. Afterwards totem asked if it could install a codec and I accepted it. Totem installed the codec it needed and I could play videos again!

---

### Post by dapple_rose on 2009-11-20
I have a similar problem. I'm running Ubuntu 9.10 kernel 2.6.31-14-generic Gnome 2.28.1 on an AMD sempron processor with 2 GB memory.  VlC gives the following error messages - Can anyone shed any light on this?

VLC media player 1.0.2 Goldeneye
[0x9529b8] main interface error: no interface module matched "globalhotkeys,none"
[0x9529b8] main interface error: no suitable interface module
[0x839888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x839888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 2 (X_ChangeWindowAttributes)
  Resource id:  0x4e0004e
[0x1e3eaf8] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

---

