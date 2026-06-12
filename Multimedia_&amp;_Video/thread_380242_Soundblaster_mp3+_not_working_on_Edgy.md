---
title: "Soundblaster mp3+ not working on Edgy"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by peterthebike on 2007-03-09
I have fresh installed Edgy as a dual boot with an old Windows 98SE. Sound has not worked with my Soundblaster mp3+ since installing, but it is OK on Windows 98SE.

Looking at [Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") I found ```
aplay -l
```showed my soundcard, but```
lspci -v
```did not list my soundcard.

As software updates had updated the kernel, I tried```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
```
This did not help. Could anyone suggest something else to try please?

---

### Post by peterthebike on 2007-03-11
Using a 5.10 Live CD sound works OK.

Using either a 6.06 or 6.10 Live CD I have no sound.

---

