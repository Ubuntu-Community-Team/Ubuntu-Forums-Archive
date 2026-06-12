---
title: "Changed displays, now none work!"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by TerrorAndHubris on 2008-02-08
Hi, I have a Dell Inspiron 6400 laptop which I most often use an external LCD instead of the internal one which is higher resolution. Thankfully, the Dell hardware will alleviate Linux from having to handle separate displays, however unfortunately Linux won't let me exceed the internal display's resolution. So in an attempt to adjust my display settings for the Screens and Graphics, I carelessly set my external as my primary display (with the proper resolution and frequency) and restarted accordingly. Now the Ubuntu hangs on boot. 

I'm sure theres a (relatively) simple way to revert my settings in the recovery mode of Ubuntu, but don't know what that would be. Any help?

Ubuntu 7.10
Dell Inspiron 6400
ATi x1400 Mobility Radeon
1280x800 internal display
1680x1050 external Dell 2007WFP LCD

---

### Post by madcow72 on 2008-02-08
If you can get into a terminal (Try Ctrl-Alt-F1) when trying to boot, then you could reconfigure your display settings with this command:

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by madcow72 on 2008-02-08
I should add that, after you do this, you'll likely need to re-install your graphics driver and re-configure your display settings, but at least you'll get into X.

---

### Post by TerrorAndHubris on 2008-02-08
Thanks a ton madcow! Worked great! I got in and was able to get everything running again.

---

### Post by madcow72 on 2008-02-12
Good to hear it!

---

