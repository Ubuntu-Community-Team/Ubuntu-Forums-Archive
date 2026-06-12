---
title: "Resolution Problems with Intel 965 Graphics"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by Doughy on 2007-05-02
I can't get my monitor (ACER AL1916) to do anything other than 1024x768 even though I know it can support it.  Ubuntu will not display any other resolutions in the preferences->screen resolution menu.  I have tried everything, and looked everywhere.  My graphics are running off my intel 965 chipset motherboard.

Already Tried:
-dpkg-reconfigure xserver-xorg
-915Resolution

It is now 1AM and I am extremely frustrated with this.  Anyone know of a fix for this problem?!?

:mad: :mad: :mad:

---

### Post by Fitzy_oz on 2007-05-02
> **Doughy said:**
> I can't get my monitor (ACER AL1916) to do anything other than 1024x768 even though I know it can support it.  Ubuntu will not display any other resolutions in the preferences->screen resolution menu.  I have tried everything, and looked everywhere.  My graphics are running off my intel 965 chipset motherboard.

Already Tried:
-dpkg-reconfigure xserver-xorg
-915Resolution

It is now 1AM and I am extremely frustrated with this.  Anyone know of a fix for this problem?!?

:mad: :mad: :mad:

You can manually add the resolutions to the xorg.conf configuration file, a pain in the **** I know but it should solve you're issues....

Look at whats already there, it should only be one resolution there but a few different color depths.  Format a new line(s) exactly the same way but with the resolutions and/or color depths that you want....

If you need more details let me know. ;)  Better yet, post you're xorg.conf file in a post for me and I'll edit it for you and you can paste it pack.

---

### Post by Doughy on 2007-05-02
When you say "Add an new line,"  Do I need to add a new line or just change the exising ones.  I tried adding resolutions to my xorg.conf last night and they never appear in the menu in gnome.  Why?

---

### Post by Fitzy_oz on 2007-05-03
> **Doughy said:**
> When you say "Add an new line,"  Do I need to add a new line or just change the exising ones.  I tried adding resolutions to my xorg.conf last night and they never appear in the menu in gnome.  Why?

Sorry mate, had a bit of a brain fart - You just need to add the resolutions to the existing options.  I have hi-lighted the lines I added to my config file.



Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		[COLOR="Red"]"1600x1200" "1280x1024" [/COLOR]"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		[COLOR="Red"]"1600x1200" "1280x1024" [/COLOR]"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		[COLOR="Red"]"1600x1200" "1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		[COLOR="Red"]"1600x1200" "1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		[COLOR="Red"]"1600x1200" "1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		[COLOR="Red"]"1600x1200" "1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by Doughy on 2007-05-03
I just figured out the problem.

I changed my xorg.conf from a default resolution of 24 to 16, and everything is working now.  I'm not sure why it won't work with 24, but that is what causes the problem.

Once I changed to 16, all the resolutions that I had listed in the conf file showed up in the gnome menu.  Finally.

---

