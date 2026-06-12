---
title: "How do I change my color depth?"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by khughes on 2006-08-02
I have an HP nc6120 laptop with an Intel 915 graphics card in it. I have been receiving errors on various programs that lead me to beleive that my color depth is only running at 16 bit and not 24 or 32. For example, when I disconnect from a terminal server session running at 24 bit, I get this error:

###############################################
WARNING: Color depth changed from 24 to 16.
NOT IMPLEMENTED: System pointer message 0x7f00
###############################################

So my question is, can someone tell me how to change my color depth to 24 or 32? I know for a fact that it can do 24 because when I was running SUSE 10.1 it was set through its YaST control center and in Windows it runs 32 by default.

---

### Post by zxee on 2006-08-02
> **khughes said:**
> 
So my question is, can someone tell me how to change my color depth to 24 or 32? I know for a fact that it can do 24 because when I was running SUSE 10.1 it was set through its YaST control center and in Windows it runs 32 by default.

If you feel comfortable with text editors you can open /etc/X11/xorg.conf and edit the default depth to reflect your system. I think 32 is just 24 with some software hack but I could be wrong. The other way to do this is from a terminal type> sudo dpkg-reconfigure xserver-xorg that opens a program/script that will alter your xorg.conf with values you enter.

---

### Post by khughes on 2006-08-02
> **zxee said:**
> If you feel comfortable with text editors you can open /etc/X11/xorg.conf and edit the default depth to reflect your system. I think 32 is just 24 with some software hack but I could be wrong.

Ok, so here is my xorg.conf section regarding my color depth. As you can see, it is showing my default depth at 24, but that doesnt explain my error about switching back down to 16 from 24?

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
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

---

