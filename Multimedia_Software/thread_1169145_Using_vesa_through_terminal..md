---
title: "Using vesa through terminal."
date: 2009-05-24
forum: Multimedia Software
---

### Post by Atrus6 on 2009-05-24
Here is my problem.  My moniter, for whatever reason runs at an awkward refresh rate.  This also means that unless I am using either the vesa drivers or the nvidia drivers, I get a nice status on my moniter stating "frequency out of range".  Annoying, I know.  My question is, how do tell the xserver to use vesa, so I can install the nvidia driver (since I can do it with the gnome gui)?  Whenever I try and use dpkg, I get a series of questions about my keyboard...and that's it.  Hardly helpful.  Even manualy going to /etc/X11/xorg.conf with nano doesn't help, because the configuration file only has the big comment in the begining plus things like

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

So, yeah, kinda stuck here.
Thanks in advance though.

---

### Post by shaloken on 2009-05-24
what is your monitor?
the mark, model, refresh rate...

---

### Post by Atrus6 on 2009-05-24
eMachines
Model:.500pw
Refresh Rate: 57hz

---

### Post by kerry_s on 2009-05-24
> **Atrus6 said:**
> eMachines
Model:.500pw
Refresh Rate: 57hz

```
Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync    	35 - 60
        VertRefresh  	50 - 57.1
EndSection
```

or

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection
```

---

### Post by Atrus6 on 2009-05-25
Thanks, worked like a charm.

---

