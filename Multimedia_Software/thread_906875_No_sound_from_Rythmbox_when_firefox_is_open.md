---
title: "No sound from Rythmbox when firefox is open"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Antihero20 on 2008-08-31
Whenever i have firefox open i can't seem to play music from rythmbox or any other player, i have to close all browser windows then re-open rythmbox to hear music, however when i do this then i can't hear anything from my browser that is flash for example youtube vids don't have sound

Anyone know how to fix this?

---

### Post by SZ07 on 2008-08-31
This is a known issue in flash. It conflicts with pulseaudio. There is a guide in the forums which will tell you how to set up pulseaudio properly.

Or you can go to system>>preferences>>sound and change the options from pulseaudio to ALSA. IIRC that should do the trick.

---

### Post by Antihero20 on 2008-08-31
where exacly is it? i can't seem to find it on the stickyes

---

### Post by wolfen69 on 2008-09-01
```
sudo apt-get install libflashsupport
```

---

### Post by SZ07 on 2008-09-01
Here is the fixing pulseaudio guide:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio)

Be sure to read the directions carefully as some things have changed since I last saw it.

About installing libflashsupport as the previous poster mentioned, you might want to try it. For me it solved the issue but then caused another problem (it caused firefox to keep crashing on flash websites).

The pulseaudio guide should work fine though. If your issue still isn't solved you can try installing flash 10 beta 2 and using ALSA instead of pulseaudio.

---

### Post by Bakon Jarser on 2008-09-01
> **SZ07 said:**
> Here is the fixing pulseaudio guide:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio)

Be sure to read the directions carefully as some things have changed since I last saw it.

About installing libflashsupport as the previous poster mentioned, you might want to try it. For me it solved the issue but then caused another problem (it caused firefox to keep crashing on flash websites).

The pulseaudio guide should work fine though. If your issue still isn't solved you can try installing flash 10 beta 2 and using ALSA instead of pulseaudio.

I was going to post that link.  It addresses the flash problems as well.

---

