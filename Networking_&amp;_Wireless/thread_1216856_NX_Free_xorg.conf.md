---
title: "NX Free xorg.conf"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by rozbarwinek on 2009-07-18
Hi

Few weeks ago I have change ubuntu to kubuntu 9.04 and installed KDE 4.3 RC2 :)
But I have one problem, I'm using NX Free on systems with polish keyboard layout, by default I can't write polish special characters in remote machine window and use arrow keys.
It can be fixed by adding whose lines to xorg.conf -->

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

and it was working on ubuntu, but when I do this on kubuntu, after reboot X wont start, it says that it can't find screen.
When I restore xorg.conf file X starts normally.
How can I make special characters working on kubuntu?

---

