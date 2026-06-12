---
title: "Force Display Resolution in Ubuntu 9.10"
date: 2010-09-18
forum: Multimedia Software
---

### Post by zibeo on 2010-09-18
I'm trying to force my machine to boot in 1360x768 every time, even when there's no monitor attached or turned on.   I've added GRUB_GFXMODE=1360x768[FONT=monospace] to /etc/default/grub and ran sudo update-grub

I've also made sure that /etc/X11/xorg.conf has Modes "1360x768" as the only mode line in the Section "Screen" area.

However, if I boot up with the monitor turned off or unplugged it boots up in 1920x1200

Can anyone tell me how to force Ubuntu 9.10 to boot up in a specified resolution regardless of what monitor is attached or not.


[/FONT]

---

### Post by rebeltaz on 2010-09-19
Have you tried going to System->Preferences->Monitors and setting that to the resolution that you need?

---

### Post by zibeo on 2010-09-20
That only works once.  If I reboot with the monitor off it reverts to the higher resolution.  I'd like to use ubuntu to power a digital sign.  If there's a power failure or the computer reboots with the monitor off the resolution will be messed up.  I won't have a keyboard or mouse connected, so it would be nice for the resolution to be permanently set.

---

