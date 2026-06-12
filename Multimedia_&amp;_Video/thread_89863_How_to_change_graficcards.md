---
title: "How to change graficcards?"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by Azyx on 2005-11-13
I have change graficcard in my computer with Breezy, but X don't start and it's start a text shell. What would i do, to reconfigure X for the new graficcard?
/Azyx

---

### Post by Lambert on 2005-11-13
Try to run this

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Azyx on 2005-11-13
[QUOTE=Lambert]Try to run this

```
sudo dpkg-reconfigure -phigh xserver-xorg
```[/QUOTE]

It worked fine :) Thanx!

---

