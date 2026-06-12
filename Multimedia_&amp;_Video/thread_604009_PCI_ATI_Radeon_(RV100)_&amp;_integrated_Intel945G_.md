---
title: "PCI ATI Radeon (RV100) &amp; integrated Intel945G how to get Xinerama working?"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by vidak on 2007-11-05
I would like to configure a dual-monitor setup. The first problem is that the integrated video card (Intel 945G) has only one output, so I experimented with an ATI Radeon RV100 in the PCI slot. 
I suppose that the BIOS is set up correctly if the primary video card is the integrated card (the options are IGD, PCI, PCI Express), since in other cases lspci lists only one video card. 

I tried to make an xorg.conf using dpkg-reconfigure xserver-xorg, to set up the intel card correctly, and then hacking it either manually, or using Kubuntu's tool for graphic settings. With no real luck of course. X11 works nice with one or the other card (and monitor), even if I start an X server :0 on intel card, modify xorg.conf on the fly, and start another with the ATI card on :1 server - they are OK with each other.
Now when trying Xinerama weird things happen: the monitor with the ATI card contains one line (with the BIOS ID of the card, something similar to "P/N 113-78501-107 RV100 785 HYUNDAI DDR with DLL BIOS"). The monitor with the intel card shows some constant lines with the colors of the rainbow, anyway the system is frozen, only a reboot helps.

(The drivers used for the cards are intel and ati)

Do you have any ideas for solution? (OK, buying a dual-output PCI-E card, probably this will be the future, but still...)

---

