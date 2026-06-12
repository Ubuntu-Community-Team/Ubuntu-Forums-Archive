---
title: "Problem with old NVIDIA intergrated Graphics and Karmic"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Alatar1 on 2009-11-17
So i jut upgraded my other machine to 9.10 and when i enabled the proprietary nvidia driver (96 was the only one that popped up, i assumed it was due to the old age of the machine) it asked to reboot, when i booted back to log in screen it was sorta glitchy, then after i enter login/password information the computer freezes completely.

Is there anyway to revert it back to the ubuntu default graphics driver or update to a newer one via command prompt mode?

---

### Post by EduardoWillians on 2009-11-18
> **Alatar1 said:**
>  when i booted back to log in screen it was sorta glitchy, then after i enter login/password information the computer freezes completely.

Is there anyway to revert it back to the ubuntu default graphic?

Im expericeing the same problem but my pc freezes on botting before asking for password.

I know a way to revert. On boot enter in text mode (Ctrl+Alt+F1). Then, use envyng to uninstall like this:

```
sudo apt-get install envyng-core
 envyng -t

```

On Envyng, choose option uninstall NVIDIA driver. Restart.


Or, you can rename xorg.conf like this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
```

Anyway, this is just to revert, but on generic video driver the screen resolution allows just 800x600, and it doens't look good, I need a higher resolution for my nvidia.

If someone can help, you're welcome.

---

### Post by realzippy on 2009-11-18
To return to free nvidia driver you can open xorg.conf:

[B]sudo nano /etc/X11/xorg.conf
[/B]
and change

*driver = "nvidia*"
to
*driver = "nv"*

To add more resolutions you can use "xrandr"...

---

