---
title: "AGP not work"
date: 2008-09-05
forum: Multimedia Software
---

### Post by Eric_123 on 2008-09-05
I have the following h/w config:

MB: Gigabyte SR533 (SIS 645 Chipset)
Nvidia 6200
Dell 2407FWP

I have the following problems:

1. system says "UNKNOWN" on Screen Resolution dialog box

2. After enabling Nvidia driver in "Hardware Drivers", and rebooting the system, the screen blinks with lines and blocks.

I really want to enable 3D acceleration. Could anyone please let me know what shall be done to resolve the problems? Thanks.

---

### Post by overdrank on 2008-09-05
Hi and welcome. you may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option to correct the graphics.
Moved :)

---

### Post by Eric_123 on 2008-09-05
yes. the machine seems working fine, but the driver is still disabled (not in use). is there way to enable the driver?

---

### Post by overdrank on 2008-09-06
> **Eric_123 said:**
> yes. the machine seems working fine, but the driver is still disabled (not in use). is there way to enable the driver?

Hi and if the driver says that it is not in use then disable and reboot then enable it again.

---

### Post by Eric_123 on 2008-09-18
:)

AGP sorted out:

added the following line to xorg.config:

Option "NvAGP" "1"

Now I am enjoying the 3D effects.

BUT... the monitor is still "UNKNOWN" in Hardy. Any suggestion / advice is appreciated.

---

