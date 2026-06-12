---
title: "Flash Player — YouTube colors messed up"
date: 2012-05-10
forum: Multimedia Software
---

### Post by sigdrifa on 2012-05-10
For the last month or so I've had this problems with Adobe's flash player, but only on YouTube — other video sites like Vimeo work just fine.

With both the adobe-flashplugin and the flashplugin-installer packages I get totally messed up colors on YT (see screenshot attached.) On Google Chrome, when I use the built-in flashplayer, the colors are correct, but the video runs at double speed.

Versions from the Chrome plugins page:

```
Shockwave Flash 11.2 r202
Name:	Shockwave Flash
Description:	Shockwave Flash 11.2 r31
Version:	11.2.31.121
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
```

and

```
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/usr/lib/flashplugin-installer/libflashplayer.so
Type:	NPAPI
```

This started when I was still using 11.10, but the upgrade to 12.04 didn't change anything.

Neither of the two problems occur on my netbook, which is also running 12.04 with the same versions of Flash.

Suggestions, anyone?

Thanks

---

### Post by shantiq on 2012-05-10
**start a YT video/go full screen /right click/choose settings/untick hardware acceleration/restart video**

You will have to do this on each browser you use and also everytime they do an upgrade of sorts


should fix it:KS

---

### Post by sigdrifa on 2012-05-10
Yaaaaaaaa!!! Thankyouthankyouthankyou so much! I tried to do that before, but I didn't go to fullscreen first, and every time the player crashed. It worked for the version installed through the package manager; people look a lot healthier now :) Didn't make a difference for the double speed problem in Chrome's built-in plugin, but that I don't care too much about, as long as I have a working version.

Thanks a million!

---

### Post by budman21901 on 2012-08-05
Thank you!

---

### Post by slavnist on 2013-01-18
Thank you:D

---

### Post by 577 Jersey on 2013-02-06
Mine is still all glittery???

---

