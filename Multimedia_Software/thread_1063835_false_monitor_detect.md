---
title: "false monitor detect"
date: 2009-02-08
forum: Multimedia Software
---

### Post by s.dalas on 2009-02-08
Hi there, 

i'm new in linux (1week) but also impressed with what they can do...
i really got help from this forum but i have a problem with my monitor. 
I have a philips 107s (17") but in the screen resolution option it says that i have philips 15". i tried the xorg and this is the result : 
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

I think that there is a problem with my graphic card too (intel integrated grpaphics X3000).

is there a way where i can see the hardware of my system (what linux see) and fix any problem?

---

### Post by s.dalas on 2009-02-09
plz any ideas?? help!!

---

### Post by redroad55 on 2009-02-09
Hi , Try this link it will give the imfo your looking for .. If not post back and will look further .. best to you
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by s.dalas on 2009-02-10
Thanks a lot for your advise, but i coudnt do anything.
I can see the different resolutions with the xrandr commant but nothing about my hardware.

i think i need something like this:

[http://ubuntuforums.org/showthread.php?t=587526&highlight=philips+107s+t4](http://ubuntuforums.org/showthread.php?t=587526&highlight=philips+107s+t4)

but i don't know where to find the "philips session" which mentioned on the above link.

Thanks a lot again!!

---

