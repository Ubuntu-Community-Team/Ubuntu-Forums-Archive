---
title: "xfce4-mixer"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by eric_ykchan on 2006-07-02
I have installed xubuntu 6.06 on my Dell Inspiron e1405/640m. Suddenly the xfce4-mixer doesn't work, nothing is shown in the xfce4-mixer window. I can still use sudo alsamixer to adjust the volume (Card: HDA Intel, Chip: SigmaTel STAC9200). I can still use sudo xmms to play mp3. But if I just run xmms, it will fails to play any sound. The *warning* message is "alsa_get_mixer(): Attaching to mixer hw:0 failed: No such device" Any help?

---

### Post by eric_ykchan on 2006-07-02
Just figure out it is the permission problem, which I have messed up my user group.

---

