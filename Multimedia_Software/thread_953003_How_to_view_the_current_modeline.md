---
title: "How to view the current modeline"
date: 2008-10-19
forum: Multimedia Software
---

### Post by xo... on 2008-10-19
Hello every one, I am new to ubuntu.
Just wanna find out that is it possible to view the modeline I am currently using. Because if i open the xorg.conf, I can only see the follows.

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"

Didnt show me what modeline I am using.
Can anyone give me a hand please.:KS

---

### Post by yabbadabbadont on 2008-10-19
In a terminal window ```
xrandr -q
``` will show you some interesting information.  The current mode is marked with an asterisk.  You can also find some interesting information about your current X session by browsing through /var/log/Xorg.0.log

---

### Post by xo... on 2008-10-19
> **yabbadabbadont said:**
> In a terminal window ```
xrandr -q
``` will show you some interesting information.  The current mode is marked with an asterisk.  You can also find some interesting information about your current X session by browsing through /var/log/Xorg.0.log

thx, what happen is I have a Dell S2409W. which if I use it in windows at 1920x1080@60hz or 50hz resolution, it will keep 'flashing', but I dont have any problem on ubuntu, thats why I was trying to get the modeline from ubuntu and use it on windows. but no luck at all.
Its very wicked, cuz ubuntu does need a driver and let me use it at 1920x1080 without any problem. And I have been changeing differnt driver and modeline in windows and try to get it work.
So now its prove that my graphic card (intel 965gm x3100) do support 1920x1080, just problem with either windows or the driver.

---

### Post by modulistic on 2013-04-08
```
xvidtune -show
``` source: [http://howto-pages.org/ModeLines/](http://howto-pages.org/ModeLines/)

---

### Post by overdrank on 2013-04-08
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

