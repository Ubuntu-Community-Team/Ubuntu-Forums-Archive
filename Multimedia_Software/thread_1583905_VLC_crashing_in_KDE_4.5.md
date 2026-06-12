---
title: "VLC crashing in KDE 4.5"
date: 2010-09-28
forum: Multimedia Software
---

### Post by damnated on 2010-09-28
VLC started to crash today, after (I think?) updating to KDE 4.5 . I'm not sure if it's the update's fault, as it was also today that I switched to KDE from GNOME. 
All I know is, that up until now, VLC was very stable, it never crashed. Now, it will start only to close in a few seconds later. I tried re-installing it, but it didn't work. It doesn't matter if I open a file directly, or start it from a terminal/menu. If I start it from a terminal, this is what I see: 
```
$ vlc
VLC media player 1.0.6 Goldeneye
(15966) KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-damnated/icon-cache.kcache" page size is 4096
(15966) KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
(15966) KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
(15966) KSharedDataCache::Private::mapSharedMemory: 5042176 bytes available out of 10485760
WARNING: QApplication was not created in the main() thread.
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
Segmentation fault
 
```
Please advise!

---

### Post by damnated on 2010-09-30
[http://ubuntuforums.org/showthread.php?t=1020868](http://ubuntuforums.org/showthread.php?t=1020868) :)

---

