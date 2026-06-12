---
title: "More flash issues and an observation"
date: 2008-12-10
forum: Multimedia Software
---

### Post by PA-J3Cub on 2008-12-10
I've read many posts dealing with flash problems, especially related to YouTube. I, too, have the same video issues when watching YouTube videos. I've upgraded flash and have done all of the other recommendations I've seen in other posts....and none have really helped.

However, I noticed something today while browsing the web using Firefox.....advertisement banners that utilize Flash play fine. Anyone else notice this? Is there a logical reason for this?

Just my observation.

---

### Post by aysiu on 2008-12-10
It could have something to do with the version of Flash you're using. Some websites employing Flash claim you don't have "the latest version of Flash" installed when, ironically, they require an older version to function properly.

---

### Post by kerry_s on 2008-12-10
it would be nice to know what fixes you tried.

i run on 450mhz 256mb ram and can play flash fine, i watch a lot of youtube. :lolflag:

the fixes i've done:

added:
```
FLASH_GTK_LIBRARY=libgtk-x11-2.0.so.0
export FLASH_GTK_LIBRARY=libgtk-x11-2.0.so.0 
```
to /etc/firefox/firefoxrc 
(i'm actually using iceweasel on debian, but the path should be the same)

i also set up firefox/iceweasel to use /tmp for cache and i have /tmp mounted in ram. (trick i saw in arch)
/etc/fstab:
```

none            /tmp            tmpfs   noatime,nodiratime,defaults,size=128M  0      0

```

firefox string:
```
browser.cache.disk.parent_directory;/tmp
```

oops, forgot, i also reniced Xorg to -10:
```
sudo dpkg-reconfigure x11-common
```

---

