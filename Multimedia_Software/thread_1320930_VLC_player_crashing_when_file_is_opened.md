---
title: "VLC player crashing when file is opened"
date: 2009-11-09
forum: Multimedia Software
---

### Post by dangman123 on 2009-11-09
Ubuntu 9.10.  Other movie players work fine.  VLC closes as soon as the movie begins to play.  Any help would be greatly appreciated.

Terminal information:

vlc
VLC media player 1.0.2 Goldeneye
[0x8f17660] main interface error: no interface module matched "globalhotkeys,none"
[0x8f17660] main interface error: no suitable interface module
[0x8e80140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8e80140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x920fd78] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x9209d18] pulse audio output: No. of Audio Channels: 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103

---

### Post by andrew.46 on 2009-11-10
Hi dangman,

> **dangman123 said:**
> 
```
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
```
 

Perhaps try a different video output? I attach a screenshot to demonstrate the options.

Andrew

---

### Post by dangman123 on 2009-11-10
Thanks for that changed video output to: **open GL video output**

working a treat now, would have been stuffed without your help, thanks andrew.46!

---

### Post by andrew.46 on 2009-11-10
Hi dangman,

> **dangman123 said:**
> working a treat now, would have been stuffed without your help, thanks andrew.46!

Excellent news :).

Andrew

---

