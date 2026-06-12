---
title: "Voodoo3 second monitor"
date: 2008-11-04
forum: Multimedia Software
---

### Post by yoda2031 on 2008-11-04
I've searched tirelessly for any help on this, and turned up a little but nothing I didn't already know.

Basically, I had a spare monitor and a spare Voodoo3 graphics card lying around so I decided "hey, might as well be using these" and slapped the card in my box, hooked up the monitor and sat back to see the new monitor stay blank.  "Ok," I thought, "This is Linux, if it doesn't work - fix it".  So I delved into my xorg.conf file and (after a good 3 hours tweaking and sighing then looking up information on the internet only to find what I already had was "supposed" to work) I have only one working monitor.

I can't rule out the fact that the second graphics card is simply fried, but for the fact it's showing in the list of devices produced by lspci.

Here are the relevant parts of my xorg.conf:

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0	"RightScreen" 0 0
	Screen		1	"LeftScreen" LeftOf "RightScreen"
EndSection

# I chopped out the second (working) Device section for brevity

Section "Device"
	Identifier	"Voodoocard"
	BusID		"PCI:5:2:0"
	Driver	"tdfx"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"LeftMon"
EndSection

# I also chopped the working Monitor section

Section "Screen"
	Identifier	"LeftScreen"
	Device		"Voodoocard"
	Monitor		"LeftMon"
SubSection "Display"
	Depth 16
	Modes	"1024x768"
EndSubSection
	DefaultDepth	16
EndSection

# and the working Screen section

```

If you want me to put in the whole config that's fine, I just thought it might be easier to read -only- the bits that affect the monitor that doesn't work for the time being.

So, any ideas?

---

### Post by yoda2031 on 2008-11-08
Is there anything I've left out from my original post?  It's just that it's been several days now and no sign of a response...

---

