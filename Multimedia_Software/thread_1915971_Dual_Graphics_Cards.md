---
title: "Dual Graphics Cards?"
date: 2012-01-27
forum: Multimedia Software
---

### Post by christophski on 2012-01-27
I just got an ATI Radeon HD 6570 to replace my previoues ATI card but I have found that the new one only has a DVI-D connector whereas the old one had a DVI-I connector. I previously used a DVI-VGA adapter to connect two monitors to my old card but I can no longer do that with this new card. Would it be possible to have both graphics cards in the computer and run one monitor off of each card?

---

### Post by christophski on 2012-01-28
I've managed to get it semi-working. I used the fglrx drivers and did
```
sudo aticonfig --adapter=all --initial
```
and
```
sudo aticonfig --xinerama=on
```

So I have both screens running, but Unity drops to Unity 2D and I get horrible artifacts when dragging windows. Is there a way to accomplish the same thing with the open source drivers? The seem to work much better.

---

