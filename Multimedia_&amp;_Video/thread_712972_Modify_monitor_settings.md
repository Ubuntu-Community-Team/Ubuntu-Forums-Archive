---
title: "Modify monitor settings"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by djm-uk on 2008-03-02
I have installed Gutsy on an epia Mini-ITX machine with an LCD monitor. With the default drivers it worked up to 1560x1050 (and I work at 1280x1024).  I then installed the VIA EPIA ubu driver from the via web site & it now won't go above 1024x768 :(

When I look in the X log file it says 'unsupported refresh rate' & deletes the resolutions from the list!  How do I tell X what the monitor is capable of (or where do I find the resolution settings used in the default driver - I don't mind editing the resolution table if I can find the right settings!!)

Thansk 

David

---

### Post by fedex1993 on 2008-03-02
um what is the highest resolution that the monitor can go? one way to fix it is sudo dpkg-reconfigure xserver-xorg and then part way threw it you canchoose your resolutions

---

### Post by djm-uk on 2008-03-02
> **fedex1993 said:**
> ... what is the highest resolution that the monitor can go? ...

well it worked at 1530x1250 and I use it at 1280x1024 usually... as I said the default driver let me set 1280x1024 but the via one doesn't. I think I need the via one to get decent display response (hware accel)
david

---

