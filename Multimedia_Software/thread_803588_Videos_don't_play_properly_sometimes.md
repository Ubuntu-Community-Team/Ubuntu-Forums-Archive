---
title: "Videos don't play properly sometimes"
date: 2008-05-22
forum: Multimedia Software
---

### Post by gottabeandrew on 2008-05-22
Sometimes when i use ubuntu, no matter which media player i use (i've tried 5) it just either doesn't play the video or plays it really slowly with no audio. This happens with various different types of video files. I tried to play a DVD earlier (The Truman Show, if anybodys interested.) but it started by playing it really slow (about 1/10 or something) and with no audio and then changed to not playing at all.

Why is this happening and what can i do to stop it?

---

### Post by cor2y on 2008-05-22
what version of ubuntu is this?
Check that dma is enabled/on.
On earlier versions of ubuntu this is how it was done
```
[COLOR=#6C7AA1][FONT=Verdana]sudo hdparm /dev/hda
```
/dev/hda would be your harddrive for the cd/dvd drive it would be /dev/hdd etc.
In hardy heron however this is different
So try this fix [http://ubuntuforums.org/showthread.php?p=4615284](http://ubuntuforums.org/showthread.php?p=4615284)
[/FONT][/COLOR]

---

