---
title: "Intel 965GM, wine and beta drivers"
date: 2008-09-25
forum: Multimedia Software
---

### Post by kalaka on 2008-09-25
Hi,
I'm sorry if this post is in the wrong section, please move it if it is.
I have a Toshiba laptop with an Intel 965GM integrated graphics card. I'm using Ubuntu Hardy 8.04. I have the appropriate video drivers (aka xserver-xorg-video-intel) which have worked quite well (I have compiz enabled and it runs smoothly). I have direct rendering enabled:
> sampi@Anna:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2


I currently have wine-1.1.5 installed (I have tried with wine-1.0 as well). My problem is I can't seem to run some games such as [SPORE]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13839") and [Star Wars: KOTOR]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4124"). I get no error output when I run these games from the terminal. It seems to be a graphics/drivers problem. I found many people have had lots of problems with this card and wine.

Has anybody experienced similar problems? How did you solve them?

Are there beta/development drivers for this card? Where can I get them and how do I install them in Ubuntu?


Thanks in advance for your help.

---

### Post by kalaka on 2008-09-27
Bump :)


Could anybody help me with this? Is there a simple way to install the beta intel drivers on Ubuntu?

---

### Post by xnostradamusx on 2008-11-08
> **kalaka said:**
> Bump :)


Could anybody help me with this? Is there a simple way to install the beta intel drivers on Ubuntu?


type this in your terminal

gksu gedit /etc/X11/xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
EndSection

add this below Identifier	"Configured Video Device"
        Driver "intel"

it should appear like this now

Section "Device"
	Identifier	"Configured Video Device"
	Driver "intel"
EndSection

that is to force your intel driver to be used instead of vesa or mesa

---

### Post by kalaka on 2008-11-09
I'm using the intel drivers but I'm still having problems. This is from my /etc/X11/xorg.conf :

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

---

