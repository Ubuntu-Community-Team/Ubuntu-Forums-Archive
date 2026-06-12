---
title: "sound issues"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by cryo4.rm on 2007-09-13
this is the second time i have set up ubuntu 7.04 on this same machine (i recently reinstalled everything from scratch)

 both times i have had the high pitch noise problem, which LAST time i was able to remedy by updating to the latest version of alsa.

 this time it didnt fix it  -- whats more there is a strange inconsistency to this problem (yesterday i had sound working fine - today i had high pitch noise -- and now later in the day i have no sound whatsoever -- and these changes APPARENTLY independent of any of my tinkering ...)

 so now i have NO SOUND. its not the alsamixer levels and i have tried muting the IEC level



any suggestions? please.

---

### Post by cryo4.rm on 2007-09-13
problem fixed! by adding 

"options snd-hda-intel position_fix=1 model=3stack" 

to "/etc/modprobe.d/alsa-base".

 thankyou to chumbas post on 

[http://www.planetamd64.com/lofiversion/index.php?t23938.html](http://www.planetamd64.com/lofiversion/index.php?t23938.html)

---

