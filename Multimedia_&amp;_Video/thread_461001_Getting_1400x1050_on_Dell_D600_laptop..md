---
title: "Getting 1400x1050 on Dell D600 laptop."
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by davemar on 2007-06-01
I've hunted high and low to find a solution to this, but with no luck.

I've got a Dell Latitude D600 laptop which uses a ATI Radeon Mobility 9000 video card (so it says). Supposedly this laptop can display a resolution of 1400x1050. Currently I'm stuck at 1024x768 and the "Screen Resolution" menu doesn't give me anything higher.

I'm running Ubuntu 6.06 LTS. Do I have to download drivers for this video chipset? I've had a fiddle with xorg.conf, but nothing improves the situation.

Any help would be gratefully received!

---

### Post by crispy_420 on 2007-06-02
Did you try the fglrx driver?

---

### Post by Rocket2DMn on 2007-06-03
A user in another thread is having the same problem, thought he is using Beryl like myself.  I'm using the same card and I just posted my advice there, perhaps you can have some luck with it, or at least follow the thread responses and hope something more useful shows up.

[http://ubuntuforums.org/showthread.php?t=462824]("http://ubuntuforums.org/showthread.php?t=462824")

---

### Post by davemar on 2007-06-04
I followed the instructions on the howtoforge page from the thread link you gave; unfortunately all I ended up with was a black screen! So I'm further away from where I was before... Good job I backed up the xorg.conf file.
I'm not fussed about having Beryl on there, just to have my desktop displaying at a higher resolution than I have currently.

Which driver should I be using, this fglrx one or another one? Where do I get them from?

---

### Post by lognok on 2007-06-05
hi davemar, here is some line from my xorg.conf file.

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

I think you need to add the "1400x1050" resolution to you xorg.conf file. It should look like: "1400x1050" "1280x1024" "1024x786",....

hope this helps you reach that resolution

---

