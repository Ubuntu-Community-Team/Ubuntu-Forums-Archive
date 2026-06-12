---
title: "Monitor errors"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by DagonX on 2006-09-08
Everytime I boot Ubuntu I get a nasty message from my Samsung 913v silver monitor about the settings not being optimal. I am not sure if it doesn't like a 60Hz refresh rate or it wants it. Anyway changing the refresh rate in preferences doesn't seem to help. Any suggestions?

---

### Post by TwoWordz on 2006-09-08
Most of the time when a monitor complains it's not optimal settings, resolution is the cause.

Check you monitor specs on the manufacturer's site, and update your xorg.conf accordingly.

you must but running your 1280x1024 monitor in 1024x768. 

TW

---

### Post by infoburner on 2006-09-08
according to this: [http://computing.kelkoo.co.uk/b/a/ps_14254707/114401.html](http://computing.kelkoo.co.uk/b/a/ps_14254707/114401.html)
the refresh rate should be 75Hz max. so i would say, try 75Hz

---

