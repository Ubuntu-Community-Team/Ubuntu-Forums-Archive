---
title: "ATI - Low resolution with dualhead clone"
date: 2008-09-14
forum: Multimedia Software
---

### Post by kcleong on 2008-09-14
I'm trying to setup a dualhead clone monitor setup on my laptop. Because of a presentation I need the clone setup. The clone setup is working but at 1024x768, I need 1280-x1024.

Hardware:
HP Compaq nc8430 laptop
Latest Ubuntu
ATI X1600 (8.8 proprietary driver)

Config/log:
xorg.conf * -  [http://paste.ubuntu.com/46975/]("http://paste.ubuntu.com/46975/")
xorg log - [http://paste.ubuntu.com/46976/]("http://paste.ubuntu.com/46976/")

* second screen is disabled in xorg.conf allowing clone mode.

The problem is the resolution stuck at 1024x768, I want it at 1280x1024. A big desktop setup (with two X's) and correct resolution is working.

Got these following lines of config for clone setup. Here I'm setting the resolution and sync for the secondary screen.

```

	Option	    "DesktopSetup" "clone"
	Option	    "clone" "clone"
	Option	    "Mode2" "1280x1024,1024x768"
	Option	    "HSync2" "80" #This sets the horizontal sync for the secondary display. 
	Option	    "VRefresh2" "75" #This sets the refresh rate of the secondary display.

```

When looking in the logs I see that my monitor (Iiyama prolite e1900) displays incorrect resolution info thru dcc/edid. I'm guessing that the root of the problem lies here. I also noticed that the extra xorg config lines for secondary resoltion/sync rates aren't displayed in the log. Anybody got a clue so I can get a higher resolution?

---

