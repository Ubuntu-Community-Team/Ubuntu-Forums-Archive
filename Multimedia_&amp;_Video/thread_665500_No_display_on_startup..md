---
title: "No display on startup."
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by Absinthe Minded on 2008-01-12
Hi all,

I'm completely new to Ubuntu. I've been using it for a while now and I love it.
Trouble is, I've tinkered with the display settings and now I just get loads of lines on the screen after start-up. I can login, but can't see my desktop.

Please help me get out of this mess!

Thanks,
Nick.

---

### Post by santaslittlehelper on 2008-01-12
Hi

Could you be a bit more specific to where you tinkered with the display settings?

One thing you could try.
Boot in to recovery mode, hit "Esc" right after boot up and you should be able to choose it.
Now issue -
```
dpkg-reconfigure -phigh xserver-xorg
```
then issue -
```
shutdown -r now
```
It might do it.

---

