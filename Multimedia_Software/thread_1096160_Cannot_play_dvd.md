---
title: "Cannot play dvd"
date: 2009-03-14
forum: Multimedia Software
---

### Post by ELD on 2009-03-14
I am trying to play an xfiles dvd in VLC and nothing happens, i ran in terminal and got this:
> 
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: XFILES_DISC6
libdvdnav: DVD Serial Number: 28B862C0
libdvdnav: DVD Title (Alternative): XFILES_DISC6
libdvdnav: Unable to find map file '/home/liam/.dvdnav/XFILES_DISC6.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000409] dvdread demux error: read failed for -1/4 blocks at 0xb90


---

### Post by faintscrawl on 2009-03-14
This won't help you-sorry--but might give you some context.

Recently my vlc has balked at a few videos which mplayer ended up playing.

---

### Post by ELD on 2009-03-14
I found the issue, i didn't have any dvd codecs installed, would have thought it would tell me that like it does with mp3 for example?

---

