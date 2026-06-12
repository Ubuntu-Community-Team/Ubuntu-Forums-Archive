---
title: "VLC Menu Font Has Become Gigantic, Unusable"
date: 2012-04-01
forum: Multimedia Software
---

### Post by galoisring on 2012-04-01
Today, I started VLC to find that the menu font had become gigantic, to the point where VLC is unusable. The font is so big, that most of a menu doesn't show when opened. I want to change the size of the font, but it's impossible to work in the preferences window, because only a small portion is visible.

Is there a way to change the font size from the command line or some other way outside of VLC? I purged and reinstalled VLC and all related packages to no avail.

Thanks
-Damian

---

### Post by papibe on 2012-04-01
Hi galoisring. Welcome to the forums!

I've never seen that kind of problem, but in case that the setting is unchangeable using the GUI, you can delete all stored settings by doing:
```
rm -rf ~/.config/vlc
```
Note that the previous command will reset all VLC settings.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by galoisring on 2012-04-02
After input of the command and a reboot, the font returned to normal. Thank you so much!

Prior to the font becoming huge, it suddenly became very small, but still quite usable. I wonder how this can happen?

---

