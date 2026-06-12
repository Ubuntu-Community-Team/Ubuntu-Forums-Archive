---
title: "ATI open source driver problem in 9.10"
date: 2009-11-02
forum: Multimedia Software
---

### Post by apparle on 2009-11-02
I have a ATI Radeon Xpress 200 which is legacy and hence I can't use fglrx driver.

But the open source drivers work for me with one quirk in xorg.conf under device section.... (Option "BusType" "PCI")

But when I installed 9.10 and made the setting and restarted the X server, the display turned off and not starting. 
If I remove that line from xorg.conf in recovery mode then the display starts fine but without any Graphics/Compositing

What to do?
I am pretty sure that the card has to be forced in PCI mode because the xorg log say that AGP card is detected and then problems start..... If it is forced as PCI then the problem is fixed.

Should anyother be settings be made in order to force the card in AGP mode

---

