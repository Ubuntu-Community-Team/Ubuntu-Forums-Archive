---
title: "New monitor, can't choose it's resolution"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Digimer on 2009-05-06
Hi all,

  For the last several years, I'd manually set my desired resolution, colour depth and H/V frequencies in xorg.conf (well, Xfree86 prior). I see that this isn't the "Ubuntu" way anymore as xorg.conf is might sparse these days.

  I've been trying to find the Ubuntu-way to set my monitor's resolution, it's an LG Flatron W2042TQ with a native resolution of 1680 x 1050. So far though, I've not been able to do this.

  I can see no reason why this should be so difficult.

  Anyway, I've tried 'dpkg-reconfigure -phigh xserver-xorg' (and without thhe '-phigh' switch) and have had no luck. The highest resolution it offers me is the odd 1360 x 768 resolution.

  So what am I missing? For that matter, what file are these settings stored in these days?

Thanks!

Digi

---

### Post by Digimer on 2009-05-06
I should mention, 'sudo dpkg-reconfigure xserver-xorg' doesn't prompt me to select a resolution. If I add '-phigh', it simple returns reporting that it backed up my xorg.conf file. When I 'diff' the backup against the new file there is no difference.

Digi

---

### Post by xc3RnbFO8P on 2009-05-06
Which video card do you have?

---

### Post by Digimer on 2009-05-06
An old ATI Radeon R200 QL (Radeon 8500 LE), according to lspci.

By the way, I manually edited the 'xorg.conf' file to setup for my monitor and it works fine, but it was tedious. I'd like to know the better way, as I do a fair amount of support work and given that the LiveCD always gets it right...

Digi

PS - Here is my working xorg.conf file:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"LG Flatron W2042TQ"
	VendorName	"LG"
	ModelName	"W2042TQ"
	HorizSync	30-83
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"LG Flatron W2042TQ"
	Device		"Configured Video Device"

	DefaultDepth 24
	Subsection "Display"
		Depth 24
		Modes "1680x1050" "1440x900"
	EndSubsection

EndSection

```

---

### Post by xc3RnbFO8P on 2009-05-06
Did you try System> Preferences> Display?

---

### Post by Digimer on 2009-05-06
Yup, that's where I saw the odd maximum res of 1360 x 768. Also, I did restart gdm after each attempt to ensure any changes were loaded.

Digi

---

### Post by xc3RnbFO8P on 2009-05-06
What about restricted driver, did you enable it?

---

