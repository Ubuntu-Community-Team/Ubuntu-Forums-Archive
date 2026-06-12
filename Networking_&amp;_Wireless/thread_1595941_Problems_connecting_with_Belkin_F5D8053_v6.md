---
title: "Problems connecting with Belkin F5D8053 v6"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by sposh on 2010-10-13
Chipset of this USB WiFi adapter is Realtek rtl8192su. Using 10.10. I have:

$ lsmod
Module                  Size  Used by
eeprom_93cx6            1789  1 r8192s_usb
r8192s_usb            317763  0 
...

$ lsusb
Bus 002 Device 002: ID 050d:815f Belkin Components F5D8053 N Wireless USB Adapter v6000 [Realtek RTL8192SU]
...

$ uname -r
2.6.35-22-generic

I get an entry in my Network Manager applet (Wireless network - Manufacturer Realtek RTL8191S WLAN Adapter) but it always shows up as disconnected. ifconfig throws up no wlan entries.

Spent ages searching & trying out various things, but no cigar yet.

---

