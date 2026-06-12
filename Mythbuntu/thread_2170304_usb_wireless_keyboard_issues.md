---
title: "usb wireless keyboard issues"
date: 2013-08-25
forum: Mythbuntu
---

### Post by z7APXKm on 2013-08-25
I have a wireless usb keyboard/mouse (Cideko) that only works when I type 

```
# cat /dev/input/event14
```

Help!  What's going on here?

---

### Post by z7APXKm on 2013-10-22
Solved!

System is recognising it as a joystick, and this wasn't caught in the conf file.  So I added the following code to 

**/usr/share/X11/xorg.conf.d/10-evdev.conf**

```

Section "InputClass"
        Identifier "evdev joystick catchall"
        MatchIsJoystick "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

```

Happy days, it's now working.

---

