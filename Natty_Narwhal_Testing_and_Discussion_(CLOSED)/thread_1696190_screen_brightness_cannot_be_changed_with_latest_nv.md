---
title: "screen brightness cannot be changed with latest nvidia driver 270.29"
date: 2011-02-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nIRV on 2011-02-27
Can anyone confirm the screen brightness can't be changed (either through keyboard shortcut or gnome power management's slider) with nvidia driver 270.29?

On my nvidia gt 330m, I lost control over brightness using 270.29, while it worked fine under 260.19.06.

---

### Post by nIRV on 2011-02-27
Thinking out loud, it might have to do with this change:

> Reorganized the NVIDIA driver's /proc file system layout to better reflect current needs: /proc/driver/nvidia/cards/0..N has been moved to /proc/driver/nvidia/gpus/0..N/information

---

### Post by nIRV on 2011-02-27
Actually I meant to refer to the screen's backlight, not the brightness (which can be adjusted by nvidia-settings).

---

### Post by plun on 2011-02-27
Add this to xorg.conf > Device
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```

Not sure if this is a gnome-power-manager bug or a driver bug...:confused:

---

### Post by nIRV on 2011-02-27
> **plun said:**
> Add this to xorg.conf > Device
```

Option "RegistryDwords" "EnableBrightnessControl=1"
```

Not sure if this is a gnome-power-manager bug or a driver bug...:confused:

plun, thanks for the help. Unfortunately, backlight/brightness control were still not working after adding the option to my xorg.conf's device section.

Any other idea? :)

---

### Post by plun on 2011-02-27
> **nIRV said:**
> plun, thanks for the help. Unfortunately, backlight/brightness control were still not working after adding the option to my xorg.conf's device section.

Any other idea? :)

Ok...  did you reboot (or restart X) after changing ?

For me it works in a Gnome Classic or Unity session but not in a GS session.

---

### Post by nIRV on 2011-02-27
Yep, rebooted computer. I'm running a unity session.

---

### Post by Appleshare on 2011-02-28
I see the same on a MacBook Pro 5,4 with the nvidia-current version you mentioned. The workaround with the xorg.conf option works partially for me. I can then use the keyboard keys to change the brightness, but I don't get an OSD notification bubble when doing so. This bubble appeared with all previous nvidia versions I used on this machine, and it still does when using the nouveau drivers.

---

### Post by Appleshare on 2011-02-28
Filed in Launchpad as LP#726692:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/726692](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/726692)

---

### Post by alexmurray on 2011-02-28
The reason you can still change brightness levels without the notification showing up is you probably have pommed installed which is doing it - the bug is probably in gnome power manager or similar then. Try uninstalling pommed and see if it still works.

---

