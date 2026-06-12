---
title: "Changing resolution problems"
date: 2008-04-24
forum: Multimedia Software
---

### Post by metroidnemesis13 on 2008-04-24
Uh oh.  So I didn't like the resolution of the monitor (800x600) and I changed it to 1024x768.  It told me I had to log out to see the settings, and now I can't see the login screen.  I've tried entering recovery mode, and all I can see is the command line.  Is there a way to change the resolution from the command line, or default it?  Thanks.  :/

---

### Post by metroidnemesis13 on 2008-04-24
Also I tried xrandr and it said it couldn't display it.

---

### Post by overdrank on 2008-04-24
> **metroidnemesis13 said:**
> Uh oh.  So I didn't like the resolution of the monitor (800x600) and I changed it to 1024x768.  It told me I had to log out to see the settings, and now I can't see the login screen.  I've tried entering recovery mode, and all I can see is the command line.  Is there a way to change the resolution from the command line, or default it?  Thanks.  :/

Hi and have you tried to reconfigure you xorg form command line
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then ```
sudo reboot
```

---

### Post by metroidnemesis13 on 2008-04-25
Thank you so much!  This worked perfectly.  You are amazing.

---

### Post by overdrank on 2008-04-25
> **metroidnemesis13 said:**
> Thank you so much!  This worked perfectly.  You are amazing.

No problem and good luck!

---

