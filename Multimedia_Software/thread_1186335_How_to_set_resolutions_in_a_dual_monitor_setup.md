---
title: "How to set resolutions in a dual monitor setup"
date: 2009-06-13
forum: Multimedia Software
---

### Post by meamusta on 2009-06-13
Hi,

There is a load of threads about xorg.conf editing, but none of them has really helped me.

I got my dual monitor system working somehow with the xorg.conf file below.

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

```

I use Jaunty and the above settings work just fine if I turn my laptop on so that the external monitor is attached. Then the dual monitor environment is enabled automatically (External monitor is extended by laptop to the right). 

Now the only problem is that even though I have given the virtual desktop 2560x1024 resolution, both of my screens are run on 1024x768 resolution. If I try to change resolutions (or anything else) from the Display Preferences the dual monitor environment gets turned off and my laptop will be the only display in use. 

I would like to have my external (CRT) monitor on 1280x1024 and laptop on 1280x800 resolution. I'm having intel 915/910 chips in my laptop and the default driver. I have read that on intel chips larger virtual resolution than 2048x2048 needs 3d acceleration disabled. That's ok for me.

If there is somewhere a simple but still comprehensive guide to xorg settings, a link to it would be much appreciated also.

---

### Post by meamusta on 2009-06-15
After adding line:
Option "NoAccell" "1"
to my Section "Device" in xorg.conf the automatics of xorg gave me a dual monitor environment where my laptop extends the external monitor. From "System" -> "Preferences" -> "Display" I was also able to change my external monitor resolution to 1152x864 from 1024x768.

But when I try to manually change my laptop resolution from 1024x768 to 1280x800 which is available, after applying the change, nothing happens.

The sum of those pixels would be below the limit of my virtual display (2560x1024), but still the change wont happen. Why?

Also why there is no option for resolution 1280x1024 or 1280x960 for my external monitor in the "Preferences -> Display" -menu?

---

### Post by meamusta on 2009-06-17
This X does what it likes.

I now commented out the "NoAccell 1" line from my xorg.conf file and restarted the machine. I thought I would not have both of my monitors on after that, but surprise surprise, for some funny reason it works still.

Once when I turned my machine on, I got my external monitor starting with 1152x864 and laptop screen with 1280x800. All the rest of the times when I turn my machine on I get my external monitor start with 1152x864 and laptop with 1024x800.

It's fun to turn your computer on and wait what kind of display set you get this time :)

---

