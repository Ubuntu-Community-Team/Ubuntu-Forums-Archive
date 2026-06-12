---
title: "Change default X resolution in terminal"
date: 2008-10-26
forum: Multimedia Software
---

### Post by PoopyTheJ on 2008-10-26
Ok, so I setup my friends Ubuntu install and got the fglrx drivers installed and functioning on my monitor which supports 2048x1600, which the drivers default to after an install. However his monitor does not support it. If I boot into Ubunto I can't login as it's an unsupported resolution, I'm hoping I can in someway set a default resolution in xorg.conf from the terminal or a live CD and reboot and have it go to that. Can someone tell me how I would go about doing that or if it's possible? Or is there some other thing I need to do to get it to work?

---

### Post by blackened on 2008-10-26
On CLI type ```
sudo nano /etc/X11/xorg.conf
``` remove the offending resolution(s) ctrl+x, yes to save then ```
startx
```

---

### Post by PoopyTheJ on 2008-10-31
Ok looked through the xorg.conf file and didn't see any resolutions listed at all. Perhaps I did something wrong? I installed the drivers using Envy, does envy do something funny to the xorg file?

---

### Post by blackened on 2008-11-01
Ah I see. You're using 8.10 I assume? If so try using
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by PoopyTheJ on 2008-11-01
on 8.04, do I still run that command? I assume I run that from the recovery kernel right? And Thank you!

---

