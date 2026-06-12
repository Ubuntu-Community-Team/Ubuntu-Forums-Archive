---
title: "X1400 on Ubuntu 9.04 problems"
date: 2009-08-01
forum: Multimedia Software
---

### Post by lpm11 on 2009-08-01
Hello everyone. Lastly I have installed driver rt73usb, removing ralink drivers from kernel. And problem appeared on next boot.
System is extremly slow and Compiz doesn't work, as it did before(with Desktop Effects and Emerald). None of them works.
I don't know what's happened. dmesg looks as usual, there are no errors. Scrolling in term is extremly slow(CPU 100%).
When I type glxinfo | grep direct there is:
"Direct Rendering: Yes".
glxgears: sth about 100FPS.

I tried to repair X by recovery boot, but it didn't help.
What could have happened? Any suggestions?
My OS: ubuntu 9.04, kernel from repository 2.6.28-15.

EDIT: Can remove.
After adding this:

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection

to xorg.conf it started working.. I don't undestrand why it stopped with default settings:/

---

