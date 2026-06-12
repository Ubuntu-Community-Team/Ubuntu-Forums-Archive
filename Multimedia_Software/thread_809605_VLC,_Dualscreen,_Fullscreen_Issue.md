---
title: "VLC, Dualscreen, Fullscreen Issue"
date: 2008-05-27
forum: Multimedia Software
---

### Post by noremac on 2008-05-27
I have a dual screen set up. A 17" on the left and 20.1" Widescreen on the right. When playing a video with VLC, and I want to go fullscreen, it automatically goes to the smaller 17" screen, and not the 20.1". I cannot get it to go fullscreen on the 20.1 at all in VLC. Other media players dont have the problem. Is there a setting for this somewhere that I haven't seen?


Thanks for any help,
-Cameron

---

### Post by noremac on 2008-06-01
Anyone, Anybody?

---

### Post by noremac on 2008-06-18
Still havent been able to fix this...Anyone?

---

### Post by Pjotr123 on 2008-06-18
Have you tried this:
```
gksudo displayconfig-gtk
```

And if you have an Nvidia video card, you could install nvidia-settings and apply
```
gksudo nvidia-settings
```

---

### Post by morganGDFP on 2008-07-13
Found it!

[http://jbopensrc.wordpress.com/2008/04/29/quickfix-vlc-fullscreen-dual-monitor-wrong-monitor/](http://jbopensrc.wordpress.com/2008/04/29/quickfix-vlc-fullscreen-dual-monitor-wrong-monitor/)

worked for me!!

---

### Post by noremac on 2008-07-14
Excellent! Thanks! That setting is buried very deeply,
-Cameron

---

