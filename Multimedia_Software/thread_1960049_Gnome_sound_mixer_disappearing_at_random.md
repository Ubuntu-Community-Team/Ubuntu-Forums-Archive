---
title: "Gnome sound mixer disappearing at random"
date: 2012-04-16
forum: Multimedia Software
---

### Post by imsety on 2012-04-16
Hi,

I'm using Ubuntu 11.10 with Gnome Classic interface on my ThinkPad laptop. My sound card is a Intel 82801H (ICH8 Family) HD Audio Controller.

Now, while using ubuntu, the gnome mixer (gnome-sound-applet) disappears randomly and the volume up/down buttons on my pc stop working. Yet, sound is still working, and volume can still be adjusted through alsamixer in terminal.

Also, when opening "Sound" in "System Settings", volume adjustment is deactivated (gray), and no device is listed in the "Hardware" tab. Normally, the intel device would appear there.

The attempt to restart gnome-sound-applet results in the following error:
```
sound-cc-panel-WARNING **: Failed to connect context: Connection refused
```

The only way to solve the problem for now is to log out and log in again.

Anyone got an idea? Help is greatly appreciated.

---

### Post by imsety on 2012-04-27
Solved the problem: The sound device only disappears when running a KDE application which tries to play a system sound. So, I deactivated all sound notifications in KDE control panel and everything is running without problems so far.

---

