---
title: "NX Free on ubuntu 9.04 and ALT key"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by rozbarwinek on 2009-05-14
How to fix ALT key on shadowed session on ubuntu 9.04?
There was no problem on 8.10

I added this to xorg.conf:
```
Section "ServerFlags"
	Option "AutoAddDevices" "false"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "pl"
EndSection
```

I need ALT key because I wrote in Polish keyboard layout.

---

