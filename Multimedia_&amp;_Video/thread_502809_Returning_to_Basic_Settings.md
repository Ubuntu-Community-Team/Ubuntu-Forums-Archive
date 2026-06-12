---
title: "Returning to Basic Settings"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by kshane on 2007-07-17
I have an ATI X1650.  It was working "ok" but I changed the settings in the KDE desktop graphics settings and can now only get 640x480.  I set the adapter settings to "ATI fglrx".

ANy ideas?  I do NOT want to re-install again...  :0

Kevin

---

### Post by renzokuken on 2007-07-17
open the terminla and run

```
sudo dpkg-reconfigure xserver-xorg
```

this will open a wizard to help reconfigure your grafix settings.

leave everything as it is, except for in the **resolutions** page (where you want to select your resolutions) and the **driver** page (where you can select the proprietary fglrx driver, assuming you have it installed, or the open source "ati" or "radeon" drivers)

---

