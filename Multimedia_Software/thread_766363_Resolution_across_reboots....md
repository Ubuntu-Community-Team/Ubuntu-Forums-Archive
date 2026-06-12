---
title: "Resolution across reboots..."
date: 2008-04-25
forum: Multimedia Software
---

### Post by orange2k on 2008-04-25
As the title says, Ubuntu doesnt remember the set resolution across reboots...

I installed the nVidia driver with the help of EnvyNG (on a fresh Hardy install) and the only way to get the resolutions above 1024x768 is to use the nVidia X server settings. Everything is fine but I cant get it to be remembered after a reboot: every time it sets back to 1024x768.

What should I do?

---

### Post by piratesmack on 2008-04-25
Open a terminal and copy and paste:

```

sudo gedit /etc/X11/xorg.conf

```

Inside xorg.conf, locate the "Screen" section. It should look something like:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

```

Change it to something like this (Use whatever resolutions you need):

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
		SubSection "Display"
			Depth 24
			Modes "1024x768" "800x600" "640x480"
		EndSubSection
EndSection

```

The first resolution after "Modes" will be the default

---

### Post by orange2k on 2008-04-25
Thanks, it worked.

---

### Post by piratesmack on 2008-04-25
> **orange2k said:**
> Thanks, it worked.

no problem

---

