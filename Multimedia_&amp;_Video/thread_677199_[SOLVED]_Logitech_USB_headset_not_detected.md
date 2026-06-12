---
title: "[SOLVED] Logitech USB headset not detected"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by iceman0407 on 2008-01-24
I just bought a Logitech USB headset. Initially I plugged it in and Sys>Pref>Sound and changed all the options to the headset and everything was fine.

Today I restarted and the computer completely ignores the headset [booting w and w/out it plugged in]

lsusb is not finding the headset, but is finding my usb mouse in all the ports

any thoughts?

---

### Post by jeffus_il on 2008-01-24
I would try the headset on another computer to verify if it is working. (Since lsusb does not detect it). Have you done a check to see if the module snd-usb-audio is loaded ```
lsmod | grep snd-usb-audio
```

---

### Post by iceman0407 on 2008-01-24
It was a defective headset. I seemed to have exhausted every other possibility so I was relieved it was!

---

