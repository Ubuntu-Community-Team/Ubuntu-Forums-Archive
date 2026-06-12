---
title: "No codec support for.."
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by torx on 2006-06-10
i followed the instructions on [DVD jon's site]("http://www.nanocrew.net/2005/09/01/compiling-vlc/") and compiled VLC. But still im gettin these errors when playing some video files.

> [00000271] main decoder error: no suitable decoder module for fourcc `wma2'.
VLC probably does not support this sound or video format.
[00000309] libvc1 decoder error: new picture failed
[00000320] main decoder error: no suitable decoder module for fourcc `SVQ3'.
VLC probably does not support this sound or video format.
[00000348] access_file access error: seeking too far
*********** Unhandled child meta
[00000361] main decoder error: no suitable decoder module for fourcc `WMV2'.
VLC probably does not support this sound or video format.
*********** Unhandled child meta
[00000370] main decoder error: no suitable decoder module for fourcc `wmap'.
VLC probably does not support this sound or video format.

So basically, i think it's trying to say i dont have codec for WMV2, WMA2, WMAP, SVQ3. So how do i add it in? Or did i screw the compile up?

---

### Post by blackjack6.21.91 on 2006-06-10
Have you installed the w32 codecs? (If not just google for the .deb, or I can send it to you on AIM)

---

### Post by torx on 2006-06-10
im not sure. but these are the list of codecs i installed, from the instructions on his site.

> libwxgtk2.6-dev libdvbpsi3-dev libmpeg2-4-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev gcc g++ automake1.9 autoconf libtool subversion cvs libx11-dev

i dun see w32 codec inside though.

---

### Post by Jucato on 2006-06-10
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)
Scroll down to the section about "other formats" like WMA/WMV, etc.

---

