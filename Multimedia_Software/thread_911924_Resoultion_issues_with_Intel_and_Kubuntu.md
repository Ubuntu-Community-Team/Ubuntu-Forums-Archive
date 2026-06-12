---
title: "Resoultion issues with Intel and Kubuntu"
date: 2008-09-05
forum: Multimedia Software
---

### Post by wandalalakers on 2008-09-05
I have a Dell D620 laptop with an Intel 945 video chipset.  I'm trying part of your xorg.conf to see if it will fix my incorrect resolution problem and unable to use screensaver problem.

I copied this info to my xorg.conf
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by overdrank on 2008-09-05
> **pcdoctor said:**
> I have a Dell D620 laptop with an Intel 945 video chipset.  I'm trying part of your xorg.conf to see if it will fix my incorrect resolution problem and unable to use screensaver problem.

I copied this info to my xorg.conf
```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection
```

Also you may try and use the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by wandalalakers on 2008-09-06
I assume that command is for gnome.  I'm using kubuntu.  Hmmm.  I turned on the laptop this morning and I got a text login.  After logging in it used the root account instead of my account.  The video settings were correct when I turned on the laptop this morning.  I'm not sure how that happened.  The settings that I cut and pasted in the xorg.conf last night from above are gone.  I did an exit and logout then logged in as me and set the video to 1280x800.  I have no idea what happened overnite.  I had to do a dpkg-reconfigure in order to get my gui login back and I told it to use the frame buffer.  I'm not sure if that's necessary. Concidently, my original xorg.conf looked kinda similar.  Well, I went ahead and took the frame buffer stuff out but I still can't view opengl screensavers.  When this happened on my kubuntu desktop with a Nvidia card it was a driver problem.  I'll go to Intel's website to see if they have an updated driver for linux.

Here is my partial new xorg.conf

open terminal
sudo nano /etc/X11/xorg.conf

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

I don't think I'll use the driver from Intel's website.  It looks like it's dated 2/7/07.

---

### Post by overdrank on 2008-09-06
Hi and I have moved your post to its own thread.
I do not have a system using KDE at the moment but have you tried booting into recovery mode and use the xfix option. If you are using hardy then the recovery mode is usually the second choice from the grub.

---

### Post by wandalalakers on 2008-09-06
I got it working now but I'm not sure how.  I modified my xorg.conf last night and when I got up this morning I got a text login instead of a gui one.  I logged in and the system was at the Root$ or Root# prompt.  Long story short I now have 1280x-800 resolution.  When I also got up this morning my xorg.conf was different that what I changed it to last night.  Basiscally, my xorg.conf is now different from my first post in this thread.  Now I just need to get my opengl screensavers to work.

---

