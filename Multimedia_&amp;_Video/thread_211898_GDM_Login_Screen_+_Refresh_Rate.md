---
title: "GDM Login Screen + Refresh Rate"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by atrophic on 2006-07-09
My monitor thinks it can support 1280x1024 @ 85Hz but it can't.  It distorts the crap out of the image and has some parts of the screen trying to display more than one pixel at one (as it gets really really bright).  If it's left like this for long, it smells like burning.  I've had a monitor do this to me on an old computer, and eventually the monitor just stopped working.  I don't want that to happen to this monitor, so I just run at 1280x1024 @ 60Hz (70/75Hz work, but cause everything but the edges of the screen to be blurry).

I have 1280x1024 @ 60Hz set as the "Default for this computer" via the Screen Resolution option in System -> Preferences.  However, the login screen for gnome does not respect that setting, apparently  I've tried playing with my xorg.conf file to outright disable any refresh rate above 60.

```

Section "Monitor"
	Identifier	"DELL M993s"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	43-60
EndSection

```

I've spent a couple hours on this now, and have searched the forums and google high and low.  Can somebody help me get gdm's login screen to respect a specified screen resolution/refresh rate?

---

### Post by atrophic on 2006-07-10
I'm allowing myself one selfish bump to get this more attention ;)

---

### Post by sr20ve on 2007-07-13
I have this same issue. My refresh rate on the login screen is 75hz which distorts my display, I'm able to login and set my refresh rate down to 60hz which works fine, but the login screen still keeps it's same setting and I can't find where to change it.

---

### Post by drewcoon on 2008-06-03
Bump I wouldn't mind a fix to this problem either :)

---

### Post by StooJ on 2008-06-04
Ran into this problem as well. I opened up the Login Window Manager (System -> Administration -> Login Window) and in the Local tab I changed the Style option from **Themed with face browser** to just **Themed**

Don't ask me why this fixed the problem, but after restarting my GDM login showed up fine.

---EDIT---
I spoke too soon. It worked once, but now I'm back to an "Out Of Range" error again. If I find a solution I will post it here.

---

### Post by BattlePanic on 2008-06-06
I just recently installed Xubuntu 8.04 and encountered something similar.  I configured the xfce desktop environment to display at 1024 x 768 @ 60hz.  Before loading xfce, I noticed that the GDM login screen starts up with a resolution of 1280 x 1024.  Only after logging in is the monitor switched to 1024 x 768.  Is there a means of setting the resolution such that the gdm session manager is also runs at 1024 x 768?

---

