---
title: "So frustrated trying to get Radeon 9200 PRO to work"
date: 2008-10-27
forum: Multimedia Software
---

### Post by deanosrs on 2008-10-27
Hi,

I'm here to report that it's just way too hard to get display settings right in ubuntu. I bloody work in software development, I'm no computer idiot, but it's just right in at the deepend and after a frustrating evening I'm coming to beg for help because I'm about to hurt something, most likely my computer.

I have a radeon 9200 Pro and am using a CIBOX C2201 monitor ([http://www.cibox.tm.fr/web/english/products/Monitor/C2201-e.htm#C2201](http://www.cibox.tm.fr/web/english/products/Monitor/C2201-e.htm#C2201)). When I first tried to get 8.10 live cd going, it gives me a horrible flicker at the login screen. The only suggestion I could find was to start in graphics safe mode, an option which isn't there in 8.10. No, I had to download all of ubuntu again for v. 8.04, and there it was.

Having installed it, the resolution was all wrong - 1024-768 - and slightly cropped to the right.

Now this is where I just have no clue what to do and have messed around with xorg.conf but everywhere seems to tell me to do something differently. I mean, seriously, some sites telling me to install xlgrf or something, others telling me to just use radeon drivers, BUT NOWHERE WANTS TO TELL ME HOW TO INSTALL THEM! It's just driving me mad (as you can see).

What advice should I actually take? How can I install new drivers? Is xlgrf a good idea? What is it? Is the 1024x768 just the graphical safe mode? Is there something I need to do to get out of this?

In short, please help and restore my faith in the open source community!

---

### Post by Yellow Pasque on 2008-10-27
No, don't install fglrx. Recent versions of it do not support the Radeon 9200 series. You should be using the radeon/ati driver. What does your xorg.conf look like? What resolution are you wanting to run?

---

### Post by deanosrs on 2008-10-27
Hi, thanks for the reply. I'd like to run 1680x1050. At the moment, xorg.conf is set to this:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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

```

Whenever I change the driver from "vesa" to "ati" or "radeon" I get flicker screen syndrome (although bizarrely the mouse renders fine) and have to go to command prompt before booting to restore the old xorg.conf.

---

### Post by deanosrs on 2008-10-28
Anyone? Please?

---

### Post by Gamjaevel on 2008-10-28
> **deanosrs said:**
> Hi, thanks for the reply. I'd like to run 1680x1050. At the moment, xorg.conf is set to this:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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

```

Whenever I change the driver from "vesa" to "ati" or "radeon" I get flicker screen syndrome (although bizarrely the mouse renders fine) and have to go to command prompt before booting to restore the old xorg.conf.

I had a similar problem with my resolution. and asked a friend for help. he told me to try adding

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
                SubSection "Display"
                    Modes           "1600x1200"
                EndSubSection
EndSection

In the Screen section. and guess what? It worked!

---

### Post by deanosrs on 2008-10-28
I tried that - it doesn't change anything. I think I'm correct in saying that in order to get the resolution to change, the driver has to be something other than vesa as that's the "safe" way of displaying ubuntu. It certainly won't change at all while hte driver is set to that anyway, yet changing it to ati/flgrx does bring up the correct resolution but I get the really bad flicker across the whole screen.

I've read in a number of places that for my graphics card I need to use the radeon driver. I can't find installation instructions for this anywhere though, does anyone know how to install this driver?

---

### Post by Gamjaevel on 2008-10-28
Uhmm. In this case I'm pretty much useless as a helper, since i'm actually having a little bit of trouble with my Radeon drivers aswell (1950x). I can change my resolution, though I can't play 3d games. Used the drivers from the resp. (Pakethanteraren) in swedish

---

### Post by norkers on 2008-12-07
I have just the same problem. I can't find the right driver to use. I've been searching for weeks to find a resolution but no joy!:icon_frown:

---

### Post by hardyn on 2008-12-07
this might be a bit of a cheeky reply... but instead of banging your head against a wall... might it be easier to find a used nvida 5xxx 6xxx used somewhere?  im sure you could buy one for only a few dollars?

---

### Post by norkers on 2008-12-07
Prior to installing the Radeon, I was using a nvidia 5500, I swapped because the nvidia started to overheat and crash alot. I'm on a small budget so I'd rather fix than replace!

---

### Post by zanox on 2009-05-14
> **Gamjaevel said:**
> I had a similar problem with my resolution. and asked a friend for help. he told me to try adding



In the Screen section. and guess what? It worked!


I've tried it on jaunty and didn't work!! :( anyone can help me?

My pc: Sempron 2200+, Radeon 9200 pro, 2GB RAM, Monitor Tatung (Vibrant) 17"

---

### Post by zanox on 2009-05-20
> **Gamjaevel said:**
> I had a similar problem with my resolution. and asked a friend for help. he told me to try adding



In the Screen section. and guess what? It worked!

It worked only if I start my pc with the monitor turned off and I turn it on when ubuntu is already loaded, but resolution menu doesn't show me 1600x1200 resolution anyway

---

