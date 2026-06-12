---
title: "Why there are two codecs for one audio device&#65311;"
date: 2010-08-25
forum: Multimedia Software
---

### Post by techlivezheng on 2010-08-25
Run:

```
cat /proc/asound/card0/codec#* | grep Codec
```

Result:

> 
Codec: Realtek ALC269
Codec: Intel G45 DEVCTG



Can someone explain to me,why there are to codecs for one audio device?

My audio device:

> 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)

---

### Post by lidex on 2010-08-28
The Realtek is for your analog, the second for digital/hdmi. The aplay -l command will show the 
devices alsa sees.

---

