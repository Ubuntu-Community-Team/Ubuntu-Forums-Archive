---
title: "No sound on Toshiba Portege P4000"
date: 2009-02-21
forum: Multimedia Software
---

### Post by pepped on 2009-02-21
I have looked around in the forums, honest, but can't find quite the right solution to this.

New to Linux and wanted to get involved and squeeze a little more life out of my old P3 Toshiba Portege P4000.

Installed Xubuntu 8.10 Intrepid Ibex and all went well. Lovely interface and very nippy, great stuff.

Did the screen size fix to get the full 1024 x something display, rather than the little screen with loads of blank space around it.

Netgear wifi card worked out of the box, fantastic.

All going well - but no sound.

Nothing whatsoever.

Any ideas?

---

### Post by ecokirby on 2009-03-07
I have the same problem with Xubuntu 8.10 on a Portege 7200. I have tried setting the sound configuration to all different possible devices, ALSA, ESS Maestro, etc, but nothing works, not even a test beep. I downloaded all the codecs to play MP3s etc, but nothing . . . 
Everything else works great. Does anyone have any ideas what to do next???

---

### Post by satellite360 on 2009-06-10
> **pepped said:**
> Did the screen size fix to get the full 1024 x something display, rather than the little screen with loads of blank space around it.


Hi

What is the screen size fix for this laptop?  I have a tiny screen with lots of blank space and cannot seem to fix it.

No problem with sound - installed Linux Mint 6 XFCE - and seems fine.

Thanks

---

### Post by kerry_s on 2009-06-10
you probably need to manually add it to xorg.conf

press alt+f2
type> gksudo mousepad /etc/X11/xorg.conf

```

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	16
	SubSection "Display"
		Viewport   0 0
		Depth      16
		Modes	   "1024x768"
	EndSubSection
EndSection

```

---

