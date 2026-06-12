---
title: "Horizon 22&quot; LCD and nvidia drivers"
date: 2009-09-19
forum: Multimedia Software
---

### Post by cazimir on 2009-09-19
Hello!I have a big problem with my display.With opensource nv driver the display it's set at native resolution,60hz refresh rate.The problem is when i want to activate the proprietary driver...after i restart X or restart computer the display goes on Stand By mode and nothing happens.I tried to manually install the nvidia driver from source but the same problem.In all Linux distributions that i tried i have the same problem.My PC is an Intel E2140@1.6ghz,3gb ddr2,Nvidia Geforce7300gt DDR3,and the display is an Horizon 2206SW 22".Please help me.Thank you very much.

---

### Post by cazimir on 2009-09-20
up

---

### Post by cazimir on 2009-09-21
Nobody can't help me?

---

### Post by PurposeOfReason on 2009-09-21
Please post your xorg.conf file when you use the nvidia driver.

---

### Post by cazimir on 2009-09-21
This is on Ubuntu 9.10 Alpha6.


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


LE: I forgot to say that i use my monitor on DVI connector.

---

### Post by cazimir on 2009-09-22
up

---

### Post by cazimir on 2009-09-23
up

---

