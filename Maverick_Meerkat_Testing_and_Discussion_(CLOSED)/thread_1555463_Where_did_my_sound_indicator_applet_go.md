---
title: "Where did my sound indicator applet go?"
date: 2010-08-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Kobalt on 2010-08-18
Hi Maverick testers,

Since a couple of days my sound indicator applet has gone missing. It has disappeared form my notification area, so I went in "Add to the panel.." searching for it: gone. 
In the meantime my sound is working, and I can adjust the volume properly from System > Pref > Sound.

Any hint for me? Is this supposed to be?
Thanks-

---

### Post by x-shaney-x on 2010-08-18
An update may have removed the package due to some conflict.
Try apt-get install indicator-sound.

---

### Post by MacUntu on 2010-08-18
> **Kobalt said:**
> Hi Maverick testers,

Since a couple of days my sound indicator applet has gone missing. It has disappeared form my notification area, so I went in "Add to the panel.." searching for it: gone.
Cannot be gone, cause it never was there. The sound indicator applet is part of "Indicator Applet". ;)

---

### Post by x-shaney-x on 2010-08-18
Sound indicator appears on the panel as part of the indicator app but is a separate package in itself.
So if the package is installed it will automatically appear on the panel if indicator applet is added.

```
apt-cache policy indicator-sound
indicator-sound:
  Installed: 0.3.9-0ubuntu2
  Candidate: 0.3.9-0ubuntu2
  Version table:
 *** 0.3.9-0ubuntu2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by cariboo on 2010-08-18
I still have it on all three of my maverick installs.

---

### Post by wilee-nilee on 2010-08-18
If you want a volume applet just go to startup application the add and put gnome-volume-control-applet in the command, it will be there on restarting X or a reboot.

---

