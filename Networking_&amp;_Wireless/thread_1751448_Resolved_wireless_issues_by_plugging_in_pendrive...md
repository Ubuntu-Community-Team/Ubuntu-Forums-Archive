---
title: "Resolved wireless issues by plugging in pendrive... (WTF?))"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by DaimonPl on 2011-05-06
My case is "a little" strange...

Here is my setup:
Ubuntu 11.04 32bit fresh install (tried 10.10 and problem is exactly the same)
WUSB54GC usb wifi (ralink chip)
Asus AT3N7A-I motherboard


Issue is simple - I can't connect to wireless network (wifi works from windows computers)... in syslog i could read things like "No IPv6 router found" and after disabling ipv6 "DHCP timeout". I checked driver blacklisting solutions and nothing worked.

I accidentally found a solution... when I plug pendrive into USB port and restart OS wireless connection starts to work... when i plug it out problem comes back again.

Tested with Ubuntu 11.04 and Windows XP bootable USB (LOL). I have no idea why it works this way but maybe this can help somebody...

---

