---
title: "Need to manually set refresh rate every reboot"
date: 2008-05-27
forum: Multimedia Software
---

### Post by v.man on 2008-05-27
I'm running Hardy 8.04 and using an 8800 GTS 512 card with nvidia driver.  I need to manually change nvidia-settings display from "auto" to "1440x900" and refresh from "auto" to "75Hz" every time I reboot.  I've tried the "save to x ..." option in the nvidia-settings menu, and the resulting x file shows the 1440x900 and 75Hz variable, but it defaults back to 50 Hz when I reboot (as evidenced in the Screen Resolution app).  Also, when I use the normal Screen Resolution app, I only get options for 50, 51, and 52 Hz refresh rates.  Is there any way to get this setting to stick?  Thanks!

Oh, running 64  bit by the way.

---

### Post by wolfen69 on 2008-05-27
try ```
gksudo nvidia-settings
```
then change it.
also, which i havnt tried yet in hardy:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by v.man on 2008-05-27
thx . . will try that tonight

---

