---
title: "Sound was working, now it is not"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by RageWarp on 2007-11-05
Upon first boot i had sound, and when i restarted after that i have no sound at all, ive checked all the hardware configs and everything says sound should be on but it is not. any helpÉ

---

### Post by krussell on 2007-11-06
Hello :-)
In a terminal, type "alsamixer" and see the volume levels. Perhaps the PCM channel is muted.
Adjust the volume to desired level, and give "alsactl --store" to save it. (to do "alsactl --store" you may need to be the root user).

---

### Post by RageWarp on 2007-11-06
this seems like it could but i notice when the mixer comes up it isnt using the correct hardware, how do i switch the card it is using

---

### Post by RageWarp on 2007-11-06
bump

---

