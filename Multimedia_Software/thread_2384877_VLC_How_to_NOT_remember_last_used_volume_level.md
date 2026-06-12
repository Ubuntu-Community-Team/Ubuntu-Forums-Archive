---
title: "VLC: How to NOT remember last used volume level?"
date: 2018-02-13
forum: Multimedia Software
---

### Post by &amp;KyT$0P# on 2018-02-13
I would like to set VLC media player to always start with volume 90%, no matter what I set the volume to.  There is a setting that looks perfect for this - "Always reset start audio level to:"

But that setting is greyed out, un-checked, and locked at 100%.

Why?  How can I use this setting?

In the advanced settings, there is a "Remember audio" checkbox that I can toggle.  But it doesn't seem to have any effect.

---

### Post by ajgreeny on 2018-02-13
In the Audio output tab of VLC's preferences set it to ALSA instead of pulseaudio; the box will suddenly become available and it makes no difference to the sound output as ALSA just passes sound to pulse anyway in Ubuntu (if I understand sound output properly, which I may not).

---

### Post by #&amp;thj^% on 2018-02-13
Along with ajgreeny's advice
Look here:/home/yourusername/.config/vlc/vlcrc

I changed to
```
# Maximum Volume displayed (integer)
qt-max-volume=90
```
I removed the # in front of "qt-max-volume=90"
Just my small effort to help.

---

### Post by &amp;KyT$0P# on 2018-02-13
> **ajgreeny said:**
> In the Audio output tab of VLC's preferences set it to ALSA instead of pulseaudio; the box will suddenly become available and it makes no difference to the sound output as ALSA just passes sound to pulse anyway in Ubuntu (if I understand sound output properly, which I may not).
Thanks ajgreeny, it works! :D

---

