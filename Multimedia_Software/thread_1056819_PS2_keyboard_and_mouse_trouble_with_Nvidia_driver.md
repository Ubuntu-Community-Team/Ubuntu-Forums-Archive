---
title: "PS2 keyboard and mouse trouble with Nvidia driver"
date: 2009-02-01
forum: Multimedia Software
---

### Post by splater on 2009-02-01
Hello,

I just installed Intrepid and everything works great untill I activate the nvidia driver form the ubuntu proprietary driver tools (the 177). The result is : just after logging in, my PS2 keyboard and mouse freeze (if I connect a USB mouse, mouse works).

I have a Geforce 6200 and a P4VXASD2+ mother board.

Any idea to resolve this issue ?

Thanks 
Splater

---

### Post by splater on 2009-02-01
i write you from a usb mouse and a virtual keyboard .... it`s hard !
i leave you my xorg.conf if you see something
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```
it`s quite simple ...

hope you can help me !
splater

---

### Post by splater on 2009-02-02
writting with a virtual keyboard is quite boring ... No one has any clue ???

:( I don't know what to do ...

---

### Post by splater on 2009-02-02
Solved ... Bios updated. PS2 works with Nvidia driver ...

bye

---

