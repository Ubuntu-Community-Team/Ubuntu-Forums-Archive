---
title: "Resolution Hell"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by stevenjo57 on 2007-06-06
Can't get Feisty 7.04 to display 1280x1024.

Have added lines to xorg.conf. Ran dpkg and went through the questions. Selected 1280x1024 and saved it. Checked xorg.conf and 1280x1024 is listed!

Still doesn't show up in Administration-Screen Resolution.

Tried sudo nvidia-settings, still doesn't list 1280x1024. Seems to top out at 1280x800.

How can something be this hard?  Got it working fine at 1680x1050 on my 22" monitor. But 1280x1024 on my 17 inch monitor? FORGET IT.

Thanks for any help.

---

### Post by NeoLithium on 2007-06-06
What's the output from terminal for:
```
lspci
```
Perhaps you're missing a specific driver to get the best out of your video card.

---

### Post by ryanVickers on 2007-06-06
Have you installed the nvidia driver (using restricted drivers manager)?  That worked for me! 1280x1024

It ads lots of options too...

---

### Post by klabak on 2007-06-07
I'm having the same problem as well. I have a RIVA TNT 2 card on an old P3 (yeah I know but I felt like making a linux box on this old system at work). While installing Ubuntu I had a resolution of 1280X1024 (my system defaulted to this) up until I installed the legacy drivers for my card. I have a viewsonic 19" (max res 1280X1024) and I know this card supports this resolution. After installing the legacy drivers and enabling them, I only have 1024x768, 800x600 and 640x480. I checked my xorg.config file and it has all the appropriate resolutions that I want under the "screen" section. Even if I try disabling the legacy drivers the default ubuntu drivers don't pick up the higher resolutions anymore. Is there anything else I can do or do I have to look at large text??? *gasp* Thanks.

---

### Post by bobo1on1 on 2007-06-07
Try increasing the HorizSync and VertRefresh values in xorg.conf, they might be too low for the resolution.

Putting the resolutions in the screen section might not be enough, you also need them in the monitor section.

---

### Post by stevenjo57 on 2007-06-10
Bobolon1 hit the nail on the head. My frequencies in the xorg.conf weren't high enough.

I copied the frequency stuff from another xorg.conf that was working at higher resolutions and everything kicked in.

Thanks for your help!

Here is my Monitor section that fixed it.
------------------------
Section "Monitor"
	Identifier	"ViewSonic VP171s"
	Option		"DPMS"
    	HorizSync       31.0 - 83.0
   	VertRefresh     56.0 - 76.0
    	Option         "DPMS"
----------------------------------------

---

