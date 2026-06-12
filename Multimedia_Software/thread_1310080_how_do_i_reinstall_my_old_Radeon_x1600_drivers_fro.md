---
title: "how do i reinstall my old Radeon x1600 drivers from 9.04?"
date: 2009-11-01
forum: Multimedia Software
---

### Post by psidrum on 2009-11-01
it looks like 9.10 installs a default driver without the 3d accelaration.

how do i enable the old driver again?

---

### Post by epek on 2009-11-01
Take the actual drivers and try something like this:

/etc/X11/xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "DRI" "true"
        Option          "DRI2" "true"
        Option          "AccelMethod" "EXA"
        Option          "AccelDFS" "true"
        Option          "DisplayPriority" "BIOS"
        Option          "ColorTiling" "1"
        Option          "EnablePageFlip" "1"
        Option          "DynamicClocks" "true"
        Option          "PanelSize" "1280x1024"
EndSection

This did the trick for a debian 5 with a much newer Xorg-binary on a X1250. your card is also supported by the radeon driver.

Installing older binaries will almost certainly lead to a desaster, IMO.

---

