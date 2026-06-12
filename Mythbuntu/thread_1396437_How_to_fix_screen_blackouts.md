---
title: "How to fix screen blackouts"
date: 2010-02-02
forum: Mythbuntu
---

### Post by scottishnarn on 2010-02-02
Using Ubuntu 9.10 64 bit edition with an NVidia (GeForce 4MX) graphics card.

Despite disabling the screen saver and power management followed by using chmod a-x on the gnome screensaver and power management tools, mythtv kept blacking out the screen. 

I eventually found that adding the following code to my session starting script (one I wrote my self but find yours in /usr/share/xsessions/) ```
xset -dpms s off
```

---

### Post by Slacker3k on 2010-02-05
Just an FYI for anyone else searching, you can also disable it in your xorg.conf.

---

