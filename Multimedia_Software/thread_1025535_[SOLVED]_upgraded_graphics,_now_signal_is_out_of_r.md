---
title: "[SOLVED] upgraded graphics, now signal is out of range."
date: 2008-12-30
forum: Multimedia Software
---

### Post by animaniac on 2008-12-30
i upgraded the crappy on-board graphics to a reasonable radeon 9200se card and now the monitor says the input signal is out of range when i boot the installed ubuntu 8.10.

I can access the console, and i have run sudo dpkg-reconfigure xserver-xorg. but that only asks for keyboard settings, ive ran it a few times with different options.

i even ran sudo dpkg-reconfigure -phigh xserver-xorg, didnt work either.

live cd works fine, but i dont think i should have to make a fresh install just because of a graphics upgrade.

i even compared the xorg on the live cd with the installed system, they look the same (pretty default) like below:

xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

any ideas?

---

### Post by animaniac on 2008-12-30
works thanks to:

[http://ubuntuforums.org/showpost.php?p=5795292&postcount=25](http://ubuntuforums.org/showpost.php?p=5795292&postcount=25)

---

