---
title: "Monitor via DVI and KVM does not work. EDID missing?"
date: 2010-03-05
forum: Multimedia Software
---

### Post by davemar on 2010-03-05
I've got a Dell E4300 laptop which has a docking station with a DVI connector. I want to connect to my monitor via a DVI KVM switch, but it doesn't work. I assume as the KVM switch removes the EDID signal, the laptop doesn't know the monitor exists.

The laptop has an Intel GMA 4500MHD graphics chipset. I'm running Ubuntu 9.10, so it seems to need xrandr based instructions to fiddle with resolutions, rather than using a Xorg.conf file which doesn't appear to exist.

Do I need to write a Xorg.conf file from scratch and grab an EDID file somehow?

---

