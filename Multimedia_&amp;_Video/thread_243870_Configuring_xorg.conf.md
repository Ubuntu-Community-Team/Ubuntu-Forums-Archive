---
title: "Configuring xorg.conf"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by yzzir on 2006-08-25
I have an Inspiron XPS Gen 2 (Geforce Go 6800 Ultra 256MB) using nvidia drivers.  I'm trying to get my external monitor working so when its plugged in it only uses the external monitor.  I can't get it working.  my xorg.conf is attached.

---

### Post by tseliot on 2006-08-25
I'm moving this thread to the video and sound section

---

### Post by Ziox on 2006-08-25
> **yzzir said:**
> I have an Inspiron XPS Gen 2 (Geforce Go 6800 Ultra 256MB) using nvidia drivers.  I'm trying to get my external monitor working so when its plugged in it only uses the external monitor.  I can't get it working.  my xorg.conf is attached.

There is no change of monitor on-the-fly for Linux, you need to either start X with the externel monitor plugged in (which will be displayed on the external monitor) or startx without the external monitor plugged (and use that)...

---

