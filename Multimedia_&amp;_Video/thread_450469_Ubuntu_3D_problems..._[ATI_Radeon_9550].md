---
title: "Ubuntu 3D problems... [ATI Radeon 9550]"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by jorgehumberto on 2007-05-21
Hi!

I'm new to Ubuntu and had some problems installing the graphic drivers on it (i'm using Feisty...)... most of the times i tried it i somehow managed to crash  "Xorg" (like 4-5 times...)...
The few times i managed to install the drivers without crashoing "Xorg", when i tried to play Warsow, all i got were bad graphics... but a good framerate....

but finally, thanks to ENVY (latest version..), i managed to install them, and be able to play games, with good graphics... and nice frame rates...  on Warsow i get around 90 fps... i have'nt  tried other games yet... so have no other results...

but, there's still one issue that bothers me...
when i run *fgl_glxgears* i get around 300 fps...

with *glxgears* it's worse... i only get around 100-150 fps...

before installing the ENVY drivers, i used to get around 1000 fps on *glxgears...* and that with direct rendering disabled...

Besides, now my screensaver is always jerky, while before it used to run smoothly...

One thing i noticed while installing Cedega was that it did pass the open gl test, did not pass the 3D acceleration test...

So, could anyone help me figure out what's going on with my 3D acceleration?

i'm running Ubuntu Feisty on:
AMD Athlon XP 1900+
512 MB DDR
ATI Radeon 9550

Thanks for all the help you can provide me...

Regards,
Jorge Humberto

---

### Post by dodgePT on 2007-05-21
The relevant sections of your xorg.conf would be helpfull ;)

---

### Post by jorgehumberto on 2007-05-21
> **dodgePT said:**
> The relevant sections of your xorg.conf would be helpfull ;)

well... that might be a good idea indeed..
lol


here goes the parts that (i think..) are relevant...

> 
...

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

...

Section "Device"
	Identifier	"ATI RADEON 9550"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:3:0:0"
EndSection

...

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "disable"
EndSection



---

### Post by dodgePT on 2007-05-21
I've got a ATI 9600 pro, i never had good results with proprietary drivers (fglrx).
After trying all possible configurations i ended up using open source drivers (radeon) with aiglx method, which allowed me to run beryl and desktop effects, with most of the screensavers working.
3D gaming also works, but i've only tried Tux Racer, don't know about the rest.
X doesn't crash anymore, and everything looks stable.
I'm not an expert but everything looks fine with your xorg.conf. I guess the cause for all this are the shitty proprietary drivers, since they're made mainly for 2D and not for 3D tasks (correct me if i'm wrong).

Uninstalling proprietary drivers might be a headache, i had to make a clean install and use open source drivers to solve the problem (i had that nasty mesa drivers bug).

Sorry for not being able to help you more :(

---

