---
title: "karmic - radeonhd - hdmi - display to large for screen"
date: 2009-12-09
forum: Multimedia Software
---

### Post by cberger on 2009-12-09
Thanks to the xorg-edgers PPA for finally getting tear-free video on my ATI HD3200!!!  Trying in vain getting ATI's fglrx versions to work over the years.  Hopefully AMD will pull in whatever the radeonhd drivers do to fix it.  The amount of time I actively spent trying to get this working goes into the....well forget it.  

I'm running Karmic x64(linux version 2.6.32-020632).

The problem I'm now having is the display size is too big for the screen.  This ONLY happens when 'Option "HDMI" "all"' is enabled in the xorg.conf file.  When not enabled, the display matches the screen size.  However, I obviously lose audio out the HDMI port.

I need to stick with the radeonhd driver as I'm finally producing tear-free video.  Using even the latest ATI drivers (9.11) doesn't produce this.  FYI for replies:-)

Tried using 'Modelines' within xorg.conf but are ignored.

---

