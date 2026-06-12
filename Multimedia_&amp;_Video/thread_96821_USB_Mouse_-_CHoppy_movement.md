---
title: "USB Mouse - CHoppy movement"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by bb002 on 2005-11-29
I have a Microsoft (shoot me) USB Mouse connected to my gateway M275.

The mouse worked fine a few weeks ago but i screwed up my ubuntu 5.04 install real bad...Like I unistalled the kernel and rebooted (don't ask why i rebooted I don't even know). Me being the Linux genius i am said screw it and reinstalled hoary. Now my usb mouse movement is choppy but if i move the mouse with the touchpad it moves just fine.

any ideas?

mouse section of xorg.conf
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

Just in case this means anything the MS mouse is three button with a scroll wheel.

---

### Post by bb002 on 2005-11-30
Um...Why is my thread in the "Video and Sound" Forum?? I had to do a search for topics by me to find this guy. Any mods out there want to move this for me, please? I don't know if I wasn't paying attention and posted here by mistake or something goofed up.

---

### Post by juliog on 2005-12-04
Had the same choppy USB mouse problem. The mouse also worked flawlessly in other Linux distros and Windows.

I've just changed the USB port where the mouse was plugged and it started working. Don't know what was wrong, but on the old port the mouse was choppy and on the port next to it, it worked :)

---

### Post by bb002 on 2005-12-05
I ended up just commenting out the configured mouse section and the mouse started working. Scroll wheel doesn't work now but atleast the choppyness is gone.

---

