---
title: "Monitor standby?"
date: 2009-01-30
forum: Multimedia Software
---

### Post by WetWired on 2009-01-30
I'd like to know how to turn the standby for the monitor off in Ibex. I'll be trying to watch a movie or something, and I have to get up every so often to shake the mouse so it'll come back on. 

In the power management settings, I've set it to never put the display to sleep, but it still does. This is highly annoying. Can anyone help?

---

### Post by sisco311 on 2009-01-30
try:
```
xset dpms 0 0 0
```


```
xset dpms x y z
```
x = standby timeout in seconds
y = suspend ...
z = off...

a timeout value of zero disables the mode.

---

### Post by WetWired on 2009-01-30
And I'd put that in my xorg, right?

---

### Post by sisco311 on 2009-01-30
> **WetWired said:**
> And I'd put that in my xorg, right?

No, just run it in a terminal.

---

### Post by WetWired on 2009-01-30
Will those settings stay applied after a restart?

---

### Post by Yashiro on 2009-01-30
In a terminal:
> xset dpms 0 0 0

In xorg.conf
> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "MX518 Optical Mouse" "SendCoreEvents"
	[B]Option	    "BlankTime" "0"
	Option	    "StandbyTime" "0"
	Option	    "SuspendTime" "0"
	Option	    "OffTime" "0"[/B]
EndSection

In the screensaver panel, disable screen saver.

Run gconf-editor and search for all instances of 'dim' or anything else that relates to turning off your screen and disable it.

Try the Inhibitor Applet for your Gnome Panel. Right click panel and 'Add to'.

---

### Post by WetWired on 2009-01-30
I don't have a server layout section in my xorg. I'm on ibex, if that makes any difference.

---

### Post by Yashiro on 2009-01-30
Just create the bits you need.
> Section "ServerLayout"
 Option "BlankTime" "0"
 Option "StandbyTime" "0"
 Option "SuspendTime" "0"
 Option "OffTime" "0"
EndSection 

---

### Post by WetWired on 2009-01-31
I tried that, then I got a window that popped up saying Ubuntu is running in low graphics mode, and my screen resolution was all messed up.

---

### Post by Yashiro on 2009-01-31
By just pasting
> Section "ServerLayout"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection 

Interesting. Those are the correct calls.
Must be to do with the obsession to remove xorg.conf. Maybe it substitues it's values for the entire ServerLayout and doesn't just add them to it's own settings. Didn't expect that.

Disabling Screensaver from the screensaver panel works anyway, though. Well it does here.

---

