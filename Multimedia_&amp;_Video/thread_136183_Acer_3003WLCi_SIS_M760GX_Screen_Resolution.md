---
title: "Acer 3003WLCi SIS M760GX Screen Resolution"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by dhm on 2006-02-25
I recently purchased the above mention laptop and upon installing ubuntu 5.10 found that I could not get my screen to display at 1200x800. After much googling and forum searching I came upon a solution that worked for me.  Before I was trying a number of fixes and combinations found in other posts, but nothing was working for me.

I finally manually edited my xorg.conf file after reading about a similar problem and solution here: [http://www.iguild.de/HOWTO/AMILO_A_1645-en.html]("http://www.iguild.de/HOWTO/AMILO_A_1645-en.html")

So if you are having similar problems, give this a shot.  The relevant section of my xorg.conf file now looks like this.

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```
 
Hope this helps.

---

### Post by Kartik Babu on 2006-03-21
This also works with the ACER AS5003WLMi laptop with Breezy running on an AMD Turion 64

---

### Post by rosslaird on 2006-04-11
Thanks very much for posting this. I searched and searched...
Works perfectly.

Cheers.

Ross

---

