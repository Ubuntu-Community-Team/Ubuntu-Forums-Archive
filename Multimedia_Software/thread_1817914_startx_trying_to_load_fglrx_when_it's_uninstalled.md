---
title: "startx trying to load fglrx when it's uninstalled"
date: 2011-08-03
forum: Multimedia Software
---

### Post by Svpam on 2011-08-03
Hi.

Recently installed Ubuntu base system and then GNOME3.

Installed fglrx but found an issue with GNOME3 loading it (defaulted to VESA drivers in GNOME30 so I went and tried the open source drivers.

I followed the purge guides and purged fglrx and the open source ati driver, and then reinstalled the ati driver.

I have no xorg.conf as suggested, and when I startx I get "Failed to load session "gnome"". When I go back to terminal I see that startx was trying to load fglrx as it says it was not found.

Anyone know what's up?

No idea how to get my Xorg log from linux to windows.

---

