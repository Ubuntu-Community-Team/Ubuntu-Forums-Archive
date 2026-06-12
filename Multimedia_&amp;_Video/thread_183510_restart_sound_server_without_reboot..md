---
title: "restart sound server without reboot."
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by dmizer on 2006-05-28
can anyone tell me if it is possible to restart the sound server without rebooting the box?

i updated libao.conf with alsa, but i'm on a server, so i'd rather not reboot if possible.

---

### Post by halfvolle melk on 2006-05-28
This should work:
```
/etc/init.d/alsa-utils restart
```

---

### Post by cwwitt on 2006-07-16
Just some humor here.
I thought I was having "intermittent sound" problems and troubleshooted it for near an hour (maybe more :)) even rebooting several times.

I wanted to slap myself when I saw that my speakers were turned off.  I turned them off this morning when an alarm came on to wake me up.

I'm just glad I didn't waste a whole evening on this "problem".

---

