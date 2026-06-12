---
title: "Can;t get WINE and Other Applications to both have Sound"
date: 2008-06-22
forum: Multimedia Software
---

### Post by Zaiden on 2008-06-22
When I run WINE, I can't use sound in, say, Firefox. If I'm using sound in Firefox, I can't use it in any WINE application. I changed all my sound settings to ALSA and change the sound to ALSA in winecfg, but it didn't work. I can't figure out how to fix this, and would love some help.

I'm using a Diamond Xtreme 5.1 PCI Sound Card.

---

### Post by Vivaldi Gloria on 2008-06-27
Let me point out a couple of guides to you:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

I used the second thread to fix all my sound issues but the first thread is newer. Now I can start an OSS application with

Code:

padsp <some-oss-program>

and it plays fine. In particular, i chose OSS in wine and i use this for wine apps.

---

