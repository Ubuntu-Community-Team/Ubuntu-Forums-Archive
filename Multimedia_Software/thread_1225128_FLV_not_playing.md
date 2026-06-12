---
title: "FLV not playing ???"
date: 2009-07-28
forum: Multimedia Software
---

### Post by deveshsamaiya on 2009-07-28
Hello everyone..
Plz anyone let me know how to play flv media files in ubuntu 8.xx . Some flv files are running but those downloaded from you tube and other websites recently are not playing. Plz help me..

---

### Post by meka4996 on 2009-08-09
Go to [http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)
or Google it: flv flash Totem internal data stream vlc undf

---

### Post by freackout on 2009-08-09
> **deveshsamaiya said:**
> Hello everyone..
Plz anyone let me know how to play flv media files in ubuntu 8.xx . Some flv files are running but those downloaded from you tube and other websites recently are not playing. Plz help me..

try this [http://www.debianadmin.com/how-to-install-vlc-media-player-099-from-source-in-debian-lenny.html](http://www.debianadmin.com/how-to-install-vlc-media-player-099-from-source-in-debian-lenny.html)

then this, in that order.
 
[http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html)

ok cos a bug will not show its cos of dependancy order. libavutil ok.... but it will sort you out plz check the make process for error edit makefile with # on the cflag --fforce-mem

mine ALL works will all codecs included took a bit to fathom though.

---

### Post by freackout on 2009-08-09
> **freackout said:**
> try this [http://www.debianadmin.com/how-to-install-vlc-media-player-099-from-source-in-debian-lenny.html](http://www.debianadmin.com/how-to-install-vlc-media-player-099-from-source-in-debian-lenny.html)

then this, in that order.
 
[http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html](http://juliensimon.blogspot.com/2008/12/howto-compiling-vlc-with-all-major.html)

ok cos a bug will not show its cos of dependancy order. libavutil ok.... but it will sort you out plz check the make process for error edit makefile with # on the cflag --fforce-mem

mine ALL works with all codecs included took a bit to fathom though.

it will remove some stuff but the site tell you how to put it back correctly.

---

