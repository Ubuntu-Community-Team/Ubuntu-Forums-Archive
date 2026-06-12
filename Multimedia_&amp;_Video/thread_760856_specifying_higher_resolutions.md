---
title: "specifying higher resolutions"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by ravalox on 2008-04-20
I have a projector that can do 1024x768 resolution, but Ubunut 8.04 won't let me reach that resolution when I start it up and attempt to change resolutions; it maintains me at 800x600.  The xorg.conf is radically different now, I can't just add that resolution there anymore, where can you specify that with the new xorg?

---

### Post by wolfen69 on 2008-04-20
not sure if this still works in hardy, but in gutsy this is what works most of the time:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Maxplayer14 on 2008-04-21
I am having the same issue with just a regular monitor.

---

### Post by ravalox on 2008-04-22
I've attempted to add a new modeline with xrandr, it added a 1024 mode but when I chose it, it did nothing.

---

### Post by ravalox on 2008-04-23
I solved it by copying the xorg.conf from my 7.10 box to the new 8.04 one.

---

