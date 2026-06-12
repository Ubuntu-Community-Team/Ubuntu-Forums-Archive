---
title: "how to start midi on startup"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by TC-cheesy on 2007-07-19
I'm using KDE, and I'm trying to figure out how to start these commands automatically upon startup:
```
sudo modprobe snd-virmidi
```
```
aconnect 20:0 128:0
```

thanks

---

### Post by TC-cheesy on 2007-07-22
:whistle:

---

### Post by jazzuban on 2007-08-07
mm... put a script in  /etc/rc5.d ?

---

### Post by svenmeier on 2007-10-25
Could you please be more specific how this can be done?

Thanks

---

### Post by svenmeier on 2007-10-27
Ok, easiest solution is to add the following line to /etc/rc.local :

    modprobe -qs snd_virmidi

---

