---
title: "Important Please Help....."
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by EZbrain on 2006-02-24
I bought myself e-GeForce 6200
DDR 256MB AGP 8x

when Ubuntu finish booting , and gets to my logon screen, it display many pink squares across the screen( all over the screen?)..... 

What to do?

---

### Post by andrewsawyer on 2006-02-24
You could try reconfiguring xorg using the following command from the prompt:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

