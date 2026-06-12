---
title: "DVD Playback / VLC"
date: 2010-08-09
forum: Multimedia Software
---

### Post by maclenin on 2010-08-09
To Whom It May Concern!

I have tried loading/playing (many different) dvds via VLC / new install of 10.04 (on a laptop through which I had been able to play / burn / rip dvds until I "upgraded")...this is what transpires:

Errors:
```
Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
```

The log reveals:
```
dvdread error: DVDRead cannot open source: /dev/sr0
main error: no access module matched "dvd"
main error: open of `dvd:///dev/sr0' failed: no access module matched "dvd"
```

Any wisdom?

---

### Post by ronnielsen1 on 2010-08-09
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> **Playing Restricted Formats**

  
Follow  these steps to play and record most common multimedia formats,  including MP3, DVD, Flash, Quicktime, WMA and WMV, including both  standalone files and content embedded in web pages. 
 
**Ubuntu 10.04 LTS (Lucid Lynx) and 9.10 (Karmic Koala)**

 **[Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")**

---

### Post by maclenin on 2010-08-09
**ronnielsen1:**

Perfect! Right on the money!

Thank you!

[Related: [http://ubuntuforums.org/showthread.php?t=1555795](http://ubuntuforums.org/showthread.php?t=1555795) ]

---

