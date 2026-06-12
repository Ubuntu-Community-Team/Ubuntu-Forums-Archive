---
title: "Screen resolution not filling entire display"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by booyabazooka on 2006-06-18
I just installed Ubuntu on a Dell Dimension 8200s.  The screen resolution is on the highest setting listed, 1024x768 (and I believe this is the highest supported by my monitor), but the displayed area is rather small, with a solid 1+ inch black margin around it.  The graphics card is something by Nvidia - I can dig up the details on the card or the monitor if that would help.

---

### Post by MonkeyBoy on 2006-06-18
I have seen that crop up on two different pcs so far.  On a friend's old desktop it was because the graphics card needed to be in 800 by 600 resolution but had defaulted to 1024 by 768.  On one of my Armada laptops it was because the LCD monitor couldn't handle 32 bit colour resolution and needed to be altered to 16 bit.

It might be worth your while trying a change in colour resolution.  Typing ```
sudo dpkg-reconfigure xserver-xorg
``` is probably the quickest way to try this out.  Keep pressing enter until it asks about the monitor then choose 16 instead of 32.  If this doesn't work it is easy to change back in exactly the same way.

I hope this helps.  :)

---

### Post by booyabazooka on 2006-06-18
Changes to the color settings and resolution have no effect.

(Side question: I had to reboot the entire system to enact the color modification; does Ubuntu have a way to just close/restart the window manager?)

---

### Post by darkpark on 2006-06-18
yes  ctrl+alt+backspace  will restart X.

by the way, have tried adjusting the refresh rate? also, the vertical and horizontal timings will/might make a difference.  check  your xorg.conf:

I have a samsung LCD monitor

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

```

---

### Post by booyabazooka on 2006-06-18
At 1024x768, my only refresh rate option is 60 Hz.  56 is listed only at 800x600.  No such changes have accomplished anything.

Under windows, I had been running "32"-bit color at 1024x768, 60 Hz, so I know the monitor supports it.  My xorg.conf is exactly as darkpark's.  It's an LCD monitor; what manufacturer I am not sure, as it has been rebranded by Dell.

---

### Post by greenstar on 2006-06-19
Try adjusting your monitor's display with the buttons on the front of the monitor. Sounds like you need to adjust the vert & horiz size from the on-screen display.

greenstar

---

### Post by booyabazooka on 2006-06-19
This monitor does not have the option to adjust width and height; and, on the digital (as opposed to vga) interface, it doesn't even have the option to adjust positioning.

I did notice something in the menu that may be helpful, though - the monitor thinks it's running at 1280x1024.  Perhaps that would explain why a 1024x768 screen doesn't fill it?

I tried adding 1280x1024 as a resolution option in /etc/X11/xorg.conf, but it won't use that res, and it doesn't show up in the Screen Resolutions option box.

---

