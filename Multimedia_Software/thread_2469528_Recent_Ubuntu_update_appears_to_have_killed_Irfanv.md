---
title: "Recent Ubuntu update appears to have killed Irfanview"
date: 2021-12-01
forum: Multimedia Software
---

### Post by waburden-4 on 2021-12-01
Ubuntu 21.10 - updated to date. I use Irfanview software on a regular basis to edit pictures and today I noticed it will not launch after a recent update. Uninstalled, rebooted and then reinstalled from Ubuntu Software and get he following when I attempt to launch - Window pops up with the following: " Preparing Windows Compatibility layer". Irfanview is displayed in the System Tray and another window pops up indicating Irfanview's configuration is being updated, which is normal during its initial launch. The update appears to finish successfully and the window closes leaving the windows compatibility window appearing to continue to operate. This window closes after a few seconds and The I notice that "Irfanview" disappears from the System Tray without launching.

Irfanview is now installed as a snap and still uses wine so I suspect that a recent update upset wine. Any ideas on a fix?

---

### Post by deadflowr on 2021-12-02
Looks like the irfanview snap was updated recently.
Try reverting it
```
snap revert irfanview
```

---

### Post by waburden-4 on 2021-12-02
Tried the snap reversion but it seems like there is no revision available. One of the disadvantages of snaps is they don't seem to keep previous versions.

---

### Post by waburden-4 on 2021-12-03
Developer responded immediately to a posting on Github. Issued another snap update in response to a bad one and issue is now resolved! Things are back to normal.

---

