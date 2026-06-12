---
title: "[SOLVED] xserver screen resolution"
date: 2008-12-28
forum: Multimedia Software
---

### Post by sabersong on 2008-12-28
I'm having trouble with my screen resolution.  I'm running a fresh install of Hardy, and the System Settings claims that my maximum resolution is 800x600.  I've tried sudo dpkg-reconfigure xserver-xorg, but it only gives me keyboard setting options, doesn't ask or offer anything about video settings.  My video card in nvidia geforce 6 series.

I've run this computer and monitor at much higher resolution fairly recently, and need to be able to do that again.

Can anyone help with this?

---

### Post by overdrank on 2008-12-28
> **sabersong said:**
> I'm having trouble with my screen resolution.  I'm running a fresh install of Hardy, and the System Settings claims that my maximum resolution is 800x600.  I've tried sudo dpkg-reconfigure xserver-xorg, but it only gives me keyboard setting options, doesn't ask or offer anything about video settings.  My video card in nvidia geforce 6 series.

I've run this computer and monitor at much higher resolution fairly recently, and need to be able to do that again.

Can anyone help with this?

Hi and have you install the nvidia drivers?
If so you may install nvidia-settings and adjust with ```
gksu nvidia-settings
```
You may also use the command ```
gksu displayconfig-gtk
``` and adjust

---

### Post by sabersong on 2008-12-28
gksudo nvidia-settings didn't seem to do anything, nor did the other that was suggested.  But before I tried those I checked on the drivers, and found that they nvidia drivers weren't enabled.  I enabled them, followed the steps suggested and the problem is gone.  Thanks for the help -- I'm not sure what step fixed it, but it's fixed.

---

