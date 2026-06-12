---
title: "dri and aiglx with the r300 driver"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by Belibem on 2006-09-13
After playing around with some compiz settings my r300 based card (radeon x800) exhibits very poor performance (9fps in compiz or tremulous). I can't figure out what setting triggered this state but I suspect it was changing the theme.  

glxinfo shows that I have direct rendering but somehow I think that my system does software rendering. Is there any case that glxinfo shows wrong info about DRI with aiglx enabled?

---

### Post by Eversmann on 2006-09-13
Did you try running compiz on XGL instead of AIGLX? i think i've read somewhere in the forums that aiglx doesn't work very well on ati cards.

---

### Post by Belibem on 2006-09-13
I strongly prefer aiglx over xgl.

---

### Post by Belibem on 2006-09-15
solution can be found here:
[http://www.ubuntuforums.org/showthread.php?t=256881](http://www.ubuntuforums.org/showthread.php?t=256881)

---

### Post by fuoco on 2006-10-27
I have also "direct rendering: yes", but I get around 30 fps in glxgears. The options mentioned here are already in my xorg.conf... Any idea ?

---

