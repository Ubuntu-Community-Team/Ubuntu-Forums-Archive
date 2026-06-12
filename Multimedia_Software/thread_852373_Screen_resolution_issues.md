---
title: "Screen resolution issues"
date: 2008-07-07
forum: Multimedia Software
---

### Post by DerEnglaender on 2008-07-07
Hi guys.
i just installed ubuntu and configured it. It was hooked up to a monitor and running at 1024*. Now ive disconnected it from the screen and using the remote desktop feature, but the resolution has reverted to 640* and the only other option i get (either using nvidia-settings or the ubuntu screen resolution under system>administartion) is 320*.

How can I get this to be 1024* again? :)

Also, my ultimate goal is to have the option of having ubuntu either output 1024* (when connected via remote desktop) or output to a tv via s-video. Is this possible, and if so could someone point me in the right direction please :)

Thanks for the help.

im running ubuntu 8.04 and ive got a gforce 5600 xt :)

---

### Post by DerEnglaender on 2008-07-08
well ive edited the xorg.conf and now i have 1024* resoluion via remote desktop, so now all i want to do is lone that sreen, make it 640* and send it via s-video to a tv.. anybody got any suggestions?

---

### Post by piratebill on 2008-07-08
I too had this same issue, and there is an easy fix.  
[http://ubuntuforums.org/showpost.php?p=4789536&postcount=110](http://ubuntuforums.org/showpost.php?p=4789536&postcount=110)

You can also get this program by right clicking on the menu bar and adding the application (it is unchecked in the "other" catagory I think).  Hope this helps

---

### Post by DerEnglaender on 2008-07-11
thanks im gonna give this a go :)

---

### Post by Mysterious_Name on 2008-07-11
> **piratebill said:**
> I too had this same issue, and there is an easy fix.  
[http://ubuntuforums.org/showpost.php?p=4789536&postcount=110](http://ubuntuforums.org/showpost.php?p=4789536&postcount=110)

You can also get this program by right clicking on the menu bar and adding the application (it is unchecked in the "other" catagory I think).  Hope this helps


Total noob here.  Where is the   usr/share/applications  ??  I don't know how to get to this.

---

### Post by m0r9un0v on 2008-07-11
Which monitor you have?

Backup current xorg.conf and try to replace subsection "Display" in your /etc/X11/xorg.conf with this:

	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection

---

### Post by Mysterious_Name on 2008-07-11
I appreciate the help, but have no idea what that means.  Talk to me like a retarded cousin or baby.

---

### Post by Mysterious_Name on 2008-07-11
My monitor is a 14.1" WXGA High-Definition BrightView Widescreen Display (1280 x 800) on a HP Pavilion 2845se notebook.

---

