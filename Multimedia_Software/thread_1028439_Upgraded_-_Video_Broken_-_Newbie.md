---
title: "Upgraded - Video Broken - Newbie"
date: 2009-01-02
forum: Multimedia Software
---

### Post by lofttroy on 2009-01-02
I built my first Linux box using Ubuntu 8.04 about a month ago.  I've mostly just been learning how use it for the last month.  I noticed that it needed several upgrades (~80 of them).

After the upgrades my video screen works properly up to the login screen (I'm using the GUI until I get better at CLI).  After I login the screen goes solid white and the computer is non-responsive.

I found a utility that attempts to correct the xorg.conf file and it brought the video back, kind of.  The video update is EXTREMELY slow and I get artifacts on the screen that will not go away (typically vertical white lines).  Prior to the upgrades the screen response was normal.

I'm very new to this OS, but it's grown on me.  I suppose fixing the issues I create will make me a better user in the end . . .

Thanks for your help,

Troy

---

### Post by wolfen69 on 2009-01-02
are you using an nvidia or ati driver? is so, uninstall it for now, and then in terminal: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then restart. let us know what happens.

---

### Post by lofttroy on 2009-01-02
I'm still getting the same results, except now my browser turns grey when I try to scroll.  My bit of research on that shows that the browser is not responding for some reason.  Maybe the screen is too slow?

Contents of xorg.conf all look pretty generic to me, but what do I know?

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

