---
title: "Intrepid multi-monitor configuration with mixed resolutions/rotation on an ATI HD4850"
date: 2008-11-01
forum: Multimedia Software
---

### Post by tomkinsc on 2008-11-01
:arrow:*Summary:*
I am having difficulties (](*,)) configuring a multi-monitor setup on Intrepid using the out-of-the-box (or off-the-mirror mirror) proprietary ATI drivers. I am running two monitors, one at 2560x1600, and a secondary at 1680x1050. The secondary monitor is rotated 90 degrees clockwise relative to the user. The graphics card is an ATI HD4850. I currently have the monitors setup to use BigDesktop. This works as I would like (with window dragging between screens, and support for separate panels for each screen), but does not seem to allow for rotation of the secondary screen.
**Is there a way to support such a setup, and if so, how?**

:arrow:*Graphical Overview:*
I'm a very visual person, so I made this image to summarize the problem. (Made with the wonderful open source Inkscape)
[Image]("http://img528.imageshack.us/img528/6965/multimonitorproblemjj6.png")

:arrow:*Current xorg.conf:*:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "PairModes" "2560x1600+2560x1600,2560x1600+1050x1680"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection
```

:arrow:*Plead for help:[-o<*
I'm fairly familiar with *nix systems, but I have never really learned how to get xorg.conf properly configured.:-k I figured this was a question for the gurus of the Ubuntu forums, guessing that if anyone would know how to get such a setup working, someone here would. Have any ideas?

Thank you for any assistance you can give.

---

### Post by tomkinsc on 2008-11-01
Is there a way xrandr or something similar could be used for this?

---

### Post by Vadi on 2008-11-01
I was told to use the Catalyst Control Center, which I recommended to a friend who was faced with this today and he said he got it working.

So, give that a try. Oh and this was on Ubuntu 8.10

---

### Post by Vadi on 2008-11-01
Edit: oops, double-post. The servers must be feeling the load from the new release

---

### Post by tomkinsc on 2008-11-01
The Catalyst Control Center works well for setting up spanning, but it does not have an option for rotation.

---

### Post by tomkinsc on 2008-11-01
What about aticonfig? It accepts so many parameters...
Do you think it could help with this?

---

### Post by tomkinsc on 2008-11-02
Bump for the Sunday crowd.
Does anyone know of a GUI for aticonfig? (something different/more flexible than ccc)

---

### Post by tomkinsc on 2008-11-07
Is there another place that might be able to help with this? Should I bother posting elsewhere?

---

### Post by meow9th on 2009-01-17
Note: I'm a Linux newbie.

I have the same kind of set up: two monitors (Monitor 0, Monitor 1), one rotated (Monitor 0), ATI graphics. After struggling for several days, I've come up with a solution that is tolerable but obviously suboptimal.

I started with a clean xorg.conf, then used aticonfig to get a minimal dual-head configuration:
```
--initial=dual-head
```
```
--screen-layout=left
``` (your mileage may vary)
```
--set-pcs-str="DDX,EnableRandr12,TRUE"
``` (to enable xrandr, according to various Google search results I ran across)

Then I installed ARandR (it's in the repo), launched it in Monitor 0, and adjusted the orientation. Saved the configuration and added it to my session startup list.

The problem is that the two displays almost act like two different sessions. Can't drag windows, can't even alt-tab between windows on different displays, weird panel behaviour, etc. But at the same time, they share the same clipboard, sometimes applications launched from one display will show up in the other, etc.

My system configuration right now is usable but hardly good. If anyone has any improvements, I would love to hear about them. I wanted to experiment with BigDesktop and ARandR, but I couldn't get into BigDesktop mode again (though in my earlier efforts I was able to do so).

---

### Post by Vadi on 2009-01-18
meow9th, if nobody answers you here - I'd recommend posting on the [Phoronix forums]("http://www.phoronix.com/forums/forumdisplay.php?f=19"). Even ATI employees lurk there and may help you.

---

