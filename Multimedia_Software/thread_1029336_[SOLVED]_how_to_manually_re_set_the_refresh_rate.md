---
title: "[SOLVED] how to manually re set the refresh rate"
date: 2009-01-03
forum: Multimedia Software
---

### Post by DarinB on 2009-01-03
i installed a game and it killed my monitor setting so i only refresh at 60hz and 800x600 options are lost in screen res tool
how do i manually re set it.
i found a post for win that it is an nvidia bug but no fixes are posted for it.
i tried changing the xorg conf
Section "Screen"
	Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        SubSection "Display"
                Modes      "1020x758"
        EndSubSection
EndSection
but it caused the troubleshoot screen at boot up and i had to edit before booting...then it was fixed (can't figure that one) but next boot it is back to low res.
help
there must be a manual fix the windows fix change hex keys for the monitor so i bet we can do this here.
anybody

---

