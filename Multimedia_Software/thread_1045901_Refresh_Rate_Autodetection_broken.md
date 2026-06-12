---
title: "Refresh Rate Autodetection broken"
date: 2009-01-20
forum: Multimedia Software
---

### Post by floborg on 2009-01-20
After changing my Gnome icon theme, logging out, and then logging back in, my screen resolution changed.  When I went to change it back using the System => Preferences => Screen Resolution tool, my previous refresh rate was not listed.  All that is listed now is 60 Hz.

My /etc/X11/xorg.conf doesn't show any specific hardware like I would expect (graphics card, monitor type).  This is it:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

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
EndSection
```

That's not even the keyboard model I selected (104-key).

I normally have 800x600 with a couple of different refresh rates listed in the Screen Resolution tool.  That's how I selected 800x600 with an 85 Hz refresh rate initially.  I never manually edited any config files.

[COLOR="Blue"]What broke the autodetection of available display modes?  How can this autodetection be restored?[/COLOR]  If it worked before, I'd like to get it back to normal rather than editing my files.

I'm running 8.04 on a Dell 530 N with Intel graphics and an old Compaq CRT.

---

### Post by floborg on 2009-01-21
OK, this is weird.  Everything is back to normal, as far as I can tell.  Here's what happened.

Booted the live Hardy CD and ran into the same problem.
Booted a Puppy 3.01 live CD and it's xorg wizard didn't seem to ID my monitor.

I did the above last night.  Today, I again booted the Hardy LiveCD and again hit the problem.  I spent some time experimenting with xrandr and adding h/v rates to my xorg to see if I could work around the problem.  Of course, the workarounds could get me a decent display mode for the live environment.

It hit me that since neither LiveCD could find my monitor that maybe it wasn't communicating it's modes properly or that my machine wasn't retrieving them.  Anyway, I disconnected my monitor's video and power cables and then reattached the cables.  I booted into the Live Puppy and the wizard gave me my familiar video modes right away.  Soooo, I booted my Hardy install off my hard drive and, presto, everything was as it should be.  Even the login screen (at a different res) looked like it did before, though not my preferred res.

What the heck!  Is my monitor dying?  Is there any way this is software-related?

---

### Post by floborg on 2009-02-19
Ok, it happened again...after a CTRL-ALT-BACKSPACE in Ubuntu.  I'm thinking this is not a hardware issue now.  Ow, my eyes!

---

### Post by floborg on 2009-02-20
...and the same fix worked - unplugging the monitor.

So, two things are clear:
1. My monitor has some sort of persistent memory and
2. Ubuntu does something to it when dropping out of X

I never had this happen with Puppy, and I dropped out of X all the time.  Of course, their version of Xorg is one release older than that used in Hardy.

---

### Post by floborg on 2009-04-13
2-month bump

Though running off a LiveUSB (and LiveHD), I didn't seem to have this problem with the Jaunty 9.04 beta.

---

