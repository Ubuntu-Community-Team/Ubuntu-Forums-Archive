---
title: "Encrypted DvD problem. Tried everything I found."
date: 2010-02-13
forum: Multimedia Software
---

### Post by d0ubl3a on 2010-02-13
Hello, I encountered a problem. I cannot play some dvds. I installed the Medibuntu repositories, I   installed libdvdcss, I tried installing libdvdcss2... etc. I tried quite   a lot of multimedia players. I played non-encrypted dvds with VLC and   it worked just fine. But when I start this one... or these ones...   because it is a 14 DVD piano course...  I  get the menu... but I can't  press any of the buttons. If I open the  dvds and go to video... there  are a couple of .bup, .info and .vob  files, and I can't open them with  VLC.
I tried to play them with totem, but it does not work. If I want to open   the disc I get the error:
"Could not open location; you might not have permission to open the   file."
And if I try to open the .vob files I get the error:
"Could not read from resource"
I tried opening the disc with totem from the terminal... and this is   what I get:


```
libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: no file info
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start ():  /GstPlayBin2:razz:lay/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists

libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start ():  /GstPlayBin2:razz:lay/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists
```
Please help me... it's really bugging  me... and I need those courses...
Oh yes I forgot to mention... I'm using Ubuntu 9.10 karmic koala, x32.

---

