---
title: "VLC closes when trying to play a file"
date: 2010-03-13
forum: Multimedia Software
---

### Post by hdrip on 2010-03-13
When I try to play an .avi file VLC closes right away.  Here is the output from Terminal...

VLC media player 1.0.3 Goldeneye
[0x95122f0] main interface error: no interface module matched "globalhotkeys,none"
[0x95122f0] main interface error: no suitable interface module
[0x9472140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9472140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb7320378] pulse audio output: No. of Audio Channels: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102
Segmentation fault


Any help is appreciated.

---

### Post by hdrip on 2010-03-13
Never mind I found the solution.  Sorry again for the double post.

---

